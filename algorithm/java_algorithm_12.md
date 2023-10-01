# 💻 자바 알고리즘 - 배열 만들기 2

<h3>📕 문제 설명</h3>

정수 l과 r이 주어졌을 때, l 이상 r이하의 정수 중에서 숫자 "0"과 "5"로만 이루어진 모든 정수를 오름차순으로 저장한 배열을 return 하는 solution 함수를 완성해 주세요.

만약 그러한 정수가 없다면, -1이 담긴 배열을 return 합니다.

<br>

<h3>📕 제한 사항</h3>

- 1 ≤ l ≤ r ≤ 1,000,000

<br>

<h3>📕 답안</h3>

```java
import java.util.*;
class Solution {
    public int[] solution(int l, int r) {
        List<Integer> arr = new ArrayList<>();
        for(int i=l; i<=r; i++) {
            String temp = String.valueOf(i);
            temp = temp.replace("0","");
            temp = temp.replace("5","");

            if(temp.length()==0) {
                arr.add(i);
            }
        }

        if(arr.size()<1) {
            int[] answer = new int[1];
            answer[0] = -1;
            return answer;
        } else {
            int[] answer = arr.stream()
                    .mapToInt(Integer::intValue)
                    .toArray();
            return answer;
        }


    }
}
```
이 문제를 해결하기 위해선 숫자가 0과 5로만 구성된 숫자인지 판별하는 것이다.

%와 /로 나눠도 판별이 나지 않아서 아예 0과 5를 공백으로 만든뒤

해당 문자열의 길이가 0일때, 즉 0과 5로만 구성되어 있을 때 배열에 추가해준다.

return 하기전 arrayList를 배열로 변경해야 되기 때문에 if, else문을 사용했는데

이렇게 하지 않더라도 더 간단하게 작성할 수 있다.

<br>
<h3>📕 개선 답안</h3>

```java
import java.util.*;
class Solution {
    public int[] solution(int l, int r) {
        List<Integer> arr = new ArrayList<>();
        for(int i=l; i<=r; i++) {
            String temp = String.valueOf(i);
            temp = temp.replace("0","");
            temp = temp.replace("5","");

            if(temp.length()==0) {
                arr.add(i);                
            }
        }

         return arr.isEmpty() ? new int[] { -1 } : arr.stream().mapToInt(i -> i).toArray();      
    }
}
```
`list`가 비어 있으면 `-1` 원소를 담은 배열을 만들어서 리턴하고, `list`가 비어있지 않다면 `arrayList`를 배열로 변환하여 리턴한다.

<br>
<h3>📕 참고</h3>

- `String.valueOf(숫자)` : 숫자를 문자열로 변경
- `문자열.replace("문자열A","문자열B")` : 문자열A를 문자열B로 변경
- `리스트.add(원소)` : 리스트에 원소 추가
- `리스트.isEmpty()` : 리스트가 비어있는지 체크하여 비어있으면 true, 비어있지 않다면 false를 리턴

