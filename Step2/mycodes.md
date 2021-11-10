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
* [83번](https://codingdojang.com/scode/476?answer=26500#answer_26500)
  * 요약                              
초기 투자액과 투자 기간, 그리고 투자 기간 중 날짜별 가치 변동율이 주어질 때 순이익과 이익 여부를 구합니다.                                                 
  * 입력                                 
첫째 줄에 투자액이 정수로 주어집니다. 두번째 줄에 투자기간이 정수로 주어집니다. 세번째 줄에 투자기간 중 일별 전일 대비 가치 변동이 각각 퍼센트 단위의 정수로 주어집니다.               
투자액은 100 이상 10000 이하의 정수입니다.      
투자 기간은 1 이상 10 이하의 정수입니다.                
일별 변동폭은 -100 이상 100 이하의 정수로 주어집니다.          
  * 출력                                     
첫째 줄에 순이익을 소수점 첫째자리에서 반올림한 값으로 나타냅니다. 두번째 줄에 이익인지 손해인지 여부를 good, same, bad로 나타냅니다. 이익이면 good, 손해이면 bad, 첫째줄에서 출력한 순이익이 0이면 same울 출력합니다.                                                             
  * 예시                    
    * 입력 예시                 
10000                       
4                                                           
10 -10 5 -5               
    * 출력 예시                
-125             
bad         
```python
def stock_investment(a,f,c):
    b = a
    for i in c:
        b += b * i//100
    if b-a > 0.5:
        return b-a, "good"
    elif b-a < -0.5:
        return b-a, "bad"
    else:
        return b-a,"same"

if __name__ == '__main__':
    a = 10000
    f = 4
    c = [10,-10,5,-5]
    print(stock_investment(a,f,c)) 
```
-----------------------------------
* [86번](https://codingdojang.com/scode/480?answer=26509#answer_26509)
  * Write a program that lets the user enter in an odd positive integer (you may assume the input is always valid), and prints out an ASCII art letter N made using the character N.                       
  * If the input is 1, the output is:                
N                    
  * If the input is 3, the output is:                        
N N                   
NNN                 
N N                   
  * If the input is 5, the output is:                                       
N   N                           
NN  N                                                                 
N N N                  
N  NN                  
N   N                   
  * If the input is 7, the output is:                    
N     N                                         
NN    N                
N N   N                 
N  N  N                                                                                 
N   N N                       
N    NN                  
N     N                   
  * The pattern continues on like this. The output may contain trailing spaces.                
```python
def ASCLL_Art_N(a):
    for i in range(a):
        for c in range(a):
            if c == 0 or c == i or c == a-1:
                print('N',end = '')
            else:
                print(' ', end = ' ')
        print()
if __name__ == '__main__':
    a = int(input())
    ASCLL_Art_N(a) 
```
-----------------------------------
* [90번](https://codingdojang.com/scode/484?answer=26517#answer_26517)
  * 파이썬과 같은 몇몇 프로그래밍 언어는 Pothole_case 를 더 선호하는 언어라고 합니다.                     
  * Example:                
codingDojang --> coding_dojang                
numGoat30 --> num_goat_3_0                      
  * 위 보기와 같이 CameleCase를 Pothole_case 로 바꾸는 함수를 만들어요!      
```python
def change(a):
    b = '0123456789'
    n = a[0]     
    for i in a[1:]:
        if i.isupper():
            i = '_'+i.lower()
        elif i in b:
            i = '_'+i
        n += i
    return n

if __name__ == '__main__':
    a = input()
    print(change(a))


첫 번째 대문자는 패스했습니다. 
```
-----------------------------------
* 91번
```python
 
```
-----------------------------------
* [94번](https://codingdojang.com/scode/490?answer=26524#answer_26524)
  * 기계를 구입하려 하는데 이 기계는 추가 부품을 장착할 수 있다. 추가 부품은 종류당 하나씩만 장착 가능하고, 모든 추가 부품은 동일한 가격을 가진다.   
원래 기계의 가격과 성능, 추가 부품의 가격과 각 부품의 성능이 주어졌을 때, 추가 부품을 장착하여 얻을 수 있는 최대 가성비를 정수 부분까지 구하시오(가격 및 성능은 상대적인 값으로 수치화되어 주어진다).                
e.g.)                                                
원래 기계의 가격 : 10                           
원래 기계의 성능 : 150                         
추가 부품의 가격 : 3                       
추가 부품의 성능 : 각각 30, 70, 15, 40, 65                    
추가 부품을 장착하여 얻을 수 있는 최대 가성비 : 17.81... → 17                
(성능이 70과 65인 부품을 장착하면 됨)                    
```python
def cost_performance(price, performance, add_price, add_performance):
    a = []
    for i in add_performance:
        if ((performance / price) < ((performance+i) / (price+add_price))): # 부품을 추가했을 때 성능이 더 좋아졌다면
            performance += i
            price += add_price
            a.append(i)
    print(a)
    return int(performance / price) 
if __name__ ==  '__main__':
    price = 10
    performance = 150
    add_price = 3
    add_performance = [30,70,15,40,65]
    print(cost_performance(price, performance, add_price, add_performance))
```
-----------------------------------
* 95번
```python
 
```
-----------------------------------
* 98번
```python
 
```
-----------------------------------
* 100번
```python
 
```
-----------------------------------
* [104번](https://codingdojang.com/scode/503?answer=26525#answer_26525)
  * 2이상 1000이하 자연수의 집합에서 소수의 개수를 구하는 알고리즘을 작성하시오.                           
```python
def decimal(a):
    count = 0
    for i in range(2,a+1):
        cnt = 0
        for  c in range(1,i+1):
            if i%c == 0:
                cnt += 1
        if cnt == 2:
            count += 1

    return count       

if __name__ == '__main__':
    a = int(input())
    print(decimal(a))
 
```
-----------------------------------
* [108번](https://codingdojang.com/scode/507?answer=26600#answer_26600)
  * 몬테카를로 방법은 과학과 공학 전 영역에 걸쳐 널리 사용되는 방법이다.                        
  * 확률적인 해석을 요구하는 문제를 풀고싶을 때, 이 방법이 주로 쓰인다. 역사적으로는 물리학에서 자주 사용되었다고 전해진다.                                 
  * 1940년도에 원자로의 연쇄 반응 제어를 최초로 실현한 물리학자 엔리코 페르미는 중성자 확산(Neutron Diffusion)을 연구하면서, 이 방법을 자주 사용하였고, 로스앨러모스에서 맨하탄 프로젝트가 수행될 때 현대적인 버전의 몬테카를로 방법이 개발되었다고 전해진다.                                                
  * 몬테카를로 방법의 가장 간단한 예시로는 원주율(π)의 값을 추정하는 것이다.                                     
  * 넓이가 1인 정사각형을 생각하자. 정사각형의 한 꼭지점을 중심으로 반지름이 1인 사분원을 정사각형 안에 그린다. 그러면 사분원이 차지하는 넓이는 π/4가 될 것이다. 이제, 0 <= x <= 1인 x를 임의로 가져오고, 독립적으로 0 <= y <= 1인 y를 임의로 가져온 후, x^2 + y^2 <= 1일 확률은 사분원이 차지하는 넓이와 같은 값인 π/4가 된다.                                            
  * 이 과정을 여러 번 수행하는 알고리즘을 작성하고, 원주율의 값을 추정하시오.                   
```python                    
import random
def Montecarlo_Method(a):
    cnt = 0
    for i in range(a):
        b = random.uniform(0,1)
        c = random.uniform(0,1)
        if b*b + c*c <= 1:
            cnt += 1
    π = (4*cnt)/a
    return π


if __name__ == '__main__':
    a =  int(input("반복횟수입력:"))  
    print(Montecarlo_Method(a)) 
```
-----------------------------------
* 110번
```python
 
```
-----------------------------------
* [117번](https://codingdojang.com/scode/525?answer=26585#answer_26585)
  * 감옥에 120명의 죄수가 있다. 간수는 복도를 120번 동안 다음 조건에 지나간다.                           
처음에 문은 모두 닫혀 있다.                   
N번째 지나갈 때에는 N의 배수인 문들이 열려 있으면 닫고, 닫혀 있으면 연다.                
마지막에 문이 열려 있으면 그 방의 죄수는 석방이다.                             
과연 몇 명의 죄수가 석방될까?             
```python
def prisoner(a):
    for i in range(1,len(a)): # 지나가는 횟수
        for n in range(1,len(a)): # 방 번호
            if n%i == 0: # 방번호가 지나가는 횟수의 배수라면 
                a[n] = a[n]*(-1) 
            else:
                continue
    return a.count(-1)

if __name__ == '__main__':
    a = [1]*121
    print(prisoner(a)) 
```
-----------------------------------
* 118번
```python
 
```
-----------------------------------
* 121번
```python
 
```
-----------------------------------
* 129번
```python
 
```
-----------------------------------
* [132번](https://codingdojang.com/scode/546?answer=26589#answer_26589)
  * 1 ~ 10 사이의 어떤 수로도 나누어 떨어지는 가장 작은 수는 2520입니다.                     
그러면 1 ~ 20 사이의 어떤 수로도 나누어 떨어지는 가장 작은 수는 얼마입니까?                         
```python
def smallest_multiple(a):
    i = a
    while True:
        x = 0
        i += 2
        for y in range(1,a+1):
            if i%y == 0:
                x += 1
            else:
                break
    if x == a:
        return i

if __name__ == '__main__':
    a = 20
    print(smallest_multiple(a))   
```
-----------------------------------
* 133번
```python
 
```
-----------------------------------
* 137번
```python
 
```
-----------------------------------
* [140번](https://codingdojang.com/scode/558?answer=26594#answer_26594)
  * 2^15 = 32768 의 각 자리수를 더하면 3 + 2 + 7 + 6 + 8 = 26 입니다.                       
  * 2^1000의 각 자리수를 모두 더하면 얼마입니까?                     
```python
def squared():
    b = 0
    for i in str(2**1000):
        b += int(i)
    return b   

if __name__ == '__main__':
    print(squared()) 
```
-----------------------------------
* 143번
```python
 
```
-----------------------------------
* 146번
```python
 
```
-----------------------------------
* 147번
```python
 
```
-----------------------------------
* 149번
```python
 
```
-----------------------------------
* 150번
```python
 
```
-----------------------------------
* 161번
```python
 
```
-----------------------------------
* 167번
```python
 
```
-----------------------------------
* [168번](https://codingdojang.com/scode/593?answer=26604#answer_26604)
  * 밥 아저씨는 돈을 힘들게 모은 끝에 한 토지를 구입했다.                                         
밥 아저씨는 그 토지에 유명한 식물을 심을려고 하는데, 그 식물은 주변 √n 미터 안에 다른 식물이 있으면 자라지 못한 다고 한다.                      
그러므로 토지의 넓이를 n으로 나누어야 한다.                      
토지의 가로와 세로의 길이를 입력받을때, 최대 심을 수 있는 식물의 개수는?               
(단, n의 값은 식이 성립하는 n의 범위 중에서 최대여야 한다.)                                        
  * 예)                                      
  * 640  400                                                      
1980 640               
  * 답)                                 
  * 40                                                          
3168                                      
  * 단 반드시 그 나무를 중심으로 한 √n 영역이 필요하다. 그리고 그 영역이 다른 영역과 겹치면 안된다                    
```python
def split_the_farm(h,v):
    n=1
    lst=[]
    while n < v:
        if h%n==0 and v%n==0:
            lst.append(n)
        n+=1
    return int((h*v/max(lst)**2))

if __name__ == '__main__':
    h=int(input("가로의 길이를 입력하십시오: "))
    v=int(input("세로의 길이를 입력하십시오: "))
    print(split_the_farm(h,v)) 
```
-----------------------------------
* [171번](https://codingdojang.com/scode/597?answer=26614#answer_26614)
  * File #1
수의 특별한 의미를 부여하는 것을 수비주의라고 한다.                  
당신은 어떤 사건을 수사하기 위해 수비주의 클럽에 들어가야한다.                        
다만 이 클럽에 들어가기 위해서는 어떤 수를 입력받고 그 수가 어떤 수인지 알려주는 프로그램을 작성해야 한다.                   
문제) 양의 정수 n을 입력받고 그 수가 과잉수인지 완전수인지 부족수인지 출력하시오.                       
예)                                             
6                
20               
15                 
답)               
완전수입니다                    
과잉수입니다                
부족수입니다                          
File #2                                                
우여곡절 끝에 당신은 수비주의 클럽에 들어가게 되었다.                   
그러다 범인을 잡을 수 있는 파일을 알게되고,                  
그 파일에 위치가 회장에 컴퓨터에 있다는 것도 알게 되었다.                                           
그 정보가 확실한지는 모르겠지만 달리 방법이 없는 터라 그 컴퓨터에 접속해야한다.                      
하지만 그 컴퓨터에는 암호가 있었고, 정해진 시간이 있는지라 그 암호를 프로그램을 이용해 입력해야한다.               
문제) 어떤 수를 입력받고 진약수들의 합과 그 수가 친화수인지 혼약수인지 일반 수인지 출력하시오.                
그러나 그 수가 혼약수이면 (친화수들의 합 -1)을 출력해야 한다.                            
예)                 
220                    
75                 
20                               
출력)                
284, 친화수입니다.                 
48, 혼약수입니다.                                               
22, 일반 수입니다.                           
진약수 : 어떤 수의 자기자신을 제외한 약수 (예 - 20의 진약수는 1,2,4,5,10)              
완전수 : 진약수들의 합이 자기 자신인 수                     
과잉수 : 진약수들의 합이 자기 자신보다 큰 수                         
부족수 : 진약수들의 합이 자기 자신보다 작은 수                     
친화수 : 두 수의 쌍이 있어, 어느 한 수의 진약수를 모두 더하면 다른 수가 되는 수                
혼약수 : 두 수의 쌍이 있어,( 어느 한 수의 진약수 - 1)를 모두 더하면 다른 수가 되는 수                             
```python                            
def defensiveness(a):
    c = 0
    for i in range(1,a):
        if a%i == 0:
            c += i
    return c

if __name__ == '__main__':
    a = int(input())
    s = defensiveness(a)
    if s == a:
        print('완전수')
    elif s < a:
        print('부족수')
    else:
        print('과잉수')
    K = 0
    for w in range(1,s):
        if s%w == 0:
            K += w
    if K == a:
        print('{0},친화수'.format(s))
    else:
        F = 0
        m = s-1
        for r in range(1,m):
            if m%r == 0:
                F += r
        if m == a:
            print('{0},혼약수'.format(m))
        else:
            print('{0},일반수'.format(s))
```
-----------------------------------
* 175번
```python
 
```
-----------------------------------
* 176번
```python
 
```
-----------------------------------
* 181번
```python
 
```
-----------------------------------
* [185번](https://codingdojang.com/scode/612?answer=26610#answer_26610)
  * 리스트에 있는 숫자들의 최빈값을 구하는 프로그램을 만들어라.             
[12, 17, 19, 17, 23] = 17                
[26, 37, 26, 37, 91] = 26, 37              
[28, 30, 32, 34, 144] = 없다                
최빈값 : 자료의 값 중에서 가장 많이 나타난 값               
① 자료의 값이 모두 같거나 모두 다르면 최빈값은 없다.                   
② 자료의 값이 모두 다를 때, 도수가 가장 큰 값이 1개 이상 있으면 그 값은 모두 최빈값이다.                     
```python
def print_mode(c):
    a = {i:c.count(i) for i in c}
    b = [n for n in a.keys()
        if a[n] == max(a.values()) and a[n] > 1]
    if b == []:
        b = ['없다']

    return "{0}".format(b)

c = [[12, 17, 19, 17, 23],[26, 37, 26, 37, 91],[28, 30, 32, 34, 144]]
for i in c:
    print(print_mode(i)) 
```
-----------------------------------
* 192번
```python
 
```
-----------------------------------
* [193번](https://codingdojang.com/scode/623?answer=26624#answer_26624)
  * 당신은 A 인터넷 카페 운영자이다.          
당신의 인터넷 카페에는 휴대폰 번호 시가 금지되어 있다.                                          
하지만 일부 회원들이 편법을 동원하여 휴대폰 번호를 게시 후 불법 거래를 시도한다.                
이를 체크하여 자동 삭제를 할 수 있도록 휴대폰 번호 검사 알고리즘을 작성하시오.             
(011~019 는 10자리여도 휴대폰 번호이다. 010은 11자리여야만 한다.)                   
    * Input                              
영일영-구구칠8-일구팔사                      
0일영.칠칠칠팔.이삼사                   
영 일 칠 삼 칠 오 팔 이 팔 이                              
영일일 34구구 4 오 9 이                      
    * Output                                       
01099781984 true                     
0107778234 false                   
0173758282 true                   
01134994592 true                      
```python
def check_phone_number(a):
    e = {'영':'0', '일':'1', '이':'2', '삼':'3', '사':'4', '오':'5', '육':'6', '칠':'7', '팔':'8', '구':'9'}
    c = []
    for i in a:
        if i in e.keys():
            c.append(e[i])
        elif i in e.values():
            c.append(i)
    print(" ".join(c),end=' ')
    if len(c) == 11 and c[0]+c[1] == '01' and c[2] in e.values():
        return True
    elif len(c) == 10 and c[0]+c[1] == '01' and c[2] in e.values():
        return True
    return False
        
a = "영일일 34구구 4 오 9 이"
print(check_phone_number(list(a)))
 
```
-----------------------------------
* 194번
```python
 
```
-----------------------------------
* 196번
```python
 
```
-----------------------------------
* 200번
```python
 
```
-----------------------------------
* 203번
```python
 
```
-----------------------------------
* [207번](https://codingdojang.com/scode/638?answer=26629#answer_26629)
  * 약수를 모두 찾는 수학 문제를 풀다가 지친 X는 컴퓨터의 도움을 받아 문제를 풀어 보기로 하였다. 하지만 계산기를 이용하자니 계산기로 하고 싶지만 찾기도 어려우며, 쉽게 찾아낼 수도 없었다.   
풀이에 지친 그는 결국 약수들이 가지고 있는 특징을 찾아 결국 몇시간에 걸쳐 복잡한 수라도 약수를 찾아줄 수 있고 개수도 알려주는 프로그램을 짜게 된다.                                     
다음은 약수를 얻기 위한 입력과 출력 예제들이다.                         
` * 입력 1                                     
24                      
출력 1                     
{ 1, 2, 3, 4, 6, 8, 12, 24}                    
약수의 개수는 8개 입니다.                    
  * 입력 2                  
36               
출력 2                           
{ 1, 2, 3, 4, 6, 9, 12, 18, 36 }                   
약수의 개수는 9개 입니다.                    
  * 입력 3                
2468013579               
출력 3                                   
{ 1, 3, 9, 61, 183, 549, 4495471, 13486413, 40459239, 274223731, 822671193, 2468013579 }                                
  * 약수의 개수는 12개 입니다.                                                                             
사용한 소스코드를 풀이에 넣어 입력과 출력이 나왔음을 보이고,                            
소스코드를 디버깅하여 123456789를 입력해 출력된 결과를 '{ a, b, ... } / 약수의 개수는 ~ 개 입니다' 형식으로 하시오.                                          
```python 
num = int(input('숫자 입력: '))
divisor = [1]
i = 2

while i <= num:
    if num % i == 0:
        divisor.append(i)
    i += 1

print(divisor)
print("약수의 개수는 %d개 입니다." % len(divisor))
```
-----------------------------------
