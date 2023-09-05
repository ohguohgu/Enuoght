# 약수 구하기

<h3>문제 설명</h3>

문자열 `my_string`이 매개변수로 주어집니다. `my_string`에서 중복된 문자를 제거하고 하나의 문자만 남긴 문자열을 return하도록 solution 함수를 완성해주세요.

<br>

<h3>제한 사항</h3>

- 1 ≤ `my_string` ≤ 110
- `my_string`은 대문자, 소문자, 공백으로 구성되어 있습니다.
- 대문자와 소문자를 구분합니다.
- 공백(" ")도 하나의 문자로 구분합니다.
- 중복된 문자 중 가장 앞에 있는 문자를 남깁니다.

<br>

<h3>답안</h3>

```java
import java.util.*;

class Solution {
    public String solution(String my_string) {
        String answer = "";
        String[] arr = my_string.split("");

        answer += arr[0];
        for(int i=1; i<arr.length; i++) {
            if(answer.contains(arr[i])) {
                continue;
            }else
            {
                answer+= arr[i];
            }
        }

        return answer;

    }
}
```

먼저 my_string을 split() 함수를 통해 String 배열로 만들어 준 뒤 answer에 첫번째 문자열을 넣는다.  
이후 for문을 돌면서 answer에 문자열이 포함되어 있으면 continue를 통해 넘어가고 불포함 되어 있으면 answer에 문자열을 더해준다.
이렇게 `contains()` 함수를 통해 포함, 불포함을 파악하여 문제를 풀어도 되지만 `indexOf()`를 통해서도 문제 풀이가 가능하다.

```java
import java.util.*;

class Solution {
    public String solution(String my_string) {
        String answer = "";
        
        for(int i=0; i<my_string.length(); i++) {
            if(i==my_string.indexOf(my_string.charAt(i))) {
                answer+=my_string.charAt(i);
            }
        }
        return answer;
    }
}
```

굳이 `my_string`을 배열로 만들지 않고 `indexOf()`의 리턴값인 문자열이 포함되어 있다면 첫번째 문자열의 인덱스를 갖고온다는 것을 이용해서 해당 알고리즘을 풀 수 있다.  
for문을 돌면서 `charAt()`을 이용해 전체 문자열에서 한글자씩 떼어내 `indexOf()`로 떼어낸 문자열의 인덱스를 확인한다.  
당연히 모든 문자는 `my_string`에 포함되어 있기 때문에 `indexOf()`를 통해 인덱스가 반환되지만  
<b>맨 처음 등장한 문자열의 인덱스가 반환</b>되기 때문에 중복된 문자열이 오더라도 `answer`에 두번 더해질 수 없다.

<br>
<h3>참고</h3>

- `문자열.split(구분자)` : 구분자를 이용해서 문자열을 끊어서 배열로 반환, 구분자가 공백인 경우 한글자씩 끊어서 배열로 반환.
- `문자열.contains(A)` : 문자열에 A 문자가 있는지 체크하는 함수, 있다면 true 없다면 false 리턴
- `문자열.indexOf(A)` : 문자열에 A 문자의 인덱스 위치 반환하는 함수, 없다면 -1를 리턴
- `문자열.charAt(인덱스)` : 기준 문자열에서 인덱스 위치에 해당하는 문자열 한글자를 char 타입으로 반환




