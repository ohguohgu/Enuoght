# 💻 자바 알고리즘 - 뒤에서 5등까지

<h3>📕 문제 설명</h3>

정수로 이루어진 리스트 `num_list`가 주어집니다. `num_list`에서 가장 작은 5개의 수를 오름차순으로 담은 리스트를 return하도록 solution 함수를 완성해주세요.
<br>

<h3>📕 제한 사항</h3>

- 6 ≤ `num_list`의 길이 ≤ 30
- 1 ≤ `num_list`의 원소 ≤ 100

<br>

<h3>📕 답안</h3>

```java
import java.util.*;
class Solution {
  public int[] solution(int[] num_list) {
    Arrays.sort(num_list);

    int[]answer = new int[5];
    for(int i=0; i<answer.length; i++) {
      answer[i] = num_list[i];
    }

    return answer;
  }
}
```
`Arrays.sort()`를 통해 배열을 오른차순으로 정렬한다. 그리고 return 해줄 길이 5의 answer 배열을 만들어 for문을 돌면서 answer에 원소를 넣어준다.  
하지만 이렇게 풀지 않아도 정렬한 배열을 그대로 복사해가면 되는 방법도 있다.

<h3>📕 개선 답안</h3>
```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] num_list) {
        Arrays.sort(num_list);

        return Arrays.copyOfRange(num_list, 0, 5);
    }
}
```
`Arrays.sort()`를 통해 정렬하는 것은 동일하지만, `Arrays.copyOfRange()`를 이용해서 정렬된 배열을 복사하여 리턴한다.

<br>
<h3>📕 참고</h3>

- `Arrays.sort(배열)` : 배열을 오른차순으로 변환
- `Arrays.copyOfRange(배열, 첫번째 인덱스, 마지막인덱스)` : 지정한 첫번째, 마지막 인덱스를 기준으로 배열 복사




