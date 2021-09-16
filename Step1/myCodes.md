* [105번](https://codingdojang.com/scode/504?answer=25989#answer_25989)
    * 1~1000에서 각 숫자의 개수 구하기
```python
num = ""
for t in range(1 ,1001):
    num += str(t)

for f in range(10):
    a = num.count('%d' % f)
    print("%d의 개수 : %d" % (f,a))
```
-----------------------------------
* [106번](https://codingdojang.com/scode/505?answer=26007#answer_26007)
    * 10~1000까지 각 숫자 분해하여 곱하기의 전체 합 구하기
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
* [120번](https://codingdojang.com/scode/529?answer=26049#answer_26049)
    * DashInsert 함수는 숫자로 구성된 문자열을 입력받은 뒤, 문자열 내에서 홀수가 연속되면 두 수 사이에 - 를 추가하고, 짝수가 연속되면 * 를 추가하는 기능을 갖고 있다. (예, 454 => 454, 4546793 => 454*67-9-3) DashInsert 함수를 완성하자.
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
* [128번](https://codingdojang.com/scode/539?answer=26026#answer_26026)
    * 자기 자신을 제외한 모든 양의 약수들의 합이 자기 자신이 되는 자연수를 완전수라고 한다. 예를 들면, 6과 28은 완전수이다. 6=1+2+3 // 1,2,3은 각각 6의 약수 28=1+2+4+7+14 // 1,2,4,7,14는 각각 28의 약수
    * 입력으로 자연수 N을 받고, 출력으로 N 이하의 모든 완전수를 출력하는 코드를 작성하라
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

* [131번](https://codingdojang.com/scode/545?answer=26066#answer_26066)
    * 세 자연수 a, b, c 가 피타고라스 정리 a^2 + b^2 = c^2 를 만족하면 피타고라스 수라고 부릅니다 (여기서 a < b < c ). 예를 들면 3^2 + 4^2 = 9 + 16 = 25 = 5^2 이므로 3, 4, 5는 피타고라스 수입니다.
    * a + b + c = 1000 인 피타고라스 수 a, b, c는 한 가지 뿐입니다. 이 때, a × b × c 는 얼마입니까?
```python
for c in range(1, 1000):
    for b in range(1, c-1):
        for a in range(1, b-1):
            if (a*a)+(b*b) == c*c and a+b+c == 1000:
                print(a*b*c)
                break
```
-----------------------------------

* [134번](https://codingdojang.com/scode/548?answer=26074#answer_26074)
    * 피보나치 수열의 각 항은 바로 앞의 항 두 개를 더한 것이 됩니다. 1과 2로 시작하는 경우 이 수열은 아래와 같습니다.
    * 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...
    * 짝수이면서 4백만 이하인 모든 항을 더하면 얼마가 됩니까?
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
* [136번](https://codingdojang.com/scode/553?answer=26082#answer_26082)
    * 1부터 10까지 자연수를 각각 제곱해 더하면 다음과 같습니다 (제곱의 합). 1^2 + 2^2 + ... + 10^2 = 385 1부터 10을 먼저 더한 다음에 그 결과를 제곱하면 다음과 같습니다 (합의 제곱). (1 + 2 + ... + 10)^2 = 55^2 = 3025 따라서 1부터 10까지 자연수에 대해 "합의 제곱"과 "제곱의 합" 의 차이는 3025 - 385 = 2640 이 됩니다. 그러면 1부터 100까지 자연수에 대해 "합의 제곱"과 "제곱의 합"의 차이는 얼마입니까?
```python
a = 0
b = 0
for i in range(1,101):
    a += i
    b += i*i

print((a*a) - (b))    
```
-----------------------------------
* [138번](https://codingdojang.com/scode/555?answer=26105#answer_26105)
    * 시저 암호는, 고대 로마의 황제 줄리어스 시저가 만들어 낸 암호인데, 예를 들어 알파벳 A를 입력했을 때, 그 알파벳의 n개 뒤에 오는(여기서는 예를 들 때 3으로 지정하였다)알파벳이 출력되는 것이다. 예를 들어 바꾸려는 단어가 'CAT"고, n을 5로 지정하였을 때 "HFY"가 되는 것이다.
    * 어떠한 암호를 만들 문장과 n을 입력했을 때 암호를 만들어 출력하는 프로그램을 작성해라.
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
* [139번](https://codingdojang.com/scode/556?answer=26149#answer_26149)
    * 2진법이란, 어떤 자연수를 0과 1로만 나타내는 것이다. 예를 들어 73은 64(2^6)+8(2^3)+1(2^0)이기 때문에 1001001으로 표현한다. 어떤 숫자를 입력받았을 때 그 숫자를 2진법으로 출력하는 프로그램을 작성하시오.
```python
n=int(input())

result=""
while n>1:
    result+= str(n%2)
    n = n//2

print(result + str(n))
```
-----------------------------------
* [144번](https://codingdojang.com/scode/562?answer=26163#answer_26163)
    * 앞에서부터 읽을 때나 뒤에서부터 읽을 때나 모양이 같은 수를 대칭수(palindrome)라고 부릅니다. 두 자리 수를 곱해 만들 수 있는 대칭수 중 가장 큰 수는 9009 (= 91 × 99) 입니다. 세 자리 수를 곱해 만들 수 있는 가장 큰 대칭수는 얼마입니까?
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
* [159번](https://codingdojang.com/scode/584?answer=26199#answer_26199)
   * 1부터 10까지의 어떤 수로도 나누어 떨어지는 가장 작은 수는 2520입니다.
   * 그렇다면 1부터 20까지의 어떤 수로도 나누어 떨어지는 가장 작은 수는 얼마입니까?
```python
lastNumber = 20
i = lastNumber
while True:
    t = 0
    i += 1
    for n in range(1, lastNumber+1):
        if i%n == 0:
            t += 1
        else:
            break    
    if t == lastNumber:
        break
        
print(i)   
```
-----------------------------------
* [160번](https://codingdojang.com/scode/585)
   * 3개의 숫자를 입력으로 받고 3개의 숫자 중에 중간값을 가지는 숫자를 출력하세요. ex1) 2, 5, 3 => 3 ex2) 4, 6, 4 => 4
```python
a = int(input('첫번째 숫자 입력: '))
b = int(input('두번째 숫자 입력: '))
c = int(input('세번째 숫자 입력: '))
result = []
for i in a,b,c:
    result.append(i)

print(sorted(result)[1])    
```
-----------------------------------
* [163번](https://codingdojang.com/scode/588)
   * 양의 정수만 입력으로 받고 그 수의 자릿수를 출력해보자. ex1) 3 > 1자리수, ex2) 649 > 3자리수 ....
```python
a= input('숫자 입력: ')
print(len(a))    
```
-----------------------------------
* [164번](https://codingdojang.com/scode/589?answer=26209#answer_26209)
   * 네이버 글자수세기 등 특정 글의 글자를 세는 프로그램은 일반적으로 공백을 제외한 글자수만을 세는 기능도 가지고 있다.
어떠한 문자열을 입력받았을 때 줄바꿈과 공백을 제외한 글자수만을 리턴하는 코드를 작성하시오.
   * 입력 예시
   * 공백을 제외한
글자수만을 세는 코드 테스트
   * 출력 예시
   * 18
```python
"방법1"
a = '공백을 제외한\n글자수만을 세는 코드 테스트'
d = a.count('\n')
b = a.count(' ')
a = len(a)
i = a - d - b
print(i)
"방법2"
a = '공백을 제외한\n글자수만을 세는 코드 테스트'
a = a.replace(" ", "")
a = a.replace("\n", "")
print(len(a))    
```
-----------------------------------
* [166번](https://codingdojang.com/scode/591?answer=26204#answer_26204)
   * 배열 [a, b, c, d]를 입력하면 배열[bcd, acd, abd, abc]를 출력하는 코드를 작성하시오.

(단, 나눗셈 사용 금지)

입출력되는 배열은 어떤 형식이든 상관없습니다.
   * 입력 예시
   * 2, 6, 4, 7
   * 출력 예시
   * 168, 56, 84, 48
```python
def get(a,b,c,d):
    i = b*c*d
    l = a*c*d
    t = a*b*d
    w = a*b*c
    return i,l,t,w

print(get(2,6,4,7))
```
-----------------------------------
* [169번](https://codingdojang.com/scode/595?answer=26212#answer_26212)
   * 철이는 아스키코드에 대해 공부하고있었습니다.
하지만 기억력이 좋지않아 순서를 잊어먹게되는탓에 프로그램을 하나 만들어두려합니다.
문자를 입력받으면 그 문자에 해당하는 아스키코드를 출력하는 코드를 작성해주세요.

   * 출력조건
      * a는 아스키코드로 97입니다.
      * d는 아스키코드로 100입니다.
      * A는 아스키코드로 65입니다.

```python
a = input('문자 1개입력: ')
i = ord(a)
print("%c는 아스키코드로 %d입니다." % (a,i))    
```
-----------------------------------
* [172번](https://codingdojang.com/scode/598?answer=26223#answer_26223)
   * 난이도:(쉬움) 현우는 축구를보다가 우리나라선수들의몸값을 알고싶었다

그래서 검색을해서 메모장에 적는데 키보드가 조그만하고 안좋은지라

자꾸 숫자가아닌 문자를 같이입력해버린다

ex: xxx : 1627000000 > xxx : 1w627r00o00p00 만 (특수문자제외)

현우는 왜인지모르지만 뜻대로안되는것에

너무화가나서 자신이수량을입력하면 문자열만 딱빼서 숫자만 반환하는 코드를 만들고싶어한다

화가난 현우를위해 코드를 만들어보자!
```python
a = input()
b = '0123456789'
for i in a:
    if i in b:
        print(i, end='')
```

```python
a = input()
b = ''
for i in a:
    if i.isdigit():
        b+=i    

print(b)
```
-----------------------------------
* [174번](https://codingdojang.com/scode/600?answer=26224#answer_26224)
   * (난이도:기초) 숫자를 입력받으면 그에해당하는 자릿수를 출력하는 코드를 작성하라.
   * 입력 : 156 출력 : 100의자리수

입력 : 18961 출력 : 10000의자릿수
```python
a= input()
a = len(a)
print("%d의자리수" % 10**(a-1))    
```
-----------------------------------
* [183번](https://codingdojang.com/scode/610?answer=26231#answer_26231)
   * 리스트에 있는 숫자들의 평균을 구하는 프로그램을 만들어라.
   * [4, 6, 8] = 6
   * [11, 17, 20, 24] = 18
   * [26, 33, 45, 51, 60] = 43
```python
a = [4,6,8]
print(sum(a)/len(a))    
```
-----------------------------------
* [184번](https://codingdojang.com/scode/611?answer=26241#answer_26241)
   * 리스트에 있는 숫자들의 중앙값을 구하는 프로그램을 만들어라.
[7, 9, 14] = 9
[24, 31, 35, 49] = 33
[17, 37, 37, 47, 57] = 37
중앙값 : 자료를 작은 값에서부터 크기순으로 나열할 때 중앙에 위치한 값
① 자료의 개수가 홀수이면 가운데 위치한 값이 중앙값이다.
② 자료의 개수가 짝수이면 가운데 위치한 두 값의 평균이 중앙값이다.

```python
even = [2, 4, 6, 8]
odd = [5, 7, 9, 11,13]

a = odd

mok = len(a) // 2
if len(a) % 2 == 1: # 홀수이면
    print(a[mok])
else: # 짝수이면
    print((a[mok] + a[mok-1])/2)
 
```
-----------------------------------
* [186번](https://codingdojang.com/scode/613?answer=26232#answer_26232)
   * 홀수와 짝수의 개수를 구하는 프로그램을 만들어라.
   * [3, 4, 5, 6, 7]
= 홀수 3개, 짝수 2개
   * [12, 16, 22, 24, 29]
= 홀수 1개, 짝수 4개 
   * [41, 43, 45, 47, 49]
= 홀수 5개, 짝수 0개
```python
a = [3,4,5,6,7]
result = 0
result1 = 0
for i in a:
    if i % 2 == 0:
        result1 += 1
    else:
        result += 1

print("홀수는{0}개, 짝수는{1}개".format(result,result1))     
```
-----------------------------------
* [187번](https://codingdojang.com/scode/614?answer=26250#answer_26250)
   * 3개의 각으로 삼각형의 예각, 직각, 둔각을 구별하는 프로그램을 만들어라.
[60, 60, 60] = 예각삼각형
[30, 60, 90] = 직각삼각형
[20, 40, 120] = 둔각삼각형
[0, 90, 90] = 삼각형이 아니다
[60, 70, 80] = 삼각형이 아니다
[40, 40, 50, 50] = 삼각형이 아니다
```python
def triangle(a):
    if(len(a)!=3 or sum(a)!=180) :
        return "It is not the triangle(삼각형이 아니다)"
    elif 90 in a:
        return "직각삼각형"
    elif max(a) > 90:
        return "둔각삼각형"
    else:
        return "예각삼각형"

if __name__ == '__main__':
    a = [70,50,90]   
    print(triangle(a)) 
```
-----------------------------------
* [208번](https://codingdojang.com/scode/639?answer=26249#answer_26249)
   * 초보자 프로그래머 홍길동은 사용자가 입력한 양의정수(범위는 int)각 자리수를 더해 출력하는 프로그램을 만들고 싶어한다. ex) 5923의 결과는 5+9+2+3인 19이다 ex) 200의 결과는 2+0+0인 2이다 ex) 6719283의 결과는 6+7+1+9+2+8+3인 36이다.
```python
a = input()
result = 0
j = len(a)
for i in range(j):
    result += int(a[i])

print(result)     
```
-----------------------------------
* 210번
```python
 
```
-----------------------------------
* [213번](https://codingdojang.com/scode/645?answer=26268#answer_26268)
   * 현우는 성인이되어 회사에입사했다.
하지만 들어간기업이 하필 할일없는 중소기업이라
퇴근시간까지 놀다가 퇴근시간에 퇴근하는것이 일상화가되어버렸다..
현우는 심심한지라 좀더효율적으로놀기위해
현재부터 퇴근시간까지 남은시간을 알려주는 계산기를 만들어
계산적으로놀고싶었다 우리가현우를 도와주자!!
(참고로 현우의퇴근시간은 17시30분이다)
input: 현재시간
output: 남은시간 : hh:mm:ss
or
남은시간 : s
심화버젼 : 이쁘게꾸며보자!
   * 퇴근시간 이후에 계산기를 작동시키면 "퇴근 시간이 지났습니다" 라고 출력하기
   * 남는시간을 초단위로 계산해서 구해보기
```python
import time

def compute_left_time(time_diff_second):
    ss = time_diff_second % 60  # 초를 60으로 나눈 나머지 = 초
    temp = time_diff_second // 60   # 초를 60으로 나는 몫 = 분
    mm = temp % 60    # 분을 60으로 나눈 나머지 = 분
    hh = temp // 60    # 분을 60으로 나눈 몫 = 시간
    return (hh, mm, ss)

def compute_time(h,m,s):
    current_time = 3600*h + 60*m + s
    get_off_time = 3600*17 + 60*30

    time_diff = get_off_time - current_time

    if(time_diff >= 0):
        hh, mm, ss = compute_left_time(time_diff)
        print(f'{hh}시간 {mm}분 {ss}초 남았습니다')
    else:
        time_diff = -time_diff
        hh, mm, ss = compute_left_time(time_diff)
        print(f'{hh}시간 {mm}분 {ss}초 지났습니다')

if __name__ == '__main__':
    t = time.localtime(time.time())
    hh = t.tm_hour
    mm = t.tm_min
    ss = t.tm_sec

    # print(compute_time(hh,mm,ss))
    compute_time(18,40,30)
```
-----------------------------------
* [214번](https://codingdojang.com/scode/646?answer=26269#answer_26269)
   * 문자와 숫자가섞인 문자열을 입력받을때 구별하여출력해라
input:
"c910m6ia 1ho"
output:
str : cma ho
int : 91061
```python
   "방법1"
a = input()
s = ""
n = ""
for i in a:
    if i <= '9':
        n += i
    else:
        s += i

print("str: {0}".format (s))
print("int: {0}".format (n))

"방법2"
a = input()
s = ""
n = ""
for i in a:
    if i.isdigit():
        n += i
    else:
        s += i

print("str: {0}".format (s))
print("int: {0}".format (n))
```
-----------------------------------
* [217번](https://codingdojang.com/scode/649?answer=26281#answer_26281)
   * 어떤 수 x와 n이 주어졌을때 조건에 따라 x가 n의 배수인지 판별하는 코드를 작성하라.
x는 0 이상의 정수이며 조건에 맞지 않는 입력은 주어지지 않는다.
여기서 하나의 함수인지 여러 함수인지는 본인이 선택하면 된다.
단 절대 산술연산자 중 %와 /는 코드에 없도록 한다.
그리고 divmod() 함수를 쓰는것도 금지한다
코드는 창의적으로 하는 것을 목적으로 한다. 속도는 크게 중점을 두지 않는다.
n의 종류는 2,3,5,7,11,13이다.
원하는 n만 선택해서 풀 수도 있다.
   * 입력   입력으로 주어질 자연수의 종류를 입력받고 차례로 그 수만큼 정수를 입력받는다.
      * 6     
      432 2   
      4 3   
      635 5   
      421 7   
      122 11   
      143 13   
   * 출력
      * 1     
      0     
      1    
      0   
      0   
      1   
   * 저는 인터넷에서 n의 배수 판정하는 법이란 글을 보게되어 여러분들에게 더욱 창의적인 방법을 묻고싶었는데
가장 기본을 생각못하다니 저도 참 무식한것 같습니다.
이미 푸신분들은 어쩔 수 없겠지만 최대한 이미 나온 조건과 더불어 이 조건도 추가하면 좋을것 같습니다.
저 좋으라고 하는일이 아닌 여러분들의 창의력을 키우기위한 문제이니까요 감사합니다.
```python
def multiple(i,s):
    while i >= s:
        i=i-s
    return i

if __name__ == '__main__':
    print(multiple(122,11)) 
```
-----------------------------------
* 238번
```python
 
```
-----------------------------------
* [246번](https://codingdojang.com/scode/685?answer=26288#answer_26288)
   * 프로그래머 X는 코딩을 하다가 문득, 수학 시간에 배운 정수와 소수를 구별하는 방법을 떠올렸다. 정수와 소수의 차이는 분수로 표현이 되느냐, 되지 않느냐에 따라 차이가 나기도 하며, 또한 파이 등 특정한 값을 나타내는 것에 의하여 소수인지 정수인지 판별이 나게 된다.
프로그래머 X는 입력값을 숫자를 입력하거나 문자를 입력하려고 하는데,
만약 숫자를 입력하였으면 그것이 정수인지, 소수인지 구별하는 프로그램을 짜보도록 하고,
만약 문자를 입력하였으면 숫자가 아니므로 math error를 표시하게 하라.
```python
def find_type(a):
    try:
        if a - int(a) == 0:
            print('정수')
        elif a - int(a) != 0:
            print('소수')   
    except:    
        print('math error')
if __name__ == '__main__':
    find_type(7446.78) 
```
-----------------------------------
* [247번](https://codingdojang.com/scode/686?answer=26296#answer_26296)
   * 기수(Cardinal)를 입력하면 영어 서수(Ordinal)로 출력하는 함수를 작성합니다.
      * 1, 21, 31, 41, ... → 1st, 21st, 31st, 41st, ...
      * 2, 22, 32, 42, ... → 2nd, 22nd, 32nd, 42nd, ...
      * 3, 23, 33, 43, ... → 3rd, 23rd, 33rd, 43rd, ...
      * 11, 12, 13, 111, 112, 113, 211, 212, 213, ...  → 11th, 12th, 13th, 111th, 112th, 113th, 211th, 212th, 213th, ...
      * 4, 5, 6, 11, 12, 13, 101, 111, 112, ... → 4th, 5th, 6th, 11th, 12th, 13th, 101th, 111th, 112th, ...
```python
def number_distinguish(a):
    i = str(a)
    if i[-1] == '1' and i[-2] != '1':
        print(i+'st')
    elif i[-1] == '2' and i[-2] != '1':
        print(i+'nd')
    elif i[-1] == '3' and i[-2] != '1':
        print(i+'rd')    
    else:
        print(i+'th')

number_distinguish(37)
 
```
-----------------------------------
* 256번
```python
 
```
-----------------------------------
* [258번](https://codingdojang.com/scode/702?answer=26302#answer_26302)
   * 항상 일정한 속도로 달리는 기계가 있다고 합시다. 이 기계의 100m 달리기 기록을 입력받으면 마라톤에서의 기록을 구하시면 됩니다. 마라톤 경기에서 달리는 거리는 42.195km입니다. 100m 달리기와 마라톤의 코스는 모두 직선이라고 합니다(회전 시 걸리는 시간을 고려하지 않습니다). 기계의 파손 및 배터리 방전 시간도 고려하지 않습니다.
```python
#결과에 소수점이 없다
record = int(input())
time = record * 42195 / 100
ss = int(time% 60)
temp = int(time // 60)
mm = int(temp % 60)
hh = int(temp // 60)
print('{0}시간 {1}분 {2}초'.format(hh,mm,ss))
#결과에 소수점이 있다
record = int(input())
time = record * 42195 / 100
ss = time% 60
temp = time // 60
mm = temp % 60
hh = temp // 60
print('{0}시간 {1}분 {2}초'.format(hh,mm,ss))
```
-----------------------------------
