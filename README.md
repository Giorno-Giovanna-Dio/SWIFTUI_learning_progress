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
### Binding state to user interface controls
- 為了可以顯示和修改一個變數的值這邊會使用 `two-way bindings`
- 要採取 two-way bindings 的變數前面要加個 `$`
- 如果是單純列印目前的變數值就不用 `$`
```Swift
import SwiftUI

struct ContentView: View {
    @State private var name = ""

    var body: some View {
        Form {
            TextField("Enter your name", text: $name)
            Text("Hello, world!")
            Text("Your name is \(name)")
        }
    }
}

#Preview {
    ContentView()
}
```
## Views in a Loop
For example, we might want to loop over an array of names and have each one be a text view, or loop over an array of menu items and have each one be shown as an image.

**`ForEach`** will run a closure once for every item it loops over, passing in the current loop item. For example, if we looped from 0 to 100 it would pass in 0, then 1, then 2, and so on.
```Swift
import SwiftUI

struct ContentView: View {
    let students = ["Harry", "Hermione", "Ron"]
    @State private var selectedStudent = "Harry"

    var body: some View {
        NavigationStack {
            Form {
                Picker("Select your student", selection: $selectedStudent) {
                    ForEach(students, id: \.self) {
                        Text($0)
                    }
                }
            }
        }
    }
}

#Preview {
    ContentView()
}
```
- 如果初始的 `selectedStudent` 給定的值不存在於陣列中，就不會顯示
- 因為需要讀和覆寫 `selectedStudent` 的值，所以前面需要 `$` 搭配 `@State`
- ForEach  中的 id 是綁定項目在 array 中的順序，改變id 會連帶影響項目在選單中呈現的順序
- ForEach 當中的 \.self  則是強調每個 string 的獨特性
---
# Day 2-3 (11/13-11/14)
## WeSplit App Accomplished
[WeSplit Project Repository](https://github.com/Giorno-Giovanna-Dio/SWIFTUI_WeSplit)
### Demo Video Below
[![Demo Video](https://img.youtube.com/vi/7df22bI3hK8/0.jpg)](https://youtu.be/7df22bI3hK8)
