# SwiftUIGenericDialog

Pull to refresh is a common UI pattern, supported in UIKit via UIRefreshControl. (Un)surprisingly, it's also unavailable in SwiftUI.

This package contains a component - `RefreshableScrollView`  - that enables this functionality with any `ScrollView`. It also doesn't rely on `UIViewRepresentable`. The end result will look like this:

![in action](https://swiftuirecipes.com/user/pages/01.blog/pull-to-refresh-with-swiftui-scrollview/ezgif-4-bf1673b185d4.gif)

### Recipe

Check out [this recipe](https://swiftuirecipes.com/blog/pull-to-refresh-with-swiftui-scrollview) for in-depth description of the component and its code. Check out [SwiftUIRecipes.com](https://swiftuirecipes.com) for more **SwiftUI recipes**!

### Sample usage

```swift
struct TestView: View {
  @State private var now = Date()

  var body: some View {
     RefreshableScrollView(onRefresh: { done in
        DispatchQueue.main.asyncAfter(deadline: .now() + 3) {
          self.now = Date()
          done()
        }
      }) {
        VStack {
          ForEach(1..<20) {
            Text("\(Calendar.current.date(byAdding: .hour, value: $0, to: now)!)")
               .padding(.bottom, 10)
           }
         }.padding()
       }
     }
   }
}
```

### Installation

This component is distrubuted as a **Swift package**. 
