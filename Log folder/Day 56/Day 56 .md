# Day 56

Tags: React, React Native
Date: September 8, 2023
Status: Done

Task of the day 

- [React Native](https://www.codecademy.com/learn/learn-react-native) pt-2

---

**NAVIGATION**

### **Introduction**

Creating easy-to-use apps is hard but important. When you create a complicated app, users might get frustrated and stop using your app. There are a few techniques to keep your app easy to use, like using existing navigational patterns. By reusing these navigational patterns, users may navigate from screen to screen without having to learn how your app works.

In this lesson, we will cover:

- Fundamentals of navigation
- Three common navigation patterns: stack, tab, and drawer
- Implementing basic patterns with `react-navigation`
- Implementing a more complex structure with nested navigation
- Implementing a basic authentication flow

---

### **Navigation Patterns**

Let’s take a look at some commonly used mobile navigation patterns. By reusing these patterns, users don’t have to re-learn how to navigate your app. Instead, they can apply some of the patterns they already know. Doing so will help your users start using your app the second they install it.

On the right side, you can see these patterns as a GIF to get an understanding of the pattern.

- **Tab Navigation** - This pattern uses a tab bar to allow users to switch between screens. Usually, these screens contain different functionality, like a home screen and a profile screen. There are more variants of the tab navigator, like [Google’s Material Design (top) Tabs](https://material.io/components/tabs). The tabs usually contain the primary functionality of an app, like a feed and profile screen.
- **Stack Navigation** - The second example is a stacked pattern. Instead of using a menu or tab bar, the user has to go from screen to screen to navigate through all screens. When a user navigates from one screen to another, the screen is pushed on a stack. The order of the stack doesn’t matter; every transition is another screen in the stack. However when going back a page, the last screen is removed from the stack and the previous screen is displayed. These stacks usually contain screens that are functional-related to each other, like a list of tasks and a task detail screen.
- **Drawer Navigation** - Instead of using a tab bar, it uses a pane that can be opened by either swiping or opening a menu button. In this pane, there is a menu where the users can switch between screens. Like the tab bar pattern, these screens often contain the primary functionality of your app.

---

### ****Navigation in practice****

![Screen Shot 2023-09-08 at 4.12.27 PM.png](Day%2056%20ba73d29e5803465192f2f84d128fab0f/Screen_Shot_2023-09-08_at_4.12.27_PM.png)

The concept of sketching out the navigational structure of your app is often referred to as “navigation hierarchy”. In its simplest form, you can draw the structure as a simple graph. Every node represents a screen, and the edges define how the user can navigate from screen to screen.

- **Login** - When users download the app, they need to authenticate in order to use the app. This part is technically more than one screen, like login and register. For simplicity, we only added the login screen here.
- **Feed** - This is a screen where users can go back to courses they started but never finished. It also includes the latest articles when they are published.
- **Catalog** - After users complete a course, they can browse the catalog to find more. They can find all of the existing courses here.
- **Search** - If a user heard about an interesting course or article, they should be able to find it by searching for it. This screen is a list of all avalaible content on Codecademy.
- **Profile** -  This part allows the user to see an overview of their achievements and streaks. It also includes a settings page where they can manage their profile.

**NAVIGATION**

### **Review**

Awesome! We’ve covered the basics of navigation with Expo and React Native, including:

- Most common mobile navigation patterns; stack, drawer, and tab navigation
- Drawn a navigation hierarchy based on Codecademy Go
- Set up the basic components for `react-navigation`
- Implementing common navigation patterns
- Connecting navigation to custom events
- Combining different navigators for more complex structures
- Implementing a basic authentication flow

---

# **Next Steps**

**Continue on your Expo and React Native journey with these suggestions**

Well done so far! At this point you can build React Native and Expo apps with core components, custom components, styling, and navigation. You can use Flexbox properties, explain density-independent pixels, and tell the difference between stack, drawer, and tab navigation patterns.

Now that you’ve mastered the basics, it’s time to leave the Codecademy nest. There are lots of packages, libraries, tools, and communities in the React Native and Expo world to explore.

Build [a few basic apps on your own to verify your learning](https://docs.expo.io/tutorial/follow-up/), then, when you’re ready for more, try your hand at these topics:

- Animation with libraries such as [Reanimated](https://docs.expo.io/versions/latest/sdk/reanimated/) or [Moti](https://moti.fyi/)
- [Working with external APIs](https://reactnative.dev/docs/network)
- [Deploying your app to app stores](https://docs.expo.io/distribution/introduction/)

And here are some useful resources to bookmark:

- [Expo documentation](https://docs.expo.io/)
- [Expo forums](https://forums.expo.io/)
- [Expo Discord](https://docs.expo.io/next-steps/community/)
- [React Native documentation](https://reactnative.dev/)
- [r/reactnative on Reddit](https://www.reddit.com/r/reactnative/)
- Popular React Native YouTube channels [here](https://www.youtube.com/c/wcandillon/videos) and [here](https://www.youtube.com/c/CatalinMironDev/videos)

Want to build your portfolio and help others? Contribute to Codecademy Docs! You can go to our [Contribution Guide](https://www.codecademy.com/resources/docs/contribution-guide) to get started.

Good job and happy coding!

I was looking at the React Native thread on Reddit. Do you think Warpcast could do something differently here?

[Learn React Native | Codecademy](https://www.codecademy.com/learn/learn-react-native)

---

[https://www.youtube.com/watch?v=YysKbNk1tj0](https://www.youtube.com/watch?v=YysKbNk1tj0)

Steps

1. [Setting up your environment](https://reactnative.dev/docs/environment-setup)