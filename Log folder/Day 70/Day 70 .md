# Day 70

Tags: React Native
Date: September 23, 2023
Status: Done

Task of the day

Core Components

- View
- Listings
- SafeAreaView
- KeyboardAvoidingView
- ScrollView
- List View
- RefreshControl
- FlatList
- SectionList
- RefreshControl

Writing Platform Specific Code

- Platform Module
- File Extensions
- React-native-web

Styling

- Stylesheets
- Layouts and Flexbox
- Accessiblity

- Networking
    - Connectivity Status
    - Fetch
    - Websockets
- Push notifications
- Interactions
    - Touchables
    - Gestures Responder System
    - Scrolling and Swiping
    - Screen and Navigation
    - Animations

---

### View

The `View` component in React Native is a fundamental container component that supports various layout styles. It is the equivalent of a `div` element in HTML and can be used to create and style containers for various elements. It is a versatile component that can handle various user interactions, including touch events, as well as serving as a decorative and functional piece in your mobile application.

Here’s an example of how to use the **`View`** component:

```jsx
import React from 'react';
import { StyleSheet, View, Text } from 'react-native';

function App() {
  return (
    <View style={styles.container}>
      <Text>Hello, World!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});

export default App;
```

In this example, the `View` component is used to create a container with a background color of white and centering its child components both vertically and horizontally. Inside the container, a `Text` component displays the message “Hello, World!“.

### Listings components

When working with listings in React Native, the commonly used components include:

**FlatList** - It is a high-performance, scrollable list component that renders a large number of items efficiently.

**Example**

```jsx
import { FlatList, Text } from 'react-native';

const data = [
  { id: 1, text: 'Item 1' },
  { id: 2, text: 'Item 2' },
  { id: 3, text: 'Item 3' },
];

const renderItem = ({ item }) => <Text>{item.text}</Text>;

const MyFlatList = () => (
  <FlatList
    data={data}
    renderItem={renderItem}
    keyExtractor={item => item.id.toString()}
  />
);
```

**SectionList** - Similar to FlatList, but it is used when you want to display data in separate sections with section headers

**Example**

```jsx
import { SectionList, Text } from 'react-native';

const sections = [
  { title: 'Section 1', data: ['Item 1', 'Item 2', 'Item 3'] },
  { title: 'Section 2', data: ['Item 4', 'Item 5', 'Item 6'] },
];

const Item = ({ text }) => <Text>{text}</Text>;
const SectionHeader = ({ title }) => <Text>{title}</Text>;

const MySectionList = () => (
  <SectionList
    sections={sections}
    renderItem={({ item }) => <Item text={item} />}
    renderSectionHeader={({ section: { title } }) => (
      <SectionHeader title={title} />
    )}
    keyExtractor={(item, index) => item + index}
  />
);
```

**VirtualizedList** - A lower-level component for rendering large lists and for more fine-grained control over list rendering performance.

**Example**

```jsx
import { VirtualizedList, Text } from 'react-native';

const data = [
  { id: 1, text: 'Item 1' },
  { id: 2, text: 'Item 2' },
  { id: 3, text: 'Item 3' },
];

const getItemCount = data => data.length;
const getItem = (data, index) => data[index];

const renderItem = ({ item }) => <Text>{item.text}</Text>;

const MyVirtualizedList = () => (
  <VirtualizedList
    data={data}
    renderItem={renderItem}
    keyExtractor={item => item.id.toString()}
    getItemCount={getItemCount}
    getItem={getItem}
  />
);
```

These components are essential when dealing with dynamic data and displaying large lists in React Native applications.

### SafeAreaView

`SafeAreaView` is a React Native core component that helps to adjust your app’s UI elements and layout to accommodate the notches, curved edges, or home indicator on iOS devices. It is particularly useful for the iPhone X and newer iPhone models, as it ensures that content is rendered within the visible portion of the screen.

Here is an example of using **`SafeAreaView`** in the code:

```jsx
import React from 'react';
import { SafeAreaView, StyleSheet, Text } from 'react-native';

const App = () => {
  return (
    <SafeAreaView style={styles.container}>
      <Text>Hello World!</Text>
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
});

export default App;
```

In this example, the **`SafeAreaView`** component wraps around the content (in this case, a **`Text`** component), ensuring that the text is displayed within the safe area of the screen. By using **`SafeAreaView`**, you no longer have to worry about placing content outside the visible area or having it obstructed by the notch on iOS devices.

Keep in mind that **`SafeAreaView`** only works on iOS devices, and has no effect on Android devices. To handle such cases, you can use platform-specific styles or libraries like **`react-native-safe-area-context`** which provide more control and customization options for additional platforms

### KeyboardAvoiding View

**`KeyboardAvoidingView`** is a built-in React Native component that automatically adjusts its children components’ position when the keyboard opens, preventing them from being obscured by the on-screen keyboard. It’s a useful component, particularly for forms and input fields where the user needs to see the text they’re typing.

**Usage**

To use the `KeyboardAvoidingView`, simply wrap the desired components that need to avoid the keyboard with the `KeyboardAvoidingView`component. The prop `behavior` is used to specify the type of animating behavior the component will use. This behavior differs depending on the platform and can be one of ‘height’, ‘position’, ‘padding’, or a custom defined behavior.

Here’s a basic example:

