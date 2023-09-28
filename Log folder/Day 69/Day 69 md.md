# Day 69

Tags: React Native
Date: September 22, 2023
Status: Done

Task of the day

Core Components

- Text
- Text Input
- Button
- Image
- imageBackground
- Switch
- StatusBar
- Activity indicator
- Modal
- Pressable

---

### Core components

Core components are the essential building blocks provided by React Native to create a user interface for mobile applications. They are platform-agnostic, meaning they work across both iOS and Android devices. Some of the common include: 

- `View` is a fundamental component for constructing the user interface. It is equivalent to a `div` in HTML and can be used as a container for other components.

```jsx
<Viewstyle={styles.container}>  <Text>Hello World!</Text></View>
```

- `Text` is used to display text content in your app. It is similar to the `p` or `span` elements in HTML.

```jsx
<Textstyle={styles.title}>Welcome to my App</Text>
```

- `Image` is used to display images in your application. It can load images from local sources or remote URLs.

```jsx
<Imagesource={require('./assets/logo.png')} /><Imagesource={{ uri: 'https://example.com/image.png' }} />
```

- `TextInput` is a basic input field that allows users to type text into your app. It is similar to the `input` element in HTML.

```jsx
<TextInputvalue={this.state.text}onChangeText={text =>this.setState({ text })}style={styles.input}/>
```

- `TouchableOpacity` is a wrapper for making elements like `View`and `Text` respond properly to touch events. It provides feedback by reducing the opacity of the wrapped component when pressed.

```jsx
<TouchableOpacityonPress={this.onButtonPress}>  <Textstyle={styles.buttonText}>Press me!</Text></TouchableOpacity>
```

- `ScrollView` is a scrollable container that allows users to scroll through its content. It is useful when you have content that exceeds the available screen size.

```jsx
<ScrollViewstyle={styles.scrollContainer}>  <Text>Content 1</Text>  <Text>Content 2</Text>  {/* ... */}</ScrollView>
```

- `FlatList` is used to render a list of items using a performant approach. It only renders items that are currently visible on the screen and removes others to save memory.

```jsx
<FlatListdata={this.state.data}renderItem={({item }) => <Text>{item.name}</Text>}keyExtractor={item => item.id}/>
```

These core components are foundational to creating functional and attractive interfaces for your React Native applications.

### Text Component

The **`Text`** component is a basic element in React Native used to display text content on the screen. While it has some basic styling properties, you usually nest it inside other components (e.g., **`View`**) to create more complex UIs.

Some common properties of the **`Text`** component include:

- `style`: Apply a set of styling rules to the text, such as font size, color, and font family.
- `numberOfLines`: Limit the number of lines shown in the text. This can be especially useful for long paragraphs or truncating a long title.
- `onPress`: Add a function that gets called when the user taps on the text.
- `allowFontScaling`: Specify whether to allow font scaling based on user’s font settings.

Here’s a simple example using the **`Text`** component:

```jsx
import React from 'react';
import { Text, StyleSheet } from 'react-native';

const SimpleText = () => {
  return (
    <Text style={styles.text} numberOfLines={2} onPress={() => alert('Hello')}>
      This is an example of a Text component in React Native. Tap on me!
    </Text>
  );
};

const styles = StyleSheet.create({
  text: {
    fontSize: 16,
    color: 'blue',
    textAlign: 'center',
    margin: 10,
    fontFamily: 'Arial',
  },
});

export default SimpleText;
```

In this example, we create a **`Text`** element with some text content, apply styling, limit it to two lines, and add an **`onPress`** event.

### Text Input

**`TextInput`** is a core component in React Native that allows the user to enter text. It is commonly used to collect user data, like emails or passwords. You can customize the appearance of **`TextInput`** by using various props such as **`placeholder`**, **`multiline`**, **`maxLength`**, and more.

Here’s a basic example of using **`TextInput`**:

```jsx
import React, { useState } from 'react';
import { TextInput, View, Button } from 'react-native';

const App = () => {
  const [text, setText] = useState('');

  const handleSubmit = () => {
    alert('You entered: ' + text);
  };

  return (
    <View>
      <TextInput
        style={{ height: 40, borderColor: 'gray', borderWidth: 1 }}
        onChangeText={text => setText(text)}
        value={text}
        placeholder="Enter text here"
      />
      <Button
        onPress={handleSubmit}
        title="Submit"
      />
    </View>
  );
};
```

In this example, the `TextInput` component is styled with a border, and there’s a placeholder text to show the user the expected input. The `onChangeText` prop is used to manage the state of the input text, and a “Submit” button is provided to process the input data.

### Button Component

A **`Button`** is a built-in React Native component used to create clickable buttons. It is a simple, customizable and easy-to-use component that captures touches and triggers an **`onPress`** event when pressed.

Here’s a simple example of how to create a Button in React Native

```jsx
import React from 'react';
import { Button } from 'react-native';

const MyButton = () => {
  const onPressHandler = () => {
    alert('Button Pressed');
  };

  return (
    <Button
      title="Click me"
      color="#841584"
      onPress={onPressHandler}
    />
  );
};

export default MyButton;
```

