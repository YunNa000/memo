### Python에서 파일 열고 읽기

1. open() 함수 사용
    - 'with'문
        - 파일을 사용한 후 자동으로 닫아줌
        - 리소스 관리를 위함_파일을 닫지않으면 시스템에 불필요한 부담을 줌
    
    - 파일읽기 관련 함수
        - read() : 파일 전체 내용을 문자열로 읽어옴
        ex)
        with open('filename.txt', 'r') as file:
            content = file.read()  # 파일의 모든 내용을 읽어옵니다.

        - readline() : 파일에서 한 줄씩 읽어옴
        ex)
        with open('filename.txt', 'r') as file:
            line = file.readline()  # 첫 번째 줄을 읽습니다.


        - readlines() : 파일의 모든 줄을 읽어서 리스트로 반환, 각 줄은 리스트의 한 요소로 저장
        ex)
        with open('filename.txt', 'r') as file:
            lines = file.readlines()  # 모든 줄을 리스트로 읽어옵니다.



    - 파일쓰기 관련 함수
        - write() : 파일에 문자열 쓰기
        ex)
        with open('filename.txt', 'w') as file:
            file.write('Hello, World!')  # 파일에 문자열을 씁니다.


        - writelines() : 리스트에 있는 여러줄의 문자열을 파일에 쓰기
        ex)
        lines = ['First line\n', 'Second line\n']
        with open('filename.txt', 'w') as file:
            file.writelines(lines)  # 여러 줄을 파일에 씁니다.

    - 파일 닫기 
        - close() : 파일을 명시적으로 닫음
            - with문을 사용하지 않을 때 파일을 닫아주는 데 사용
        ex) 
        file = open('filename.txt', 'r')
        content = file.read()
        file.close()  # 파일을 닫습니다.

 

    ex) with문 없이 파일 열기
    file = open('filename.txt', 'r')  # 파일을 읽기 모드로 엽니다.
    content = file.read()             # 파일 내용을 모두 읽어들입니다.
    file.close()                      # 파일을 닫습니다.

    ex) with문을 사용한 파일 열기
    with open('file.txt', 'r') as file:
        content = file.read()         # 파일 내용을 읽습니다.
    # 이 블록이 끝나면 파일은 자동으로 닫힙니다.

    - 파일 열기 모드의 종류
        - open() 함수를 사용하여 파일을 열 때, 파일을 열고 작업하는 방법을 지정하기 위해 다양한 모드 사용

            1. 읽기모드 ('r') : 파일을 읽기 전용으로 열기
                - 파일을 열어 그안에 있는 내용을 확인하거나 데이터 분석을 하고 싶을때
                - 파일 없으면 오류 발생
                - 파일의 내용에 수정이나 추가는 불가함
                ex) 텍스트파일에서 저장된 글을 불러오기
                    csv 파일에서 데이터를 읽어오기

            2. 쓰기모드 ('w') : 쓰기모드로 파일을 열면, 열릴때 기존의 모든 내용이 삭제되고 파일이 비어있는 상태가 됨
                - 파일에 데이터를 쓰기 위해 사용
                - 파일이 이미 존재하면 그파일의 기존 내용은 모두 지워지고 새로운 내용이 저장 
                - 파일이 없으면 새로 만듦
                ex) 새로운 데이터를 파일에 저장할 때
                    기존 파일의 내용을 완전히 덮어쓰고 싶을때
            -> write(), writelines()를 사용하여 새로운 내용을 파일의 시작부분부터 쓰게 됨

            3. 추가모드 ('a') : 기존 파일 내용이 삭제되지 않고 그대로 유지
                - 파일의 끝에 데이터를 추가하기 위해 사용
                - 파일이 없으면 새로 만듦
                ex) 로그 파일에 새로운 로그를 추가하거나 기존 문서의 끝에 새로운 내용을 추가할 때 사용
            -> write(), writelines()을 사용하면 새로운 내용이 파일의 끝에 추가

            4. 읽기 및 쓰기 모드 ('r+') : 읽기 쓰기 모두 가능
                - 기존의 내용을 유지하면서 원하는 위치에 내용을 추가하거나 덮어쓸 수 있음
                - 다만, 파일을 처음 열면, 파일 포인터는 파일의 맨앞에 위치하므로 write()를 사용하면 기존 내용을 덮어쓰게 됨 
                - 파일이 없으면 오류 발생
            -> seek 함수를 사용해서 원하는 위치에 내용 추가
            

        - 바이너리 모드 ('b') (바이너리 파일 : 컴퓨터가 직접이해할 수 있는 이진데이터로 저장된 파일 : 이미지, 동영상, 오디오, 실행파일, 압축파일)
            <-> 텍스트파일 (사람이 읽을 수 있는 문자로 구성된 파일)

            - rb : 읽기모드로 바이너리 파일 열기
            - wb : 쓰기모드로 바이너리 파일 열기
            - ab : 추가모드로 바이너리 파일 열기
            - r+b : 읽기 및 쓰기 모드로 바이너리 파일 열기


2. pandas 라이브러리를 사용한 파일 열기
    - with문을 사용하지 않아도 됨
    - csv 파일 읽기
        - df = pd.read_csv("filename.csv") # csv 파일을 읽어서 데이터프레임로 만들기
    - Excel 파일 읽기
        - df = pd.read_excel('filename.xlsx')  

    pd.read_csv("filename.csv",sep=',' or '\t', encoding="utf-8" -> default)
    - utf-8 : 유니코드 표준 인코딩 방식
    - cp949 : 한국어를 표현하기 위한 문자 인코딩 방식 (한자와 기타 몇몇 특수문자도 포함)
    - CP1252 : 서유럽 언어(예: 영어, 프랑스어, 독일어 등)를 표현