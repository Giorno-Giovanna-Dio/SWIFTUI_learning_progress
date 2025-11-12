# Day 1 (11/12)
## Foundations
- struct view 會遵守 view 協定，所有文字或是按鈕都需要搭建在 view 上面
- view 只有要求在最後回傳的時候有個 body
- padding 會將整個 vstack 先padded 之後再回傳給 body
- #preview 是不會真實出現在app 當中的，只是用做 canvas去呈現目前的 app 運行概況的，如果要更新 canvas的話可以用快捷 `cmd+option+p`
## Form
- 創建一個灰底的列表
```Swift
Form {
  Section{
    Text("hello1")
  }
}
```
## Navigation Bar
```Swift
struct ContentView: View {
    var body: some View {
        NavigationStack{
            Form {
                    Section{
                        Text("hello1")
                    }
                    Section{
                        Text("hello2")
                        Text("hello3")
                    }
            }.navigationTitle("Navigation Bar")
             .navigationBarTitleDisplayMode(.inline)
        }
        
    }
}
```
## Program State Controll
When we say SwiftUI’s views are a function of their state, we mean that the way your user interface looks – the things people can see and what they can interact with – are determined by the state of your program.
### Property Wrapper
- 針對需要的變數開一個state
- 有 `@State` 可以繞過剛剛 struct 視為 constant的僵局
- 如果說這個變數只出現在當前的view 也可以加 `private`
```Swift
//Contentview is a struct so it's a constant which is immutable.
struct ContentView: View {
    @State var tapCount = 1000

    var body: some View {
        Button("Tap Count: \(tapCount)") {
            tapCount += 10
        }
    }
}
```
