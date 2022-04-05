# SwiftUI
* https://developer.apple.com/tutorials/swiftui

## 미리보기
```sh
# Editor > Canvas 체크
# SwiftStudy/ContentView.swift > Resume > 50% > Play 버튼으로 Live 모드
## Live 모드에서 XCode 오류가 덜 발생함
```

## 단축키
* Command + Click: `Editor 창`에서 해당 속성의 `자주 사용하는 메뉴` 띄우기
* Control + Option + Click: `Editor 창`에서 해당 속성의 `UI 메뉴` 띄우기

## 이미지, SwiftUI View 추가
* Assets < 이미지 추가
* File > New > File... > SwiftUI View > 파일명
```swift
struct 파일명: View {
    var body: some View {
        Image("추가 이미지명")
    }
}
```

## JSON 파일 추가
```sh
# JSON 파일을 프로젝트로 Drag > Copy items if nedded > 체크
## 이제 프로젝트 어디서든 사용 가능
```
