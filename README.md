# SwiftUIGenericDialog

Display a **custom dialog in SwiftUI**. You can customize the dialog content in any way you want.

The end result can look like this:

![in action](https://swiftuirecipes.com/user/pages/01.blog/custom-view-dialog-in-swiftui/Screenshot%202021-02-03%20at%2012.57.05.png)

The package also contains a **progress dialog / HUD in SwiftUI**:

![in action](https://swiftuirecipes.com/user/pages/01.blog/progress-dialog-hud-in-swiftui/Screenshot%202021-02-18%20at%2011.07.59.png)

### Recipe

Check out [this recipe](https://swiftuirecipes.com/blog/custom-view-dialog-in-swiftui) for in-depth description of the component and its code, as well as [this one for the progress dialog](https://swiftuirecipes.com/blog/progress-dialog-hud-in-swiftui). Check out [SwiftUIRecipes.com](https://swiftuirecipes.com) for more **SwiftUI recipes**!

### Sample usage

```swift
struct DialogTest: View {
  @State private var showDialog = true
  var body: some View {
    List(1..<6) { index in
      Text("Item \(index)")
    }.customDialog(isShowing: $showDialog) { // HERE
      VStack {
        Text("Dialog title")
          .fontWeight(.bold)
        Divider()
        Text("Some longer description")
          .padding(.bottom, 10)
        Button(action: {
          showDialog = false            
        }) {
          Text("Close dialog")
            .autocapitalization(.allCharacters)
            .frame(minWidth: 0, maxWidth: .infinity)
            .padding()
        }.buttonStyle(MyButtonStyle())
      }.padding()
    }
  }
}

struct ProgressDialogTest: View {
  @State private var isLoading = false

  var body: some View {
    VStack {
      Text("Content")
    }.progressDialog(isShowing: $isLoading, message: "Loading...")
  }
}
```

### Installation

This component is distrubuted as a **Swift package**. 
