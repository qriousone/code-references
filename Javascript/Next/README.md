# Next.js Notes
Next.js is a framework by Zeit. The framework allows you to jump right into developement with little to no webpack configuration. Out of the box, it comes with SSR (Server-side rendering) and intuitive page-routing with a lot more bells and whistles.

Most of the notes and content will be coming from nextjs own website for learning the framework. Link here:
https://nextjs.org/learn/basics/getting-started

### Setup
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
