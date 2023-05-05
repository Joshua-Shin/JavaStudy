#### 코테용
---------------
- 배열 길이 .length
- 문자열 길이 .length()
- 컬렉션 사이즈 .size()
- import java.util.*;
```
int[] arr = {1,3,4,5,6};
Arrays.sort(arr);
```
````
int answer = 1;
answer = Math.max(answer,100);
// answer : 100
````
- s.charAt(i); 문자열 개별 접근
- double result = Math.sqrt(25); : 제곱근. 입력 출력 다 double형
- int[] arr = new int[5]; 배열 초기화. 배열은 사이즈가 고정.
- list.get(i); // List 개별 접근
- list.add(i); // List에 요소 추가.
- list.remove(int index); // List 해당 index의 요소 삭제.
- list.remove("SHIN"); // List 해당 문자열 객체 삭제.
- List<Integer> list; 의 경우. 
  - list.remove(1) // index 1의 요소 삭제
  - list.remove(new Integer(1)) // 숫자 1인 요소 삭제. 제일 처음 발견한 해당 요소만을 삭제.
- s.substring(int beginIndex, int endIndex)
- Integer.parseInt("1234") : 문자열을 숫자로.
- String.valueOf(1234) : 숫자를 문자열로.
- Collections.sort(list) : List 오름차순 정렬
- Collections.sort(list, Collections.reverseOrder()) : List 내림차순 정렬
