# 💻 자바 알고리즘 - 수 조작하기 2

<h3>📕 문제 설명</h3>

정수 배열 `numLog`가 주어집니다. 처음에 `numLog[0]`에서 부터 시작해 "w", "a", "s", "d"로 이루어진 문자열을 입력으로 받아 순서대로 다음과 같은 조작을 했다고 합시다.

- `w` : 수에 1을 더한다.
- `s` : 수에 1을 뺀다.
- `d` : 수에 10을 더한다.
- `a` : 수에 10을 뺀다.
그리고 매번 조작을 할 때마다 결괏값을 기록한 정수 배열이 numLog입니다. 즉, numLog[i]는 numLog[0]로부터 총 i번의 조작을 가한 결과가 저장되어 있습니다.

주어진 정수 배열 numLog에 대해 조작을 위해 입력받은 문자열을 return 하는 solution 함수를 완성해 주세요.
<br>

<h3>📕 제한 사항</h3>

- 2 ≤ `numLog`의 길이 ≤ 100,000
  - 100,000 ≤ `numLog[0]` ≤ 100,000
  - 1 ≤ i ≤ numLog의 길이인 모든 i에 대해 |numLog[i] - numLog[i - 1]|의 값은 1 또는 10입니다.

<br>

<h3>📕 답안</h3>

```java
class Solution {
    public String solution(int[] numLog) {
        String answer = "";
        int startNum = numLog[0];
        for(int i=1; i<numLog.length; i++) {
            switch(numLog[i]-startNum) {
                case 1:
                    answer+="w";
                    break;
                case -1:
                    answer+="s";
                    break;
                case 10:
                    answer+="d";
                    break;
                case -10:
                    answer+="a";
                    break;
            }
            startNum = numLog[i];
        }
        return answer;
    }
}
```

첫번째 숫자는 시작하는 기준 숫자고 그 다음 원소부터가 움직인 결과값이 된다. 그렇기 때문에 `startNum`이라는 변수에 `numLog[0]`을 담고 그 다음원소를 빼준 값을 기준으로 1,-1,10,-10일 경우 `answer`에 그에 맞는 문자열을 붙여주는 식으로 풀면된다.


<br>
<h3>📕 참고</h3>
 
- `배열.length` : 배열의 길이를 반환




