# Day 53

Tags: Astro
Date: September 6, 2023
Status: Done

Task of the day

- Static Site Generators
    - Next.js SSG
    - Astro
    
    # **Astro**
    
    Astro is an all-in-one web framework for building fast, content-focused websites. Astro combines the power of a modern component-based framework with the performance and flexibility of a static site generator.
    
    - Component Islands: A new web architecture for building faster websites.
    - Server-first API design: Move expensive hydration off of your users’ devices.
    - Zero JS, by default: No JavaScript runtime overhead to slow you down.
    - Edge-ready: Deploy anywhere, even a global edge runtime like Deno or Cloudflare.
    - Customizable: Tailwind, MDX, and 100+ other integrations to choose from.
    - UI-agnostic: Supports React, Preact, Svelte, Vue, Solid, Lit and more

---

**Static site generator** 

A static site generator is a tool that generates a full static HTML website based on raw data and a set of templates. Essentially, a static site generator automates the task of coding individual HTML pages and gets those pages ready to serve to users ahead of time. Because these HTML pages are pre-built, they can load very quickly in users' browsers.

Static site generators are an alternative to content management systems (CMS) — another type of tool for managing web content, generating webpages, and implementing templates. (A template is a reusable format for web content; developers use templates to avoid writing the same formatting over and over.) Static site generators are typically part of a [JAMstack](https://www.cloudflare.com/learning/performance/what-is-jamstack/) web development approach.

****What is a static website?****

A static website is made up of one or more HTML webpages that load the same way every time. Static websites contrast with dynamic websites, which load differently based on any number of changing data inputs, such as the user's location, the time of day, or user actions. While static webpages are simple HTML files that can load quickly, dynamic webpages require the execution of JavaScript code within the browser in order to render.

### ****What are the pros and cons of using a static site generator?****

*Pros*

- **Performance:** Because static site generators create webpages in advance instead of on demand (as with a CMS), webpages load slightly faster in users' browsers.
- **Customization:** Developers can create any template they want. They are not limited by the fields provided by a CMS, nor by a CMS's built-in templates.
- **Lighter backend:** Static websites are lightweight and do not require as much code to run on the server side, whereas CMS-based websites constantly query the server side for content.

### **How does JAMstack relate to static site generators?**

JAMstack (JAM stands for "JavaScript, APIs, Markup") is a methodology for efficiently creating lightweight, fast-performing web applications. JAMstack applications are static, with APIs used for any backend functionality. Static site generators enable developers to quickly build a JAMstack application frontend.

---

### [Next.js SSG](https://nextjs.org/docs/pages/building-your-application/deploying/static-exports)

Static Exports

Next.js enables starting as a static site or Single-Page Application (SPA), then later optionally upgrading to use features that require a server.

When running `next build`, Next.js generates an HTML file per route. By breaking a strict SPA into individual HTML files, Next.js can avoid loading unnecessary JavaScript code on the client-side, reducing the bundle size and enabling faster page loads.

Since Next.js supports this static export, it can be deployed and hosted on any web server that can serve HTML/CSS/JS static assets.

---

### Astro

[https://www.youtube.com/watch?v=BoeZqPaYw9s](https://www.youtube.com/watch?v=BoeZqPaYw9s)

[https://www.youtube.com/watch?v=zrPVTf761OI](https://www.youtube.com/watch?v=zrPVTf761OI)

# **Astro**

[Astro](https://astro.build) is an all-in-one web framework for building fast, content-focused websites. Astro combines the power of a modern component-based framework with the performance and flexibility of a static site generator.

- Component Islands: A new web architecture for building faster websites.
- Server-first API design: Move expensive hydration off of your users’ devices.
- Zero JS, by default: No JavaScript runtime overhead to slow you down.
- Edge-ready: Deploy anywhere, even a global edge runtime like Deno or Cloudflare.
- Customizable: Tailwind, MDX, and 100+ other integrations to choose from.
- UI-agnostic: Supports React, Preact, Svelte, Vue, Solid, Lit and more

---