## 이프 세팅 및 실행 방법(도커 사용)
1. 도커가 없을 경우 도커를 설치합니다.
2. `docker compose up -d`를 통해 데이터베이스를 셋업할 수 있습니다.
3. `config.py.example`의 이름을 `config.py`로 바꾼 후 아래를 참고하여 잘 적습니다. 도커로 DB를 세팅한 경우 DB 관련 기본값은 그대로 두셔도 됩니다.
4. 잘 실행해 봅니다.

## 이프 세팅 및 실행 방법(도커 미사용 시)

코딩을 대충 아시는 분들을 기준으로 설명해 두었습니다.
아래 방법과 상관없이 도커를 사용할 수 있는 분은 도커로 여시면 됩니다. 도커에 DB 세팅이 포함되어 있습니다.

### 파이썬 세팅
1. 파이썬이 설치되어 있어야 합니다. 파이참을 쓰신다면 걔가 알아서 다 할 겁니다.
2. requirements.txt의 요구사항을 설치합니다. `pip install -r requirements.txt` 파이참을 쓰신다면 역시 걔가 물어보는 것만 OK 하면 알아서 해 줄 겁니다.

### DB 세팅
3. postgreSQL을 설치합니다.
    - postgreSQL 데이터베이스 관리에는 pgAdmin 프로그램을 추천합니다.
4. 데이터베이스를 셋업합니다. sql 파일 대신 이미지를 드리겠습니다.

### 이프 세팅
6. `config.example.py`에서 `.example`을 떼어 `config.py` 파일을 만든 후, 안에 필요한 내용을 적습니다.
    - 봇 토큰, 데이터베이스 관련 항목을 입력하지 않을 경우 이프가 정상적으로 작동하지 않습니다.
    - `ERROR_LOGGING_CHANNEL`은 이프에 오류가 발생했을 시 메시지를 띄울 채널 ID를 적으시면 됩니다. 물론 이프에게 메시지 쓰기 권한이 있는 채널이어야 합니다.
    - `ANNOUNCE_CHANNEL`은 이프 뉴스(일일 랭킹)를 띄울 채널 ID를 적으시면 됩니다. 물론 이프에게 메시지 쓰기 권한이 있는 채널이어야 합니다.
    - 낚시카드 서버를 입력하지 않을 경우에는 내부에서 낚시카드를 직접 만드므로 적지 않으셔도 됩니다.
7. 구동할 때는 main.py를 실행하시면 됩니다. `python main.py` (Windows일 경우 `run.bat` 파일을 실행하셔도 됩니다.)

## 주의 및 안내사항

-   `config.py`의 `debug` 옵션을 `True`로 설정할 경우에는 디버그 모드로 실행됩니다. 디버그 모드에서는 더욱 상세한 로그를 띄울 수 있습니다.
-   `debug`를 켰을 때는 `DEBUG_TOKEN`을 통해 봇이 켜집니다.
-   운영 중인 이프봇에 대한 기여만을 상정한 레포지토리로 이를 이용해 이프 사설 서버를 만들어 운영하는 것은 허용하지 않습니다.
-   PR을 통해 기여해 주시면 관리자가 검토를 거쳐 이프에 추가하는 구조입니다.