```jsx
import React from 'react';
import { View, TextInput, StyleSheet, KeyboardAvoidingView } from 'react-native';

const App = () => {
  return (
    <KeyboardAvoidingView
      style={styles.container}
      behavior="padding" // Additional padding when the keyboard is open.
    >
      <TextInput
        placeholder="Type something here"
        style={styles.textInput}
      />
    </KeyboardAvoidingView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
  },
  textInput: {
    borderWidth: 1,
    borderColor: 'black',
    padding: 10,
    margin: 20,
  },
});

export default App;
```

Remember to test the behavior on different devices and platforms to ensure the desired result is achieved.

### Scroll View

In React Native, the `ScrollView` is a generic scrolling container used to provide a scrollable view to its child components. It is useful when you need to display scrollable content larger than the screen, such as lists, images, or text. A `ScrollView` must have a bounded height in order to properly work

Here’s a simple example of how to use the `ScrollView` component in your React Native app:

```jsx
import React from 'react';
import { ScrollView, Text } from 'react-native';

const MyScrollView = () => {
  return (
    <ScrollView>
      <Text>Item 1</Text>
      <Text>Item 2</Text>
      <Text>Item 3</Text>
      <Text>Item 4</Text>
      <Text>Item 5</Text>
      <Text>Item 6</Text>
    </ScrollView>
  );
}

export default MyScrollView;
```

In this example, the **`ScrollView`** component is imported from the **`react-native`** package, and it’s used as a container for several **`Text`**components that represent items in a list. Users can scroll through the items if they don’t fit on the screen.

Keep in mind that **`ScrollView`** is not optimized for long lists of items, and you should use the **`FlatList`** or **`SectionList`** components for better performance in those cases. However, it’s still useful for smaller content where you need a scrollable area, such as forms or when the content size is unknown.

### List Views

List views are an essential component in mobile applications when you need to display a list of items in an organized and efficient way. In React Native, there are two primary components to display a list - `FlatList` and `SectionList`. Let’s dive into each one with some examples.

**FlatList**

A **`FlatList`** is a simple list view component that renders a list of items in a user-friendly scrolling format. FlatList is great for large lists of data that only render a small number of items on the screen at a time. It supports both horizontal and vertical scrolling, allows you to customize the appearance of items, and provides built-in performance optimizations.

Here’s a basic example using FlatList:

```jsx
import React from 'react';
import { View, FlatList, Text, StyleSheet } from 'react-native';

const data = [
  { id: '1', title: 'Item 1' },
  { id: '2', title: 'Item 2' },
  { id: '3', title: 'Item 3' },
];

const renderItem = ({ item }) => (
  <View style={styles.item}>
    <Text>{item.title}</Text>
  </View>
);

const App = () => (
  <FlatList
    data={data}
    renderItem={renderItem}
    keyExtractor={item => item.id}
  />
);

const styles = StyleSheet.create({
  item: {
    backgroundColor: '#f9c2ff',
    padding: 20,
    marginVertical: 8,
  },
});

export default App;
```

### SectionList

A **`SectionList`** is a more complex list view component that presents items in multiple sections with optional section headers. It is suitable for use cases where you need to categorize data into separate sections and display a header for each section.

Here’s a basic example using SectionList:

```jsx
import React from 'react';
import { View, SectionList, Text, StyleSheet } from 'react-native';

const data = [
  {
    title: 'Section 1',
    data: ['Item 1.1', 'Item 1.2', 'Item 1.3'],
  },
  {
    title: 'Section 2',
    data: ['Item 2.1', 'Item 2.2', 'Item 2.3'],
  },
];

const renderItem = ({ item }) => (
  <View style={styles.item}>
    <Text>{item}</Text>
  </View>
);

const renderSectionHeader = ({ section: { title } }) => (
  <View style={styles.header}>
    <Text>{title}</Text>
  </View>
);

const App = () => (
  <SectionList
    sections={data}
    keyExtractor={(item, index) => item + index}
    renderItem={renderItem}
    renderSectionHeader={renderSectionHeader}
  />
);

const styles = StyleSheet.create({
  item: {
    backgroundColor: '#f9c2ff',
    padding: 20,
    marginVertical: 8,
  },
  header: {
    backgroundColor: 'skyblue',
    padding: 20,
  },
});

export default App;
```

In summary, **`FlatList`** and **`SectionList`** are the primary list view components in React Native. Use **`FlatList`** for simple lists and when performance is a priority, and use **`SectionList`** when you need to organize data into multiple sections.

### FinalList

**`FlatList`** is a **`React Native`** core component that displays a scrolling list of changing, but similarly structured, data. It is an efficient list component that makes use of a limited scrolling **`renderWindow`**, reducing the memory footprint and creating smooth scrolling. Additionally, **`FlatList`** supports-Headers, Footers, Pull-to-refresh, and Horizontal scrolling, among other things.

Here is a basic example demonstrating how to use the **`FlatList`**component:

```jsx
import React from 'react';
import { FlatList, View, Text } from 'react-native';

const data = [
  { id: '1', content: 'Item 1' },
  { id: '2', content: 'Item 2' },
  { id: '3', content: 'Item 3' },
  // ...
];

const renderItem = ({ item }) => (
  <View>
    <Text>{item.content}</Text>
  </View>
);

const MyFlatList = () => (
  <FlatList
    data={data}
    renderItem={renderItem}
    keyExtractor={item => item.id}
  />
);

export default MyFlatList;
```

