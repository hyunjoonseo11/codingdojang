# Coding Dojang codes
## Step 1
* 105번
```python
num = ""
for t in range(1 ,1001):
    num += str(t)

for f in range(10):
    a = num.count('%d' % f)
    print("%d의 개수 : %d" % (f,a))
```
-----------------------------------
* 106번
```python
a = 0
for i in range(10,1001):
    b = 1
    # 숫자 각각에 대해서
    for t in str(i): # str(10) -> '10'
        b = b*int(t)
    a += b
print("%d" % a)      
```
-----------------------------------
* 120번
```python
def DashInsert(str_a):
    # str_a에 있는 문자 하나에 대해서
    prev = []
    answer = ''
    # 각각의 숫자에 대해서
    for s in str_a:
        if len(prev) == 0:  # 첫번째 숫자라면
            prev.append(int(s))
            answer+=s
            continue
        else: #두번째 숫자부터는
            #이전 숫자와 현재 숫자가 둘 다 홀수 라면
            if (prev[0]%2==1) and (int(s)%2==1):
                answer+='-'
            #이전 숫자와 현재 숫자가 둘 다 짝수 라면
            elif (prev[0]%2==0) and (int(s)%2==0):
                answer+='*'
            #그 이외의 경우라면
            answer+=s

            #현재 숫자를 prev에 저장
            prev[0] = int(s)
    return answer


if __name__ == '__main__':
    a = input('숫자: ')
    str_a = str(a)
    print(DashInsert(str_a))    
```
-----------------------------------


* 번
```python
    
```
-----------------------------------

