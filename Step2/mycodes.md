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
def check_odd_even(u):
    if u % 2 == 0: # 짝수라면
        return u/2
    else: # 홀수라면
        return u*3+1

def compute_cycle_length(u):
    a = 1
    while 1:
        if u == 1:
            break
        u = check_odd_even(u)    
        a += 1
    return a    

def compute_cycle_length_two(h,l):
    c = compute_cycle_length(h)
    for s in range(h,l+1):
        if c < compute_cycle_length(s):
            c = compute_cycle_length(s)
    return c


if __name__ == '__main__':
    x,y = map(int, input().split())
    z = compute_cycle_length_two(x,y)
    
    print("{0}\t{1}\t{2}".format(x,y,z))
 
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
def change_even_digit(s): 
    for i in range(len(s)):
        if i%2 == 1 and s[i].isdigit():
            print('*',end='')
        else:
            print(s[i],end='')
    print("")

if __name__ == '__main__':
    s = 'a1b2cde3~g45hi6'       
    change_even_digit(s) 
 
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

    if s == True:
        print("yes")
    else:
        print("no")

def check_lamps(inArray):
    for i in range(len(inArray)):
        if inArray[i] != '0':
            number = int(inArray[i])
            lamp(number)


if __name__ == '__main__':
    inArray = input().split()
    check_lamps(inArray)     
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
def count_ones(arr):
    for i in range(len(arr)):
        c = int(arr[i])
        b = 1 
        cnt = 1
        while True:
            
            if b%c == 0:
                print(cnt)
                break
            else:
                b = b*10 + 1# c의 자리수를 계속해서 증가시킨다.
                cnt += 1 


if __name__ == '__main__':
    arr = input().split()
    count_ones(arr)
```
----------------------------------- 
* 45번
```python
 
```
-----------------------------------
* [46번](https://codingdojang.com/scode/433?orderby=&langby=#answer-filter-area)
  * 디브온에서 미니대안언어축제가 진행되던 M2 밖에 텍스트큐브 부스에서 재미있는 코드골프 문제 풀기가 있었습니다. 150자 이하로 푸신 분들에게는 즉석에서 제공되는 원두커피와 텀블러가 상으로 주어졌다고 합니다.                          
문제는 아래와 같습니다. 이 결과가 나와야 하는데 언어 제약은 없답니다.                                    
``` 
 문제                
     *
     *
    * *
   *   *
  *     *
**       **
  *     *
   *   *
    * *
     *
     *
```     
```python
print('''
     *
     *
    * *
   *   *
  *     *
**       **
  *     *
   *   *
    * *
     *
     *''') 
```
-----------------------------------
* 54번
```python
 
```
-----------------------------------
* 55번
```python
 
```
-----------------------------------
* 56번
```python
 
```
-----------------------------------
* 58번
```python
 
```
-----------------------------------
* [60번](https://codingdojang.com/scode/447?answer=26443#answer_26443)
  * 약 2,000년 전에는 전쟁에서 병사들이 적들에 의해 동굴에 갇히게 되는 경우가 종종 있었다고 한다.                        
그들은 포로가 되는것을 방지하기 위해 동그랗게 서서 마지막 한 사람이 남을 때 까지 순서대로 돌아가며 세번째에 해당되는 사람을 죽여 나갔다고 한다.                        
마지막으로 남게되는 사람은 자살하기로 약속되어 있었지만 보통 적들에게 항복을 하는 경우가 많았다고 한다.                              
여러분이 풀어야 할 문제는 총 인원수(N)와 간격(K)이 주어졌을 때 가장 마지막에 살아남는 병사의 위치(the safe position)를 알아내는 것이다.                           
예를 들어 병사수가 총 10명이고 돌아가며 세번째에 해당되는 병사를 제거하는 경우는 다음과 같다:                        
N = 10, K = 3                                 
위의 경우 다음과 같은 순서로 병사들이 제거된다. (괄호는 제거되는 병사를 의미한다)                      
1st round: 1 2 (3) 4 5 (6) 7 8 (9) 10                   
2nd round:                            1 (2) 4 5 (7) 8 10                     
3rd round:                                                (1) 4 5 (8) 10                   
4th round:                                                               4 (5) 10                 
5th round:                                                                        4 (10)                 
위 예에서 끝가지 살아남는 병사는 4, 즉 4번째 병사이다.                  
입력 데이터는 총 병사수 N과 간격 K이다.                        
출력 데이터는 마지막까지 살아남는 병사의 위치이다.                   
(단, 최초 시작은 1번 병사부터이다.)                        
입출력 예는 다음과 같다:                  
  * initial data:               
10 3                 
  * answer:                 
4                
```python
def Josephus_Problem(N,K):
    soldiers = list(range(1,N+1))
    a = 1
    while True:
        if len(soldiers) == 2:
            break
        elif a == K:
            del soldiers[0]
            a = 1
            continue
        else:
            soldiers.append(soldiers[0])
            del soldiers[0]
            a += 1
            continue
    return soldiers[1]

if __name__ == '__main__':
    N,K = map(int, input().split()) 
    print(Josephus_Problem(N,K)) 
```
-----------------------------------
* 61번
```python
 
