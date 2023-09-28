# Day 71

Tags: React, React Native
Date: September 24, 2023
Status: Done

Task of the day

- Deep Linking
- Security
    - Authentification
    - Networking
    - Storage
- Storage
    - react-native-async-storage
    - Other Storage options
- Expo Ecosystem
    - expo-secure-store
    - expo-file-system
    - expo-sqlite
- Testing
    - Jest
- Performance
    - Understand Frame Rates
    - Common problem sources
    - Speeding up builds
    - Optimizing flatlist config
    - RAM bundles + inline requires
    - Profiling
- Using Native Modules
    - For IOS
- Publishing Apps
    - Apple App Store

---

### ****Deep Linking****

Deep linking is a technique used in mobile applications that allows you to open a specific screen, content, or functionality within the application using a URL or a custom URL scheme. This is useful for providing seamless user experiences by navigating the user directly to the desired part of the app. Deep linking can be triggered by clicking on a link in an email, scanning a QR code, or through a push notification.

There are two types of deep links:

1. 1. **Universal Links** (iOS) / **App Links** (Android): These are HTTPS URLs that allow the user to navigate to a specific screen when the app is installed and fallback to a specified website when the app is not installed.
2. 1. **Custom URL Schemes**: Unique URLs, like `myapp://my-screen`, that can open the app directly to a specific screen when clicked.

**Handling deep links in React Native**

In React Native, you can handle deep links using the **`Linking`** module which provides the necessary methods to work with deep links.

First, you have to import **`Linking`** from **`"react-native"`**:

```jsx
import { Linking } from 'react-native';
```

To handle deep links, you need to add a listener that will be triggered when the app receives a deep link. You can add the listener in the **`componentDidMount`** lifecycle method and remove it in the **`componentWillUnmount`** method.

For example:

```jsx
import React from 'react';
import { Linking, Text, View } from 'react-native';

class App extends React.Component {
  componentDidMount() {
    Linking.addEventListener('url', this.handleOpenURL);
  }

  componentWillUnmount() {
    Linking.removeEventListener('url', this.handleOpenURL);
  }

  handleOpenURL(event) {
    // Handle your deep link logic
    console.log('Received deep link: ', event.url);
  }

  render() {
    return (
      <View>
        <Text>Hello from React Native!</Text>
      </View>
    );
  }
}

export default App;
```

