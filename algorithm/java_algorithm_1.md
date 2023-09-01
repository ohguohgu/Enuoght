
# 자릿수 더하기

## 문제 설명
정수 n이 매개변수로 주어질 때 n의 각 자리 숫자의 합을 return하도록 solution 함수를 완성해주세요

## 제한 사항
- 0 ≤ n ≤ 1,000,000

## 답안
```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        while(n>0) {

            answer+= n%10;
            n/=10;
        
        }
        return answer;
    }
}
```
이 문제는 각 자리의 숫자의 합을 더하는 것, 즉 10으로 나눴을 때 나머지를 더해주면 되는 문제다.  
`n % 10`을 통해 도출된 나머지를 `answer`에 더해주고 그 다음 나머지를 구하기 위해 n을 10으로 나눠서 저장한다.


