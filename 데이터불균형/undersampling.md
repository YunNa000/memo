Random undersampling

under sampling
강아지 80마리와 고양이 20마리 불균형이 있으니
majority 것을 줄이자 강아지를 줄이자

어떻게 줄일까?
-> 랜덤 언더샘플링이니까

임의의 것을 뽑아 줄이기 -> minority 의 개수만 큼 줄이기

랜덤으로 없애다보니, case ㅠㅛ case로 각 상황별 편차가 커짐
-> 이 방법은 좋은 방법이 아님

어떤 의사결정선을 기준으로 분류해야하나

Tomek links 

두 범주 사이를 탐색해보는 것

부정확한 분류 경계선을 방지

i는 major에서 뽑은것 j는 소수클래스에서 뽑으넛

undersampling -> sample eliminate의 과정

minority class의 샘플사이즈만 남기고 지워버리기



CNN rules (condensed nearest neighbor rule)
다수 범주의 데이터를 제거하는 규칙을 정의
소수 범주의 전체와 다수 범주에서 무작위로 하나의 관측치를 선택


멀리 떨어져있는 

데이터가 데이터공간내에서 어떻게 생겼나에 따라 완전히 다르기 때문에

One side selection (oss)
