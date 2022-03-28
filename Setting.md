# Setting

## App 만들기, 실행
App.swift
```swift
print("Hello")
```
```sh
swiftc -o App App.swift
./App

# 한줄로
swiftc -o App App.swift; ./App
```

## Debugging Swift in VSCode
* https://dev.to/vknabel/debugging-swift-in-vs-code-in-2022-4blk

```sh
mkdir SwiftTests
cd SwiftTests
swift package init --type executable
code .

# 확장 > Swift > 설치 > VSCode 재시작
# CodeLLDB 묻는 창에서 Workspace 선택
# main.swift 파일에 Breakpoint 지정
# 실행 및 디버그 > Play 버튼 (Debug 보다는 Release가 빠름)
```
* ❕ 갑자기 `CPU` 사용이 늘어 난다면 `활성 상태 보기`에서 `electron` 중지

## Online Swift
* https://www.tutorialspoint.com/compile_swift_online.php