In the example above:

- We import the `FlatList` along with `View` and `Text`components.
- We have an array of data containing objects with a unique ID and content.
- `renderItem` is a function that takes an item and returns the components to render for that item.
- In the `MyFlatList` component, we use the `FlatList` and pass the data, the `renderItem` function, and a `keyExtractor` to extract a key from the item.

### SectionList

**`SectionList`** is a component used to render sections and headers in a scroll view. It helps to manage and optimize a large list of items divided into categories. It is one of the List View components provided by React Native along with FlatList.

The key difference between SectionList and FlatList is that SectionList separates data items into sections, with headers.

Here’s an example of how to use a SectionList in your app:

```jsx
import React, {Component} from 'react';
import {SectionList, StyleSheet, Text, View, SafeAreaView} from 'react-native';

export default class App extends Component {
  render() {
    return (
      <SafeAreaView style={styles.container}>
        <SectionList
          sections={[
            {
              title: 'Section 1',
              data: ['Item 1.1', 'Item 1.2', 'Item 1.3'],
            },
            {
              title: 'Section 2',
              data: ['Item 2.1', 'Item 2.2', 'Item 2.3'],
            },
          ]}
          renderItem={({item}) => <Text style={styles.item}>{item}</Text>}
          renderSectionHeader={({section}) => (
            <Text style={styles.sectionHeader}>{section.title}</Text>
          )}
          keyExtractor={(item, index) => String(index)}
        />
      </SafeAreaView>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    paddingRight: 10,
    paddingLeft: 10,
  },
  sectionHeader: {
    fontSize: 20,
    fontWeight: 'bold',
    backgroundColor: 'lightgrey',
    padding: 5,
  },
  item: {
    fontSize: 16,
    padding: 10,
    borderBottomWidth: 1,
    borderBottomColor: 'black',
  },
});
```

In this example, we have two sections: ‘Section 1’ and ‘Section 2’. Each section has its own data items.

**`renderItem`** is a function that takes an object containing an item property and returns a Text component with the item value.

**`renderSectionHeader`** is a function that takes an object containing a section property and returns a text component with the section’s title.

### Refresh Control

`RefreshControl` is a component in React Native that is used to provide pull-to-refresh functionality for scrollable components like `ScrollView`, `ListView`, and `FlatList`.

**How to use RefreshControl**

Import **`RefreshControl`** from ‘react-native’:

```jsx
import { RefreshControl } from 'react-native';
```

Add **`RefreshControl`** to a scrollable component (**`ScrollView`**, **`ListView`**, or **`FlatList`**). Here is an example with **`FlatList`**:

```jsx
import React, { useState } from 'react';
import { FlatList, RefreshControl, Text } from 'react-native';

const App = () => {
    const [refreshing, setRefreshing] = useState(false);

    const fetchData = () => {
        // Fetch the data and update your state accordingly
    };

    const onRefresh = () => {
        setRefreshing(true);
        fetchData().then(() => {
            setRefreshing(false);
        });
    };

    return (
        <FlatList
            data={['Item 1', 'Item 2', 'Item 3']}
            renderItem={({ item }) => <Text>{item}</Text>}
            refreshControl={
                <RefreshControl refreshing={refreshing} onRefresh={onRefresh} />
            }
        />
    );
};

export default App;
```

In the example above, we have a **`FlatList`** that renders a list of items. When the user pulls down the list, the **`onRefresh`** function is triggered and fetches new data. The **`refreshing`** state is used to control the visibility of the refresh indicator. When **`refreshing`** is set to **`true`**, the refresh indicator is shown. It is hidden when **`refreshing`** is set to **`false`**.

---

### Writing platform specific code

**Platform specific code**

In React Native, you might need to maintain certain parts of your application differently for iOS and Android. This is where “Platform Specific Code” comes into play. There are two ways you can achieve this:

### **Platform module**

The Platform module, as the name suggests, is a part of React Native that detects the platform on which the app is running. This enables you to have specific code for either Android or iOS, allowing you to account for platform-specific differences in design or behavior.

To utilize the Platform module, you need to import it and then access the `OS` property. This property returns a string, which denotes the platform — either `'ios'` or `'android'`.

**Example**

```jsx
import { Platform } from 'react-native';

if (Platform.OS === 'ios') {
  console.log('Running on iOS');
} else if (Platform.OS === 'android') {
  console.log('Running on Android');
}
```

For a more elegant way to define platform-specific properties, React Native provides the `Platform.select` method. This method takes an object with keys `'ios'` and `'android'`, representing the respective platforms, and returns the value associated with the current platform.

Here’s an example of **`Platform.select`** in use:

```jsx
import { Platform, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    ...Platform.select({
      ios: {
        backgroundColor: 'red',
      },
      android: {
        backgroundColor: 'blue',
      },
    }),
  },
});
```

In this example, the container’s background color will be red on iOS and blue on Android.

With the Platform module, you can easily create platform-specific code, enabling you to have the best user experience for each platform. Just remember to import the module and use the provided properties and methods.

### **File extensions**

In React Native, you can write platform-specific code by using specific file extensions. By appending `.android.` or `.ios.` to your file’s name, React Native will load the file corresponding to the platform you are running your app on.

There are two main scenarios where you can use this approach:

### Platform-Specific Component Files

