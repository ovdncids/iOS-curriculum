# iOS - Swift

## 목차
* [변수](#변수-variable)
* [상수](#상수-constant)
* [연산자](#연산자-operator)
* [if문](#if문제어문--조건문)
* [배열](#배열)
* [for문](#for문제어문--반복문)
* [함수](#함수)
* [오브젝트](#오브젝트-객체)
* [try catch문](#try-catch문제어문--예외처리문)

## 개발환경 설정
```sh
# 프로젝트 생성
Xcode > Create a new Xcode Project > iOS > App >
  Product Name: SwiftStudy

# 실행
iOS Simulator 선택(iPhone SE) > 실행 버튼 누르기

## 실행중 오류가 발생하면 Team을 등록 해야 한다.
좌측 Project navigator > SwiftStudy > Signing & Capabilities > Team >
  Add an Account...
```

### Xcode
```sh
# 에디터창 분할
파일 선택 후 오른쪽 상단쪽에 네모에 쌓여있는 +버튼 누르기

# Xcode에서 Finder 열기
File > Show in Finder

# Finder에서 Terminal 열기
Finder > 서비스 > 폴더에서 새로운 터미널 열기

# Xcode에서 경로 복사 후 Terminal 열고 이동
좌측 Project navigator > SwiftStudy > Show File Inspector > Full Path > Path 복사
Terminal > cd `복사한 Path 붙여 넣기`
```

# 기본 문법

## 테스트 문서 파일 만들기
SwiftStudyTests > New file... > Swift File > VariableTests.swift
```swift
import XCTest

class VariableTests: XCTestCase {
    func test() throws {
        print(1)
        print("a")
        print(true)
    }
}
```
* `print(1)` 라인번호를 눌러서 `breakpoint` 생성
* `class` 라인번호에 있는 다이아몬드 버튼 눌러서 테스트 실행
* ` 모드` 설명

## Git
```sh
# Commit
좌측 Source control navigator > Changes > 하단에 ... > Commit...

# Github 연결
## github에서 새로운 레파지토리 SwiftStudy 생성
좌측 Source control navigator > Repositories > SwiftStudy > Add Existing Remote...
  Remote Name: origin
  Location: https://github.com/xxx/SwiftStudy.git

# Push
상단 Source Control > Push... > origin/main
  Sgin in to your Github account
    Account: 깃헙계정
    Token: 생성한 토큰
  Create a token on Github
    # 토큰을 생성하면서 다음 권한 선택
    admin:public_key
    write:discussion
    repo
    user
```
* [Create a token on Github](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

<!--
.gitignore
```
# Breakpoint
**/Breakpoints_v2.xcbkptlist

# 사용자 화면 배치
**/UserInterfaceState.xcuserstate
```
-->

## 변수 (Variable)
### 변수를 사용하는 이유
1. 자료형 데이터를 보관 할 수 있고, 자유롭게 값을 수정 할 수 있다.
```swift
func testVariable1() throws {
    // 변수 Create
    var v1 = true
    var v2 = 100
    var v3 = "abc"

    // 변수 Read
    print(v1, v2, v3)

    // 변수 Update
    v1 = false
    v2 = -10
    v3 = "def"

    // 변수 Read
    print(v1, v2, v3);

    // 변수 Delete
}
```
* 자료형에는 `Boolean`(true, false), `Number`(숫자), `String`(문자) 3가지가 주로 쓰인다.
* `var` 선언문 설명
* `print()` 설명
* ❔ `v1` 변수에 var를 2번 선언 한다면
* ❔ 선언 하지 않은 `v4` 변수를 `print(v4)`로 읽는(Read)다면
* `변수`에 대한 `CRUD` 설명
* ❕ `변수명`에 대한 규칙
  ```
  제어문 이름으로 사용 불가 (if, for, switch, while, ...)
  연산자 이름으로 사용 불가 (+, -, *, /, ==, !, <, >, self, ...)
  자료형 또는 예약어(명령어) 사용 불가 (true, false, nil, ...)
  숫자를 앞으로 사용 불가 (1a, 2b, ...)
  영문, _, 숫자 조합으로 사용 (_a, b1, c_2, ...)
  대소문자 구분 (lowUP, LowUp, LOWUP)
  주로 `Camel(낙타) 표기법`으로 사용 (carUse, busTake, ...)
  ```

2. `디버깅 모드`에서 연산의 과정을 볼 수 있다.
```swift
func testVariable2() throws {
    print(1 + 2 + 3)
    var num1 = 1
    var num2 = 2
    var num3 = 3
    var sum1 = num1 + num2
    var sum2 = sum1 + num3
    print(sum2)
}
```
* ❕ 경고 해결은 숙제

3. 변수 수정으로 프로그램 전체를 수정 가능하다.
```swift
func testVariable3() throws {
    var calc = 100
    print(calc + 10)
    print(calc - 10)
    print(calc * 10)
    print(calc / 10)
}
```
* ❔ 변수 `calc` 값 수정해 보기

### 한줄에 변수 여러개 선언하기 (선언문)
```swift
var a, b, c
```
* ❔ 문제: 한줄로 변수 `a, b, c`에 각각 `1, 2, 3` 넣어 보기
* <details><summary>정답</summary>

  ```swift
  var a = 1, b = 2, c = 3
  ```
</details>

## 상수 (Constant)
SwiftStudyTests/ConstantTests.swift
```swift
import XCTest

class ConstantTests: XCTestCase {

}
```

### 상수를 사용하는 이유
1. 한번 선언된 값의 변경을 막기 위해 사용 한다.
```swift
func testConstant() throws {
    // 상수 Create
    let c1 = true
    let c2 = 100
    let c3 = "abc"

    // 상수 Read
    print(c1, c2, c3)

    // 상수 Update
    // 상수 Delete
}
```
* ❔ c1 상수에 const을 2번 선언 한다면
* ❔ c1 상수에 값을 변경해 보기
* 상수에 대한 CRUD 설명

## 연산자 (Operator)
SwiftStudyTests/OperatorTests.swift
```swift
import XCTest

class OperatorTests: XCTestCase {

}
```

1. 문자에 대한 사칙 연산자 (`+, -, *, /`)
```swift
func testOperator1() throws {
    let int1 = 1
    let int2 = 2
    let result1 = int1 + int2
    let result2 = int1 - int2
    let result3 = int1 * int2
    let result4 = int1 / int2
}
```
* ❔ `int1` 값을 문자 "1"로 바꾼다면
* ❔ `int2` 값을 문자 "2"로 바꾼다면
* ❔ `int1` 값을 문자 "a"로 `int2` 값을 문자 "b"로 바꾼다면
* ❔ 문제: 다음의 `r` 값은?
  ```swift
  let r = 2 + "1"
  ```
* <details><summary>정답</summary>

  ```swift
  오류 발생
  ```
</details>

* ❔ 문제: 프리랜서 개발자가 월 500만원을 받고 있다. 3.3% 원천징수를 때고 받는 실수령액과 세금을 계산하라.
  ```swift
  let salary: Double = 5000000
  let rate: Double = 3.3
  let tax: Double = ??
  let realSalary = ??

  힌트: 세금 계산식 = 급여 * 원천징수 / 100
  ```
* <details><summary>정답</summary>

  ```swift
  let salary: Double = 5000000
  let rate: Double = 3.3
  let tax: Double = salary * rate / 100
  let realSalary = salary - tax
  ```
</details>
* ❔ `: Double`을 `: Int`로 바꾼다면

2. 일치 연산자
```swift
let oNum1 = "1" == "1"
let oNum2 = true != false
```
* ❕ 연산이 끝나면 `Boolean` 형식으로 결과를 반환한다.
* ❔ 문자 "1"을 숫자 `1` 바꾼다면
* ❔ 논리 `true`를 문자 "true"로 바꾼다면
* ❔ 문제: `1`과 `2`를 `일치 연산자`로 비교 후에 상수 `x`에 넣고, `x`를 `print`로 찍어 보기
* <details><summary>정답</summary>

  ```swift
  let x = 1 == 2
  print(x)
  ```
</details>

3. 비교 연산자 (<, <=, >, >=)
```swift
let compare1 = 1 < 1
let compare2 = 2 <= 2
let compare3 = 3 > 3
let compare4 = 4 >= 4
```

4. 논리 연산자 (&&, ||)
```swift
let logical1 = true && true
let logical2 = false || false
```
* `&&`를 사용하는 상황: 로그인이 되어 있고, 글수정 권한이 있는 아이디인 경우, 글수정 버튼 활성화
* `||`를 사용하는 상황: 프리미엄 회원이거나 광고를 본 경우, 영상 시청 가능
* ❕ `true && true`를 `true && 1`으로 바꾼다면
* ❕ `false || false`를 `false || "a"`으로 바꾼다면
* ❕ `논리 연산자`는 주로 `if문` 안에서 사용

5. 소괄호() 연산자
```swift
let roundBracket1 = 1 + 2 * 3
let roundBracket2 = (1 + 2) * 3
let roundBracket3 = ((1 + 2) * 3)
```
* ❕ `소괄호 연산자`는 `사칙 연산자`보다 우선 순위를 갖는다.
* ❔ 문제: `소괄호 연산자` 안에서 `true`와 `false`를 `일치 연산자`로 연산 후에 상수 `y`에 넣고, `y`를 `print`로 찍어 보기
* <details><summary>정답</summary>

  ```swift
  let y = (true == false)
  print(y)
  ```
</details>

## if문(제어문 > 조건문)
1. 기본 구조
```swift
if (조건1) {
    // 조건1이 참인 경우 실행
} else if (조건2) {
    // 조건2가 참인 경우 실행
} else if (조건3) {
    // 조건3이 참인 경우 실행
    // else if는 여러게 사용 가능
} else {
    // 해당 되는 조건이 없을 경우 실행
}
```
* 예제
```swift
let if1 = 1
if (if1 == 1) {
    print("참1")
} else if (if1 == 2 || if1 == 3) {
    print("참2 또는 참3")
} else if (if1 == 4 && true) {
    print("참4")
} else {
    print("거짓")
}
```
* 조건은 주로 연산자를 사용해서 `Boolean` 형식으로 받는다.
* `if1` 값을 수정하여 `참2 또는 참3`이 나오게 만들기
* `if1` 값을 수정하여 `참4`이 나오게 만들기
* `if1` 값을 수정하여 `거짓`이 나오게 만들기

* ❔ 문제: 조건이 `1 == 1`인 `if`문을 만들고, 참인 경우 `print("참")`을 찍어 보기
* <details><summary>정답</summary>

  ```swift
  if (1 == 1) {
      print("참")
  }
  ```
</details>

### 3항 연산자
```swift
let condition3 = 1 == 1 ? "a" : "b"
```
* ❔ 문제: 조건이 `2 == 3`인 `3항 연산자`문을 만들고, 참인 경우 `"c"` 거짓인 경우 `"d"`를 `condition4` 상수에 넣어 보기
* <details><summary>정답</summary>

  ```swift
  let condition4 = 2 == 3 ? "c" : "d"
  ```
</details>

## 배열
SwiftStudyTests/ArrayTests.swift
```swift
import XCTest

class ArrayTests: XCTestCase {

}
```

### 배열을 사용하는 이유
1. 순차적인 반복 작업에 사용한다. (주로 동일한 데이터 타입으로 묶인 경우가 많다.)
2. 숫자(index)를 바탕으로 해당 데이터에 접근 한다.

### 배열 선언, CRUD
```swift
func testArray1() throws {
    let array1: [Any] = []
    let array2 = [1, 2, 3]
}
```

https://t1.daumcdn.net/blogfile/fs8/27_25_21_25_0O7Ul_IMAGE_0_42.jpg?original&filename=42.jpg

### 배열의 CRUD
```swift
// 배열 Create
array1.append(1)
array1.append("2")
array1.append("삼")

// 배열 Read
array1[0]
let a1 = array1[0]
let a2 = array1[1]
let a3 = array1[2]

// 배열 Update
array1[0] = 0
array1[1] = false
array1[2] = [1, 2, 3]

// 배열 Delete
array1.remove(at: 0)
array1.remove(at: 1)
array1.remove(at: 2)
```
* ❔ `배열의 CRUD` 부분 주석 처리하고, 개발자 도구 Console 창에서 `배열의 CRUD` 실행 해보기

### 배열의 크기
```swift
let length1 = array1.count
let length2 = array2.count
let firstValue = array2.first
let lastValue = array2.last
```

### 배열의 성격
```swift
func testArray2() throws {
    var arr1 = [1, 2, 3]
    let arr2 = [1, 2, 3]
    // quiz1
    if (arr1 == arr2) {
      let result = "참"
      print(result)
    } else {
      let result = "거짓"
      print(result)
    }
    let quiz2 = arr1[5]
    // quiz3
    arr1[9] = 10
}
```
* ❔ 문제: `arr1`와 `arr2`는 같을까?
<!--
* <details><summary>정답</summary>

  https://ovdncids.github.io/javascript-curriculum/images/memory.png
  ```
  배열은 선언과 동시에 별도의 `메모리 공간`에 존재하고, 변수는 단지 해당 배열이 있는 `메모리 주소`를 가지고 있다.
  따라서 `arr1`과 `arr2`는 서로 다른 배열의 주소를 가지므로 같지 않다.
  만약 `arr1` 변수의 값을 변화 시킨다면, `메모리 주소`를 잃어 버리므로 해당 배열은 더이상 접근할 수 없게 된다.
  ```
</details>
-->
* ❔ 해당 배열이 가진 `count`보다 큰 `index`를 `Read` 한다면?
* ❔ 해당 배열이 가진 `count`보다 큰 `index`를 `Update` 한다면?

### 익명 배열
```swift
print([1, 2, 3])
```
* 해당 배열의 `메모리 주소`를 누구도 받지 않으므로 재사용 할 수 없다.

### 배열 실습
* 1부터 5까지 더하기(total 변수를 만들어서 한번씩 더해서 만듬)
```swift
func testArray3() throws {
    var testArray1 = [1, 2, 3, 4, 5]
    var  total1 = testArray1[0]
    total1 = total1 + testArray1[1]
    total1 = total1 + testArray1[2]
    total1 += testArray1[3]
    total1 += testArray1[4]
}
```

* `testArray1` 평균 구하기
```swift
let avg = total1 / testArray1.count
```

* `testArray1` 홀수만 더하기
```swift
let odd1 = testArray1[0] + testArray1[2] + testArray1[4]
```

* `testArray1` 짝수만 더하기
```swift
let even1 = testArray1[1] + testArray1[3]
```

* 홀수만 지우기
```swift
testArray1.remove(at: 0)
testArray1.remove(at: 1)
testArray1.remove(at: 2)
```
* ❔ 문제: 짝수만 지우기

## for문(제어문 > 반복문)
SwiftStudyTests/ForTests.swift
```swift
import XCTest

class ForTests: XCTestCase {

}
```

### for문을 사용하는 이유
1. 반복 작업을 한곳으로 묶기 위해 사용함 (주로 배열이 사용 된다.)
2. 주로 게시판에 목록을 보여줄때 주로 사용함

### for문 문법
1. 기본 구조1
```swift
for 변수 in 초기값...마지막값 {
    실행문
    ...
}
```
* 예제
```swift
func testFor1() throws {
    for index1 in 0...2 {
        print(index1)
    }
}
```

2. break
```swift
for index2 in 0...2 {
    print(index2)
    break
}
```

3. continue
```swift
for index3 in 0...2 {
    if (index3 == 1) {
        continue
    }
    print(index3)
}
```

* ❔ 문제: `1`부터 `10`까지 반복에서 `5`보다 작은 경우만 `실행문`에서 `print`로 찍어 보기
* <details><summary>정답</summary>

  ```swift
  for index4 in 1...10 {
      if (index4 < 5) {
          print(index4)
      }
  }
   ```
</details>

* ❔ 문제: `2`부터 `9`까지 반복에서 `6`보다 작은 경우 `실행문`에서 `print`로 찍어고, 크면 `for문`을 빠져 나가기
* <details><summary>정답</summary>

  ```swift
  for index5 in 2...9 {
      if (index5 < 6) {
          print(index5)
      } else {
          break
      }
  }
  ```
</details>

### 홀수와 짝수 표현하기
```swift
for index6 in 1...10 {
    if (index6 % 2 == 1) {
        print("숫자 " + String(index6) + "은 홀수 입니다.")
    } else {
        print("숫자 " + String(index6) + "은 짝수 입니다.")
    }
    let oddEven = index6 % 2 == 1 ? "홀수" : "짝수"
    print("숫자 " + String(index6) + "은 " + oddEven + " 입니다.")
}
```

### for문의 범위(Scope), 로컬(Local) 변수와 블록(Block) 변수의 차이
1. 초기문 사용하지 않기
```swift
var index7 = 0
for index7 in 0...3 {
    let blockLet = index7
    print(blockLet)
}
print(index7)
```
* 가림 현상 설명 (Xcode에서 `index7` 마우스 오버해보기, Ctrl(또는 command) 키를 눌러서 해당 변수 이동)
* Block(Local) 변수 설명
* ❔ `for문` 안의 변수 `index7`을 `_index7`으로 변경 (에러가 발생할지 생각해 보기)
* `print` 밑에 `index7 += 1` 넣기
* ❕ 결과적으로 `변수 index7`은 for문이 반복된 횟수가 된다.
* ❔ 문제: `for문` 위에 `변수 total1`에 `0`을 넣고, `for문`을 이용해 `total1`에 1부터 5까지 더하고, `total1`을 `for문` 밖에서 `print`로 찍어 보기
* <details><summary>정답</summary>

  ```swift
  var total1 = 0
  for index8 in 1...5 {
      total1 += index8
  }
  print(total1)
  ```
</details>

* ❔ 문제: `total1`의 `평균` 값을 구해 `avg1` 상수에 넣고, `avg1`을 `print`로 찍어 보기
* ❕ 힌트: 평균으로 나눌 `5`값을 얻는 과정이 중요 (변수 또는 상수를 여러개 사용해도 무관, 사직연산 가능)
* <details><summary>정답</summary>

  ```swift
  var total1 = 0
  var count = 0
  for index8 in 1...5 {
      total1 += index8
      count += 1
  }
  let avg1 = total1 / count
  print(avg1)
  ```
  `total1 / 5` 이렇게 바로 나누었다면, 나중에 프로그램이 1에서 10까지로 변한다면, `5`값을 `2군데`에서 수정 해야 한다.
</details>

### for문에서 배열 사용하기
```swift
let array1 = [1, 2, 3]
for (var index9 = 0; index9 < array1.length; index9++) {
  print(array1[index9])
}
```
* ❔ 문제: `Script 상수 array2`에 `빈 배열`을 넣고, 위에 for문을 이용해 `array2` 배열을 `[1, 2, 3]`으로 만들고, `array2`를 for문이 끝나고 `print`로 찍어 보기
* <details><summary>정답</summary>

  ```swift
  let array1 = [1, 2, 3]
  let array2 = []
  for (var index9 = 0; index9 < array1.length; index9++) {
    array2.push(array1[index9])
  }
  print(array2)
  ```
</details>

* ❕ 결과적으로 `array2`는 `array1`을 복사하였다.
* ❔ `array1 === array2` 참일까요?
* ❕ 메모리 설명
```swift
var array3 = [1, 2, 3]
var array4 = array3
```
* ❔ `array3 === array4` 참일까?
```swift
array3 = 3
array4 = 4
```
* ❔ 문제: `array3`에서 사용하던 배열에 다시 접근할 수 있을까?
* <details><summary>정답</summary>

  없다. (따라서 배열은 `let`로 사용 해야한다.)
</details>

### index++와 ++index의 차이
```swift
var index = 0
let diff1 = index++
let diff2 = ++index
```
* <details><summary>동작</summary>

  ```swift
  var index = 0
  // let diff1 = index++
  let diff1 = index
  index += 1

  // let diff2 = ++index
  index += 1
  let diff2 = index
  ```
</details>
