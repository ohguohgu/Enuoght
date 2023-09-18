# 💻 자바 알고리즘 - 이어 붙인 수 

<h3>📕 문제 설명</h3>

정수가 담긴 리스트 num_list가 주어집니다. num_list의 홀수만 순서대로 이어 붙인 수와 짝수만 순서대로 이어 붙인 수의 합을 return하도록 solution 함수를 완성해주세요.
<br>

<h3>📕 제한 사항</h3>

- 2 ≤ num_list의 길이 ≤ 10
- 1 ≤ num_list의 원소 ≤ 9
- num_list에는 적어도 한 개씩의 짝수와 홀수가 있습니다.

<br>

<h3>📕 답안</h3>

```java
class Solution {
    public int solution(int[] num_list) {
        int answer = 0;
        String even = "";
        String odd = "";

        for(int i=0; i<num_list.length; i ++) {
            if(num_list[i]%2==0) {
                even += String.valueOf(num_list[i]);
            }
            else {
                odd += String.valueOf(num_list[i]);
            }
        }

        return Integer.valueOf(even) + Integer.valueOf(odd);
    }
}
```

num_list의 모든 원소를 돌면서 원소가 짝수일 땐 even 변수에 원소를 문자열로 형변환하여 붙여주고, 홀수일 땐 odd에 원소를 문자열로 형변환하여 붙여준다. 그리고 두 문자열을 Integer.parseInt() 함수를 통해 숫자 타입으로 형변환하여 더한 값을 리턴한다.


<br>
<h3>📕 참고</h3>
 
- `String.valueOf(숫자타입 변수)` : 숫자 변수를 문자타입으로 형변환
- `Integer.valueOf(문자열타입 변수)` : 문자열 변수를 숫자타입으로 형변환