You can create separate files for each platform’s specific components, keeping the implementation and styling different for Android and iOS.

For example, if you have a **`Header`** component, you can create two separate files **`Header.ios.js`** and **`Header.android.js`**. React Native will automatically pick the right file depending on the platform it’s running on.

**Example:**

Let’s say you have two files in your project, **`Header.ios.js`** and **`Header.android.js`**. When you import the **`Header`** component in your code, React Native will automatically import the correct file for the platform.

```jsx
// Header.ios.js
import React from 'react';
import { View, Text } from 'react-native';

const Header = () => {
  return (
    <View style={{ backgroundColor: 'blue' }}>
      <Text>iOS Header</Text>
    </View>
  );
};

export default Header;
```

```jsx
// Header.android.js
import React from 'react';
import { View, Text } from 'react-native';

const Header = () => {
  return (
    <View style={{ backgroundColor: 'green' }}>
      <Text>Android Header</Text>
    </View>
  );
};

export default Header;
```

### ****Platform-Specific Code within a File****

You can also use the **`Platform`** module from React Native to determine which platform-specific code to run within a single file.

```jsx
import { Platform, StyleSheet, Text } from 'react-native';

const ComponentWithPlatformSpecificCode = () => {
  return <Text style={styles.content}>Hello World!</Text>;
};

const styles = StyleSheet.create({
  content: {
    color: Platform.select({
      ios: 'blue',
      android: 'green',
    }),
  },
});

export default ComponentWithPlatformSpecificCode;
```

Using file extensions and the **`Platform`** module, you can create tailor-made components and features for different platforms while maintaining a clean and organized codebase.

---

### React Native Web

React Native Web is an extension of React Native which allows you to run your React Native apps not only on iOS and Android devices, but also on the web. It uses the same components and APIs you’re familiar with in React Native, but renders them into the DOM of a webpage instead of native UI elements.

The main goal of React Native Web is to provide a consistent developer experience across platforms, reducing the effort needed to build and maintain multi-platform apps.

**Platform-specific code**

While React Native Web is designed to provide a consistent experience across platforms, there may still be cases where you want to use platform-specific code for an improved native experience.

For example, let’s say you have a React Native app with the following styles:

```jsx
const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  text: {
    fontSize: 16,
    color: 'blue',
  },
});
```

Now, let’s say you want to apply some platform-specific styling. You can create separate stylesheets for each platform, like **`styles.native.js`**and **`styles.web.js`**. The contents of **`styles.native.js`** would look like this:

```jsx
import { StyleSheet } from 'react-native';

export default StyleSheet.create({
  container: {
    // Your platform-specific styles
  },
  text: {
    // Your platform-specific styles
  },
});
```

And the contents of **`styles.web.js`** would look like this:

```jsx
import { StyleSheet } from 'react-native';

export default StyleSheet.create({
  container: {
    // Your platform-specific styles
  },
  text: {
    // Your platform-specific styles
  },
});
```

Then, in your main component file, you can import the appropriate styles for each platform automatically:

```jsx
import styles from './styles';

// Now, your styles are platform-specific!
```

This way, you can cater your styles to the specific platform your app is running on, without having to clutter your main component code with conditional styling.

React Native Web also provides a utility called **`Platform`** that you can use to determine the current platform and apply platform-specific code directly:

```jsx
import { Platform, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    ...Platform.select({
      web: {
        // Web-specific styles
      },
      native: {
        // Native-specific styles
      },
    }),
  },
  text: {
    ...Platform.select({
      web: {
        // Web-specific styles
      },
      native: {
        // Native-specific styles
      },
    }),
  },
});
```

With these techniques, you’ll be able to create tailored experiences across different platforms while maintaining a consistent development experience.

---

### Styling

Styling in React Native is accomplished through JavaScript and uses a subset of CSS properties. Unlike CSS in web development, React Native has its own set of components and styling rules. The main components used for styling are **`StyleSheet`**, **`View`**, and **`Text`**.

### StyleSheet

**`StyleSheet`** is a module provided by React Native to manage and optimize styles. It is similar to a CSS stylesheet and helps in creating and working with multiple styles efficiently.

```jsx
import { StyleSheet, View, Text } from 'react-native';

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  text: {
    fontSize: 20,
    fontWeight: 'bold',
  },
});
```

### View and Text components

**`View`** and **`Text`** components are the basic building blocks for creating a user interface in React Native. They are used to add structure and style to the layout.

```jsx
import React from 'react';
import { StyleSheet, View, Text } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Hello, React Native!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
  text: {
    fontSize: 20,
    fontWeight: 'bold',
  },
});
```

### Inline styles

In some cases, you might prefer to apply styles directly to a component using inline styling. However, it is not recommended for larger applications due to performance issues.

```jsx
import React from 'react';
import { View, Text } from 'react-native';

export default function App() {
  return (
    <View
      style={{
        flex: 1,
        backgroundColor: '#fff',
        alignItems: 'center',
        justifyContent: 'center',
      }}
    >
      <Text
        style={{
          fontSize: 20,
          fontWeight: 'bold',
        }}
      >
        Hello, React Native!
      </Text>
    </View>
  );
}
```

In summary, styling in React Native is done through JavaScript using a subset of CSS properties. The main components used for styling are `StyleSheet`, `View`, and `Text`. You can also use inline styles when necessary, although it’s not recommended for performance reasons.

---

