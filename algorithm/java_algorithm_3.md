# 약수 구하기

<h3>문제 설명</h3>

정수 `n`이 매개변수로 주어질 때, `n`의 약수를 오름차순으로 담은 배열을 return 하도록 solution 함수를 완성해주세요.

<br>

<h3>제한 사항</h3>

- 1 ≤ n ≤ 10,000

<br>

<h3>답안</h3>

```java
import java.util.*;

class Solution {
    public int[] solution(int n) {
        ArrayList<Integer> arr = new ArrayList<>();

        for(int i=1; i<=n; i++) {
            if(n%i==0) {
                arr.add(i);
            }
        }

        int[] answer = new int[arr.size()];

        for(int j=0; j<answer.length; j++) {
            answer[j] = arr.get(j);
        }

        return answer;
    }
}
```

for문을 돌면서 <b>i로 나눈 값이 0이 되는 인자(약수)</b>를 배열에 추가해야 되기 때문에 길이가 고정된 배열을 쓰기보다는  
`ArrayList`를 사용해서 인자를 다 넣은 후 배열로 바꿔주는 방식을 사용한다.  
이후 다시 한번 for문을 돌면서 배열에 `ArrayList` 인자를 넣어 리턴한다.

