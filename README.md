# HearGuide: 디지털 소외계층을 위한 AI 음성 사서
"복잡한 키오스크 대신, 말 한마디로 도서관의 모든 정보를 찾다."

HearGuide는 음성 인식(STT)과 LLM(Gemini)의 Text-to-SQL 기술을 결합하여, 어르신과 어린이 같은 디지털 취약계층이 자연어 발화만으로 도서 추천, 서가 위치, 강연 정보를 쉽게 얻을 수 있도록 돕는 스마트 도서관 어시스턴트입니다.


## 핵심 기능 (Key Features)
다차원 복합 필터링 도서 추천
사용자의 연령, 성별, 관심 주제를 AI가 분석하여 실제 대출 통계 기반 인기도서를 추천합니다.
예: "초등학생 남자애가 좋아할 만한 과학 책 알려줘"


자연어 기반 서가 위치 안내
도서관의 KDC(한국십진분류법) 체계를 이해하지 못해도, 책 이름만 말하면 해당 도서가 위치한 서가 번호를 즉시 안내합니다.

AI Vision 기반 강연 정보 추출
이미지 포스터로만 제공되어 검색이 어려운 도서관 강연 정보를 Gemini Vision으로 분석 및 정형화하여, 상세한 일정과 대상별 조회가 가능합니다.

안정적인 데이터 파이프라인 (Caching)
외부 API의 트래픽 제한(Rate Limit) 문제를 해결하기 위해 로컬 MySQL DB 적재 및 캐싱 아키텍처를 구축, 1.5초 이내의 빠른 응답 속도를 보장합니다.


## 기술 스택 (Tech Stack)
Frontend: Streamlit

AI & NLP: Gemini 2.5 Flash (Text-to-SQL, Vision), OpenAI Whisper (STT), gTTS (TTS)

Backend: Python, SQLAlchemy, Selenium (Crawling)

Database: MySQL

Data Analysis: Pandas, NumPy, Openpyxl

### 시작하기 (How to Run)
1. 필수 라이브러리 설치
이 프로젝트는 Python 3.9+ 환경에서 최적화되었습니다. 아래 명령어를 통해 필요한 라이브러리를 설치하세요.

```bash
pip install streamlit streamlit-autorefresh pandas numpy sounddevice torch wavio requests gTTS transformers sqlalchemy pymysql google-generativeai selenium openpyxl

2. 데이터 파일 준비
mapo_library_data_CLEANED_FINAL_CONDITIONAL.xlsx 파일을 프로젝트 루트 폴더에 다운로드합니다.

코드 내 update_library_loans() 함수에서 파일 경로를 확인하세요.

3. API 키 및 DB 설정
보안을 위해 실제 키 값은 코드에 직접 입력하지 않고 secrets.toml 파일로 관리하는 것을 권장합니다. 프로젝트 폴더 내에 .streamlit/secrets.toml 파일을 생성하세요.
