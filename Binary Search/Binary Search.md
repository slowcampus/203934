# 이진 탐색 ( 분할정복 알고리즘 )  

![binary_search](https://blog.kakaocdn.net/dn/bCRI11/btqDEFKLWFh/Fh5mKeR8p6YxJ1lhKAiJYk/img.gif)

<br>
<pre>
- 탐색 대상을 1/2 로 나누면서, 빠르게 찾는 방법 ( 정렬이 되어 있어야 함. )
- 분할정복 알고리즘 이다. ( 조건이 맞는 영역에 대해서만 탐색하는 기법 ) 
- 순차는 최대 o(N) 탐색, 이진탐색은 O(logN)
</pre>

 ### Example
![image](https://camo.githubusercontent.com/c2075ff2cd7addf00519d2c6b719caa84f43264782669ba790ce06a496cd3993/68747470733a2f2f7777772e6765656b73666f726765656b732e6f72672f77702d636f6e74656e742f75706c6f6164732f42696e6172792d5365617263682e706e67)

찾고자 하는 값(x) : 23
1. x 를 중간 원소인 16 {N/2 = 5, (ind:4)}과 비교한다.
2. 16이 x보다 작으므로, x는 해당원소보다 배열의 우측에 존재한다.
3. 왼쪽 절반(2,5,8,12) 값들을 버리고, 오른쪽 배열 ( 23,38,56,72,91) 에서 이진탐색을 재실행한다.
4. 오른쪽 배열의 중간값 56 {5/2 = 3 (ind:2)} 이다.
5. 56 은 x 보다 크다
6. x는 56보다 배열의 좌측에 존재한다.
7. 배열의 오른쪽 ( 56,72,91) 값들을 버리고, 왼쪽 ( 23,38) 에서 다시 검색한다.
8. 왼쪽 배열의 중간값 23 {2/2 =1 (ind:0)} 이다.
9. 위치값 5를 리턴한다.

```pseudo code
// 반복

binarySearch(A[0..N-1], value) {
  low = 0
  high = N - 1                  // 시작(low)과 끝(high)값 설정
  while (low <= high) {
      mid = (low + high) / 2    // 중간 요소 설정
      if (A[mid] > value)
          high = mid - 1        // 오른쪽 배열 버리고 다시 이진 탐색 (while문)
      else if (A[mid] < value)
          low = mid + 1         // 왼쪽 배열 버리고 다시 이진 탐색 (while문)
      else
          return mid            // found k
  }
  return -1                     // not found k
}
```