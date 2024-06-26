## 아이디어를 코드로 바꾸는 구현
- 코딩테스트에서 구현이란 '머릿속에 있는 알고리즘을 소스코드로 바꾸는 과정'이다.
- 구현 문제 유형은 모든 범위의 코딩 테스트 문제 유형을 포함하는 개념이다.
- 프로그래밍 언어의 문법을 정확히 알고 있어야 한다.
- 구현 유형의 예시
  - 알고리즘은 간단한데 코드가 지나칠 만큼 길어지는 문제
  - 실수 연산을 다루고, 특정 소수점 자리까지 출력해야 하는 문제
  - 문자열을 특정한 기준에 따라서 끊어 처리해야 하는 문제
    - 문자열이 입력으로 주어졌을 때 한 문자 단위로 끊어서 리스트에 넣어야 하는 문제
    - (문자열 처리의 경우 파이썬이 다른 언어에 비해서 상대적으로 사용하기에 편하다.)
  - 적절한 라이브러리를 찾아서 사용해야 하는 문제
- 구현 대표 유형
  - 완전 탐색: 모든 경우의 수를 주저 없이 다 계산
  - 시뮬레이션: 문제에서 제시한 알고리즘을 한 단계씩 차례대로 직접 수행

- 파이썬에서 리스트의 크기
  - 파이썬에서 리스트를 이용할 때에 고려해야 할 사항은 코딩 테스트의 메모리 제한이다.
  - 파이썬에서 정수 데이터를 다룰 때
    - 데이터의 개수가 1,000개면 약 4KB
    - 데이터의 개수가 1,000,000개면 약 4MB
    - 데이터의 개수가 10,000,000개면 약 40MB

### 문제 - 상하좌우
- 문제 분석
  - N X N 크기의 정사각형 공간
  - 가장 왼쪽 위 좌표는 (1, 1) - 여기서 시작
  - 가장 오른쪽 아래 좌표는 (N, N)
  - 상 U, 하 D, 좌 L, 우 R로 이동할 수 있다.
  - 입력
    - N
    - 이동할 계획서
  - 출력
    - 최종적으로 도착할 좌표의 지점 (X, Y)
- 문제 해설
  - 이동 횟수가 N번인 경우 시간 복잡도는 O(N)이다.

### 문제 - 시각
- 문제 설명
  - 정수 N이 입력되면 00시 00분 00초부터 N시 59분 59초까지 모든 시각 중에서 3이 하나라도 포함되는 모든 경우의 수
  - 입력
    - 정수 N
  - 출력
    - 3이 하나라도 포함되는 모든 경우의 수
- 문제 해설
  - 모든 시각의 경우를 하나씩 모두 세서 쉽게 풀 수 있는 문제다.
  - 완전 탐색 유형이다.
    - 데이터 개수가 큰 경우 정상적으로 동작하지 않을 수 있다.
    - 데이터의 개수가 100만개 이하일 때 적절하다.

### 문제 - 왕실의 나이트
- 문제 설명
  - 체스판 8 X 8
  - 특정한 한 칸에 나이트가 서있다.
  - 나이트는 L자 형태로만 이동할 수 있다.
    - 수평 2칸 수직 1칸
    - 수직 2칸 수평 1칸
  - 입력
    - 나이트가 위치한 곳의 좌표
      - a1
  - 출력
    - 나이트가 이동할 수 있는 경우의 수
- 문제 해설
  - 나이트가 이동할 수 있는 8가지 방향을 정의한다.
    - move = [(-2, -1), (-2, +1), (+2, -1), (+2, +1), (-1, -2), (-1, +2), (+1, -2), (+1, +2)]
  
### 문제 - 게임 개발
- 문제 설명
  - N X M 크기의 직사각형
  - 각각의 칸은 육지 또는 바다
  - 맵의 각 칸은 (A, B)
    - A는 북쪽으로부터 떨어진 칸의 개수 - 행
    - B는 서쪽으로부터 떨어진 칸의 개수 - 열
  - 상하좌우로 움직일 수 있고, 바다에는 갈 수 없다.
    - 1 현재 방향을 기준으로 왼쪽부터 반시계 방향으로 차례대로 갈 곳을 정한다.
    - 2 바로 왼쪽 칸이 가보지 않았다면 회전 후 전진한다. 가봤다면 회전만 하고 1단계로 돌아간다.
    - 3 네 방향 모두 가본 칸이거나 바다라면, 바라보는 방향을 유지한 채 한 칸 뒤로 가고 1단계로 돌아간다.
      - 한 칸 뒤가 바다라면 움직임을 멈춘다.
  - 입력
    - 맵의 세로크기 N, 가로크기 M
    - (A, B) d
      - 0 북
      - 1 동
      - 2 남
      - 3 서
    - 육지 0, 바다 1 정보
  - 출력
    - 캐릭터가 방문한 칸의 수
- 문제 해설
  - 전형적인 시뮬레이션 문제
  - 일반적으로 방향을 설정해서 이동하는 문제 유형에서는 dx, dy라는 별도의 리스트를 만들어 방향을 정하는 것이 효과적이다.
  - 이차원 리스트 초기화
    - 리스트 컴프리헨션 이용
    - `d = [[0] * m for _ in range(n)]`