```
-----------------------------------
* 62번
```python
 
```
-----------------------------------
* [63번](https://codingdojang.com/scode/450?answer=26444#answer_26444)
  * 어떤 수를 소수의 곱으로만 나타내는 것을 소인수분해라 하고, 이 소수들을 그 수의 소인수라고 한다.                            
예를 들면 13195의 소인수는 5, 7, 13, 29 이다.                       
600851475143의 소인수 중에서 가장 큰 수를 구하시오.                     
```python
def Largest_prime_factor(s):
    a = 2
    while a < s:
        if s%a == 0:
            s = s//a
        a += 1
    return s


if __name__ == '__main__':
    s = int(input())
    print(Largest_prime_factor(s)) 
```
-----------------------------------
* [67번](https://codingdojang.com/scode/457?answer=26469#answer_26469)
  * 아래는 괄호를 이용한 연산식이다.                    
(5+6)∗(7+8)/(4+3)                          
우리는 여는 괄호가 있으면 닫는 괄호가 반드시 있어야 한다는 것을 잘 알고 있다.                            
  * 다음은 정상적인(balanced) 괄호 사용의 예이다.                           
(()()()())                         
(((())))                   
(()((())()))                                   
  * 다음은 비정상적인(not balanced) 괄호 사용의 예이다.                       
((((((())               
()))                         
(()()(()                   
(()))(                        
())(()                               
  * 괄호의 사용이 잘 되었는지 잘못 되었는지 판별 해 주는 프로그램을 작성하시오.                            
```python
def SimpleBalancedParentheses(a,x = False):
    cnt = 0
    for i in a:
        if i == '(':
            cnt += 1
        else:
            cnt = cnt -1
    if cnt < 0:
        return x
    elif cnt == 0:
        return True
    else:
        return cnt == 0

if __name__ == '__main__':
    a = input()
    print(SimpleBalancedParentheses(a)) 
```
-----------------------------------
* 68번
```python
 
```
-----------------------------------
* [73번](https://codingdojang.com/scode/465?answer=26480#answer_26480)
  * 문자열을 입력받아서, 같은 문자가 연속적으로 반복되는 경우에 그 반복 횟수를 표시하여 문자열을 압축하기.                 
입력 예시: aaabbcccccca                 
출력 예시: a3b2c6a1                    
```python
def string_short(a):
    c = []
    cnt = 0
    for i in a:
        if cnt == 0:
            c.append(i)
            cnt += 1
        elif i == c[-1]:
            cnt += 1
        elif i != c[-1]:
            c.append(str(cnt))
            c.append(i)
            cnt = 1
    c.append(str(cnt))
    return "".join(c)

if __name__ == '__main__':
    a = input()
    print(string_short(a)) 
```
-----------------------------------
* 74번
```python
 
```
-----------------------------------
* [76번](https://codingdojang.com/scode/469?answer=26484#answer_26484)
  * 문자열 형식으로 입력 받은 모스코드(dot: . dash:-)를 해독하여 영어 문장으로 출력하는 프로그램을 작성하시오.              
글자와 글자 사이는 공백 하나, 단어와 단어 사이는 공백 두개로 구분한다.                   
예를 들어 다음 모스부호는 "he sleeps early"로 해석해야 한다.               
.... .  ... .-.. . . .--. ...  . .- .-. .-.. -.--                        
모스부호 규칙 표                
문자	부호	문자	부호                   
A	.-	N	-.                  
B	-...	O	---               
C	-.-.	P	.--.                
D	-..	Q	--.-                
E	.	R	.-.                  
F	..-.	S	...              
G	--.	T	-          
H	....	U	..-                 
I	..	V	...-                 
J	.---	W	.--                   
K	-.-	X	-..-                  
L	.-..	Y	-.--                
M	--	Z	--..           
```python
a = {'.-':'A','-...':'B','-.-.':'C','-..':'D','.':'E','..-.':'F',
    '--.':'G','....':'H','..':'I','.---':'J','-.-':'K','.-..':'L',
    '--':'M','-.':'N','---':'O','.--.':'P','--.-':'Q','.-.':'R',
    '...':'S','-':'T','..-':'U','...-':'V','.--':'W','-..-':'X',
    '-.--':'Y','--..':'Z','':' '}
def morse_code(morse):
    for i in morse.split(' '): 
        print(a[i],end='')

if __name__ == '__main__':
    morse = ".... .  ... .-.. . . .--. ...  . .- .-. .-.. -.--"
    morse_code(morse)   
```
-----------------------------------
* [78번](https://codingdojang.com/scode/471?answer=26486#answer_26486)
  * 20150111을 출력합니다.                  
4가지 기준만 만족하면 됩니다.                       
코드 내에 숫자가 없어야 합니다.                       
파일 이름이나 경로를 사용해서는 안됩니다.                    
시간, 날짜 함수를 사용해서는 안됩니다.                    
에러 번호 출력을 이용해서는 안됩니다.                 
```python
def number_print(a,c):
    k = ''
    for i in c:
        k += str(a.index(i))
    return k
    print(a,c)

if __name__ == '__main__':
    a = 'abcdef' 
    c = 'cabfabbb'
    print(number_print(a,c)) 
```
-----------------------------------