In this example, we import the Button component from ‘react-native’, create a functional component **`MyButton`**, and define an **`onPressHandler`** function that will be called when the button is pressed. We then use the **`Button`** component and pass in the following props:

- `title`: The text to display on the button.
- `color`: The background color of the button.
- `onPress`: The function to call when the button is pressed.

When the button is pressed, the **`onPressHandler`** function will be called, and an alert will pop up saying “Button Pressed”

### Image Component

The **`Image`** component is used to display images in a React Native application. It allows you to load and display local as well as remote images, providing essential props and methods for better image handling and customization.

To use the **`Image`** component, you need to import it from ‘react-native’:

```jsx
import { Image } from 'react-native';
```

To display a local image in the application, you have to require it in the **`source`** prop of the **`Image`** component. Place the image file in your project directory and use the following syntax:

```jsx
<Image source={{ uri: 'https://path/to/your/remote/image.png' }} />
```

Keep in mind that you need to define the dimensions (width and height) when using remote images:

```jsx
<Image source={{ uri: 'https://path/to/remote/image.png' }} style={{ width: 200, height: 200 }} />
```

You can set image scaling and positioning with the **`resizeMode`** prop. It accepts the following values: **`cover`**, **`contain`**, **`stretch`**, **`repeat`**, and **`center`**. Default value is **`cover`**.

```jsx
<Image source={require('./path/to/your/image.png')} resizeMode="contain" />
```

There are additional props which you can use to further modify the image behavior.

- `blurRadius`: Adds a blur effect to the image.
- `defaultSource`: Displays a placeholder image while the target image is loading (only for Android).
- `loadingIndicatorSource`: Similar to `defaultSource`, but works on both Android and iOS.
- `onLoad`: A callback function that gets called when the image finishes loading.

Here’s an example combining some of these props:

```jsx
<Image style={{ width: 300, height: 200 }}
       source={{ uri: 'https://path/to/remote/image.png' }}
       resizeMode="contain"
       onLoad={() => console.log('Image loaded')}>
```

### ImageBackground Component

**`ImageBackground`** is a React Native core component that allows you to display an image as a background while still being able to place content inside the component. This helps in creating beautiful layouts with images and text or other content on top.

To use **`ImageBackground`**, you need to import it from the **`react-native`** package and then include it in your JSX.

```jsx
import React from 'react';
import { View, Text, ImageBackground, StyleSheet } from 'react-native';

const App = () => (
  <ImageBackground
    source={{ uri: 'https://some-image-url.com/background.jpg' }}
    style={styles.background}
    resizeMode="cover"
  >
    <Text style={styles.text}>Hello, World!</Text>
  </ImageBackground>
);

const styles = StyleSheet.create({
  background: {
    flex: 1,
    justifyContent: 'center',
  },
  text: {
    color: 'white',
    fontSize: 42,
    lineHeight: 84,
    fontWeight: 'bold',
    textAlign: 'center',
  },
});

export default App;
```

In the above example, `source` prop is used to add the image URL, `style` prop for adding some custom styling, and `resizeMode` to define how the image should stretch to fill the available space. The `Text`component inside the `ImageBackground` is then rendered on top of the image.

### Switch Component

A **`Switch`** is a core component in React Native used to implement a “toggle” or “on-off” input. It provides a UI for the user to switch between two different states, typically true or false. The primary use case is to enable or disable a feature or setting within an application.

**`Switch`** component has a boolean **`value`** prop (true for on, false for off) and an **`onValueChange`** event handler, which is triggered whenever the user toggles the switch.

Here’s an example of how to use **`Switch`** in a React Native application:

```jsx
import React, {useState} from 'react';
import {View, Switch, Text} from 'react-native';

const App = () => {
  const [isEnabled, setIsEnabled] = useState(false);

  const toggleSwitch = () => setIsEnabled(previousState => !previousState);

  return (
    <View>
      <Text>Enable Feature:</Text>
      <Switch
     trackColor={{ false: "#767577", true: "#81b0ff" }}
     thumbColor={isEnabled ? "#f5dd4b" : "#f4f3f4"}
      onValueChange={toggleSwitch}
      value={isEnabled}
      />
    </View>
  );
};

export default App;
```

In this example, `Switch` component’s `value` prop is set to the state hook `isEnabled`. The `onValueChange` event handler triggers `toggleSwitch`function, which updates the state of `isEnabled`. The colors for the track and thumb of the switch can be customized using `trackColor` and `thumbColor` props.

### StatusBar component

The **`StatusBar`** component is used to control the appearance of the status bar on the top of the screen. It may strike as a bit unusual since, unlike other React Native components, it doesn’t render any visible content. Instead, it sets some native properties that can help customize the look of status bars on Android, iOS, or other platforms.

To use the **`StatusBar`** component, you need to import it from ‘react-native’ and use it in your **`React`** component. Here’s an example:

```jsx
import React from 'react';
import { View, StatusBar } from 'react-native';

const App = () => {
  return (
    <View>
      <StatusBar barStyle="dark-content" backgroundColor="#F0F0F0" />
      {/* Your other components */}
    </View>
  );
};

export default App;
```

Here are some common properties you might want to use:

