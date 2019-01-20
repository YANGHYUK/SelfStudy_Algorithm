<h1>
    048_removeNumbersLargerThan
<h3>
    Object안에서 주어진 조건에 맞는 value값 추출하기

문제

```
Write a function called "removeNumbersLargerThan".

Given a number and an object, "removeNumbersLargerThan" removes any properties whose values are numbers greater than the given number.

var obj = {
  a: 8,
  b: 2,
  c: 'montana'
}
removeNumbersLargerThan(5, obj);
console.log(obj); // --> { b: 2, c: 'montana' }
```



풀이

```javascript
function removeNumbersLargerThan(num, obj) {
  
  for(var keys in obj){
    if(obj[keys] > num ){
        delete obj[keys]    
    }
  }
    return obj;
}

removeNumbersLargerThan(5, obj);  // -->  { b: 2, c: 'montana' }

```



이 문제를 풀면서 한 가지 중요하게 여겨져야 되는 부분이 있음을 알게 되었다.  

그 부분은 아래와 같다.

```javascript
if(obj[keys] > num )
```

문제에서 원하는 조건은 Object의 Value값이 주어진 num 보다 작은 것들을 선별하고 그와 동시에 Value의 Type이 String것들은 그대로 남겨두는 것이다.

그런데 위의 if(obj[keys] > num) 이라는 조건 하나만으로도 원하는 num의 조건에 맞는 값들을 선별함과 동시에 Value의 Type이 String인 것을 자동으로 건너뛰어준다.  

즉, 보통 숫자와 문자를 비교할 수 없다고 생각되지만 

javascript에서는 . . .
if 함수의 조건이 주어지면, 입력된 Data type이 'string'임에도 그 조건에 지나치고 자동으로 Data type이 'number'인 값과 비교해준다.

