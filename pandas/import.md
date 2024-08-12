### import : Python에서 모듈과 패키지를 가져오는 방법

1. import
- 다른 프로그램으로부터 데이터를 갖고 오는 것
- 다른 모듈에 있는 코드들에 대한 접근권을 얻음

    - 'import 모듈명' 
        - 모듈 전체를 가져옴 (모든 함수, 클래스, 변수에 접근)
        - 사용 시에는 항상 모듈 이름을 앞에 붙여서 사용
        ex) import math
            result = math.sqrt(16) # math 모듈 내의 sqrt 함수 사용

    - 'import 모듈명 as 별칭' : 모듈 이름이 길거나 자주사용될 때 유용
        ex) import pandas as pd
        
    - 'from 모듈명 import 특정_항목'
        - 모듈에서 특정함수나 클래스만 가져오고 싶을때
        - 모듈 이름을 붙일 필요가 없음
        ex) from math import sqrt
            result = sqrt(16)
        
    - 'from 모듈명 import 특정_항목 as 별칭
        ex) from math import sqrt as sqare_root
            result = sqare_root(16) 

    - 'from 모듈명 import *' : 권장되지않음, 여러모듈에서 같은 이름의 함수나 클래스가 있을 수 있기 때문
        - 모듈 내의 모든 항목을 가져옴


    ?) import 모듈명 vs from 모듈명 improt * 의 차이?!
        - import 모듈명에서는 모듈을 정의하고 함수나 클래스를 쓰기때문에 후자보다 ㅈ덜 위험함. 따라서 전자 방법을 더 선호


    +) 상대경로 임포트
        -   # 패키지 구조:
            # mypackage/
            # ├── __init__.py
            # ├── module_a.py
            # └── module_b.py

            # module_a.py 안에서
            from . import module_b  # 같은 패키지 내의 module_b를 가져옴

        - '.' (점하나) : 현재 디렉토리를 나타냄
            ex) from . import test : 현재 디렉토리에 있는 'test'를 가져옴
                from .test import some_function : 현재 디렉토리에 있는 'test'모듈에서 'some_function'을 가져옴
        
        - '..' (점두개) : 한단계 상위 디렉토리, 부모(상위) 디렉토리를 나타냄
            ex) from .. import test1 : 부모 디렉토리에 있는 test1을 가져옴
                from ..folder import test2 : 부모 디렉토리에 있는 folder안의 tets2 모듈을 가져옴

            ?) 가져오는 test는 모듈(파일)이거나 패키지(디렉토리)일 수 있음
                1. module로써 파일을 가져오는 경우
                    - test 내의 함수, 클래스, 변수를 test.some_function()과 같이 쓸 수 있음
                    ex) 
                    parent_directory/
                    ├── test.py
                    └── sub_directory/
                        └── current.py
                    
                    current.py에서 
                    from .. import test1  # 부모 디렉토리의 test1.py 파일을 가져옴
                    test1.some_function()  # test1 모듈 내의 함수 사용

                2. package로써 폴더를 가져오는 경우
                    - test라는 이름의 디렉토리
                    - test 디렉토리 내에 '__init__.py 파일이 있어야하며, 이 파일이 있으면 test를 패키지로 인식
                    ex)
                    parent_directory/
                    ├── test/
                    │   ├── __init__.py
                    │   └── module_a.py
                    └── sub_directory/
                        └── current.py
                    current.py 에서
                    from .. import test1  # 부모 디렉토리의 test1 패키지를 가져옴
                    test1.module_a.some_function()  # test1 패키지 내의 module_a 모듈 사용

        - '...' (점세개) : 부모의 부모 디렉토리(상위 디렉토리의 상위)를 나타냄
            ex) from ... import test3 : 부모의 부모 디렉토리에 있는 test3을 가져옴


