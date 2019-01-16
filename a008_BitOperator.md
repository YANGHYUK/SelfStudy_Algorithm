## 비트연산자 활용 /알고리즘[a008.isOddWithoutModulo.js]

주어진 알고리즘 문제

```javascript
function isOddWithoutModulo(num) {
    
}
var output = isOddWithoutModulo(-5);
console.log(output); // --> true
```



**Before** 기존에 풀이법

```javascript
function isOddWithoutModulo(num) {
  
  var AbsNum = Math.abs(num);
    if(num === 0){
        return false;
    }
  var result;
  for(var n = 1; n*2 <= AbsNum ; n++){
    result = n;
  }
  switch(AbsNum-result*2){
      case 1 :
        return true;
        break;
      case 0 :
        return false;
  }
}

var output = isOddWithoutModulo(-5);
console.log(output); // --> true
```

위의 기존 풀이법에서는 주어진 수에 절대값을 취하고(여기서 마이너스를 고려해줌) 2로 나누는 작업을 반복하여 몫을 먼저 찾고, 몫을 제외한 나머지의 **값**이 **1**이면 **true** 아니라면 **false**를 출력하게 하였다.

**BUT**

이진법을 공부하게 된 후의 풀이는 보다 간단해진다.



 **After** 이진법에 대한 맛을 본 후의 풀이법

```javascript
function isOddWithoutModulo(num) {
  var AbsNum = Math.abs(num);
  var BinaryNum = AbsNum.toString(2)  
  var LastIdxinBinary = BinaryNum[BinaryNum.length-1];

  if( LastIdxinBinary === '1' ){
    return true;
  }else{
    return false;
  }
}

var output = isOddWithoutModulo(-5);
console.log(output); // --> true
```

위의 풀이는 기존 풀이법과 마찬가지로 주어진 수에 절대값을 취하고 주어진 수가 **이진법** 인것을 확인한 후, **이진법** 의 1의 자리가 **1** 인지 **0** 인지를 판별하여 **true** 혹은 **false** 값을 판별한다.( 주어진 수가 0임을 고려할 필요도 없다. 만약 숫자가 0이라면 이진법의 1의 자리에서도 0이기 때문이다.)