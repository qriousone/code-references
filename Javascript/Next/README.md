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
The only special directories next needs are `/pages` and `/public`. Other directories could be named anything.

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

Next.js supports client-side history — when you hit the back button, it will navigate to the page client-side.

If we need to add title attribute to the link you should do it like this:
```javascript
<Link href="/about">
  <a title="About Page">About Page</a>
</Link>
```
## Shared Components
Create header component `components/Header.js` with code below:
```javascript
import Link from 'next/link';

const linkStyle = {
  marginRight: 15
};

const Header = () => (
  <div>
    <Link href="/">
      <a style={linkStyle}>Home</a>
    </Link>
    <Link href="/about">
      <a style={linkStyle}>About</a>
    </Link>
  </div>
);

export default Header;
```
### Import component

Replace code inside pages/index.js with:
```javascript
import Header from '../components/Header';

export default function Index() {
  return (
    <div>
      <Header />
      <p>Hello Next.js</p>
    </div>
  );
}
```
### Layout component
Add this code to `components/MyLayout.js`:
```javascript
import Header from './Header';

const layoutStyle = {
  margin: 20,
  padding: 20,
  border: '1px solid #DDD'
};

const Layout = props => (
  <div style={layoutStyle}>
    <Header />
    {props.children}
  </div>
);

export default Layout;
```
```javascript
import Layout from '../components/MyLayout';

export default function About() {
  return (
    <Layout>
      <p>This is the about page</p>
    </Layout>
  );
}
```
### Other methods for creating a Layout components
#### Method 1 - High Order Component
```javascript
// components/MyLayout.js

import Header from './Header';

const layoutStyle = {
  margin: 20,
  padding: 20,
  border: '1px solid #DDD'
};

const withLayout = Page => {
  return () => (
    <div style={layoutStyle}>
      <Header />
      <Page />
    </div>
  );
};

export default withLayout;
```
```javascript
// pages/index.js

import withLayout from '../components/MyLayout';

const Page = () => <p>Hello Next.js</p>;

export default withLayout(Page);
```

#### Method 2 - Page content as a prop
```javascript
// components/MyLayout.js

import Header from './Header';

const layoutStyle = {
  margin: 20,
  padding: 20,
  border: '1px solid #DDD'
};

const Layout = props => (
  <div style={layoutStyle}>
    <Header />
    {props.content}
  </div>
);

export default Layout;
```
```javascript
// pages/index.js

import Layout from '../components/MyLayout.js';

const indexPageContent = <p>Hello Next.js</p>;

export default function Index() {
  return <Layout content={indexPageContent} />;
}
```
## Dynamic Pages
Create a list of posts by replacing the content in `pages/index.js` with:
```javascript
import Layout from '../components/MyLayout';
import Link from 'next/link';

const PostLink = props => (
  <li>
    <Link href={`/post?title=${props.title}`}>
      <a>{props.title}</a>
    </Link>
  </li>
);
export default function Blog() {
  return (
    <Layout>
      <h1>My Blog</h1>
      <ul>
        <PostLink title="Hello Next.js" />
        <PostLink title="Learn Next.js is awesome" />
        <PostLink title="Deploy apps with Zeit" />
      </ul>
    </Layout>
  );
}
```
The above example is passing data via query string. The data is from title prop is being passed through the `title` query param.

### Create post page
`pages/post.js`
```javascript
import { useRouter } from 'next/router';
import Layout from '../components/MyLayout';

const Page = () => {
  const router = useRouter();
  return (
    <Layout>
      <h1>{router.query.title}</h1>
      <p>This is the blog post content.</p>
    </Layout>
  );
};

export default Page;
```
`useRouter` allows you to access the router object inside the page, it's a React Hook, and it works with functional components.

In the following example you can see useRouter being added to a component other than the exported page:

```javascript
import { useRouter } from 'next/router';
import Layout from '../components/MyLayout.js';

const Content = () => {
  const router = useRouter();
  return (
    <>
      <h1>{router.query.title}</h1>
      <p>This is the blog post content.</p>
    </>
  );
};

const Page = () => (
  <Layout>
    <Content />
  </Layout>
);

export default Page;
```
It data doesn't have to be pass query strings it could be done with clean URLs (Example:  `http://localhost:3000/blog/hello-nextjs`)
