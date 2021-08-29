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
* 128번
```python
a = int(input('숫자: '))
def number(c):
    e = []
    # c보다 작은 모든 수에 대해서
    for i in range(1, c+1):
        b = 0
        # i보다 작은 모든 수에 대해서
        for y in range(1,i):
            if i % y == 0:  # y가 i의 약수라면,
                b += y
        if i == b:  # 완전수라면
            e.append(i)
    return e    

print(number(a))    
```
-----------------------------------

* 131번
```python
for c in range(1, 1000):
    for b in range(1, c-1):
        for a in range(1, b-1):
            if (a*a)+(b*b) == c*c and a+b+c == 1000:
                print(a*b*c)
                break
```
-----------------------------------

* 134번
```python
a = 0
b = 1
c = 0
while b <= 4000001:
    a += b
    b,a = a,b
    if b % 2 == 0:
        c += b

print(c)  
```
-----------------------------------
* 136번
```python
a = 0
b = 0
for i in range(1,101):
    a += i
    b += i*i

print((a*a) - (b))    
```
-----------------------------------
* 138번
```python
abc = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R","S", "T", "U", "V", "W", "X", "Y", "Z"]
a = int(input("숫자입력: "))
b = str(input("문자입력: "))
b = list(b)
for i in range(len(b)):
    for r in range(len(abc)):
        d = []
        if b[i] == abc[r]:
            d = r+a
            if 25 < d:
                d = r+a-25
            b[i] = abc[d]
            break
print(b)    
```
-----------------------------------
* 139번
```python
n=int(input())

result=""
while n>1:
    result+= str(n%2)
    n = n//2

print(result + str(n))
```
-----------------------------------
* 144번
```python
def give():
    a = 0
    for i in range(100,1000):
        for r in range(100,1000):
            if str(i*r) == str(i*r)[::-1] and i*r > a:
                a = i*r
    return a

print(give())    
```
-----------------------------------
* 155번
```python
    
```
-----------------------------------
* 159번
```python
    
```
-----------------------------------

