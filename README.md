# autobot_ai
![image](https://github.com/user-attachments/assets/6e015aef-1250-4ccc-ab6e-562a22b51f9f)
## 🐝 Bumblebee: AI 이미지 설명 및 대화 프로젝트

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<img src="https://img.shields.io/badge/Python-3.7+-blue.svg" alt="Python Version"> <img src="https://img.shields.io/badge/FastAPI-0.95.0+-green.svg" alt="FastAPI Version"> <img src="https://img.shields.io/badge/httpx-0.24.0+-red" alt="Httpx Version">

### ✨ 프로젝트 소개

Bumblebee는 **Ollama**, **FastAPI**, **Edge-TTS/Web Speech API**, 그리고 최신 웹 기술들을 활용하여 만든 **AI 기반 이미지 설명 및 대화** 프로젝트입니다.  웹캠 이미지를 분석하여 설명을 생성하고, 사용자와 텍스트 또는 음성으로 상호작용할 수 있습니다.

### 🚀 주요 기능

*   **이미지 설명:**
    *   웹캠을 통해 실시간으로 이미지를 캡처합니다.
    *   캡처된 이미지를 Ollama (Gemma 모델)에게 전달하여 설명을 생성합니다.
    *   생성된 설명을 텍스트와 음성(Edge-TTS 또는 브라우저 내장 TTS)으로 제공합니다.
*   **텍스트/음성 대화:**
    *   사용자는 텍스트 입력 또는 음성 입력(Web Speech API)을 통해 프롬프트를 입력할 수 있습니다.
    *   "범블비"라는 호출어를 사용하여 음성 명령을 시작할 수 있습니다.
      *  "범블비, 앞에 뭐가 있어?"라고 말하면, 현재 웹캠 이미지를 분석하여 상황을 설명합니다.
      *  "범블비" + 다른 텍스트 프롬프트를 입력하면, 해당 내용에 대한 응답 생성.
    *   Ollama (Gemma 모델)는 이전 대화 내용을 기억하고, 문맥에 맞는 응답을 생성합니다.
    *   응답은 텍스트와 음성(Edge-TTS 또는 브라우저 내장 TTS)으로 제공됩니다.
*   **실시간 스트리밍:** Ollama API와의 통신은 비동기 스트리밍 방식으로 처리되어, 응답 속도가 빠르고 사용자 경험이 향상됩니다.
*   **반응형 웹 디자인:**  다양한 기기(PC, 태블릿, 스마트폰)에서 최적화된 화면을 제공합니다.
*   **세련된 UI:** 최신 웹 디자인 트렌드를 반영하여 깔끔하고 직관적인 사용자 인터페이스를 제공합니다.

### 🛠️ 기술 스택

*   **Ollama (Gemma):** 이미지 설명 및 대화 생성을 위한 AI 모델. [https://ollama.com/](https://ollama.com/)
*   **FastAPI:** 빠르고 현대적인 Python 웹 프레임워크. [https://fastapi.tiangolo.com/](https://fastapi.tiangolo.com/)
*   **httpx:** 비동기 HTTP 클라이언트.
*   **Edge-TTS:** (선택 사항) Microsoft Edge의 TTS 엔진을 사용하여 고품질 음성 합성.  `pip install edge-tts`로 설치.
*  **Web Speech API** : (선택 사항, 기본) 브라우저 내장.
*   **HTML/CSS/JavaScript:** 웹 프론트엔드 개발.
*   **Python 3.7+:**  프로그래밍 언어.

### ⚙️ 설치 및 실행 방법

1.  **Ollama 설치 및 모델 다운로드:**
    *   [Ollama 공식 웹사이트](https://ollama.com/)에서 운영체제에 맞는 Ollama를 설치합니다.
    *   터미널(또는 명령 프롬프트)에서 다음 명령을 실행하여 `gemma3:4b` 모델을 다운로드합니다.  다른 모델을 원하면, 해당 모델 이름으로 변경하세요.
        ```bash
        ollama pull gemma3:4b
        ```

2.  **Python 환경 설정:**
    *   Python 3.7 이상이 설치되어 있는지 확인합니다.
    *   프로젝트 폴더를 생성하고, 해당 폴더로 이동합니다.
    *   가상 환경을 생성하고 활성화합니다 (선택 사항이지만 권장).
        ```bash
        python3 -m venv venv
        source venv/bin/activate  # Linux/macOS
        venv\Scripts\activate  # Windows
        ```

3.  **필수 패키지 설치:**
    ```bash
    pip install fastapi uvicorn httpx edge-tts python-multipart
    ```    *   `python-multipart`는 파일 업로드(이미지) 처리에 필요.

4.  **코드 다운로드:**
    *   이 GitHub 저장소를 클론하거나, `main.py` (FastAPI 백엔드)와 `static/index.html` (프론트엔드) 파일을 다운로드하여 프로젝트 폴더에 넣습니다.
    *   `static` 폴더를 `main.py`와 같은 위치에 생성.

5.  **서버 실행:**
    ```bash
    uvicorn main:app --reload --host 0.0.0.0 --port 8000
    ```
   * `--reload`: 코드 변경 시 자동 재시작
   * `--host 0.0.0.0`: 외부 접근 허용 (선택 사항)
   * `--port 8000`: 사용할 포트 번호 (기본값: 8000)

6.  **웹 브라우저에서 접속:**
    *   웹 브라우저를 열고 `http://localhost:8000` (또는 지정한 포트 번호)로 접속합니다.
    *   웹캠 접근 권한을 허용합니다.

### 📝 사용 방법

1.  **이미지 설명:**
    *   웹 페이지가 로드되면 웹캠이 자동으로 시작됩니다.
    *   "Capture Image" 버튼을 클릭하여 현재 웹캠 이미지를 캡처합니다.
    *   기본 프롬프트("이 이미지를 설명해줘")가 자동으로 입력됩니다.  다른 프롬프트를 입력할 수도 있습니다.
    *   잠시 후, 이미지 설명이 텍스트로 표시되고, 음성으로도 출력됩니다.

2.  **텍스트 프롬프트:**
    *   "Enter prompt..." 텍스트 상자에 원하는 질문이나 명령을 입력합니다.
    *   "Submit Prompt" 버튼을 클릭하여 프롬프트를 서버로 전송합니다.
    *   Ollama 모델이 생성한 응답이 텍스트와 음성으로 제공됩니다.

3.  **음성 입력 (호출어 "범블비"):**
   * "Start Listening" 버튼을 클릭합니다.
   * "범블비"라고 말한 후, 명령어를 말합니다. 예) "범블비, 앞에 뭐가 있어?", "범블비, 오늘 날씨 어때?"
   * 음성 인식 결과를 바탕으로, 적절한 동작(이미지 캡처 및 설명, 텍스트 응답)이 수행됩니다.

### 📁 폴더 구조
```
bumblebee_project/
├── main.py       # FastAPI 백엔드 코드
└── static/
    └── index.html  # 프론트엔드 (HTML, CSS, JavaScript)
```

### 🤝 기여

프로젝트 개선에 기여하고 싶으신 분들은 언제든지 Pull Request를 보내주세요!

### 📄 라이선스

이 프로젝트는 MIT 라이선스에 따라 배포됩니다. 자세한 내용은 `LICENSE` 파일을 참조하세요.
