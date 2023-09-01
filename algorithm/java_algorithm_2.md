# 문자열 계산하기

<h3>문제 설명</h3>
`my_string`은 "3 + 5"처럼 문자열로 된 수식입니다.  
문자열 `my_string`이 매개변수로 주어질 때, 수식을 계산한 값을 return 하는 solution 함수를 완성해주세요.  


<h3>제한 사항</h3>
- 연산자는 +, -만 존재합니다.
- 문자열의 시작과 끝에는 공백이 없습니다.
- 0으로 시작하는 숫자는 주어지지 않습니다.
- 잘못된 수식은 주어지지 않습니다.
- 5 ≤ my_string의 길이 ≤ 100
- my_string을 계산한 결과값은 1 이상 100,000 이하입니다.
- my_string의 중간 계산 값은 -100,000 이상 100,000 이하입니다.
- 계산에 사용하는 숫자는 1 이상 20,000 이하인 자연수입니다.
- my_string에는 연산자가 적어도 하나 포함되어 있습니다.
- return type 은 정수형입니다.
- my_string의 숫자와 연산자는 공백 하나로 구분되어 있습니다.


<h3>답안</h3>
```java
class Solution {
    public int solution(String my_String) {
        String[] arr = my_String.split(" ");
        int answer = 0;
        boolean chk = true;
        
        for(int i=0; i<arr.length; i++) {
            if(i%2==0) {
                answer+=chk?Integer.parseInt(arr[i]):-Integer.parseInt(arr[i]);
            }
            else {
                chk = arr[i].eqauls("+");
            }
        }
        return answer;
    }
}
```

먼저 `split()` 함수를 통해 `my_String`을 배열로 만든다.  
그렇게 만들어진 배열의 길이만큼 for문을 돌면서 i가 짝수번일 때, 즉 arr 원소가 숫자일 때만 `answer`에 원소를 더하고  
숫자가 아닌 경우엔 기호를 파악할 용도로 사용할 chk 변수에 "+" 기호와 비교하여 true 또는 false를 넣는다.
`answer`에 값을 더해줄 때는 삼항연산자를 통해 `chk`가 `true`일 땐 양수, `false`일 땐 음수를 더한다.