### Stylesheets

**Stylesheets in React Native**

In React Native, stylesheets are objects that define the appearance of components. They provide a way to separate styling from the component’s logic. Stylesheets are created using **`StyleSheet.create`** method, which ensures a standardized and efficient way to manage styles for your components.

**Creating a stylesheet**

You can create a stylesheet by importing **`StyleSheet`** from ‘react-native’, and then defining your styles using **`StyleSheet.create`** method.

```jsx
import { StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  text: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
});
```

**Applying styles to componets**

To apply styles, simply reference the style object from your stylesheet using **`styles.styleName`**. 

For example:

```jsx
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const App = () => {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Hello, React Native!</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  text: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
});

export default App;
```

**Combining styles**

You can combine multiple styles by passing an array of styles to the **`style`** prop of a component. The last style in the array takes precedence if there are conflicting styles.

```jsx
<View style={[styles.container, styles.backgroundRed]}>
  <Text style={styles.text}>Hello, React Native!</Text>
</View>

// Adding backgroundRed to the existing styles
const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  text: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
  backgroundRed: {
    backgroundColor: 'red',
  },
});
```

That’s a brief summary of stylesheets in React Native. You can now create, apply, and combine styles for your React Native components.

### **Layouts in React Native**

In React Native, layouts are primarily managed using the Flexbox styling system. Flexbox is a powerful and flexible layout system that allows you to create responsive and complex UIs using a set of simple rules.

**Flexbox**

Flexbox consists of three key elements: the **`container`**, **`main axis`**, and **`cross axis`**.

- The `container` is the parent flex container that holds and distributes all the child elements.
- The `main axis` is the primary direction of the layout (horizontal or vertical).
- The `cross axis` is the perpendicular direction, opposite of the main axis.

Here are some of the most commonly used Flexbox styles:

- **`flexDirection`**: This style specifies the primary axis using four possible values: `row`, `row-reverse`, `column`, or `column-reverse`.

```jsx
<View style={{flexDirection: 'row'}}>
  <Text>First child</Text>
  <Text>Second child</Text>
</View>
```

• **`alignItems`**: This style is used to align the child items along the cross-axis. It uses the values `flex-start`, `flex-end`, `center`, `stretch`, or `baseline`.

```jsx
<View style={{flexDirection: 'row', alignItems: 'center'}}>
  <Text>First child</Text>
  <Text>Second child</Text>
</View>
```

• **`justifyContent`**: This style is used to align the child items along the main axis. It accepts the values `flex-start`, `flex-end`, `center`, `space-between`, or `space-around`.

```jsx
<View style={{flexDirection: 'row', justifyContent: 'space-between'}}>
  <Text>First child</Text>
  <Text>Second child</Text>
</View>
```

• **`flexWrap`**: Set to either `wrap` or `nowrap` to specify if child items should wrap around to the next line when there’s not enough space on the current line.

```jsx
<View style={{flexDirection: 'row', flexWrap: 'wrap'}}>
  <Text>First child</Text>
  <Text>Second child</Text>
  <Text>Third child</Text>
</View>
```

• **`flex`**: This style determines how the child items grow or shrink when there’s remaining space in the container. It’s a shorthand for `flex-grow`, `flex-shrink`, and `flex-basis`.

```jsx
<View style={{flexDirection: 'row'}}>
  <Text style={{flex: 1}}>First child</Text>
  <Text style={{flex: 2}}>Second child</Text>
</View>
```

You can use these styles in various combinations to create flexible layouts in React Native. Flexbox makes it easy to create responsive UIs that adapt to changes in screen size or orientation. Note that some of these styles might not work as expected in React Native compared to in CSS for the web, but the overall concepts remain the same.

### Accessibility

Accessibility (a11y) in React Native allows you to create applications that are usable to everyone, including people with disabilities. It provides a set of attributes and APIs to customize UI components by considering diverse user needs.

**Accessibility props**

React Native provides several accessibility properties that can be applied to components for enhancing their a11y features:

**`accessible`** : (Boolean) - Indicates if the element can be focused by screen readers.

```jsx
<TouchableOpacity accessible={true} />
```

**`accessibilityLabel`** : (String) - Used by the screen reader to describe the element to the user.

```jsx
<TouchableOpacity accessibilityLabel="Tap me!">
```

**`accessibilityHint`** : (String) - Gives a hint to the user of the components behavior.

```jsx
<TouchableOpacity accessibilityHint="Tapping this button will show a welcome text">
```

**`accessibilityRole`** : (String) - Describes the role of the element for the screen reader.

```jsx
accessibilityValue : (Object with properties: min, max, now) - Defines the accessibility values for elements such as progress bars or sliders, among others.
```

**`accessibilityValue`** : (Object with properties: min, max, now) - Defines the accessibility values for elements such as progress bars or sliders, among others.

```jsx
<Slider
  accessibilityValue={{
    min: 0,
    max: 100,
    now: 50,
  }}
/>
```

`accessibilityState` : (Object) - Represents the current state of the component

```jsx
<TouchableOpacity
  accessibilityState={{
    disabled: false,
    selected: true,
  }}
/>
```

`accessibilityActions` and `onAccessibilityAction` are used to create custom actions.

