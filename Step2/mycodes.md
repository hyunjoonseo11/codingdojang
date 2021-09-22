* 1번
```python
 
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
    a = input()
    b = input()
    for i in range(len(a)):
        if a.count('0') == len(a):
            return ' '
        if b.count('0') == len(b):
            return ' '   
        if int(a[-i]) + int(b[-i]) >= 10:
            cnt += 1
        else:
            cnt == 0
    if cnt == 0:
        return 'No carry operation.'
    elif cnt == 1:
        return '1 carry operation.'  
    else:
        return '{0} carry operations.'.format(cnt) 
if __name__ == '__main__':
    print(help_children())     
```
-----------------------------------
