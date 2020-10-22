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
    for i in range(1, len(array)):
        for j in range(i, 0, -1):
            if array[j] < array[j-1]:
                array[j-1], array[j] = array[j], array[j-1]
            ## 앞의 수는 이미 정렬이 되어있으므로
            else:
                break
    return array
```
