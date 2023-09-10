# 외계어 사전

<h3>📕 문제 설명</h3>

PROGRAMMERS-962 행성에 불시착한 우주비행사 머쓱이는 외계행성의 언어를 공부하려고 합니다. 알파벳이 담긴 배열 `spell`과 외계어 사전 `dic`이 매개변수로 주어집니다. `spell`에 담긴 알파벳을 한번씩만 모두 사용한 단어가 `dic`에 존재한다면 1, 존재하지 않는다면 2를 return하도록 solution 함수를 완성해주세요.

<br>

<h3>📕 제한 사항</h3>

- `spell`과 `dic`의 원소는 알파벳 소문자로만 이루어져있습니다.
- 2 ≤ `spell`의 크기 ≤ 10
- `spell`의 원소의 길이는 1입니다.
- 1 ≤ dic의 크기 ≤ 10
- 1 ≤ dic의 원소의 길이 ≤ 10
- spell의 원소를 모두 사용해 단어를 만들어야 합니다.
- spell의 원소를 모두 사용해 만들 수 있는 단어는 dic에 두 개 이상 존재하지 않습니다.
- dic과 spell 모두 중복된 원소를 갖지 않습니다.

<br>

<h3>📕 답안</h3>

```java
class Solution {
    public int solution(String[] spell, String[] dic) {
        int answer = 0;
        int idx = 0;
        for(String str : dic) {
            while(spell.length > idx) {
                if(!str.contains(spell[idx++])) {
                    answer = 2;
                    break;
                }
                answer = 1;
            }
            if(answer == 1) break;
        }
        return answer;
    }
}
```
`dic` 배열의 원소만큼 for문을 돌면서 `spell`에 있는 문자열이 포함되어 있는지 확인한다.  
하나라도 불포함 됐다면 `answer`에 `2`를 넣어주고 `break`를 통해 `while문`을 빠져나간다.  
불포함된게 하나라도 없다면 모두가 포함됐다는 의미이니 `answer`에 `1`을 넣어주고 answer가 1인 경우 break를 이용하여 for문을 빠져나간다.


<br>
<h3>📕 참고</h3>

- `배열.length` : 배열의 원소 길이(갯수)를 리턴 
- `문자열.contains(문자열B)` : 문자열에 문자열B가 포함되어 있는지 확인후 포함됐다면 true, 불포함이라면 false를 리턴




