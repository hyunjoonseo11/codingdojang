* [1번](https://codingdojang.com/scode/365?answer=26393#answer_26393)
  * 어떤 자연수 n이 있을 때, d(n)을 n의 각 자릿수 숫자들과 n 자신을 더한 숫자라고 정의하자.           
예를 들어       
d(91) = 9 + 1 + 91 = 101       
이 때, n을 d(n)의 제네레이터(generator)라고 한다. 위의 예에서 91은 101의 제네레이터이다.              
어떤 숫자들은 하나 이상의 제네레이터를 가지고 있는데, 101의 제네레이터는 91 뿐 아니라 100도 있다.  
그런데 반대로, 제네레이터가 없는 숫자들도 있으며, 이런 숫자를 인도의 수학자 Kaprekar가 셀프 넘버(self-number)라 이름 붙였다.  
예를 들어 1,3,5,7,9,20,31 은 셀프 넘버 들이다.           
1 이상이고 5000 보다 작은 모든 셀프 넘버들의 합을 구하라.
```python
def find_generated_numbers(a):
    g = []
    for n in range(a):
        y = n
        while n > 0:
            y += n % 10
            n = n//10
        g.append(y)
    return g       

if __name__ == '__main__':
    a = int(input())
    G = find_generated_numbers(a)
    S = []
    for i in range(a):
        if i not in G:
            S.append(i)
    print(sum(S))        
```
```python
def d_fn(n):
    y = n
    while n > 0:
        y += n % 10
        n //= 10
    return y

Z = [d_fn(n) for n in range(5000)]
A = [n for n in range(5000) if n not in Z]
print (sum(A)) 
```
> 모든 자리수를 더하는 코드
```python
def add_each_number(n):
    y = 0
    while n > 0:
        y += n % 10
        n //= 10
    return y
```
> 어떤 결과를 빈 배열에 계속 추가하는 코드 (예)
```python
Z = [함수(n) for n in range(5000)]
```
-----------------------------------
* [7번](https://codingdojang.com/scode/393?answer=26361#answer_26361)
  * 1부터 10,000까지 8이라는 숫자가 총 몇번 나오는가?     
8이 포함되어 있는 숫자의 갯수를 카운팅 하는 것이 아니라 8이라는 숫자를 모두 카운팅 해야 한다.       
(※ 예를들어 8808은 3, 8888은 4로 카운팅 해야 함)     
```python
def find_8():
    cnt = 0
    for i in range(1,10001):
        cnt += str(i).count('8')
    return cnt
        
if __name__ == '__main__':
    print(find_8())
```
-----------------------------------
* [11번](https://codingdojang.com/scode/397?answer=26369#answer_26369)
  * 첫 번째 계산             
아이들은 여러 자리 숫자들을 더하기 위해서 우에서 좌로 숫자를 하나씩 차례대로 더 하라고 배웠다. 1을 한 숫자 위치에서 다음 자리로 더하기위해 이동하는 "한자리올림"연산을 많이 발견하는 것은 중요한 도전이 된다. 당신의 일은 교육자가 그들의 어려움을 평가하기 위하여, 덧셈 문제들의 각 집합에 대해서 한자리올림 연산들의 수를 계산하는 것이다.             
입력               
입력의 각 라인은 10개의 숫자들보다 미만인 양의 정수들 두 개를 포함한다. 입력의 마지막 라인은 0 0 을 포한한다.
출력                            
마지막을 제외한 입력의 각 라인에 대해서 당신은 두 숫자들을 더한 결과에서 한자리올림 연산들의 수를 아래 처럼 보여지는 형식으로 계산하여 출력해야 한다.                  
입력 샘플                 
123 456                 
555 555                
123 594            
0 0               
출력 샘플               
No carry operation.                   
3 carry operations.                 
1 carry operation.                    
```python
def help_children():
    cnt = 0
    a = int(input())
    b = int(input())
    carry = 0
    for i in range(len(str(max(a,b)))):
        if a%10 + b%10 + carry >= 10:
            cnt += 1
            carry = 1
        else:
            carry = 0
        a = a//10
        b = b//10

    if cnt == 0:
        return 'No carry operation.'
    elif cnt == 1:
        return '1 carry operation.'  
    else:
        return '{0} carry operations.'.format(cnt) 
if __name__ == '__main__':
    print(help_children())       
```
> [map](https://wikidocs.net/32#map) 함수를 이용하여 여러 숫자를 한 번에 입력받는 코드 (예: 숫자 두 개를 입력 받을 때)
```python
x, y = map(int, input().split())
```
-----------------------------------
* 14번
```python
 
```
-----------------------------------
* 18번
```python
 
```
-----------------------------------
