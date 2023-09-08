# 컨트롤 제트

<h3>문제 설명</h3>

숫자와 "Z"가 공백으로 구분되어 담긴 문자열이 주어집니다. 문자열에 있는 숫자를 차례대로 더하려고 합니다. 이 때 "Z"가 나오면 <B>바로 전에 더했던 숫자를 뺀다는 뜻</b>입니다. 숫자와 "Z"로 이루어진 문자열 `s`가 주어질 때, 머쓱이가 구한 값을 return 하도록 solution 함수를 완성해보세요.

<br>

<h3>제한 사항</h3>

- 1 ≤ s의 길이 ≤ 200
- -1,000 < s의 원소 중 숫자 < 1,000
- s는 숫자, "Z", 공백으로 이루어져 있습니다.
- s에 있는 숫자와 "Z"는 서로 공백으로 구분됩니다.
- 연속된 공백은 주어지지 않습니다.
- 0을 제외하고는 0으로 시작하는 숫자는 없습니다.
- s는 "Z"로 시작하지 않습니다.
- s의 시작과 끝에는 공백이 없습니다.
- "Z"가 연속해서 나오는 경우는 없습니다.

<br>

<h3>답안</h3>

```java
import java.util.*;

class Solution {
    public int solution(String s) {
        String[] arr = s.split(" ");
        int answer = 0;
        int temp = 0;
        
        for(int i=0; i<arr.length; i++) {
            if(arr[i].equals("Z")) {
                answer -= temp;
            }
            else {
                answer += Integer.parseInt(arr[i]);
                temp = Integer.parseInt(arr[i]);
            }
        }
        return answer;
    }
}
```
입력된 문자열은 공백으로 구분하여 인자를 나눌 수 있기 때문에 `split()`함수를 이용해서 `String` 배열로 만든다.  
그리고 for문을 돌면서 `arr`의 인자가 `Z`와 동일할 경우 `answer`에 `temp` 값을 빼주고, 동일하지 않은 경우 즉 숫자인 경우  
`answer`에 인자를 더해주고 숫자를 `temp`에 담는다.


<br>
<h3>참고</h3>

- `기준 문자열.split(구분자)` : 기준 문자열을 구분자를 통해 구분해서 배열로 리턴, 구분자가 없는 경우 한글자씩 떼서 배열로 리턴
- `문자열.equals(문자열)` : 문자열끼리 내용 비교, 일치하면 true 불일치시 false 리턴
- `Integer.parseInt()` : 문자열을 int형으로 바꿔주는 함수




