---
emoji: ๐ฟ
title: Remix Quickstart ๋ฐ๋ผํด๋ณด๊ธฐ
date: '2022-02-13 23:00:00'
author: ์ ์
tags: remix quickstart typescript vscode
categories: challenge
---


## Remix Quickstart ๋ค์ด๊ฐ๊ธฐ ์ ์
- ๋ฆฌ๋ฏน์ค์์ ์ ๊ณตํ๋ Quickstart์ ์ฃผ์ ๋ Blog ๋ง๋ค๊ธฐ์ด๋ค.
- ํ์คํ ํ๋ ์์ํฌ์ด์ง๋ง ๋ณธ ์์ ์์ DB๋ฅผ ๋ค๋ฃจ์ง๋ ์๋๋ค. ๋์  ํ์ผ ์์คํ ์ฝ๊ณ  ์ฐ๋ ๊ฒ์ ์ฌ์ฉํ๋ค.
- [์๋ฌธ](https://remix.run/docs/en/v1/tutorials/blog)์์๋ JS๋ฅผ ๋จผ์  ์ฌ์ฉํ๊ณ  ๋์ค์ type์ ์ถ๊ฐํด TS๋ก ๊ตฌ์ฑํ๋ ๋ฐฉ์์ด์ง๋ง ๋ณธ ํฌ์คํ์์๋ TS์ฝ๋๋ฅผ ๋ฐ๋ก ์ฌ์ฉํ๋ค. 


### 1. ์์ ์  ์ธํ
- Node.js 14 ์ด์
- npm 7 ๋ฒ์  ์ด์

### 2. shell ๋ก ๋ฆฌ๋ฏน์ค ํ๋ก์ ํธ ๋ง๋ค๊ธฐ
์ด๋ฏธ ์์ ํด๋๋ฅผ ๋ง๋ค์๋ค๋ฉด 1-option1 ์ ์ฌ์ฉํ๊ณ  ๊ทธ๋ ์ง ์๋ค๋ฉด 1-option2๋ฅผ ์ฌ์ฉํ๋ค.

```shell
// 1-option1 ์ด ๋ฐฉ๋ฒ์ ์ฌ์ฉํ๋ฉด package.json์ ํ๋ก์ ํธ name์ remix-app-template์ผ๋ก ์์ฑ๋๋ค
$ mkdir remix-text
$ npx create-remix@latest .

// 1-option2 
$ npx create-remix@latest remix-test

// 2. ์คํ๋๋ prompt ์์ ๋ฐฐํฌ ํ๋ซํผ, ์ฌ์ฉ ์ธ์ด, npm ์ค์น ์ฌ๋ถ๋ฅผ ๋ฌป๋๋ค. 
๋ณธ ํฌ์คํ์์๋ Remix App Server, typescript, npm install์ ์ ํํ๋ค.

// 3. ๊ฐ๋ฐ๋ชจ๋๋ก ์คํํ๋ค
$ npm run dev
```
<br />
ํ๋กฌํํธ์์ ์ ํํ  ์ ์๋ ๋ฐฐํฌ ํ๋ซํผ์๋ Remix App Server, Express Server, AWS Lambda, Fly.io, Netlify, Vercel, Cloudflare Pages, Cloudflare Workers ๊ฐ ์๋ค. <br/>
๋ณธ ํฌ์คํ์์๋ Remix App Server๋ฅผ ์ฌ์ฉํ๋ค. <br/>
๋ง์ฝ ๋ฐฐํฌํ  ๊ณํ์ด ์๋ค๋ฉด ๋ฐฐํฌ ํ๋ซํผ์ ๋ง๊ฒ๋ ํ๊ฒ์ ๋ณ๊ฒฝํด์ฃผ๋ฉด ๋๋ค. ๋ณ๊ฒฝํ๋ ๋ฐฉ๋ฒ์ ์์ฑ๋ ํ๋ก์ ํธ์ README ์์ ํ์ธ ๊ฐ๋ฅํ๋ค. ์๋๋ ํ๋กฌํํธ์์ ๋ฐฐํฌ ํ๊ฒ์ ์ ํ๋ ๋จ๊ณ์ ์บก์ณ๋ณธ์ด๋ค.
<br />

![create remix prompt](../../assets/02_create-remix-prompt.png)

์ฑ ์คํ ์ http://localhost:3000 ์์ ์ ๋๋ก ์คํ๋์ง ์๋๋ค๋ฉด `postinstall` ์ด ์คํ๋์๋์ง ํ์ธํด๋ณธ๋ค. ๋ง์ฝ ์คํ๋์ง ์์๋ค๋ฉด `npm run postintall`๋ก ์ง์  ์คํํด์ค๋ค. npm config ํ์ผ์ `ignore-scripts=true`๊ฐ ์ถ๊ฐ๋์ด์๊ฑฐ๋ pnpm ๋๋ ๋ค๋ฅธ ํจํค์ง ๋งค๋์ ๋ฅผ ์ฌ์ฉํ๊ณ  ์๋ค๋ฉด ์๋์ผ๋ก postinstall ์ด ์คํ๋์ง ์์ ์ ์๋ค.

### 3. routes ํด๋๋ฅผ ์ฌ์ฉํด /posts ๋ผ์ฐํธ ๋ง๋ค๊ธฐ

์ด๋ฏธ ์์ฑ๋์ด ์๋ `app/routes/index.tsx` ์ ๊ธฐ์กด ๋ด์ฉ์ ์ง์ฐ๊ณ  ์๋์ ๊ฐ์ด ๊ตฌ์ฑํด ์ค๋ค.

```ts
// app/routes/index.tsx

import { Link } from 'remix';

export default function Index() {
    return <Link to='/posts'>Posts</Link>;
}
```

+ ์ฐธ๊ณ : `app/root.tsx`์ `<Outlet/>`, `<Scripts />`๊ฐ ์๊ธฐ ๋๋ฌธ์ `<Link />`๋ ์ด๋ ๊ณณ์์๋ ์ฌ์ฉ ๊ฐ๋ฅํ๋ค. 

๋ค์์ `app/routes/posts/index.tsx`๋ฅผ ์์ฑํด์ค๋ค.

```ts
// app/routes/posts/index.tsx

export default function Posts() {
  return (
    <div>
      <h1>Posts</h1>
    </div>
  );
}
```
์ด์  http://localhost:3000/posts ์์ Posts๋ฅผ ํ์ธํ  ์ ์์ ๊ฒ์ด๋ค.
ํด๋๋ช ํ์์ index๋ผ๋ ์ด๋ฆ์ผ๋ก ์ปดํฌ๋ํธ๋ฅผ ๋ง๋ฆ์ผ๋ก ํด๋๋ช๊ณผ ๊ฐ์ route๋ฅผ ์์ฑํ  ์ ์๊ณ , index๊ฐ ์๋ ๋ค๋ฅธ ํ์ผ๋ช์ ์ถ๊ฐํ  ๊ฒฝ์ฐ, `/ํด๋๋ช/index๊ฐ ์๋ ํ์ผ๋ช` ์ผ๋ก ๋ผ์ฐํธ๊ฐ ์์ฑ๋๋ค.


### 4. loader๋ฅผ ์ฌ์ฉํด ๋ฐ์ดํฐ ๋ถ๋ฌ์ค๊ธฐ
๋ฆฌ๋ฏน์ค ํ๋ก ํธ ์ปดํฌ๋ํธ์์๋ fetch๋ฅผ ์ฌ์ฉํ  ํ์๊ฐ ์๋ค. loader๋ฅผ ํตํ ๋ฐ์ดํฐ ๋ถ๋ฌ์ค๋ ๋ก์ง์ ๋ฆฌ๋ฏน์ค ์์ฒด์ ์ผ๋ก ์ ๊ณตํด์ฃผ๊ณ  ์๋ค. 

์์์ ๋ง๋  `routes/posts/index.tsx`์ loader๋ฅผ ๋ถ์ฌ๋ณด์.

posts๋ฅผ ๊ฐ์ ธ์ค๋ ๋ชจ๋ ํ์ผ์ ์๋์ ๊ฐ์ด ๋ง๋ ๋ค.

```ts
// app/post.ts

export type Post = {
  slug: string;
  title: string;
};

export function getPosts() {
  const posts: Post[] = [
    {
      slug: "my-first-post",
      title: "My First Post"
    },
    {
      slug: "90s-mixtape",
      title: "A Mixtape I Made Just For You"
    }
  ];
  return posts;
}

```

<br/>

ํด๋น ํ์ผ์ `/routes/posts/index.tsx` ์ import ์์ผ loader์ ์ ์ฉ์์ผ์ค๋ค.
๊ทธ๋ฆฌ๊ณ  post์ slug๋ก ์ด๋ํ๊ฒ ๋๋ Link๋ ์ถ๊ฐํด์ค๋ค.

```ts 
// app/route/posts/index.tsx

import { Link, useLoaderData } from 'remix'; // ์ถ๊ฐ
import { getPosts, Post } from "~/post";

export const loader = async () => {
  return getPosts(); // ์ถ๊ฐ
};

export default function Posts() {
  const posts = useLoaderData<Post[]>(); // ์ถ๊ฐ
  console.log(posts); // ํ์คํธ์ฉ ์ฝ์ ๋ก๊ทธ ์ถ๊ฐ

  return (
    <div>
      <h1>Posts</h1>
      <ul>
        {posts.map(post => ( // ์ถ๊ฐ
          <li key={post.slug}> // ์ถ๊ฐ
            <Link to={post.slug}>{post.title}</Link> // ์ถ๊ฐ
          </li> // ์ถ๊ฐ
        ))} // ์ถ๊ฐ
      </ul>
    </div>
  );
}
```
<br />

loader๋ ์ปดํฌ๋ํธ๋ฅผ ์ํ ๋ฐฑ์๋ API์ด๊ณ  `useLoaderData`๋ก ๋ฐ์ดํฐ๋ฅผ ๋ถ๋ฌ์ ์ฌ์ฉํ  ์ ์๋ค. ์๋ฒ์ ๋ธ๋ผ์ฐ์  ์ฝ์ ๋ชจ๋ ์ด๋ ค์๋ค๋ฉด ๋ ๊ตฐ๋ฐ ๋ชจ๋ log๊ฐ ์ฐํ ๊ฒ์ ๋ณผ ์ ์์ ๊ฒ์ด๋ค. ์ด์ ๋ ๋ฆฌ๋ฏน์ค๊ฐ ์๋ฒ์์ HTML ํ์ผ์ ๋ณด๋ด๊ธฐ ์ํด render ํ๊ณ  ์ดํ ํด๋ผ์ด์ธํธ์์ ํด๋น HTML ํ์ผ๋ก hydrate ํ๊ธฐ ๋๋ฌธ์ด๋ค.
[์ฐธ๊ณ : React > hydrate()](https://ko.reactjs.org/docs/react-dom.html#hydrate)

### 5. ํ์ผ ์์คํ์ผ๋ก ํ์ผ ๋ถ๋ฌ์ค๊ธฐ
์ผ๋ฐ์ ์ผ๋ก ์ ์ฅํ๊ณ  ๋ถ๋ฌ์ค๋ ์์์ DB๋ฅผ ํ์ฉํ๊ฒ ์ง๋ง ์ง๊ธ์ ํํ ๋ฆฌ์ผ์ด๋ ํ์ผ ์์คํ์ ์ฌ์ฉํ๋ค.

์ต์์ ๋๋ ํ ๋ฆฌ์ ๋ฐ์ดํฐ๋ฒ ์ด์ค๊ฐ ๋  posts ํด๋๋ฅผ ์์ฑํ๋ค.
๊ทธ ์์ `my-first-post.md`, `90s-mixtape.md`๋ฅผ ์์ฑํ๋ค.

```md
// posts/my-first-post.md

---
title: My First Post
---

# This is my first post

Isn't it great?


// post/90s-mixtape.md

---
title: 90s Mixtape
---

# 90s Mixtape

- I wish (Skee-Lo)
- This Is How We Do It (Montell Jordan)
```
<br/>
๋ถ๋ฌ์ฌ ํ์ผ๋ค์ ๋ง๋ค์์ผ๋ getPosts์์ ์ด ํ์ผ๋ค์ ์ฝ์ด์ฌ ์ ์๋๋ก ์์ ํ๋ค.

์ฐ์  ํ์ผ ์์คํ์ ์ฝ๊ธฐ ์ํด ์๋ ๋๊ฐ์ง ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ ์ค์นํ๋ค.

```sh
// ํ์ผ์ ํ์ฑํ๋ ์ญํ 
$ npm add front-matter

// ํ์ผ ํ์ ์ฒดํฌํ๋ ์ญํ 
$ npm add tiny-invariant
```
<br/>
๊ทธ ๋ค์ getPosts๋ฅผ ์๋์ ๊ฐ์ด ์๋ฐ์ดํธํ๋ค.

```ts
// app/post.ts

import path from "path";
import fs from "fs/promises";
import parseFrontMatter from "front-matter";
import invariant from "tiny-invariant";

export type Post = {
  slug: string;
  title: string;
};

export type PostMarkdownAttributes = {
  title: string;
};

const postsPath = path.join(__dirname, "..", "posts");

function isValidPostAttributes(
  attributes: any
): attributes is PostMarkdownAttributes {
  return attributes?.title;
}

export async function getPosts() {
  const dir = await fs.readdir(postsPath);
  return Promise.all(
    dir.map(async filename => {
      const file = await fs.readFile(
        path.join(postsPath, filename)
      );
      const { attributes } = parseFrontMatter(
        file.toString()
      );
      invariant(
        isValidPostAttributes(attributes),
        `${filename} has bad meta data!`
      );
      return {
        slug: filename.replace(/\.md$/, ""),
        title: attributes.title
      };
    })
  );
}
```
### 6. $๋ฅผ ์ฌ์ฉํ Dynamic route ์ถ๊ฐํ๊ธฐ

์์์ slug๋ก ์ฐ๊ฒฐ๋๋ Link๋ฅผ ์ถ๊ฐํ์ผ๋, slug ๋ผ์ฐํธ์ ํด๋นํ๋ ํ๋ฉด์ ์ถ๊ฐํด์ผ ํ๋ค.

/routes/posts ํด๋ ํ์์ $slug ํ์ผ์ ์์ฑํ๋ค.
ํ์ผ๋ช์ `$`๋ฅผ ๋ถ์ด๋ฉด loader์ params ๊ฐ์ฑ์์ `$`๋ท ๊ฐ์ key๋ก ๋ฐ์์ฌ ์ ์๋ค.

```ts
// app/routes/posts/$slug.tsx

import { useLoaderData } from "remix";
import type { LoaderFunction } from "remix"; // ์ถ๊ฐ

export const loader: LoaderFunction = async ({ params }) => { //์ถ๊ฐ
  return params.slug; // ์ถ๊ฐ
};

export default function PostSlug() {
  const slug = useLoaderData(); // ์ถ๊ฐ
  return (
    <div>
      <h1>Some Post: {slug}</h1> // ์ถ๊ฐ
    </div>
  );
}
```

### 7. params๋ก ๋ฐ์ดํฐ ๊ฐ์ ธ์ค๊ธฐ
`post.ts`์ getPost๋ผ๋ ์๋ก์ด ํจ์๋ฅผ ์ถ๊ฐํ๋ค. slug๋ฅผ ์ธ์๋ก ๋ฐ๊ณ  ๊ทธ์ ํด๋นํ๋ title, slug๋ฅผ ๋ฆฌํดํ๋ค.

```ts
// app/post.ts

export async function getPost(slug: string) {
  const filepath = path.join(postsPath, slug + ".md");
  const file = await fs.readFile(filepath);
  const { attributes } = parseFrontMatter(file.toString());
  invariant(
    isValidPostAttributes(attributes),
    `Post ${filepath} is missing attributes`
  );
  return { slug, title: attributes.title };
}

```
<br/>

์์ getPost ํจ์๋ฅผ `$slug.tsx` loader์ ์ ์ฉ์ํจ๋ค.

```ts
// app/routes/posts/$slug.tsx

import { useLoaderData } from "remix";
import type { LoaderFunction } from "remix";
import invariant from "tiny-invariant"; // ์ถ๊ฐ (ํ์  ์ฒดํฌ์ฉ)

import { getPost } from "~/post"; // ์ถ๊ฐ 

export const loader: LoaderFunction = async ({
  params
}) => {
  invariant(params.slug, "expected params.slug"); // ์ถ๊ฐ (ํ์  ์ฒดํฌ์ฉ)
  return getPost(params.slug); // ์ถ๊ฐ 
};

export default function PostSlug() {
  const post = useLoaderData(); // ์ถ๊ฐ 
  return (
    <div>
      <h1>{post.title}</h1> // ์ถ๊ฐ
    </div>
  );
}

```
<br />

์คํํด์ ํ์ธํด๋ณด๋ฉด ๊ฐ ๋งํฌ๋ค์ด ํ์ผ๋ณ๋ก ๋งํฌ๊ฐ ์๊ณ  ํ๋๋ฅผ ํด๋ฆญํ์ ๋, ํด๋นํ๋ ๋งํฌ๋ค์ด ํ์ผ ์ด๋ฆ์ผ๋ก ๋ผ์ฐํธ๊ฐ ์ด๋๋๊ณ  ํ์ผ์ title์ ๊ทธ๋ฆฌ๋ ๊ฒ์ ํ์ธํ  ์ ์๋ค.

๋ง์ง๋ง์ผ๋ก `marked`๋ผ๋ ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ ์ฌ์ฉํด ๋งํฌ๋ค์ด ํ์ผ ๋ด์ฉ์ html ๋ณํํด ํ๋ฉด์ ๊ทธ๋ฆฌ๋ ๋จ๊ณ๊ฐ ์์ง๋ง ์ฌ๊ธฐ์๋ ๋์ด๊ฐ๋๋ก ํ๊ฒ ๋ค. 

### 8. ๋ธ๋ก๊ทธ ์ด๋๋ฏผ ๋ง๋ค๊ธฐ

๊ธ์ ํฌ์คํํ  ๋, ๋จ์ ์คํ ์์ ์ผ๋ก ์ธํด ๋งค๋ฒ ๋ฐฐํฌํ๋ ๊ฒ์ ๋ถํ์ํ๋ค. 
 ์์ ๋ ๊ธ์ ๋ฐ์ดํฐ๋ฒ ์ด์ค์ ๋ฐ๋ก ๋ฑ๋กํ๋ค๋ฉด ๋งค๋ฒ ๋ฐฐํฌ๋ฅผ ํด์ผํ  ์ผ์ ์์ ๊ฒ์ด๋ค. ๊ทธ๋์ ํฌ์คํ ๊ธ์ ๊ด๋ฆฌํ๋ ์ด๋๋ฏผ์ ๋ง๋ค์ด๋ณด๋ ค๊ณ  ํ๋ค.

์๋์ฒ๋ผ admin ๋ผ์ฐํธ๋ฅผ ๋ง๋ ๋ค.
```ts
//app/routes/admin.tsx

import { Link, useLoaderData } from "remix";

import { getPosts } from "~/post";
import type { Post } from "~/post";

export const loader = async () => {
  return getPosts();
};

export default function Admin() {
  const posts = useLoaderData<Post[]>();
  return (
    <div className="admin">
      <nav>
        <h1>Admin</h1>
        <ul>
          {posts.map(post => (
            <li key={post.slug}>
              <Link to={`/posts/${post.slug}`}>
                {post.title}
              </Link>
            </li>
          ))}
        </ul>
      </nav>
      <main>...</main>
    </div>
  );
}

```
<br />

์์ํ๊ธฐ์ ์์ ์คํ์ผ๋ง์ ๋จผ์  ํด์ค๋ค. (์๋์์ ์งํํ๋ Nested Routes๋ฅผ ์ข ๋ ์ ๋ณด์ฌ์ฃผ๊ธฐ ์ํจ์ด๋ค.)

``` css
/* app/styles/admin.css */

.admin {
  display: flex;
}

.admin > nav {
  padding-right: 2rem;
}

.admin > main {
  flex: 1;
  border-left: solid 1px #ccc;
  padding-left: 2rem;
}

em {
  color: red;
}

```
<br />
์์ ์คํ์ผ ์ํธ๋ฅผ admin ๋ผ์ฐํธ์ ์ฐ๊ฒฐ์์ผ์ค๋ค.

``` ts
// app/routes/admin.tsx

import { Link, useLoaderData } from "remix";

import { getPosts } from "~/post";
import type { Post } from "~/post";
import adminStyles from "~/styles/admin.css";

export const links = () => {
  return [{ rel: "stylesheet", href: adminStyles }];
};

...
```
<br/>

๋ผ์ฐํธ์์ ์ฌ์ฉ๋๋ links๋ `<link>` ํ๊ทธ๋ฅผ ๋ฐํํ๊ณ  ๋ชจ๋  ๋งํฌ๋ค์ด ๋ชจ์ฌ root.tsx์ ์๋ `<Links />`์ ๋ ๋๋ง๋๋ค. 

### 9. Outlet์ ์ฌ์ฉํ Nested Routes ๋ง๋ค๊ธฐ

์ด์  nested routes๋ฅผ ๋ง๋ค์ด๋ณด์.
admin ํด๋๋ฅผ ๋ง๋ค๊ณ  ๊ทธ ์์ `index.tsx`๋ฅผ ๋ง๋ ๋ค. ํด๋ฆญ์ `/new`๋ก ์ด๋๋๋ ๋งํฌ๋ ์ถ๊ฐํด์ค๋ค.
```ts
// app/routes/admin/index.tsx

import { Link } from "remix";

export default function AdminIndex() {
  return (
    <p>
      <Link to="new">Create a New Post</Link>
    </p>
  );
}

```
<br />

๊ทธ๋ฆฌ๊ณ  `/routes/admin.tsx`์ ๋ฆฌ๋ฏน์ค์์ ์ ๊ณตํ๋ `<Outlet />` ์ปดํฌ๋ํธ๋ฅผ ์ถ๊ฐํ๋ค.

```ts
// app/routes/admin.tsx

import { Outlet, Link, useLoaderData } from "remix"; // ์ถ๊ฐ

//...
export default function Admin() {
  const posts = useLoaderData<Post[]>();
  return (
    <div className="admin">
      <nav>
      ...
      </nav>
      <main>
        <Outlet /> // ์ถ๊ฐ
      </main>
    </div>
  );
}
```
<br/>

์ด์  `/new`์ ํด๋นํ๋ ๋ผ์ฐํธ๋ ๋ง๋ค์ด๋ณด์.

```ts
// app/routes/admin/new.tsx

export default function NewPost() {
  return <h2>New Post</h2>;
}
```
<br/>

์คํํด์ ํ์ธํด๋ณด์. routes ํด๋ ํ์์ `admin.tsx` ๋ฅผ ๋ง๋ค๊ณ  ํด๋น ํ์ผ์์ `<Outlet />`์ ์ฌ์ฉํ๋ฉด ๊ทธ ์๋ฆฌ์ ___ํ์ผ๋ช๊ณผ ๋์ผํ___ ๋๋ ํ ๋ฆฌ ๋ด๋ถ ๊ฐ์ ๊ฐ์ ธ์จ๋ค. `index.tsx`๊ฐ ๊ธฐ๋ณธ ๊ฐ์ด ๋๊ณ  `new.tsx` ์ ๊ฒฝ์ฐ `/admin/new`์ ๊ฐ์ด ๋ผ์ฐํธ๊ฐ ์์ฑ๋๋ค.

### 10. action์ ์ฌ์ฉํด ํฌ์คํํ๊ณ  useActionData๋ฅผ ์ฌ์ฉํด ์๋ฌ ํธ๋ค๋งํ๊ธฐ
/new ๋ผ์ฐํธ์ ์๋ก์ด ๊ธ์ ํฌ์คํํ  ์ ์๋ form์ ๋ง๋ค์ด๋ณด์.

```ts
// app/routes/admin/new.tsx

import { Form } from "remix";

export default function NewPost() {
  return (
    <Form method="post">
      <p>
        <label>
          Post Title: <input type="text" name="title" />
        </label>
      </p>
      <p>
        <label>
          Post Slug: <input type="text" name="slug" />
        </label>
      </p>
      <p>
        <label htmlFor="markdown">Markdown:</label>
        <br />
        <textarea id="markdown" rows={20} name="markdown" />
      </p>
      <p>
        <button type="submit">Create Post</button>
      </p>
    </Form>
  );
}

```
<br />
ํฌ์คํํ  ์ ์๋ createPost ํจ์๋ฅผ post.ts ๋ชจ๋์ ์ถ๊ฐํ๋ค.

```ts
// app/post.ts
...
type NewPost = {
  title: string;
  slug: string;
  markdown: string;
};

export async function createPost(post: NewPost) {
  const md = `---\ntitle: ${post.title}\n---\n\n${post.markdown}`;
  await fs.writeFile(
    path.join(postsPath, post.slug + ".md"),
    md
  );
  return getPost(post.slug);
}

```
<br />

createPost๋ฅผ `new.tsx` ์ปดํฌ๋ํธ action์ ์ถ๊ฐํ๊ณ , useActionData๋ฅผ ์ฌ์ฉํด ์๋ฌ ๋ฐ์ UI๋ฅผ ๋ง๋ ๋ค.

```ts
// app/routes/admin/new.tsx

import { redirect, Form, useActionData } from "remix";
import type { ActionFunction } from "remix";
import { createPost } from "~/post";
import invariant from "tiny-invariant";

type PostError = {
  title?: boolean;
  slug?: boolean;
  markdown?: boolean;
};

export const action: ActionFunction = async ({ request }) => {
  const formData = await request.formData();

  const title = formData.get("title");
  const slug = formData.get("slug");
  const markdown = formData.get("markdown");

  const errors: PostError = {};
  if (!title) errors.title = true;
  if (!slug) errors.slug = true;
  if (!markdown) errors.markdown = true;

  if (Object.keys(errors).length) {
    return errors;
  }

  invariant(typeof title === "string");
  invariant(typeof slug === "string");
  invariant(typeof markdown === "string");

  await createPost({ title, slug, markdown });

  return redirect("/admin");
};

export default function NewPost() {
  const errors = useActionData();

  return (
    <Form method="post">
      <p>
        <label>
          Post Title:{" "}
          {errors?.title ? (
            <em>Title is required</em>
          ) : null}
          <input type="text" name="title" />
        </label>
      </p>
      <p>
        <label>
          Post Slug:{" "}
          {errors?.slug ? <em>Slug is required</em> : null}
          <input type="text" name="slug" />
        </label>
      </p>
      <p>
        <label htmlFor="markdown">Markdown:</label>{" "}
        {errors?.markdown ? (
          <em>Markdown is required</em>
        ) : null}
        <br />
        <textarea id="markdown" rows={20} name="markdown" />
      </p>
      <p>
        <button type="submit">Create Post</button>
      </p>
    </Form>
  );
}

```
์ง๊ธ ์ ์ํ๋ก ์คํํ๋ฉด ์๋ฐ์คํฌ๋ฆฝํธ ์์ด๋ ์๋ํ๋ค. ๋ฆฌ๋ฏน์ค๊ฐ HTTP, HTML๋ก๋ง ๊ตฌ์ฑ๋์๊ธฐ ๋๋ฌธ์ด๋ค.

### 11. useTransition์ ์ฌ์ฉํ Pending UI ๋ง๋ค๊ธฐ

`/admin/new.tsx` action ๋ด๋ถ์ setTimeout์ ์ฌ์ฉํด ๋๋ ์ด๋ฅผ ์ค๋ค.

```ts
// app/routes/admin/new.tsx

// ...
export const action: ActionFunction = async ({
  request
}) => {
  await new Promise(res => setTimeout(res, 1000)); // ์ถ๊ฐ

  const formData = await request.formData();

  const title = formData.get("title");
  const slug = formData.get("slug");
  const markdown = formData.get("markdown");
  // ...
};
//...

```
<br />

๋ฆฌ๋ฏน์ค์์ ์ ๊ณตํ๋ useTransition์ ์ฌ์ฉํด form์ด ํฌ์คํ ์ค์ธ์ง์ ๋ํ ์ฌ๋ถ๋ฅผ ๋ฐ์์ฌ ์ ์๋ค.

```ts
// app/routes/admin/new.tsx

import {
  useTransition, // ์ถ๊ฐ
  useActionData,
  Form,
  redirect
} from "remix";

// ...

export default function NewPost() {
  const errors = useActionData();
  const transition = useTransition(); // ์ถ๊ฐ

  return (
    <Form method="post">
      {/* ... */}

      <p>
        <button type="submit">
          {transition.submission // ์ถ๊ฐ
            ? "Creating..." // ์ถ๊ฐ
            : "Create Post"} // ์ถ๊ฐ
        </button>
      </p>
    </Form>
  );
}
```

## ๋ง๋ฌด๋ฆฌ
Remix Docs์์ ์ ๊ณตํ๋ [Quickstart](https://remix.run/docs/en/v1/tutorials/blog)๋ฅผ ๋ฐ๋ผํด๋ณด์๋ค.
Remix์ ๊ฐ์ฅ ๊ธฐ๋ณธ์ด ๋๋ routing, loader, action์ ์ฌ์ฉํด๋ณผ ์ ์์๊ณ , ์ ๋ฐ์ ์ผ๋ก ๋ฆฌ๋ฏน์ค๊ฐ ์ด๋ป๊ฒ ๋์๊ฐ๋์ง์ ๋ํ ์ดํด๋ฅผ ํ  ์ ์์๋ค. ๋ณธ ํํ ๋ฆฌ์ผ์์ ์ ๊ณตํ๋ ๊ธฐ๋ฅ ์ธ์๋ ๋ฉํ ํ๊ทธ, ์๋ฌ ๋ฐ์ด๋๋ฆฌ ๋ฑ ํธ๋ฆฌํ ๊ธฐ๋ฅ์ด ํ ๋๊ฐ๊ฐ ์๋๋ค. ์ด๊ฒ ํ๋ ์์ํฌ์ง! ๋ผ๋ ์๊ฐ์ ํ๋ฉฐ... <br/>
๋ค์ ํฌ์คํ์์๋ ํ์ผ์์คํ ์ฌ์ฉ์ด ์๋ ์ค์  DB๋ฅผ ์ฐ๋ํ๊ณ  ์ฌ์ฉํ๋ ๋ฐฉ๋ฒ๊น์ง ํฌ์คํํด๋ณด๋ ค๊ณ  ํ๋ค.

```toc
```


