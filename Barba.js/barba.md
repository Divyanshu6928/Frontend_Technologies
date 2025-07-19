# ✨ Barba.js Made Simple

## 📖 What is Barba.js?

**Barba.js** is a small JavaScript tool that helps you make **smooth page transitions** on your website — like animations when moving from one page to another, without refreshing the whole page.

It's like making your website feel more like an app — fast and smooth.

🔗 Official website: [https://barba.js.org](https://barba.js.org)

---

## 🔥 Why Use Barba.js?

* Makes your website look **cool and smooth**
* Animates when changing pages (fade, slide, etc.)
* Keeps parts like **navbar** or **footer** in place (no reload)
* Works with animation tools like **GSAP** or **Anime.js**
* Very small file size (fast to load)

---

## ⚙️ How to Add Barba.js

### 👉 If you’re using NPM/Yarn

```bash
npm install @barba/core
# or
yarn add @barba/core
```

### 👉 Or use this in your HTML:

```html
<script src="https://unpkg.com/@barba/core"></script>
```

---

## 📁 Simple Folder Structure

```plaintext
/
├── index.html
├── about.html
├── js/
│   └── main.js (Barba setup goes here)
├── css/
│   └── styles.css
```

---

## 🧠 Important Things to Know

### ✅ "Views"

Each page can be treated differently using its **name (namespace)**.

### ✅ "Transitions"

You can animate **how the old page goes out** and **new page comes in**.

### ✅ "Hooks"

Hooks let you run code at different moments during the transition.

---

## 🧪 Basic Example

### In your HTML (Home page)

```html
<a href="about.html">Go to About</a>

<div id="barba-wrapper">
  <div class="barba-container" data-barba="container" data-barba-namespace="home">
    <!-- Your content here -->
  </div>
</div>
```

### In your About page

```html
<div class="barba-container" data-barba="container" data-barba-namespace="about">
  <h1>This is About Page</h1>
</div>
```

### JavaScript (`main.js`)

```js
import barba from '@barba/core';

barba.init({
  transitions: [
    {
      name: 'fade-transition',
      leave(data) {
        return gsap.to(data.current.container, {
          opacity: 0,
          duration: 0.5
        });
      },
      enter(data) {
        return gsap.from(data.next.container, {
          opacity: 0,
          duration: 0.5
        });
      }
    }
  ]
});
```

---

## 🧠 What Are "Hooks"?

Hooks let you say:

* “Do this before the page changes”
* “Do this after the new page is loaded”

Example:

```js
barba.hooks.before(() => {
  console.log('Before page transition starts');
});

barba.hooks.after(() => {
  console.log('After page transition ends');
});
```

---

## 📚 Using Barba for Different Pages

You can give your pages names (called **namespaces**) and run different code on each.

```js
barba.init({
  views: [
    {
      namespace: 'home',
      afterEnter() {
        console.log('Welcome to Home Page');
      }
    },
    {
      namespace: 'about',
      afterEnter() {
        console.log('Welcome to About Page');
      }
    }
  ]
});
```

---

## 💡 Useful Tips

* Always add this to your page’s wrapper:

  ```html
  data-barba="container" data-barba-namespace="your-page-name"
  ```
* For better effects, use GSAP or other animation libraries.
* If you have interactive elements (like buttons, sliders), **re-initialize them** after the page changes.

---

## 🎨 Example Animations

| Transition Type | What It Does          |
| --------------- | --------------------- |
| Fade            | Page fades in and out |
| Slide           | Page slides from side |
| Zoom            | Page zooms in/out     |
| Flip            | Rotates the page      |

---

## ❗ Common Problems & Fixes

| Problem                         | Fix                                       |
| ------------------------------- | ----------------------------------------- |
| Page doesn’t load               | Check `data-barba="container"` is there   |
| Animation not working           | Check page names (namespaces) are correct |
| JS not working after transition | Re-run scripts in `afterEnter` or `enter` |

---

## 🛠 Want to Animate with GSAP?

Example:

```js
leave(data) {
  const done = this.async(); // Wait for animation to finish
  gsap.to(data.current.container, {
    opacity: 0,
    duration: 0.5,
    onComplete: done
  });
}
```

---

## 🌐 Helpful Links

* Docs: [https://barba.js.org/docs](https://barba.js.org/docs)
* Examples: [https://barba.js.org/examples](https://barba.js.org/examples)
* GitHub: [https://github.com/barbajs/barba](https://github.com/barbajs/barba)

---

## ✅ Final Words

If you want your website to feel **modern, fast, and animated**, Barba.js is a great choice.

It’s easy to use, especially if you know a bit of JavaScript and want to make your site feel like a real app.

**Happy coding !! DG here 😎**