To work with universal links or app links, you need to configure your app on both iOS and Android. You can follow the official guide **[here](https://reactnative.dev/docs/linking)**.

You can also use popular libraries like **`react-navigation`** or **`react-native-navigation`** that provide built-in support for handling deep links in your app.

---

### React Native Security

React Native is a framework for building cross-platform mobile applications using JavaScript and ReactJS. As with any application development, security is a crucial aspect to protect your application data and user information. Here is a brief overview of some React Native security best practices.

**Secure Storage**

Store sensitive data, such as authentication tokens, encryption keys, or user credentials, securely using a storage solution that comes with built-in encryption mechanisms.

**Example:**

For React Native, **[react-native-keychain](https://github.com/oblador/react-native-keychain)** and **[react-native-encrypted-storage](https://github.com/emeraldsanto/react-native-encrypted-storage)** are popular libraries handling secure storage.

```jsx
import * as Keychain from 'react-native-keychain';

// Save data to the keychain
await Keychain.setGenericPassword(username, password);

// Retrieve data from the keychain
const credentials = await Keychain.getGenericPassword();
```

**Secure Communication**

Use HTTPS for network communication with APIs and remote services. This ensures that the data exchanged between server and client is encrypted and secure.

**Example:**

Use the **[fetch](https://reactnative.dev/docs/network)** method with URLs starting with ‘https://‘.

```jsx
const response = await fetch('https://example.com/api/data');
const data = await response.json();
```

**Minimize permissions**

Request only the necessary permissions from the user that your application needs to function, and do this at runtime when the feature actually needs the permission.

Example:

Using **[react-native-permissions](https://github.com/zoontek/react-native-permissions)**, you can request permissions when they are needed:

```jsx
import {check, PERMISSIONS, request, RESULTS} from 'react-native-permissions';

async function requestLocationPermission() {
  const result = await check(PERMISSIONS.IOS.LOCATION_WHEN_IN_USE);

  if (result === RESULTS.DENIED) {
    return await request(PERMISSIONS.IOS.LOCATION_WHEN_IN_USE);
  }

  return result;
}
```

**Validate User Input**

Ensure you validate and sanitize all user input before processing it. This helps to prevent potential threats like SQL injection or cross-site scripting (XSS).

**Example:**

Use a validation library like **[Yup](https://github.com/jquense/yup)** to validate user input.

```jsx
import * as Yup from 'yup';

const loginSchema = Yup.object({
  email: Yup.string().email('Invalid email address').required('Required'),
  password: Yup.string()
    .min(8, 'Password must be at least 8 characters')
    .required('Required'),
});

loginSchema.validate({email: 'user@example.com', password: 'password'});
```

**Keep Dependencies up to date**

Regularly update your dependencies to ensure they don’t contain known security vulnerabilities. Use tools like **[npm audit](https://docs.npmjs.com/cli/v7/commands/npm-audit)** and **[dependabot](https://github.com/dependabot/dependabot-core)** to automatically audit and update your dependencies.

Example:

Using npm, you can update your dependencies and check for potential vulnerabilities:

```jsx
npm update
npm audit
```

Following these best practices will help you create more secure React Native applications, protecting your application’s data and your users’ information.

---

### Authentication

Authentication is a crucial aspect of securing your React Native application. It enables you to verify the identity of users and give access to protected resources and features. Here are the common methods used for authentication in React Native:

- JWT Authentication
- OAuth
- Simple Token Authentication

Have a look at the following react native page for further details about security.

- **[Authentication and Deep Linking](https://reactnative.dev/docs/security#authentication-and-deep-linking)**

---

### Networking

React Native offers various ways to handle networking tasks like making API calls, sending/receiving data from remote servers, and handling different networks protocols.

- Fetch
- HTTP Call Libraries
- Web Sockets

These are the major ways to handle networking tasks in React Native. Choose the method that best suits your specific use case and allows you to take full advantage of the features offered.

---

### Storage

React Native provides a few ways to persist data locally in the app. Here’s a brief summary of the storage options available:

- Async Storage
- Expo Secure Store
- Expo File System
- Expo SQLite

Choose the storage option that best fits your app’s requirements and use cases. Keep in mind that AsyncStorage and SecureStorage are more suited for small-scale data storage, while Realm and SQLite support more complex storage and querying needs.

---

### Other Storage Options

Besides AsyncStorage, there are other options available for handling data storage in React Native applications. This guide will briefly cover some popular options: Realm, Firebase Realtime Database, and SQLite.

- **[Realm](https://github.com/realm/realm-js)**
- **[Firebase Realtime Database](https://firebase.google.com/docs/database)**

These are just a few examples of additional storage options for React Native. Depending on your requirements, you may choose the one that best fits your project.

---

### **react-native-async-storage**

An asynchronous, unencrypted, persistent, key-value storage system for React Native.

• **[Visit the Documentation](https://github.com/react-native-async-storage/async-storage)**

---

### Expo-secure-store

Expo Secure Store is a built-in package provided by the Expo SDK to store encrypted data securely on users’ devices. It is a key-value storage system, but it is not designed to store larger amounts of data such as app databases or complex data structures. It is most appropriate for storing secret keys, access tokens, and small user preferences.

First, you need to install the package by running:

```jsx
expo install expo-secure-store
```

Then, import the module into your app:

```jsx
import * as SecureStore from 'expo-secure-store';
```

**Saving data**

To save data to the secure store, use the **`setItemAsync`** method. It takes two arguments: a key and a value. Both should be strings.

```jsx
async function saveData() {
  try {
    await SecureStore.setItemAsync('your_key', 'your_value');
    console.log('Data saved successfully!');
  } catch (error) {
    console.error('Error saving data:', error);
  }
}
```

**Retrieving Data**

To retrieve data from the secure store, use the **`getItemAsync`** method, which takes the key as a parameter and returns a Promise that resolves to the value.

```jsx
async function getData() {
  try {
    const value = await SecureStore.getItemAsync('your_key');
    if (value !== null) {
      console.log('Data retrieved:', value);
    } else {
      console.log('No data found with that key.');
    }
  } catch (error) {
    console.error('Error retrieving data:', error);
  }
}
```

**Deleting Data**

To delete data from the secure store, use the **`deleteItemAsync`** method. It takes the key as a parameter.

```jsx
async function deleteData() {
  try {
    await SecureStore.deleteItemAsync('your_key');
    console.log('Data deleted successfully!');
  } catch (error) {
    console.error('Error deleting data:', error);
  }
}
```

Please note that Expo Secure Store uses different security mechanisms based on the platform (iOS or Android). Additionally, while the store is encrypted, remember that it is not foolproof, and a determined attacker may be able to extract data. However, it provides a good balance between security and usability for most use cases.

---

### Expo-file-system

Expo File System is a universal module that provides access to the file system on the device. Using this module, you can perform various file operations like reading, writing, copying, moving, and deleting files and folders. It also supports reading file metadata and querying file URI.

To use the Expo File System library, you need to install the **`expo-file-system`** package:

```jsx
expo install expo-file-system
```

First, import the **`expo-file-system`** module:

```jsx
import * as FileSystem from 'expo-file-system';
```

Here are some examples of how to use the Expo File System:

**Reading a file**

```jsx
async function readFileAsync() {
    const fileUri = FileSystem.documentDirectory + 'myFile.txt';

    try {
        const content = await FileSystem.readAsStringAsync(fileUri);
        console.log('File content:', content);
    } catch (error) {
        console.error('Error while reading file:', error);
    }
}
```

**Writing a file**

```jsx
async function writeFileAsync() {
    const fileUri = FileSystem.documentDirectory + 'myFile.txt';
    const content = 'Hello, World!';

    try {
        await FileSystem.writeAsStringAsync(fileUri, content);
        console.log('File written successfully');
    } catch (error) {
        console.error('Error while writing file:', error);
    }
}
```

**Copying & Moving a file**

```jsx
async function copyAndMoveFileAsync() {
    const srcUri = FileSystem.documentDirectory + 'myFile.txt';
    const destUri = FileSystem.documentDirectory + 'copiedFile.txt';

    try {
        await FileSystem.copyAsync({ from: srcUri, to: destUri });
        console.log('File copied successfully');

        const newDestUri = FileSystem.documentDirectory + 'movedFile.txt';
        await FileSystem.moveAsync({ from: destUri, to: newDestUri });
        console.log('File moved successfully');
    } catch (error) {
        console.error('Error while copying/moving file:', error);
    }
}
```

**Deleting a file**

```jsx
async function deleteFileAsync() {
    const fileUri = FileSystem.documentDirectory + 'myFile.txt';

    try {
        await FileSystem.deleteAsync(fileUri);
        console.log('File deleted successfully');
    } catch (error) {
        console.error('Error while deleting file:', error);
    }
}
```

I hope this brief summary of Expo File System helps you understand its functionality and usage. Remember to visit the **[official documentation](https://docs.expo.dev/versions/latest/sdk/filesystem/)** for more details and other available features.

---

### Expo-Sqlite

Expo SQLite is a powerful tool for handling local SQLite databases in your React Native application. By using this API, you can create, read, update, and delete data as needed, without writing native code. Expo SQLite is available as part of the **[expo-sqlite](https://docs.expo.dev/versions/latest/sdk/sqlite/)** package, which provides an easy-to-use interface for SQLite functionalities.

With Expo SQLite, you can efficiently manage SQLite databases within your React Native applications. It enables you to perform various database operations without the need for writing native code.

---

### Testing

When it comes to testing, you can use a combination of Jest, React Test Renderer, React Native Testing Library, Detox and Appium for all sorts of API needs.

---

### **Jest**

Jest is a delightful JavaScript Testing Framework with a focus on simplicity. It works with projects using: Babel, TypeScript, Node, React, Angular, Vue and more!

Visit the following resources to learn more:

- **[Official Website](https://jestjs.io/)**
- **[Official Documentation](https://jestjs.io/docs/getting-started)**
- **[Jest Crash Course - Unit Testing in JavaScript](https://www.youtube.com/watch?v=7r4xVDI2vho)**

---

### React Test Renderer (Component tests)

React Test Renderer is a library provided by the React team that allows you to render React components as JavaScript objects without depending on the DOM or a native mobile environment. It can be used to test components in Node.js environments where the actual rendering is not required.

- **[React Test Renderer](https://jestjs.io/docs/tutorial-react)**

---

### React Native Testing Library(Component tests)

React Native Testing Library (RNTL) is a collection of tools and utilities to test React Native components. It is built on top of the Testing Library ecosystem, designed to work seamlessly with Jest and other testing frameworks. Its primary goal is to enable efficient and effective testing by providing simple and intuitive APIs that promote best practices, like testing UI components in isolation and promoting accessibility checks.

- It encourages testing from a user’s perspective, focusing on interaction and accessibility rather than component implementation details.
- Built-in support for React Native’s asynchronous APIs like `act` and `flushMicrotasksQueue`.
- Provides utility methods to query, fire events, and wait for elements in the components tree.

Follow the links below for more details:

- **[React Native Testing Library](https://callstack.github.io/react-native-testing-library/)**
- **[React Native Testing Library (Docs)](https://testing-library.com/docs/react-native-testing-library/intro/)**

---

### Detox

Detox is an end-to-end testing framework for React Native applications. It enables you to run tests on an actual device or in a simulator/emulator environment. The goal of Detox is to maintain a high level of confidence in your application’s behavior while allowing for quick test runs and easy debugging.

Learn more about Detox from the following links:

- **[Detox Official Docs](https://wix.github.io/Detox/)**

---

### Appium

Appium is an open-source test automation framework for mobile devices, targeting native, hybrid, or mobile-web apps for iOS, Android, and Windows platforms. Appium works with multiple programming languages, including JavaScript, Ruby, Python, Java, and C#.

Appium uses the WebDriver protocol, which allows you to write tests that can interact with your app through a series of commands. The WebDriver protocol interprets these commands into actions that are then performed on the app.

Learn more about Appium from the following resources:

- **[Appium Documentation](http://appium.io/)**

---

### Understand Frame Rates

Frame rates represent the number of frames (or images) displayed per second in an animation or video. The performance of a React Native application can be highly impacted by the frame rate, so it is important to optimize your application for the best possible user experience. Higher frame rates provide smoother animations, but may require more system resources. To achieve the desired frame rate, the application should ensure that each frame is computed and rendered within the time budget.

In general, frame rates can be categorized into two types:

- **Static Frame Rate**: This is when your application’s frame rate remains constant during its runtime.
- **Adaptive Frame Rate**: This is when your application adjusts the frame rate according to device performance and available resources.

**Animated library**

One of the ways to achieve high frame rates and smooth animations in React Native is by using the **`Animated`** library. This library provides a set of methods and components that help you manage animations efficiently. By using the **`Animated`** library, you can define animations declaratively, avoid unnecessary render cycles, and utilize the native driver to offload animation from the JavaScript thread.

Here’s an example of using the **`Animated`** library to create a simple fade-in animation:

```jsx
import React, { useEffect, useRef } from 'react';
import { Animated, StyleSheet, View } from 'react-native';

const FadeIn = (props) => {
  const opacity = useRef(new Animated.Value(0)).current;

  useEffect(() => {
    Animated.timing(opacity, {
      toValue: 1,
      duration: 500,
      useNativeDriver: true, // This line offloads animation to the native driver
    }).start();
  }, []);

  return (
    <Animated.View
      style={[
        styles.container,
        {
          opacity: opacity, // This line applies the animated opacity value
        },
      ]}
    >
      {props.children}
    </Animated.View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
});

export default FadeIn
```

By following best practices and leveraging tools like the **`Animated`** library, you can optimize your React Native application’s performance and achieve smooth, high-quality animations with optimal frame rates.

---

### Common Problem Sources

**Console logs**

Excessive console logs can lead to decreased performance in React Native, especially in debug mode. In order to avoid this, keep the usage of console logging to a minimum, and clean up unnecessary logs before releasing the app.

**Images**

Heavy and unoptimized images can lead to performance issues in React Native. To avoid this, use the following techniques:

- Optimize image size and resolution before bundling them in the application.
- Use `resizeMode` prop on the `Image` component to cache images for better rendering.

```jsx
<Image source={require('./my-image.png')} resizeMode="cover" />
```

**Inline Functions and Styles**

Using inline functions and styles within components can lead to unnecessary re-rendering and performance issues. Instead, define functions and styles outside of the component render method.

```jsx
// Bad
render() {
  return (
    <TouchableOpacity onPress={() => this.onPress()}>
      <Text style={{fontSize: 16, color: 'blue'}}>Click me</Text>
    </TouchableOpacity>
  );
}

// Good
const styles = StyleSheet.create({
  buttonText: {
    fontSize: 16,
    color: 'blue',
  },
});

onPressHandler = () => {
  // Handle press
};

render() {
  return (
    <TouchableOpacity onPress={this.onPressHandler}>
      <Text style={styles.buttonText}>Click me</Text>
    </TouchableOpacity>
  );
}
```

**PureComponent and React.memo**

Components that extend **`React.PureComponent`** or are wrapped in **`React.memo()`** can lead to performance issues in case they’re updating frequently and causing unnecessary re-renders. Make sure to only use them when appropriate to avoid performance bottlenecks.

**ListView and FlatList**

When working with large lists in React Native, using **`ListView`** instead of **`FlatList`** can cause performance issues. Replace **`ListView`** with the more performant **`FlatList`** or **`SectionList`** components.

```jsx
// Use FlatList instead of ListView
<FlatList
  data={this.state.data}
  renderItem={({item}) => <MyListItemComponent item={item} />}
  keyExtractor={(item) => item.id}
/>
```

**JavaScript Thread blockage**

Blocking the JavaScript thread with expensive synchronous computations can lead to poor performance. Make sure to handle heavy computations asynchronously or offload them to native modules.

---

### **Speeding up builds**

Building your React Native app could be expensive and take several minutes of developers time. This can be problematic as your project grows and generally in bigger organizations with multiple React Native developers.

• **[Speeding up your Build phase](https://reactnative.dev/docs/build-speed)**

---

### Optimizing FlatList Config

In React Native, the FlatList component is used to efficiently display large lists of items. It’s crucial to optimize the FlatList configuration for better performance. Here are some important tips to help you optimize FlatList configurations:

### Set ****`windowSize`****

**`windowSize`** is a prop that determines the number of pages rendered above and below the current window. By default, this value is 21. You can decrease it based on your needs to reduce the number of off-screen rendered components.

Example:

```jsx
<FlatList
  data={data}
  renderItem={renderItem}
  keyExtractor={item => item.id}
  windowSize={10}
/>
```

### Set ****`removeClippedSubviews`****

Enable the **`removeClippedSubviews`** prop to unmount components that are off the screen.

Example:

```jsx
<FlatList
  data={data}
  renderItem={renderItem}
  keyExtractor={item => item.id}
  removeClippedSubviews={true}
/>
```

### Set****`maxToRenderPerBatch`****

**`maxToRenderPerBatch`** prop helps to control the number of items to be rendered per batch. By default, this is set to 10. Optimize this value according to your list’s requirements.

Example:

```jsx
<FlatList
  data={data}
  renderItem={renderItem}
  keyExtractor={item => item.id}
  maxToRenderPerBatch={5}
/>
```

### Set ****`initialNumToRender`****

**`initialNumToRender`** is used to set the number of items to be rendered initially. Setting this value to a reasonable number can help in avoiding blank screens on load.

Example:

```jsx
<FlatList
  data={data}
  renderItem={renderItem}
  keyExtractor={item => item.id}
  initialNumToRender={10}
/>
```

### Set ****`getItemLayout`****

Using the **`getItemLayout`** prop allows you to specify the exact dimensions of each item. This prevents the need for measuring them dynamically, resulting in improved performance.

Example:

```jsx
<FlatList
  data={data}
  renderItem={renderItem}
  keyExtractor={item => item.id}
  getItemLayout={(data, index) => (
    {length: ITEM_HEIGHT, offset: ITEM_HEIGHT * index, index}
  )}
/>
```

Implementing these optimizations in your FlatList config will help improve the performance of large lists in your React Native application.

---

### RAM Bundles + Inline Requires

If you have a large app you may want to consider the Random Access Modules (RAM) bundle format, and using inline requires. This is useful for apps that have a large number of screens which may not ever be opened during a typical usage of the app. Generally it is useful to apps that have large amounts of code that are not needed for a while after startup. For instance the app includes complicated profile screens or lesser used features, but most sessions only involve visiting the main screen of the app for updates. We can optimize the loading of the bundle by using the RAM format and requiring those features and screens inline (when they are actually used).

• **[RAM Bundles and Inline Requires](https://reactnative.dev/docs/ram-bundles-inline-requires)**

---

### Profiling

Use the built-in profiler to get detailed information about work done in the JavaScript thread and main thread side-by-side. Access it by selecting Perf Monitor from the Debug menu.

For iOS, Instruments is an invaluable tool, and on Android you should learn to use **`systrace`**.

Visit the following for more details:

- **[Profiling React Native](https://reactnative.dev/docs/profiling)**

---

### Using Native Modules

Sometimes a React Native app needs to access a native platform API that is not available by default in JavaScript, for example the native APIs to access Apple or Google Pay. Maybe you want to reuse some existing Objective-C, Swift, Java or C++ libraries without having to reimplement it in JavaScript, or write some high performance, multi-threaded code for things like image processing.

The NativeModule system exposes instances of Java/Objective-C/C++ (native) classes to JavaScript (JS) as JS objects, thereby allowing you to execute arbitrary native code from within JS. While we don’t expect this feature to be part of the usual development process, it is essential that it exists. If React Native doesn’t export a native API that your JS app needs you should be able to export it yourself!

 **[Native Modules Introduction](https://reactnative.dev/docs/native-modules-intro)**

For iOS:  **[iOS Native Modules](https://reactnative.dev/docs/native-modules-ios)**

For Android:  **[Android Native Modules](https://reactnative.dev/docs/native-modules-android)**

---

### Publishing Apps

Publishing React Native apps is the process of deploying your application on various app stores so that users can download and use your app. The two most popular app stores for publishing are the Apple App Store (iOS) and the Google Play Store (Android).

**Publishing Apps in App store**

The App Store is Apple’s official platform for distributing iOS apps to users with iPhones, iPads, and iPod Touch devices. To publish an app on the App Store, you need to follow specific guidelines and use the necessary tools provided by Apple.

**Publishing React Native Apps on Google Store**

Publishing your React Native app on Google Store consists of several steps.

- **[Publishing to Google Play Store](https://reactnative.dev/docs/signed-apk-android)**