이프 오픈소스를 여행하는 히치하이커를 위한 안내서
=================
*아래 설명은 코딩을 대충 아시는 분들을 기준으로 구성되어 있습니다.*


## 개발 환경
* 개발 언어 : Python
* 디스코드 API 라이브러리 : Pycord 2.0.0b
* 데이터베이스 : PostgreSQL, SQLite(Read-Only), Json(Read-Only)


## 이프 오픈소스 세팅
### 1. 가져오기
1. [여기](https://github.com/KimuSoft/Epbot-Origin/)의 우측 상단의 포크(Fork) 버튼을 눌러 이 레포지토리를 복사할 수 있습니다.
2. 포크한 레포지토리를 개발할 컴퓨터에 클론합니다. (CLONE URL: `https://github.com/KimuSoft/Epbot-Origin.git`)
    * Visual Studio Code: 레포지토리 URL을 입력합니다. (깃허브 계정 연동이 되어 있다면, 자신의 레포지토리 목록에서 포크한 이프 오픈소스 레포지토리를 선택합니다.)
    * Pycharm: 메인 화면 → Get From VCS -> 레포지토리 URL 입력 -> 클론(Clone)
    * IDE를 사용하지 않는 경우(Windows): 이프 오픈소스를 세팅할 폴더에서 CMD를 연 후 `git clone https://github.com/KimuSoft/Epbot-Origin.git` (Git이 깔려 있어야 함)
    * 그 외 터미널: `git clone https://github.com/KimuSoft/Epbot-Origin.git <경로>`

## 2. 파이썬 및 라이브러리 세팅
```Pycharm 등 몇몇 IDE는 클론한 이후 프로젝트를 실행하면 바로 가상환경 세팅을 물어봅니다. 'Yes'만 누르면 다 알아서 해 줄 테니 이 부분을 패스하셔도 됩니다.```
1. 파이썬이 설치되어 있지 않다면 최신 버전의 파이썬을 설치합니다.
2. (가상환경을 사용할 경우) 프로젝트 폴더에서 `python -m venv venv`로 이 프로젝트 전용 가상환경을 만듭니다.
3. (가상환경을 사용할 경우) 프로젝트 폴더에서 `.\venv\Scripts\activate.bat` (Windows 기준)를 하면, 입력창 앞부분에 (venv)가 붙습니다. 이렇게 됐다면 가상환경이 올바로 활성화된 것입니다. 이후 다시 프로젝트를 열었을 때 입력창 앞에 (venv)가 없다면 다시 이 방법을 사용해야 합니다.
    * 대부분의 IDE는 가상환경이 있다면 자동으로 연결해 주니 걱정하지 않으셔도 됩니다.
4. 프로젝트 폴더에서 `pip install -r requirements.txt`를 입력하여 필요한 라이브러리를 설치합니다.

## 3. 데이터베이스 세팅
이프를 실행하기 위해서는 유저 정보, 낚시터 정보 등의 정보가 저장될 데이터베이스를 세팅해 주어야 합니다.

### 도커를 사용할 경우
1. 도커가 없을 경우 도커를 설치합니다.
2. 프로젝트 폴더에서 `docker compose up -d`를 입력하면 자동으로 데이터베이스가 세팅됩니다.

### 수동으로 세팅하는 경우
1. PostgreSQL을 설치합니다. (DB 툴은 pgAdmin을 추천합니다.)
2. 새 데이터베이스를 만든 후, `setup.sql`파일이나 DB 예시 이미지를 참고로 하여 똑같이 만들어 봅니다.
3. 파이팅


### 4. 이프 설정 세팅
1. `config.py.example`를 복사한 후 복사한 파일의 이름을 `config.py`로 바꿉니다. 이는 이프의 설정 파일입니다.
2. 아래 주의사항을 참고하여 config.py를 작성합니다.
    - 봇 토큰, 데이터베이스 관련 항목을 입력하지 않을 경우 이프가 정상적으로 작동하지 않습니다.
        - 단, Docker를 사용하여 DB 세팅을 하셨다면 DB 관련 항목은 기본값으로 두셔도 됩니다. 
    - `ERROR_LOGGING_CHANNEL`은 이프에 오류가 발생했을 시 메시지를 띄울 채널 ID를 적으시면 됩니다. 물론 이프에게 메시지 쓰기 권한이 있는 채널이어야 합니다.
    - `ANNOUNCE_CHANNEL`은 이프 뉴스(일일 랭킹)를 띄울 채널 ID를 적으시면 됩니다. 물론 이프에게 메시지 쓰기 권한이 있는 채널이어야 합니다.
    - `ADMIN_COMMAND_GUILD`에는 이프의 슬래시 커맨드중 관리자용 명령어를 사용할 수 있는 서버의 ID를 적으시면 됩니다.
    -   `config.py`의 `debug` 옵션을 `True`로 설정할 경우에는 디버그 모드로 실행됩니다. 디버그 모드에서는 더욱 상세한 로그를 띄울 수 있습니다.
    -   `debug`를 켰을 때는 `DEBUG_TOKEN`을 통해 봇이 켜집니다.

### 5. 낚시카드 서버 세팅하기
```낚시카드 서버가 없을 경우 이프 내부의 레거시 코드를 통해 낚시카드를 생성합니다.```
* 낚시카드 서버
    * [pikokr/ep-image-generator](https://github.com/pikokr/ep-image-generator) : 낚시카드 서버(Read-Only)
    * [Kimu-Nowchira/ep-image-generator](https://github.com/Kimu-Nowchira/ep-image-generator) : 키뮤가 포크한 낚시카드 서버 (권장, 최신 낚시카드 테마 포함)

* 낚시카드 제작기
    * 낚시카드 제작기로 등급 별로 낚시카드를 만든 후 json으로 다운받은 후 낚시카드 서버에 `skins/테마명/등급번호.json`로 저장하시면 적용됩니다.
    * 그리고 이프의 `Constants.py`의 `THEMES` 딕셔너리에 테마 데이터를 추가하면 `/테마` 명령어를 통해 해당 테마로 설정할 수 있게 됩니다.
    * `Constants.py`에 테마를 등록하지 않아도 `/미리보기 <테마명> <등급번호: 0~5>` 명령어를 통해 해당 테마를 테스트해볼 수 있습니다.
    * [pikokr/fishcard-editor](https://github.com/pikokr/fishcard-editor) : 낚시카드 제작기(Read-Only)

### 6. 이프 실행하기
1. 구동할 때는 main.py를 실행하시면 됩니다. 프로젝트 폴더에서 `python main.py` (Windows일 경우 `run.bat` 파일을 실행하셔도 됩니다.)


## 코드 기여
* 풀 리퀘스트를 날려주시면 관리자가 검토한 후 코드를 리뷰해드립니다. 통과될 경우 이프 오픈소스에 적용됩니다.

## 주의 및 안내사항
-   운영 중인 이프봇에 대한 기여만을 상정한 레포지토리로 이를 이용해 이프 사설 서버를 만들어 운영하는 것은 허용하지 않습니다.
-   PR을 통해 기여해 주시면 관리자가 검토를 거쳐 이프에 추가하는 구조입니다.
