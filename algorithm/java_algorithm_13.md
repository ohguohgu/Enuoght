# 💻 자바 알고리즘 - 문자열 바꿔서 찾기

<h3>📕 문제 설명</h3>

문자 "A"와 "B"로 이루어진 문자열 `myString`과 `pat`가 주어집니다. myString의 "A"를 "B"로, "B"를 "A"로 바꾼 문자열의 연속하는 부분 문자열 중 pat이 있으면 1을 아니면 0을 return 하는 solution 함수를 완성하세요.

<br>

<h3>📕 제한 사항</h3>

- 1 ≤ `myString`의 길이 ≤ 100
- 1 ≤ `pat`의 길이 ≤ 10
  - `myString`과 `pat`는 문자 "A"와 "B"로만 이루어진 문자열입니다.

<br>

<h3>📕 답안</h3>

```java
class Solution {
    public int solution(String myString, String pat) {
        String str = "";
        String[] arr = myString.split("");
        int answer = 0;
        for(int i=0; i<arr.length; i++) {
            str += (arr[i].equals("A"))?"B":"A";
        }

        return (str.contains(pat))?1:0;
    }
}
```
문제를 보니 `replace()`를 쓰면 될줄 알았는데 그렇게 되면 이미 바뀐 문자열이 또 바뀌기 때문에 문자열이 꼬이게 된다. 그래서 `myString`을 String 배열에 담아서 그 배열의 길이 만큼 for문을 돌면서 문자열 원소가 A와 동일하면 B, 아니면 A를 문자열 변수 `str`에 이어 붙인다. 그렇게 담은 str과 pat을 비교하여 문자열이 포함되어 있으면 1, 아니면 0을 리턴한다.

<br>
<h3>📕 개선 답안</h3>

```java
class Solution {
    public int solution(String myString, String pat) {
        myString = myString.replace("A","a").replace("B","A").replace("a","B");

        return (myString.contains(pat))?1:0;
    }
}
```
for문을 쓰지 않고 replace()만을 이용하여 풀이도 가능한데 A 문자열을 소문자 a로 바꾸고 그 문자열에서 B를 A로 변환한 뒤 소문자 a를 대문자 B로 변환하여 그 문자열과 pat을 비교하는 방법이다.

이렇게 하면 replace()를 쓰더라도 문자열이 꼬이지 않고 제대로 변환되는 것을 알 수 있다.

<br>
<h3>📕 참고</h3>

- `문자열변수.replace("기존 문자열","변경 문자열")` : 기존 문자열을 변경할 문자열로 변경해주는 함수
- `문자열.contains(문자열)` : 문자열에 특정 문자열이 포함되어 있는지 확인하여 true, false를 리턴하는 함수
- `문자열.equals(문자열)` : 문자열의 값을 비교하여 같다면 true, 다르다면 false를 리턴하는 함수

