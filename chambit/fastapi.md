# LECTURERECOMMENDATION

- api-test
  - fastAPI_chatbot
  - node/react-test
    - node_modules
    - public
    - src
      - Lecture
      - ListedLecture
      - MainPage
      - MyPage
      - trash-bin
      - User
      - App.css
      - App.js
      - App.test.js
      - chat.js
      - chatbot.js
      - index.css
      - index.js
      - Login.js
      - logo.svg
      - reportWebVitals.js
      - setupTests.js
    - .gitignore
    - package-lock.json
    - package.json
    - README.md
- server
  - __pycache__
  - router
    - __pycache__
    - auth.py
    - chat.py
    - creditList.py
    - lecture.py
    - ocr.py
    - user.py
    - userInfo.py
  - .env
  - db.py
  - kwu-lecture-database-v6-<somehash>.db
  - kwu-lecture-database-v6.db
  - main.py
  - model.py
- test
  - structure.md
- crawling
- data_preprocessing
- env
- note
- .gitignore
- README.md
- requirements.txt


### 백엔드 (.py)
userInfo.py
creditList.py


### main.py 
from router import user, auth, ... (파일명.py)
...(생략)
app include router(user.router) -> import와 동일한 user

import user, auth, ... from router



### index.js
import class명 from 파일명.js (경로가 다르다면 상대경로 표시)
import Chat from "./chatbot"
from "./chatbot" import Chat


