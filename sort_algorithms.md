면접을 봤다. 정렬 알고리즘 뭐가 있냐고 물었다. 버블이랑 퀵밖에 생각나는게 없었다. 그럼 그 둘이 비교할 수 있냐고 했다. 말하지 못했다.<br>
나 자신에 대한 반성으로 알고리즘 빡세게 복습 다시한다!!!!!!!!!!

## Bubble Sort
- 인접한 두 수를 비교하여 앞의 수가 더 크다면 swap한다.
- 한번 정렬될 때마다 해당 범위중 가장 큰 수가 배열의 뒤로 정렬된다.
- 시간복잡도는 `O(n^2)`, 완전 정렬되어 있는 경우에는 `O(n)`이다.
```python
def bubble_sort(array):
    for i in range(len(array)-1):
        swap = False
        for j in range(len(array)-i-1):
            if array[j] > array[j+1]:
                array[j], array[j+1] = array[j+1], array[j]
        if not swap:
            break
    return array
```

## Insertion Sort
- 배열의 두번째 요소(key)부터 시작하여 key의 앞의 요소들 중 key보다 작은 수가 있다면 그 수 뒤로 해당 key를 삽입한다.
- 삽입이라고는 하지만 삽입 그대로를 한다기보다는 대소관계에 따라 swap을 계속 해준다고 생각하면 된다.
- 거꾸로 탐색 하는 것에 주의하자.
- 시간복잡도 `O(n^2)`, 최선의 경우에는 `O(n)`이다.
```python
def insertion_sort(array):
    for end in range(1, len(array)):
        for j in range(end, 0, -1):
            if array[j] < array[j-1]:
                array[j-1], array[j] = array[j], array[j-1]
            else:
                break
    return array
```

## Selection Sort
- 배열 탐색 후 가장 작은 수를 현재 범위의 가장 앞으로 보낸다.
- 시간 복잡도는 `O(n^2)`이다. 선택 정렬은 최선의 경우에도 `O(n^2)`이다.
```python
def selection_sort(array):
    for i in range(len(array)-1):
        lowest = i
        for j in range(i+1, len(array)):
            if array[lowest] > array[j]:
                lowest = j
        array[lowest], array[i] = array[i], array[lowest]
    return array
```

## Quick Sort
- 정렬 알고리즘의 꽃이라고도 불린다.
- 기준(pivot)을 정해두고 기준보다 작으면 left, 크면 right로 분류하는 함수를 정의하고 left와 right에 함수를 재귀적으로 적용한다.
- 시간 복잡도는 `O(nlogn)`이며 최선의 경우에는 `O(nlogn)`, 최악의 경우에는 `O(n^2)`이다.
```python
def q_sort(array):
    if len(array)<=1:
        return array

    pivot = array[0]
    left, right = list(), list()

    for i in range(1, len(array)):
        if pivot < array[i]:
            right.append(array[i])
        else:
            left.append(array[i])

    return q_sort(left) + [pivot] + q_sort(right)
```

## Merge Sort
- 하나의 리스트를 두 개의 균등한 크기로 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하며 정렬을 수행하여 전체가 정렬된 리스트가 되게 하는 방법
- 시간 복잡도는  `O(nlogn)`이며 최선과 최악의 경우에도 모두 `O(nlogn)`이다.
- 개인적으로 어렵게 느껴지는 정렬 방법.......

```python
def merge(left, right):
    merged = list()
    left_point, right_point = 0, 0

    while len(left) > left_point and len(right) > right_point:
        if left[left_point] > right[right_point]:
            merged.append(right[right_point])
            right_point += 1
        else:
            merged.append(left[left_point])
            left_point += 1

    while len(left) > left_point:
        merged.append(left[left_point])
        left_point += 1

    while len(right) > right_point:
        merged.append(right[right_point])
        right_point += 1

    return merged


def mergesplit(data):
    if len(data)<=1:
        return data

    medium = int(len(data)/2)
    left = mergesplit(data[:medium])
    right = mergesplit(data[medium:])
    
    return merge(left, right)
 ```
