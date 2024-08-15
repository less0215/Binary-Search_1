# 이분탐색1 (예산 분배 알고리즘 Q&A)
- 백준(BOJ) 2512번 문제

## 입력 및 변수

**Q: `requests = list(map(int, input().split()))` 이 코드가 작동하는 원리는 무엇인가요?**

A: 이 코드는 사용자로부터 공백으로 구분된 여러 숫자를 입력받아 정수 리스트로 변환합니다. 작동 원리는 다음과 같습니다:

1. `input()`: 사용자로부터 한 줄의 입력을 문자열로 받습니다.
2. `.split()`: 입력받은 문자열을 공백을 기준으로 나눠 문자열 리스트로 만듭니다.
3. `map(int, ...)`: 리스트의 각 문자열 요소를 정수로 변환합니다.
4. `list(...)`: map 객체를 리스트로 변환합니다.

**Q: 왜 입력을 3번만 받나요? 6번 받아야 하지 않나요?**

A: 이 코드는 효율성을 위해 요청 금액들을 한 번에 입력받도록 설계되었습니다. 실제 입력은 다음과 같이 이루어집니다:

1. 첫 번째 입력: 지방의 수 (n)
2. 두 번째 입력: 모든 지방의 요청 금액 (한 줄에 공백으로 구분)
3. 세 번째 입력: 총 예산 (budget)

이 방식은 입력의 효율성을 높이고 코드를 간결하게 만듭니다.

## 함수 및 알고리즘

**Q: `calculate_needed_budget` 함수의 목적은 무엇인가요?**

A: 이 함수는 "각 지방이 요청한 금액에 대해, 일정 상한선(upper_bound)을 적용했을 때 필요한 총 예산을 계산하는 함수"입니다. 주요 특징:

- 상한선 적용: 모든 요청을 그대로 수용하는 것이 아니라, 상한선을 넘는 요청은 제한합니다.
- 총 예산 계산: 각 지방별로 계산된 금액을 모두 합산하여 총 예산을 구합니다.
- 함수의 역할: 특정 상한선을 적용했을 때의 시나리오를 계산합니다.

**Q: `good_upper_bound = -1`은 무슨 의미인가요?**

A: 이는 변수를 초기화하는 과정입니다:

- -1은 '아직 적절한 값을 찾지 못했다'는 것을 나타내는 특별한 값입니다.
- 예산은 항상 0 이상이므로, -1은 실제 상한액으로 나올 수 없는 값입니다.
- 알고리즘이 진행되면서, 조건을 만족하는 상한액을 찾으면 이 변수를 업데이트합니다.

**Q: `answer = max(answer, given)`에서 왜 `answer`를 인자로 넣나요?**

A: 이 코드는 모든 요청에 대해 실제로 지원되는 금액 중 가장 큰 값을 찾는 것입니다:

- `answer`는 지금까지 본 값들 중 가장 큰 값을 유지합니다.
- `given`은 현재 요청에 대해 실제로 지원되는 금액입니다.
- 이 방식으로 모든 요청을 순회하면서 최대값을 효율적으로 찾을 수 있습니다.
- 이는 '진행하면서 최대값 유지하기'라는 일반적인 알고리즘 패턴입니다.

이 Q&A는 예산 분배 알고리즘의 주요 개념과 코드 구조를 이해하는 데 도움이 될 것입니다.