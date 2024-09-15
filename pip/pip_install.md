모듈 설치했는데도 다음과 같은 에러가 뜰때,
ModuleNotFoundError: No module named 'pdfplumber'

1. pip 자체를 update 해보기
python -m pip install --upgrade pip

2. In 가상환경, 해당 가상환경 위치 안에 pip install을 했는지 확인
(env) D:\LectureRecommendationService> 이렇게 맨앞에 가상환경에 들어왔다하더라도

shift + ctrl + p 를 하여 .\env\Scripts\python.exe 파이썬이 실행되고 있는 위치를 파악하여

해당 D:\LectureRecommendationService\env\Scripts> 환경으로 들어와 'activate'까지 해주고

그 위에 모듈 설치하면 됨.