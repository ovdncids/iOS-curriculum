# Struct type
## Struct와 Class의 가장 큰 차이
* Class는 `참조 타입 객체`를 만들고, Struct는 `값 타입 객체`를 만든다.
* Class는 `참조 복사`하고, Struct는 `깊은 복사`를 한다.

SwiftStudyTests/StructTests.swift
```swift
import XCTest

class StructTests: XCTestCase {
    class Class1 {
        var key1 = true
        var key2 = 100
        var key3 = "abc"
    }
    struct Struct1 {
        var key1 = true
        var key2 = 100
        var key3 = "abc"
    }
    func testStruct1() throws {
        let class1 = Class1()
        let class2 = class1
        var struct1 = Struct1()
        let struct2 = struct1

        // Class 참조 복사 활용
        class1.key1 = false
        let compare1 = class1 === class2
        let compare2 = class1.key1 == class2.key1

        // Struct 깊은 복사 활용
        // let compare3 = struct1 == struct2
        // struct1.key1 = false
        // let compare4 = struct1 == struct2
        // let compare5 = struct1.key1 == struct2.key1
    }
}
```
* ❕ 메모리 설명
* `let compare3 = struct1 == struct2` 주석 풀고
```diff
- struct Struct1 {
+ struct Struct1: Equatable {
```

## 배열의 메모리 주소
* ❕ 배열은 `Struct 형`이다.
```swift
func testStruct2() throws {
    func getBufferAddress<T>(array: [T]) -> Int {
        return array.withUnsafeBufferPointer { buffer in
            return Int(bitPattern: buffer.baseAddress)
        }
    }
    var array1 = [1, 2, 3]
    var array2 = array1
    print(array1 == array2)
    print(getBufferAddress(array: array1))
    print(getBufferAddress(array: array2))
    print(getBufferAddress(array: array1) == getBufferAddress(array: array2))
}
```

```swift
array1[0] = 1
print(getBufferAddress(array: array1))
print(getBufferAddress(array: array2))
print(getBufferAddress(array: array1) == getBufferAddress(array: array2))
```
* ❔ `array1[0] = 1` 이렇게 값을 동일 하게 수정 해도 `메모리 주소`가 변할까?
<!-- * [깊은 복사, 얕은 복사](https://velog.io/@ellyheetov/Shallow-Copy-VS-Deep-Copy) -->
* [Copy on write](https://icksw.tistory.com/256) 설명
