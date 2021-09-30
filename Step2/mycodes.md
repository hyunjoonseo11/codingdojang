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
* 22번
```python
 
```
-----------------------------------
* [23번](https://codingdojang.com/scode/409?answer=26400#answer_26400)
  * 어떤 정수 n에서 시작해, n이 짝수면 2로 나누고, 홀수면 3을 곱한 다음 1을 더한다.    
  * 이렇게 해서 새로 만들어진 숫자를 n으로 놓고, n=1 이 될때까지 같은 작업을 계속 반복한다. 예를 들어, n=22이면 다음과 같은 수열이 만들어진다.     
  * 22 11 34 17 52 26 13 40 20 10 5 16 8 4 2 1             
  * n이라는 값이 입력되었을때 1이 나올때까지 만들어진 수의 개수(1을 포함)를 n의 사이클 길이라고 한다.                
  * 위에 있는 수열을 예로 들면 22의 사이클 길이는 16이다. i와 j라는 두개의 수가 주어졌을때, i와 j사이의 모든 수(i, j포함)에 대해 최대 사이클 길이를 구하라.         
    * 입력 예                 
1    10               
100  200                  
201  210                   
900  1000                   
    * 출력 예           
1    10    20             
100  200   125              
201  210   89              
900  1000  174              

```python
def cycle_length_first(u):
    if u % 2 == 0: # 짝수라면
        return u/2
    else: # 홀수라면
        return u*3+1

def cycle_length_middle(u):
    a = 1
    while 1:
        if u == 1:
            break
        u = cycle_length_first(u)    
        a += 1
    return a    

def cycle_length_last(h,l):
    c = cycle_length_middle(h)
    for s in range(h,l+1):
        if c < cycle_length_middle(s):
            c = cycle_length_middle(s)
    return c


if __name__ == '__main__':
    print(cycle_length_last(22,89))
 
```
-----------------------------------
* 31번
```python
 
```
-----------------------------------
* 37번
```python
 
```
-----------------------------------
* [41번](https://codingdojang.com/scode/428?answer=26404#answer_26404)
  * 모든 짝수번째 숫자를 * 로 치환하시오.(홀수번째 숫자,또는 짝수번째 문자를 치환하면 안됩니다.) 로직을 이용하면 쉬운데 정규식으로는 어려울거 같아요.                        
    * Example: a 1 b 2 c d e 3 ~ g 4 5 h i 6 → a * b * c d e * ~ g 4 * h i 6                     
```python
s = 'a1b2cde3~g45hi6'
for i in range(len(s)):
    if i%2 == 1 and s[i].isdigit():
        print('*',end='')
    else:
        print(s[i],end='')
 
```
-----------------------------------
* [42번](https://codingdojang.com/scode/429?answer=26409#answer_26409)
  * 우리 학교에는 복도 불을 켜고 끄는 마부(Mabu)라는 사람이 있다.                      
  * 전구마다 불을 켜고 끄는 스위치가 있다. 불이 꺼져 있을 때 스위치를 누르면 불이 켜지고 다시 스위치를 누르면 불이 꺼진다. 처음에는 모든 전구가 꺼져 있다.                      
  * 마부라는 사람은 특이한 행동을 한다. 복도에 n개의 전구가 있으면, 복도를 n번 왕복한다. i번째 갈 때 그는 i로 나누어 떨어지는 위치에 있는 스위치만 누른다. 처음 위치로 돌아올 때는 아무 스위치도 건드리지 않는다. i번째 왕복은 (이런 이상한 행동을 하면서) 복도를 한 번 갔다가 오는 것으로 정의된다.                       
  * 마지막 전구의 최종 상태를 알아내자. 과연 그 전구는 켜져 있을까 아니면 꺼져 있을까?              
  * Input                         
복도에 있는 n번째 전구를 나타내는 숫자가 입력된다. (2^32-1 이하의 정수가 입력된다.) 0은 입력의 끝을 의미하며 그 값은 처리하지 않는다.                   
  * Output                       
그 전구가 켜져 있으면 "yes"를, 꺼져 있으면 "no"를 출력한다. 테스트 케이스마다 한 줄에 하나씩 출력한다.                       
  * Sample Input                  
3               
6241              
8191                
0                 
  * Sample Output
no             
yes             
no            
```python
def lamp(n):
    s = False
    for i in range(1, n+1):
        if n == 0:
            s = False
        elif n%i == 0:
            s = not s
    return s


if __name__ == '__main__':
    print(lamp(0))     
```
> False를 True로 바꾸고 싶을 때 사용할 수 있는 코드
```python
s = False
s = not s
```
-----------------------------------
* [44번](https://codingdojang.com/scode/431?answer=26417#answer_26417)
  * 2나 5로 나눌 수 없는 0 이상 10,000 이하의 정수 n이 주어졌는데, n의 배수 중에는 10진수로 표기했을 때 모든 자리 숫자가 1인 것이 있다. 그러한 n의 배수 중에서 가장 작은 것은 몇 자리 수일까?              
  * Sample Input                               
3           
7             
9901               
  * Sample Output             
3                
6               
12                
```python
a = int(input('0보다 크고 10000보다 작은 수를 입력:'))
b = 1 
cnt = 1
while True:
    if a%2 == 0 or a%5 == 0:
        print('너는 2나 5로 나눌수 없는 숫자를 너어야 해. 다시 해 봐!!!')
        break
    elif b%a == 0:
        print(cnt)
        break
    else:
        b = b*10 + 1# b의 자리수를 계속해서 증가시킨다.
        cnt += 1 
```
-----------------------------------
