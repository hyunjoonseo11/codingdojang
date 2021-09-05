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

print(get(2,6,4,7)
```
-----------------------------------
* [169번](https://codingdojang.com/scode/595?answer=26212#answer_26212)
   * 철이는 아스키코드에 대해 공부하고있었습니다.

하지만 기억력이 좋지않아 순서를 잊어먹게되는탓에 프로그램을 하나 만들어두려합니다.

문자를 입력받으면 그 문자에 해당하는 아스키코드를 출력하는 코드를 작성해주세요.
   * 출력조건

a는 아스키코드로 97입니다.

d는 아스키코드로 100입니다.

A는 아스키코드로 65입니다.
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
        print(i,end='')    
```
-----------------------------------
* [174번](https://codingdojang.com/scode/600?answer=26224#answer_26224)
   * (난이도:기초) 숫자를 입력받으면 그에해당하는 자릿수를 출력하는 코드를 작성하라.
   * 입력 : 156 출력 : 100의자리수

입력 : 18961 출력 : 10000의자릿수
```python
a= input()
a = len(a)
print("%d의자리수"%10**(a-1))    
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
* 184번
```python
 
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
