# Short Coding

> 자주 사용되는 간단한 로직들의 효율적인 방법들을 작성합니다.

## Index

### 손코딩

* [배열에서 K번째로 큰 수 찾기](#N-길이의-배열에서-K번째로-큰-수-찾기)

### LeetCode

##### [배열 (Array)](#Array)

* [1. 리스트의 두 수의합 O(n)](#1.-리스트의-두-수의합-O(n)-Link)

* [2. 최솟값과 최대값을 제외한 수들의 평균값](#2.-최솟값과-최대값을-제외한-수들의-평균값-Link)

* [3. 1개만 있는 수](#3.-1개만-있는-수-Link)

* [4. Intersection of Two Arrays](#4.-Intersection-of-Two-Arrays-Link)

* [5. Move Zeros](#5. Move-Zeros)


##### [문자열 (String)](#String)



## 손코딩

#### N 길이의 배열에서 K번째로 큰 수 찾기

* QuickSelect 함수를 이용해서 쓸 수 있다.

```python
def quickSelect(arr, k):
	if len(arr) == 1:  # 배열에 하나의 요소만 남았을 경우
        return arr[0]

    # pivot 값을 랜덤하게 선택합니다.
    pivot_index = random.randint(0, len(arr) - 1)
    pivot_index = partition(arr, pivot_index)
	partition(arr, pivot)                       # pivot이 몇번째로 큰 숫자인지 반환

    if k == pivot_index:                     # k 번째 큰 수를 찾고자한다.
        return arr[k]
    elif k > pivot_index:                    # 만약 pivot이 k보다 작으면
        return quickSelect(arr[pivot_index + 1:], k - pivot_index - 1)   # 값이 더 작은 애들 중에서 k-pivot_idx-1 찾아야함
    else:                                               # 만약 pivot이 k보다 크면
        return quickSelect(arr[:pivot_index], k)  		# 더 큰 애들 중에서 k번째를 찾아야한다.


def partition(arr, pivot_idx):
    pivot_value = arr[pivot_idx]
    result = 0

    arr[pivot_idx], arr[-1] = arr[-1], arr[pivot_idx]

    for i in range(len(arr) - 1):
        if arr[i] > pivot_value:						# 기준보다 크면
            arr[i], arr[result] = arr[result], arr[i]	# 앞으로 보냄
            result += 1

    arr[result], arr[-1] = arr[-1], arr[result]

    return result
```

##### Point

* QuickSelect는 quicksort와 유사한 방식으로 동작한다. 다만 전체 정렬을 진행하지 않고 K번째를 찾아가는데 필요한 부분만 진행을 한다.

```python
# quickSort
def quickSort(arr, start, end):
    if start >= end:
        return
    mid = (start + end) // 2
    pivot = arr[mid]
    now = start
    arr[mid], arr[end] = arr[end], arr[mid]

    for i in range(start, end):
        if pivot > arr[i]:
            arr[i], arr[now] = arr[now], arr[i]
            now += 1

    arr[end], arr[now] = arr[now], arr[end]
    quickSort(arr, start, now-1)
    quickSort(arr, now+1, end)
```



## Array

### 1. 리스트의 두 수의합 O(n) [Link](https://leetcode.com/problems/two-sum/)

리스트의 두 수의 합이 target이 되는 수 두개를 List로 반환하시오.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        check = {}
        for i in range(len(nums)):
            if nums[i] in check:
                return [i, check[nums[i]]]
            check[target - nums[i]] = i
```

##### Point

* check의 경우 HashTable을 사용하는 dictionary 또는 set을 사용한다 => O(1)
* 1번의 순회만으로 이를 해결할 수 있도록 target-nums[i]를 check에 저장해둔다. => O(1)



<br>

### 2. 최솟값과 최대값을 제외한 수들의 평균값 [Link](https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary/)

리스트가 주어졌을 때 최솟값과 최대값을 제외한 수들의 평균값을 구하시오.

```python
def average(salary) -> float:
    q = []
    for i in salary:
        heapq.heappush(q, salary[i]) 		# O(nlogn)
        
    # heapq.heapyfy(salary) 를 이용하면 list를 heapq 형태로 빠르게 변환할 수 있다. O(n)

    heapq.heappop(q)					# O(nlogn)
    answer = 0
    while len(q) > 1:
        answer += heapq.heappop(q)		# O(nlogn)

    return answer / (len(salary)-2) 


def average2(salary) -> float:
    salary.remove(max(salary))			# O(n)	-> 2n
    salary.remove(min(salary))			# O(n)	-> 2n
    return sum(salary)/len(salary)		# O(n)	-> n

def average3(salary) -> float:
    salary.sort()						# O(nlogn) -> nlogn
	return sum(salary[1:-1]) /(len(salary)-2) # O(n) -> 2n

def average4(salary) -> float:
    salary.sort()						# O(nlogn) -> nlogn
	return (sum(salary) - salary[0] - salary[-1]) /(len(salary)-2) # O(n) -> n

# Test 결과 (n= 2, 000, 000)
solution1 time :  3.095670461654663 	# 3nlogn
solution2 time :  0.48767900466918945 	# 5n
solution3 time :  0.6692276000976562 	# 2n + nlogn
solution4 time :  0.6733450889587402	# n + nlogn
```

첫번째 풀이의 경우 heap을 사용해서 O(nlogn)으로 풀이가 가능하다.

두번째 풀이의 경우 빌트인 메서드인 max, min과 remove을 이용해서 문제를 풀었는데 생각보다 문제 2번의 속도가 더 빨라서 메서드 내부 구조를 확인해보았다.

##### Point

* sort() 메서드는 Timsort 알고리즘을 사용하며 stable하고
  * `stable sort` : 동일한 값이 있는 경우, 이들의 상대적인 위치가 유지되는 정렬 방식
  * `unstable sort` : 동일한 값이 있는 경우 상대적인 위치를 보장하지 않는 방식, 일반적으로 성능은 더 좋음
* heapq.heapyfy(salary) 를 이용하면 list를 heapq 형태로 빠르게 변환할 수 있다. O(n)



<br>

### 3. 1개만 있는 수 [Link](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/549/)

숫자들로 이루어진 리스트가 주어진다. 그 중 하나의 숫자만 1개가 있고 나머지 숫자들은 2개씩 있을 때, 1개만 있는 숫자를 구하시오.

```python
def findSingleNumber1(nums: List[int]) -> int:
    check = set()
    for i in range(len(nums)):			
        if nums[i] in check:					# O(1)
            check.remove(nums[i])				
        else:
            check.add(nums[i])

    return list(check)[0]

def findSingleNumber2(nums: List[int]) -> int:
    answer = 0
    for num in nums:
        answer ^= num

    return answer
```

##### Point

* 가장 쉽게 생각하는 방법이 순회하면서 각 value마다 flag를 두어 1번 있는지 2번 있는지를 확인하는 것이다. 하지만 이 때, dictionary나 set이 사용되어 추가적인 메모리가 필요하게 된다. (dictionary와 set의 경우 HashTable로 구현되어 있어 탐색시 O(1)의 시간복잡도를 가진다.)

* 같은 수끼리 XOR 연산을 하게 되면 0이 되는 성질을 사용하면 O(N)으로 풀 수 있다.




<br>

### 4. Intersection of Two Arrays [Link](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/674/)

두 리스트가 주어졌을 때, 공통 원소를 가지는 List를 반환하시오. 만약 같은 원소가 2개 이상 들어 있을 시에는 똑같이 2개를 반환하여야한다.

```python
def intersect(self, nums1, nums2):   
    d = defaultdict(int)
    for a in nums1:					# n
        d[a] += 1					# O(1)
        
    result = []
    for b in nums2:					# n
        if d[b] > 0:				# O(1)
            result.append(b)		
            d[b] -= 1				

    return result					# 최종 O(n)

def intersect2(self, nums1, nums2):
    result = []
    if len(nums1) >= len(nums2):
        nums1, nums2 = nums2, nums1
        
    for i in range(len(nums1)):						# n
        if nums1[i] in nums1 and nums1[i] in nums2:	# O(n)
            result.append(nums1[i])
            nums2.remove(nums1[i])					# O(n)
                    
     return result									# 최종 O(n^2)
```

##### Point

* 첫 번째 해결책의 경우 dictionary를 사용하여 해당 A에 대한 값들을 적어놓고 다시 B를 순회하면서 dictionary 값들을 수정하고 이를 기반으로 result를 구하는 방법이다. dictionary의 경우 추가, 변경, 조회의 시간복잡도가 O(1)이기 때문에 최종적으로 O(N)의 시간복잡도를 가진다. 하지만 이 방법의 경우 dictionary 사용으로 인한 추가 메모리가 사용된다.
* 두 번째 해결책의 경우 주어진 두개의 리스트만을 사용(추가 메모리 사용 x)해서 풀이하는 방식이다. 이 경우는 for문 내에 list의 in이 사용되기 때문에 O(n^2)의 시간 복잡도를 가진다. 특히 이 때 for문을 더 짧은 Array를 사용하는것이 시간적으로 이득이다.
* 두 가지 방법으로 문제를 풀이하였는데 모든 개발자들은 각자 주어진 환경이 다를 것이다. 시간 최적화가 필요할 수도, 메모리 최적화가 필요할 수도 있다. 각자의 환경에 적합한 알고리즘을 짤 수 있어야 한다.



<br>

### 5. Move Zeros [Link](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/567/)

정수 배열 'nums'가 주어지면 0이 아닌 요소의 상대적 순서를 유지하면서 모든 '0'을 끝으로 이동합니다.  단, 어레이를 복사하지 않고 내부에서 이 작업을 수행해야 합니다

```python
def moveZeroes(nums) -> None:	# Array를 복사했을 때, 
    N = len(nums)
    result = []
    for num in nums:							# O(n)
        if num:
            result.append(num)
            
    for _ in range(len(result), N):				# O(k) k는 0의 개수
        result.append(0)

    nums[:] = result
    
def moveZeros2(nums) -> None:
    N = len(nums)
    j = 0
    for i in range(N):							# O(n)
        if nums[i] != 0:
            nums[i], nums[j] = nums[j], nums[i]
            j += 1

    while j < N:								# O(k)
        nums[j] = 0
        j += 1
    
```

##### Point

* 가장 쉽게 생각할 수 있는 방법은 0이 아닌 것들을 별도의 array에 담아서 복사하는 것이다. 하지만 이렇게 했을 경우 추가적인 메모리를 사용한다. index를 이용해서 원소끼리의 위치 변경을 꾀하는 것이 대부분의 경우 메모리적으로 빠르다.



<br>

---

### String

#### 1. Reverse String

```java
class Solution {
    public void reverseString(char[] s) {
        int A = s.length / 2;
        for (int i=0; i < A ; i++) {				// O(n)
            swap(s, i, s.length-i-1);   
        }
    }
    
    private void swap(char[] s, int i, int j) {
        char tmp = s[i];
        s[i] = s[j];
        s[j] = tmp;
    }
}
```

```python
def reverseString(s):
    return s[::-1]
```

##### Point

* 절반까지만 순회하는 것이 중요하다. 파이썬의 경우 슬라이싱으로 쉽게 할 수 있다.
* Java에서 몫을 구하는 연산자는 `/`이다.(python은 //)



<br>

#### 2. Reverse Integer[Link]()

부호 있는 32비트 정수 x가 지정되면 숫자가 반대로 된 x를 반환합니다. x를 반대로 설정하면 값이 서명된 32비트 정수 범위[-2^31, 2^31 - 1]를 벗어나면 0을 반환합니다

```java
class Solution {
    public int reverseInteger(int x) {
        int flag = x < 0 ? 1 : 0;
        if (flag == 1){
            x = -x;
        }
            
        int result = 0;
        while (x > 0) {
            if (result > Integer.MAX_VALUE / 10) {
                return 0;
            }
            result = result * 10 + x % 10;
            x /= 10;
        }
        
        result = flag == 0 ? result : -result;
        return -Math.pow(2, 31) <= result && result <= Math.pow(2, 31)-1 ? result : 0;
    }
}
```

##### Point

* 이 문제에서 신경써야할 부분은 크게 2가지였다. 음수일 때의 -부호 처리와 정수범위를 벗어났을 때의 예외처리가 필요한 문제였다.
* 이 때, 2*31즉, 2147483648보다 result가 커지게되면, overflow가 발생해서 값이 왜곡되어 대소비교의 의미가 없어진다. 따라서 곱하기 연산을 수행하기전 result 값의 크기를 이용해서 예외 처리를 해야한다.



<br>

#### 3. First Unique Character in String  [Link](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/881/)

주어진 문자열에서 반복되지 않는 첫 번째 문자를 찾은 후 인덱스를 반환합니다. 존재하지 않으면 -1을 반환합니다. 주어진 문자열은 영어 소문자로 이루어져 있습니다.

```python
def firstUniqChar(s:str) -> int:
    check = dict()
    arr = list(s)
    for i in range(len(s)):
        if arr[i] in check:
            arr[check[arr[i]]] = "."
            arr[i] = "."
        else:
            check[arr[i]] = i

    for i in range(len(arr)):
        if arr[i] != ".":
            return i

    return -1

def firstUniqChar2(s:str) -> int:					# pythonic한 방식
	was = set()
    for i in range(len(s)):							# n번 반복
        if s[i] in was:
            continue

        try:
            s.index(s[i], s.index(s[i], 0) + 1)		# 이후의 substring에서 찾아봄 O(n)																 
        except:										# 없으면 리턴
            return i

        was.add(s[i])
    return -1										# O(n^2)

def firstUniqChar3(s:str) -> int:					# s의 경우 영어 소문자라는 것을 사용
    result = []
    for char in range(ord("a"), ord("z") + 1):		# index를 사용하지 않더라도 그냥 for 문
        try:										# 돌면서 찾아도 될 것 같다.
            a = s.index(chr(char))
            try:
                s.rindex(chr(char), a+1)
            except:
                result.append(a)

                continue

        except:
            continue

    return min(result) if result else -1

# solution1 time :  0.01300358772277832
# solution2 time :  0.0020034313201904297
# solution3 time :  0.0
```

##### Point

* 왜 solution2가 solution1보다 빠른가?



<br>

#### 4. Valid Anagram [Link](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/882/)

주어진 두개의 문자열이 Anagram인지 반환하시오. 이 때, `Anagram`이란 하나의 단어에 존재하는 알파벳들을 재배치하여 다른 단어를 만들 수 있음을 의미한다.

```python
def isAnagram(s: str, t: str) -> bool:
    d = dict()
    for char in s:
        if char in d:
            d[char] += 1
        else:
            d[char] = 1

    for char in t:
        if char in d:
            d[char] -= 1
            if not d[char]:
                d.pop(char)
        else:
            return False

    return False if d else True
```



<br>

#### 5. Valid Palindrome [Link](https://leetcode.com/explore/interview/card/top-interview-questions-easy/127/strings/883/)

`Palindrome`이란 모든 대문자를 소문자로 변환하고, 영숫자를 제외한 모든 문자를 제거한 후 뒤에서 앞으로 읽었을 때 같은 단어를 의미합니다.

주어진 문자열이 palindrome인지를 반환하세요