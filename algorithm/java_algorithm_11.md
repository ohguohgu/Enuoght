# 💻 자바 알고리즘 - 원하는 문자열 찾기

<h3>📕 문제 설명</h3>

알파벳으로 이루어진 문자열 myString과 pat이 주어집니다. myString의 연속된 부분 문자열 중 pat이 존재하면 1을 그렇지 않으면 0을 return 하는 solution 함수를 완성해 주세요.

단, 알파벳 대문자와 소문자는 구분하지 않습니다.
<br>

<h3>📕 제한 사항</h3>

- 1 ≤ myString의 길이 ≤ 100,000
- 1 ≤ pat의 길이 ≤ 300
- myString과 pat은 모두 알파벳으로 이루어진 문자열입니다.

<br>

<h3>📕 답안</h3>

```java
class Solution {
    public int solution(String myString, String pat) {
        if(pat.length() > myString.length() ) {
            return 0;
        }

        return myString.toLowerCase().contains(pat.toLowerCase())? 1:0;
    }
}
```
문자열에 특정 문자열이 포함 되어 있는지 `true`, `false`로 확인할 수 있는 `contains()`을 이용하면 쉽게 풀 수 있는데 이 때 대/소문자는 구분하지 않는다는 조건이 있기 때문에 모두 소문자로 변경하여 체크했다. 이 때 대문자로 바꿔도 상관 없다.

근데 테스트 케이스에서 실패한 문제가 있어서 살펴보니 myString이 pat보다 길이가 작은 경우, 예를 들어 myString이 'aaaa'이고 pat이 'aaaaa'이면 contains은 이를 true로 판별한다.   
<b>그렇기 때문에 myString의 길이가 pat보다 작은 경우는 문자열을 포함하지 않는걸로 보고 0을 리턴한다.</b>

<br>
<h3>📕 참고</h3>

- `문자열.length()` : 문자열 길이 값 리턴
- `문자열.toLowerCase()` : 문자열을 모두 소문자로 변환
- `문자열.contains(포함문자열)` : 포함 문자열이 기준 문자열에 포함되어 있는지 확인하여 포함되어 있다면 true, 아니라면 false를 리턴



