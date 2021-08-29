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
---
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
---

## Step 2
