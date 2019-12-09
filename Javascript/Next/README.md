# Next.js Notes
Next.js is a framework by Zeit. The framework allows you to jump right into developement with little to no webpack configuration. Out of the box, it comes with SSR (Server-side rendering) and intuitive page-routing with a lot more bells and whistles.

Most of the notes and content will be coming from nextjs own website for learning the framework. Link here:
https://nextjs.org/learn/basics/getting-started

## Setup
1. Run these commans for sample project:
    ```ssh
    mkdir hello-next
    cd hello-next
    npm init -y
    npm install --save react react-dom next
    mkdir pages
    ```
2. Replace `scripts` in  package.json with these lines:
    ```javascript
    "scripts": {
      "dev": "next",
      "build": "next build",
      "start": "next start"
    }
    ```
3. Run dev server:
    ```javascript
    npm run dev
    ```
4. View in http://localhost:3000 and you'll see a 404 page.

## Creating a Page
1. Create pages/index.js by running the following:
    ```sh
    cd pages
    touch index.js
    ```
2. In index.js add:
    ```javascript
    const Index = () => (
      <div>
        <p>Hello Next.js</p>
      </div>
    );
    export default Index;
    ```
## Navigate Between Pages
Create `pages/about.js` and add the following code to the file.
```javascript
export default function About() {
  return (
    <div>
      <p>This is the about page</p>
    </div>
  );
}
```
This page could be access by going to http://localhost:3000/about

### Linking to pages
We want to avoid using HTML anchor tags because the browser will do a server request, go to the page, and refreshes. It is ideal to do client-side navigation — It's done by importing from  `'next/link'` from Next.js Link API . `<Link />` will prefetch and navigate to the page without page refresh.

Add this code to `page/index.js`
```javascript
// This is the Link API
import Link from 'next/link';

const Index = () => (
  <div>
    <Link href="/about">
      <a>About Page</a>
    </Link>
    <p>Hello Next.js</p>
  </div>
);

export default Index;
```
>This is client-side navigation; the action takes place in the browser, without making a request to the server. You can verify this by opening your browser's network request inspector.

Source: https://nextjs.org/learn/basics/navigate-between-pages/using-link

Next.js supports client-side history — so when you hit the back button, it will navigate to the page client-side.