```jsx
import { AccessibilityInfo, Text, View } from 'react-native';

function CustomButton() {
  const [count, setCount] = React.useState(0);

  const onIncrement = () => {
    setCount(count + 1);
  };

  React.useEffect(() => {
    const announce = () => {
      AccessibilityInfo.announceForAccessibility(`Count raised to ${count}`);
    };
    announce();
  }, [count]);

  return (
    <View
      accessible={true}
      accessibilityActions={[
        { name: "increment", label: "increase count" },
      ]}
      onAccessibilityAction={(event) => {
        switch (event.nativeEvent.actionName) {
          case "increment":
            onIncrement();
            break;
        }
      }}
    >
      <Text>Increment Counter: {count}</Text>
    </View>
  );
}
```

---

### Networking

React Native provides the ability to make network requests and manage data fetched from remote sources. Networking can be accomplished through the following techniques:

**Fetch**

The **`fetch`** function is a top-level API to make HTTP requests. It is a promise-based API for handling network requests. It allows you to fetch resources (typically JSON data) from a provided URL.

**Fetch Example**

```jsx
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then((response) => response.json())
  .then((json) => console.log(json))
  .catch((error) => console.error(error));
```

**Axios** 

Axios is a popular and widely-used library for making HTTP requests in javascript applications. It’s promise-based and provides a simple-to-use API.

---

### **Connectivity Status**

Connectivity refers to the mechanisms that allow data transfer between your React Native app and external resources through various means of communication. It is essential to ensure efficient communication with APIs, servers, and external systems, to update your app’s data, fetching content or enabling real-time interactions.

**Networking Types**

**Fetch API**: The Fetch API is a native JavaScript way to make HTTP requests that can be used in React Native. It provides a simple interface for fetching resources and returns a Promise that resolves to the response of the request.

Example:

```jsx
fetch('https://api.example.com/data')
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error(error));
```

**XMLHttpRequest**: React Native has built-in support for XMLHttpRequest, which is a popular choice for communication with APIs. It can deal with various data types, like XML, JSON, or even binary data.

Example

```jsx
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 200) {
    console.log(xhr.responseText);
  }
};
xhr.open('GET', 'https://api.example.com/data', true);
xhr.send();
```

**WebSockets**: WebSockets allow you to establish real-time communication between your React Native app and a server. It provides a two-way communication mechanism over a single, long-held TCP connection, enabling real-time data transfer.

Example

```jsx
const webSocket = new WebSocket('wss://example.com/ws');

webSocket.onopen = () => {
  webSocket.send('Hello from React Native app!');
};

webSocket.onmessage = (event) => {
  console.log('Message from the server:', event.data);
};

webSocket.onerror = (error) => {
  console.error('WebSocket error:', error);
};

webSocket.onclose = (event) => {
  console.log('WebSocket connection closed:', event.code, event.reason);
};
```

**Library for networking**

In addition to the built-in networking types, you can use external libraries to simplify networking tasks, such as:

**Axios**: Axios is a promise-based HTTP client for the browser and Node.js environment. It supports various features like intercepting requests and responses, timeouts, and handling retries.

**Example:**

```jsx
import axios from 'axios';

axios
  .get('https://api.example.com/data')
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

**Apollo Client**: Apollo Client is a comprehensive GraphQL client that helps you manage your data in a better and more efficient way, making it easier to build powerful and scalable applications.

**Example:**

```jsx
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';

const client = new ApolloClient({
  uri: 'https://api.example.com/graphql',
  cache: new InMemoryCache(),
});

client
  .query({
    query: gql`
      query GetData {
        data {
          id
          name
        }
      }
    `,
  })
  .then((result) => console.log(result))
  .catch((error) => console.error(error));
```

By understanding these options, you can choose the most appropriate connectivity method for your React Native app, and efficiently communicate with APIs, servers, and external systems.

---

### Fetch

*Fetch* is a JavaScript function available in React Native that is used to make network requests, similar to XMLHttpRequest in web applications. It allows you to handle requests and retrieve data from APIs or other sources. The Fetch API is built on Promises, making it simple to handle success and error cases.

**Usage**

Here’s a basic example demonstrating how to use fetch to make a GET request:

```jsx
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In this example, we are using `fetch()` to make a GET request to a sample API. The function `fetch()` returns a Promise that resolves to the Response object representing the response to the request. Using `then()`, we manage the response and extract the JSON data from it. If an error occurs, we catch it with `catch()`.

**POST Request**

To make a POST request using fetch, you need to provide an additional object with the **`method`**, **`headers`**, and **`body`** properties:

```jsx
fetch('https://jsonplaceholder.typicode.com/todos', {
  method: 'POST',
  headers: {
    'Accept': 'application/json',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    title: 'New Task',
    completed: false
  })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In this example, we are making a POST request to add a new task to the sample API. The `method` property is set to ‘POST’, and `headers` define the content type as ‘application/json’. The `body` property contains the new task in JSON format, which needs to be converted to a string using `JSON.stringify()`. Just like the GET request, we handle the response and catch any errors that occur.

---

### Webpockets

WebSockets are a protocol that allows full-duplex communication between a client and a server over a single, long-lived connection. They are useful when real-time communication is needed, such as in chat applications, online gaming, or financial trading platforms.

**Setting up a websocket connection**

In React Native, you can use the **`WebSocket`** API to establish a WebSocket connection with the server. Here’s an example of how to open a WebSocket connection:

```jsx
const webSocket = new WebSocket('ws://my-websocket-server.com');
```

**Receiving and sending messages**

You can handle the different events associated with a WebSocket connection by attaching event listeners to the **`WebSocket`** instance.

****Handling connection****

To handle connection establishment, you can use the **`onopen`** event listener:

```jsx
webSocket.onopen = (event) => {
  console.log('WebSocket connection opened:', event);
};
```

****Handling incoming messages****

To receive messages from the server, you can use the `onmessage` event listener:

```jsx
webSocket.onmessage = (event) => {
  console.log('Received from server:', event.data);
};
```

**Sending messages to the server**

To send messages to the server, you can use the **`send`** method:

```jsx
webSocket.send('Hello server');
```

**Handling connection error and closure**

You can catch connection errors and closure events using the `onerror`and `onclose` event listeners:

```jsx
webSocket.onerror = (event) => {
  console.log('WebSocket error:', event);
};

