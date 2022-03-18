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
  영문, _, $, 숫자 조합으로 사용 (_a, $b, c1, ...)
  대소문자 구분 (lowUP, LowUp, LOWUP)
  주로 `Camel(낙타) 표기법`으로 사용 (carUse, busTake, ...)
  ```

2. `디버깅 모드`에서 연산의 과정을 볼 수 있다.
```js
func testVariable1() throws {
    console.log(1 + 2 + 3);
    let num1 = 1;
    let num2 = 2;
    let num3 = 3;
    let sum1 = num1 + num2;
    let sum2 = sum1 + num3;
    console.log(sum2);
}
```
* breakpoint 설명

3. 변수 수정으로 프로그램 전체를 수정 가능하다.
```js
let calc = 100;
console.log(calc + 10);
console.log(calc - 10);
console.log(calc * 10);
console.log(calc / 10);
```
* ❔ 변수 `calc` 값 수정해 보기

### 한줄에 변수 여러개 선언하기 (선언문)
```js
let a, b, c;
```
* ❔ 문제: console.log(a); 한다면
* ❔ 문제: 한줄로 변수 `a, b, c`에 각각 `1, 2, 3` 넣어 보기
* <details><summary>정답</summary>

  ```js
  let a = 1, b = 2, c = 3;
  ```
</details>

## 상수 (Constant)
SwiftStudyTests/ConstantTests.swift
```swift
```
