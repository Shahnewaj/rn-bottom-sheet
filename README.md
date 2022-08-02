# rn-bottom-sheet


- Super Lightweight Component
- Add Your own Component To Bottom Sheet
- Customize Whatever You Like
- Support Drag Down Gesture
- Support All Orientations
- Support Both Android And iOS
- Smooth Animation
- Zero Configuration
- Zero dependency
- Top Search Ranking (react native bottom sheet) at [npms.io](https://npms.io/search?q=react%20native%20bottom%20sheet)

|                                                      Showcase iOS                                                      |                                                    Showcase Android                                                    |
| :--------------------------------------------------------------------------------------------------------------------: |

## Installation

```
npm i rn-bottom-sheet --save
```

### or

```
yarn add rn-bottom-sheet
```

## Example

#### Class component

```jsx
import React, { Component } from "react";
import { View, Button } from "react-native";
import RBSheet from "rn-bottom-sheet";

export default class Example extends Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
        <Button title="OPEN BOTTOM SHEET" onPress={() => this.RBSheet.open()} />
        <RBSheet
          ref={ref => {
            this.RBSheet = ref;
          }}
          height={300}
          openDuration={250}
          customStyles={{
            container: {
              justifyContent: "center",
              alignItems: "center"
            }
          }}
        >
          <YourOwnComponent />
        </RBSheet>
      </View>
    );
  }
}
```

#### Functional component

```jsx
import React, { useRef } from "react";
import { View, Button } from "react-native";
import RBSheet from "rn-bottom-sheet";

export default function Example() {
  const refRBSheet = useRef();
  return (
    <View
      style={{
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
        backgroundColor: "#000"
      }}
    >
      <Button title="OPEN BOTTOM SHEET" onPress={() => refRBSheet.current.open()} />
      <RBSheet
        ref={refRBSheet}
        closeOnDragDown={true}
        closeOnPressMask={false}
        customStyles={{
          wrapper: {
            backgroundColor: "transparent"
          },
          draggableIcon: {
            backgroundColor: "#000"
          }
        }}
      >
        <YourOwnComponent />
      </RBSheet>
    </View>
  );
}
```

#### Dynamic Bottom Sheet

```jsx
renderItem = (item, index) => (
  <View>
    <Button title={`OPEN BOTTOM SHEET-${index}`} onPress={() => this[RBSheet + index].open()} />
    <RBSheet
      ref={ref => {
        this[RBSheet + index] = ref;
      }}
    >
      <YourOwnComponent onPress={() => this[RBSheet + index].close()} />
    </RBSheet>
  </View>
);
```

## Props

| Props            | Type     | Description                                             | Default  |
| ---------------- | -------- | ------------------------------------------------------- | -------- |
| animationType    | string   | Background animation ("none", "fade", "slide")          | "none"   |
| statusBarTranslucent    | boolean         | Android Status Bar(true , false)          | "false"   |
| height           | number   | Height of Bottom Sheet                                  | 260      |
| minClosingHeight | number   | Minimum height of Bottom Sheet before close             | 0        |
| openDuration     | number   | Open Bottom Sheet animation duration                    | 300 (ms) |
| closeDuration    | number   | Close Bottom Sheet animation duration                   | 200 (ms) |
| closeOnDragDown  | boolean  | Use gesture drag down to close Bottom Sheet             | false    |
| dragFromTopOnly  | boolean  | Drag only the top area of the draggableIcon to close Bottom Sheet instead of the whole content | false    |
| closeOnPressMask | boolean  | Press the area outside to close Bottom Sheet            | true     |
| closeOnPressBack | boolean  | Press back android to close Bottom Sheet (Android only) | true     |
| onClose          | function | Callback function when Bottom Sheet has closed          | null     |
| onOpen           | function | Callback function when Bottom Sheet has opened          | null     |
| customStyles     | object   | Custom style to Bottom Sheet                            | {}       |
| keyboardAvoidingViewEnabled     | boolean   | Enable KeyboardAvoidingView             | true (ios) |

### Available Custom Style

```
customStyles: {
  wrapper: {...}, // The Root of Component (You can change the `backgroundColor` or any styles)
  container: {...}, // The Container of Bottom Sheet
  draggableIcon: {...} // The Draggable Icon (If you set closeOnDragDown to true)
}
```

## Methods

| Method Name | Description        |
| ----------- | ------------------ |
| open        | Open Bottom Sheet  |
| close       | Close Bottom Sheet |

## Note


## License

This project is licensed under the MIT License - see the [LICENSE.md](https://github.com/Shahnewaj/rn-bottom-sheet/blob/master/LICENSE) file for details

## Author

Made with ❤️ by [NY Samnang](https://github.com/Shahnewaj).
