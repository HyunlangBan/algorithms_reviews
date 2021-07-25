## Fail
### Solution
```python
def check(col):
    for i in range(col):
        if row[i] == row[col]:
            return False
        if abs(row[i] - row[col]) == (col - i):
            return False
    return True
    
def dfs(col):
    global result
    if col == n:
        result += 1
    else:
        for i in range(n):
            row[col] = i
            if check(col):
                dfs(col + 1)

n = int(input())
result = 0
row = [0] * n
dfs(0)
print(result)

```
- 체스에서 queen은 위, 아래, 왼쪽, 오른쪽, 대각선으로 모두 공격할 수 있다.
- 행을 기준으로 dfs를 해나가는 것이 포인트였다. 그리고 직접 그래프를 그리지 않고 `row` 리스트에 각 행에대한 열의 정보만 담아서 비교하는 것도 인상적이었다.
- 언제쯤 그래프 문제에서 안쫄고 풀수있을까.. ㅠ_ㅠ