webSocket.onclose = (event) => {
  console.log('WebSocket connection closed:', event);
};
```

**Closing the Websocket connection**

To close the WebSocket connection, you can use the **`close`** method:

```jsx
webSocket.close();
```

That’s a brief summary of using WebSockets in React Native! Don’t forget to handle various edge cases such as connection loss, reconnection, and graceful shutdowns in a real-world application

---

### Push Notifications in React Native

Push notifications are a way to engage and retain users by delivering alerts, messages, or other information directly to their devices, even when the app is not running. They are an essential feature in modern mobile applications as they help keep users informed about important updates and allow developers to encourage user interaction with the app.

In React Native, you can implement push notifications using third-party libraries or services. Some popular options are:

- Firebase Cloud Messaging (FCM) for both Android and iOS
- Apple Push Notification Service (APNs) for iOS

[https://www.youtube.com/watch?v=UkfmKz3kcho](https://www.youtube.com/watch?v=UkfmKz3kcho)

---

### Interactions

Interaction in React Native means dealing with how the user can interact with your application. This typically involves handling touch events, gestures, and animations to provide a more engaging and dynamic user experience. There are several built-in components and libraries available in React Native to help you build interactive elements in your app.

**Touchables**

Touchables components are used to recognize various touch events in you application. React Native provides a few touchable components that you can use:

**TouchableHighlight**: Responds to the press event with a visual effect, such as highlighting the touched area.

```jsx
import { TouchableHighlight, Text } from 'react-native';

function MyButton() {
  return (
    <TouchableHighlight onPress={() => console.log('Button pressed')}>
      <Text>Press me!</Text>
    </TouchableHighlight>
  );
}
```

**TouchableOpacity**: Responds to the press events by making the touched area semi-transparent.

```jsx
import { TouchableOpacity, Text } from 'react-native';

function MyButton() {
  return (
    <TouchableOpacity onPress={() => console.log('Button pressed')}>
      <Text>Press me!</Text>
    </TouchableOpacity>
  );
}
```

**TouchableWithoutFeedback**: Responds to the press events without any visual feedback.

```jsx
import { TouchableWithoutFeedback, Text } from 'react-native';

function MyButton() {
  return (
    <TouchableWithoutFeedback onPress={() => console.log('Button pressed')}>
      <Text>Press me!</Text>
    </TouchableWithoutFeedback>
  );
}
```

**Gesture Responder System**

The Gesture Responder System is a low-level API for capturing touch events and managing touch responsiveness in a React Native application. It allows components to take ownership of touch events and determine how they should be handled.

```jsx
import { View, Text, StyleSheet } from 'react-native';

function MyComponent() {
  return (
    <View
      style={styles.container}
      onStartShouldSetResponder={() => true}
      onResponderGrant={(event) => console.log('Touch started')}
      onResponderMove={(event) => console.log('Touch moving')}
      onResponderRelease={(event) => console.log('Touch released')}
    >
      <Text>Touch me!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    borderWidth: 1,
    borderColor: 'black',
    padding: 10,
  },
});
```

**PainResponder**

PanResponder is a gesture responder helper that deals with touch events using the Gesture Responder System. It simplifies creating components that respond to various touch events.

```jsx
import { PanResponder, View, Text, StyleSheet } from 'react-native';

function MyComponent() {
  const panResponder = PanResponder.create({
    onStartShouldSetPanResponder: () => true,
    onPanResponderGrant: (event) => console.log('Touch started'),
    onPanResponderMove: (event) => console.log('Touch moving'),
    onPanResponderRelease: (event) => console.log('Touch released'),
  });

  return (
    <View style={styles.container} {...panResponder.panHandlers}>
      <Text>Touch me!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    borderWidth: 1,
    borderColor: 'black',
    padding: 10,
  },
});
```

**Animated**

The **`Animated`** library provides a way to create smooth animations in a React Native application. It can handle various types of animations, such as opacity, scaling, and rotation.

```jsx
import { Animated, TouchableOpacity } from 'react-native';

