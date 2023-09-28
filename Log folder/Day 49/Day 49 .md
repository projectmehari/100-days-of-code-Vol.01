# Day 49

Tags: React, Vitest
Date: September 2, 2023
Status: Done

Task of the day

- **Testing with Vitest**
- **Authentication Strategies**
    - basic auth
    - Session Based Authentication
    - Token Based Authentication
    - JWT Authentication
    - OAuth — Open Authorization
    - SSO — Single Sign On
- **Web Security Knowledge**
    - [HTTPS](https://www.cloudflare.com/en-gb/learning/ssl/what-is-https/)
    - [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
    - [Content security policy](https://web.dev/csp/)
- ****Web Components****
    - Custom elements
    - Shadow DOM
    - HTML Templates

---

# **Testing your apps**

Before delivering your application to users, you need to be sure that your app meets the requirements it was designed for, and that it doesn’t do any weird, unintended things (called ‘bugs’). To accomplish this, we ‘test’ our applications in different ways.

[https://www.youtube.com/watch?v=G-4zgIPsjkU](https://www.youtube.com/watch?v=G-4zgIPsjkU)

### ****Basic Authentication****

![https://roadmap.sh/guides/basic-authentication.png](https://roadmap.sh/guides/basic-authentication.png)

### Session Based Authentication

![https://roadmap.sh/guides/session-authentication.png](https://roadmap.sh/guides/session-authentication.png)

### ****Token Based Authentication****

![https://roadmap.sh/guides/token-authentication.png](https://roadmap.sh/guides/token-authentication.png)

### ****JWT Authentication****

![https://roadmap.sh/guides/jwt-authentication.png](https://roadmap.sh/guides/jwt-authentication.png)

****OAuth — Open Authorization****

![https://roadmap.sh/guides/oauth.png](https://roadmap.sh/guides/oauth.png)

****SSO — Single Sign On****

![https://roadmap.sh/guides/sso.png](https://roadmap.sh/guides/sso.png)

---

### ****HTTPS****

HTTPS is a secure way to send data between a web server and a browser.

Hypertext transfer protocol secure (HTTPS) is the secure version of HTTP, which is the primary protocol used to send data between a web browser and a website. HTTPS is encrypted in order to increase security of data transfer. This is particularly important when users transmit sensitive data, such as by logging into a bank account, email service, or health insurance provide

### **How does a website start using HTTPS?**

Many website hosting providers and other services will offer TLS/SSL certificates for a fee. These certificates will be often be shared amongst many customers. More expensive certificates are available which can be individually registered to particular web properties.

[All websites using Cloudflare receive HTTPS for free](https://www.cloudflare.com/plans/) using a shared certificate (the technical term for this is a multi-domain SSL certificate). Setting up a free account will guarantee a web property receives continually updated HTTPS protection. You can also explore our paid plans for individual certificates and other features. In either case, a web property receives all the benefits of using HTTPS.

### Cross

Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.

---

# **Web Components**

Web Components is a suite of different technologies allowing you to create reusable custom elements — with their functionality encapsulated away from the rest of your code — and utilize them in your web apps.

[https://www.youtube.com/watch?v=PCWaFLy3VUo](https://www.youtube.com/watch?v=PCWaFLy3VUo)

### Custom Elements

- Create custom HTML tags
- Create custom class
- Lifecycle methods available
    - Eg. **constructor():** called when an instance of the element is created or upgraded
    

```html
class AppDrawer extends HTMLElement {...}
window.customElement.define('app-drawer', AppDrawer);

<app-drawer></app-drawer>
```

### Shadow DOM

- Used for self-contained components
- Encapsulate styles and markup
- Create with element.attachShadow({mode: open})
- Creates a “shadowRoot” that we can reference and interact with.

### HTML Templates

- Define the encapsulated markup of our web component
- Template tag stores markup on page
- Include both HTML and CSS in templates
- Use slots to add custom text