# Struct type
## Struct와 Class의 가장 큰 차이
* Class는 `참조 복사`하고, Struct는 `깊은 복사`를 한다.

## 배열의 메모리 주소
```swift
func testFor4() throws {
    func getBufferAddress<T>(array: [T]) -> Int {
        return array.withUnsafeBufferPointer { buffer in
            return Int(bitPattern: buffer.baseAddress)
        }
    }
    var array3 = [1, 2, 3]
    var array4 = array3
    print(getBufferAddress(array: array3))
    print(getBufferAddress(array: array4))
    print(getBufferAddress(array: array3) == getBufferAddress(array: array4))
}
```
* ❕ 메모리 설명
* ❕ 배열은 `Struct 형`이다.
* ❔ `array3 == array4` 참일까?
* [Copy on write](https://icksw.tistory.com/256) 설명

```swift
array3 = [3]
array4 = [4]
print(getBufferAddress(array: array3))
print(getBufferAddress(array: array4))
print(getBufferAddress(array: array3) == getBufferAddress(array: array4))
```
* ❔ 문제: `array3`에서 사용하던 `[1, 2, 3]` 배열에 다시 접근할 수 있을까?
* ❔ `array3[0] = 3` 이렇게 값을 동일 하게 수정 해도 `메모리 주소`가 변할까?
* [깊은 복사, 얕은 복사](https://velog.io/@ellyheetov/Shallow-Copy-VS-Deep-Copy)