function MyAnimatedComponent() {
  const opacity = new Animated.Value(1);

  function animateOpacity() {
    Animated.timing(opacity, {
      toValue: 0,
      duration: 1000,
      useNativeDriver: true,
    }).start();
  }

  return (
    <TouchableOpacity onPress={animateOpacity}>
      <Animated.View style={{ opacity }}>
        {/* Your content */}
      </Animated.View>
    </TouchableOpacity>
  );
}
```

These components and libraries will help you build more interactive and engaging user experiences in your React Native applications.

### Scrolling and Swiping

In React Native, scrolling and swiping interactions can be defined and customized with a set of built-in components. These components are efficient and provide fluid navigation through the elements inside them.

**Scrolling**

React Native provides **`ScrollView`** and **`FlatList`** components to handle scrolling interactions. Both components have their own use cases. Let’s discuss them in detail:

**ScrollView:** Used for simple and short lists with a known number of elements. It renders all the child elements in memory at once, which can negatively impact performance for longer lists.

**Example**

```jsx
import React from 'react';
import { ScrollView, Text } from 'react-native';

const ScrollViewExample = () => (
  <ScrollView>
    {['Element 1', 'Element 2', 'Element 3'].map((item, index) => (
      <Text key={index}>{item}</Text>
    ))}
  </ScrollView>
);
```

**FlatList:** Used for long and complex lists where the number of elements is unknown or potentially infinite. It optimizes performance by rendering only the currently visible elements in the viewport.

**Example**

```jsx
import React from 'react';
import { FlatList, Text } from 'react-native';

const DATA = [
  { id: '1', text: 'Element 1' },
  { id: '2', text: 'Element 2' },
  { id: '3', text: 'Element 3' },
];

const renderItem = ({ item }) => (
  <Text>{item.text}</Text>
);

const FlatListExample = () => (
  <FlatList
    data={DATA}
    renderItem={renderItem}
    keyExtractor={(item) => item.id}
  />
);
```

**Swiping**

To implement swiping in React Native, the community-driven package **`react-native-gesture-handler`** is commonly used. One of its components is **`Swipeable`**, which allows you to create swipeable elements with custom swipe actions.

Example

```jsx
import React from 'react';
import { Text, View } from 'react-native';
import { RectButton } from 'react-native-gesture-handler';
import Swipeable from 'react-native-gesture-handler/Swipeable';

const RightActions = (progress, dragX, onPress) => {
  return (
    <RectButton onPress={onPress}>
      <View>
        <Text>Delete</Text>
      </View>
    </RectButton>
  );
};

const SwipeableExample = () => {
  const handleDelete = () => {
    alert('Delete action');
  };

  return (
    <Swipeable
      renderRightActions={(progress, dragX) =>
        RightActions(progress, dragX, handleDelete)
      }
    >
      <View>
        <Text>Swipeable Element</Text>
      </View>
    </Swipeable>
  );
};
```

In summary, React Native provides various components for smooth scrolling and swiping interactions. Components like **`ScrollView`**, **`FlatList`**, and **`react-native-gesture-handler`** are essential tools in creating a seamless user experience.

**[Screen Navigation](https://reactnavigation.org)**

In React Native, navigating from one screen to another is a crucial aspect of app development. The most commonly used navigation libraries are React Navigation and React Native Navigation.

[](https://github.com/react-navigation/react-navigation/tree/main/example)

### Animations

React Native supports two types of animations: **`Animated`** and **`LayoutAnimation`**. The **`Animated`** API provides a basic set of methods for creating and managing animations, while the **`LayoutAnimation`** API provides a way to animate changes from one layout to another.

**Animated**

**`Animated`** is a declarative API that focuses on handling animation-related calculations. It allows you to create and combine animations with fine-grained control over the specific properties that are being animated. You can use this API to create a variety of effects, such as fading, scaling, and translating components on the screen.

Here’s a simple example of how to use **`Animated`** to move a view across the screen:

```jsx
import React, { Component } from "react";
import { Animated, View } from "react-native";

class MoveView extends Component {
  constructor(props) {
    super(props);
    this.position = new Animated.ValueXY({ x: 0, y: 0 });
  }
  
  componentDidMount() {
    Animated.timing(this.position, {
      toValue: { x: 100, y: 100 },
      duration: 1000,
    }).start();
  }

  render() {
    return (
      <Animated.View style={this.position.getLayout()}>
        {/* Your content here */}
      </Animated.View>
    );
  }
}
```

It creates a new **`Animated`** value that represents the position of the view and moves it to another location over a duration of 1000 milliseconds.

**LayoutAnimation**

`LayoutAnimation` is a higher-level abstraction for animating changes to the layout. Instead of animating individual properties, you define how the changes should occur and React Native takes care of updating the layout accordingly. This is particularly useful for animating multiple components or modifying the layout in response to user interaction, such as adding/removing/reordering items in a list

Here’s an example of how to use **`LayoutAnimation`** to animate a view when it is added to or removed from a list of items:

```jsx
import React, { Component } from "react";
import { LayoutAnimation, TouchableOpacity, View } from "react-native";

class ListItem extends Component {
  componentDidMount() {
    LayoutAnimation.configureNext(LayoutAnimation.Presets.easeInEaseOut);
  }

  componentWillUnmount() {
    LayoutAnimation.configureNext(LayoutAnimation.Presets.easeInEaseOut);
  }

  render() {
    return (
      <View style={styles.itemContainer}>
        <TouchableOpacity onPress={this.props.onRemove}>
          {/* Button content here */}
        </TouchableOpacity>
        {/* Item content here */}
      </View>
    );
  }
}
```

In this example, whenever a **`ListItem`** component is added or removed, the layout will be animated using the preset **`easeInEaseOut`**configuration.

These two animation methods in React Native help you create smooth, natural-looking animations for a variety of interactions and use cases in your applications.