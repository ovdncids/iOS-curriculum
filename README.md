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
  자료형 또는 예약어(명령어) 사용 불가 (true, false, null, ...)
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