- `barStyle`: Sets the color of the status bar text (light-content, dark-content, or default)
- `backgroundColor`: Sets the background color of the status bar (Android only)
- `hidden`: Hides or shows the status bar (true or false)
- `animated`: Defines whether or not to animate status bar style changes (true or false)
- `translucent`: Sets the status bar to be translucent (Android only)

You can set these properties like in the following example:

```jsx
<StatusBar
  barStyle="light-content"
  backgroundColor="#6A0E37"
  hidden={false}
  animated={true}
  translucent={true}
/>
```

Remember, some properties work only on specific platforms (Android/iOS), so it’s essential to check the compatibility when using different properties.

### Activity Indicator

The **`ActivityIndicator`** is a core component in React Native that provides a simple visual indication of some ongoing activity or loading state within your application. It shows a spinning animation, which gives the user feedback that something is happening in the background. This component is particularly useful when fetching data from an external source, like a server, or while performing time-consuming operations.

To use the **`ActivityIndicator`** component, simply import it from ‘react-native’, and add it to your component tree. You can customize the appearance and behavior of the **`ActivityIndicator`** by providing various optional props, such as **`animating`**, **`color`**, and **`size`**.

Below is an example of how to use the **`ActivityIndicator`** component within a functional React component:

```jsx
import React from 'react';
import { ActivityIndicator, View, Text } from 'react-native';

const LoadingScreen = () => (
  <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
    <Text>Loading, please wait...</Text>
    <ActivityIndicator size="large" color="#0000ff" />
  </View>
);

export default LoadingScreen;
```

In this example, the `ActivityIndicator` is placed within a `View`component alongside a `Text` component. The `ActivityIndicator` has its `size` set to ‘large’ and `color` set to blue. By default, the component will be animating. If you want to control the animation, you can use the `animating` prop and set it to `true` or `false`.

### Modal Component

A **`Modal`** is a component that displays content on top of the current view, creating an overlay that can be used for various purposes, such as displaying additional information, confirmation messages, or a selection menu.

```jsx
import React, {useState} from 'react';
import {Modal, Text, TouchableHighlight, View, Alert} from 'react-native';

const App = () => {
  const [modalVisible, setModalVisible] = useState(false);

  return (
    <View>
      <Modal
        animationType="slide"
        transparent={true}
        visible={modalVisible}
        onRequestClose={() => {
          Alert.alert('Modal has been closed.');
          setModalVisible(!modalVisible);
        }}>
        <View>
          <View>
            <Text>Hello, I am a Modal!</Text>

            <TouchableHighlight
              onPress={() => {
                setModalVisible(!modalVisible);
              }}>
              <Text>Hide Modal</Text>
            </TouchableHighlight>
          </View>
        </View>
      </Modal>

      <TouchableHighlight
        onPress={() => {
          setModalVisible(true);
        }}>
        <Text>Show Modal</Text>
      </TouchableHighlight>
    </View>
  );
};

export default App;
```

In this example, **`Modal`** is imported from **`react-native`** and used to create a modal overlay. The modal visibility is managed using the **`useState`**hook and is toggled using the **`TouchableHighlight`** components.

Some of the modal properties include:

- `animationType`: Controls how the modal appears and disappears. Possible values are `none`, `slide`, and `fade`. Default is `none`.
- `transparent`: Determines whether the background is transparent or not. Default is `false`.
- `visible`: Controls the visibility of the modal. Default is `true`.
- `onRequestClose`: Called when the user tries to close the modal. Required on Android to properly handle the hardware back button.

### Pressable Component

Pressable is a core component in React Native that makes any view respond properly to touch or press events. It provides a wide range of event handlers for managing user interactions, such as onPress, onPressIn, onPressOut, and onLongPress. With Pressable, you can create custom buttons, cards, or any touchable elements within your app.

To use Pressable in your React Native application, you need to import it from ‘react-native’:

```jsx
import { Pressable } from 'react-native';
```

Wrap any view or component you want to make pressable with the Pressable component:

```jsx
<Pressable onPress={() => console.log('Pressed!')}>
  <Text>Press me</Text>
</Pressable>
```

Pressable allows you to customize its appearance and behavior according to the user interaction state. You can use the **`style`** prop and pass a function that sets the style based on the state.

Here’s an example of a custom button that changes its background color when pressed:

```jsx
import React from 'react';
import { Pressable, Text, StyleSheet } from 'react-native';

export default function CustomButton() {
  return (
    <Pressable
      onPress={() => console.log('Pressed!')}
      style={({ pressed }) => [
        styles.button,
        pressed ? styles.pressedButton : styles.normalButton,
      ]}
    >
      <Text style={styles.buttonText}>Press me</Text>
    </Pressable>
  );
}

const styles = StyleSheet.create({
  button: {
    padding: 10,
    borderRadius: 5,
  },
  normalButton: {
    backgroundColor: 'blue',
  },
  pressedButton: {
    backgroundColor: 'darkblue',
  },
  buttonText: {
    color: 'white',
    textAlign: 'center',
  },
});
```

In this example, when the Pressable is pressed, it will change its background color from “blue” to “darkblue”.