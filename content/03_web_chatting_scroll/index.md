---
emoji: ๐ฌ
title: ์น์์ ์ฑํ ์คํฌ๋กค ๊ตฌํํด๋ณด๊ธฐ
date: '2022-03-27 23:00:00'
author: ์ ์
tags: WebAPI ResizeObserver IntersectionObserver chatting scroll react
categories: featured challenge
---

์น์์ ์ฑํ ๊ธฐ๋ฅ์ ๊ตฌํํ  ๊ธฐํ๊ฐ ์์๋ค. ์์ผ์ ํ์ฉํด ์ค์๊ฐ ์ฑํ์ ๊ตฌํํ๋ ๊ฒ ์ธ์๋ ์ ๋ฅผ ๋จน์๋ ์์f์ด ์์๋๋ฐ, ๋ฐ๋ก ์คํฌ๋กค์ด์๋ค. 

์ด์  ์ฑํ ๋ชฉ๋ก์ ํ์ธํ๊ธฐ ์ํด ์คํฌ๋กค์ ์๋ก ์ฌ๋ฆฌ๋ฉด ์ ์ ๊ฐ ๋ณด๊ณ  ์๋ ์คํฌ๋กค์ ๊ทธ๋๋ก ์ ์งํ ์ฑ, ์์๋ง ๋ด์ฉ์ ๋ถ๋ฌ์ ๋ถ์ฌ์ผ ํ๋ค. 

์ด ์์์ React ํ๋ก์ ํธ์์ ์ด๋ป๊ฒ ์ ๊ทผํ๋์ง ์ ์ด๋ณด๋ ค๊ณ  ํ๋ค. 

## ๋ฐ์ค ๋๋๊ธฐ
์๋ ์ด๋ฏธ์ง์ฒ๋ผ ์ฑํ์ฐฝ์ด ์๋ค๊ณ  ๊ฐ์ ํด๋ณด์.
![chat basic](../../assets/03_chat-basic.png)

์ฑํ์ฐฝ์ ๊ฐ์ธ๋ ์ปจํ์ด๋(= chatContainer)๋ฅผ ๋ง๋ค์๋ค. ์ด ์ปจํ์ด๋๋ ์ ์ ๊ฐ ์ฑํ์ ๋ณด๋ ๊ฐ์ ์์ญ์ด ๋๋ค.
![chat container](../../assets/04_chat-container.png)

๊ทธ๋ฆฌ๊ณ  ์ฑํ ๋ฆฌ์คํธ๋ฅผ ๊ฐ์ธ๋ ์ปจํ์ด๋(= chatListContainer)๋ฅผ ๋ง๋ค์๋ค. ์ฑํ ๋ฆฌ์คํธ ์ปจํ์ด๋ ์ต์๋จ์๋ ์ฑํ ๋ชฉ๋ก์ ์ถ๊ฐ๋ก ๋ถ๋ฌ์ฌ ํธ๋ฆฌ๊ฑฐ ์ญํ ์ ํ๋ ์์(= loadMoreTrigger)๋ฅผ ๋์๋ค. 
![load more trigger with container](../../assets/07_load-more-trigger-with-container.png)

์๋ ๊ทธ๋ฆผ์ ์ ์ ๊ฐ ์คํฌ๋กค์ ์ฌ๋ ค chatListContainer ๋์ loadMoreTrigger๊ฐ ๊ฐ์ ์์ญ์ ํฌํจ๋๋ ์ํฉ์ด๋ค.
![scroll](../../assets/08_scroll.png)

## Infinite ์คํฌ๋กค ๋ง๋ค๊ธฐ - IntersectionObserver
Web API์์ ์ ๊ณตํ๋ [IntersectionObserver](https://developer.mozilla.org/ko/docs/Web/API/Intersection_Observer_API)๋ฅผ ์ฌ์ฉํด Infinite ์คํฌ๋กค์ ๊ตฌํํ๋ค.

์ ์์  ์ด๋ฏธ์ง์ loadMoreTrigger๊ฐ IntersectionObserver์ observe ํ๋ ๋์์ด ๋๋ค. ์ ์ ๊ฐ ์คํฌ๋กค์ ์ฌ๋ ค loadMoreTrigger๊ฐ ๊ฐ์์์ญ์ ๋ค์ด์ค๊ฒ ๋๋ฉด(= isIntersecting) ๋ค์ ๋ํ๋ชฉ๋ก์ ๋ถ๋ฌ์ค๋ api ์์ฒญ์ ํ๋ค.



```js
const loadMoreTrigger = useRef<HTMLDivElement | null>(null);
const isloadMore = useRef<boolean>(false);

useEffect(() => {
  const loadMoreObserver = new IntersectionObserver(
    ([{ isIntersecting }]) => {
      if (isIntersecting) {
        onFetchPreviousPage();
        isloadMore.current = true;
      }
    }
  );

  const trigger = loadMoreTrigger.current!;
  loadMoreObserver.observe(trigger);

  return () => {
    loadMoreObserver.unobserve(trigger);
  };
}, [onFetchPreviousPage]);
```

## ์คํฌ๋กค ์์น ์ ์งํ๊ธฐ - ResizeObserver
์ด์  ๋ํ ๋ชฉ๋ก์ ๋ถ๋ฌ์ค๋ ์คํฌ๋กค์ด ๋ถ๋ฌ์จ ๋ฐ์ดํฐ๋ฅผ ๋ฐ๋ผ ์๋ก ์ฌ๋ผ๊ฐ๋ค. ์ฑํ ๋ชฉ๋ก์ด ์ถ๊ฐ๋์ด๋ ์คํฌ๋กค์ด ๋ฐ๋ผ ์ฌ๋ผ๊ฐ์ง ์๊ฒ๋  ํ๊ธฐ ์ํด ์ฌ์ฉํ ๊ฒ์ด
[ResizeObserver](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver) ์ด๋ค.

- ์ ์์  ๊ทธ๋ฆผ์์ chatListContainer๋ฅผ observe ๋์์ผ๋ก ํ๋ค. ์ด์  ๋ํ ๋ชฉ๋ก์ ๋ถ๋ฌ์ chatListContainer์ resize ์ด๋ฒคํธ๊ฐ ๋ฐ์ํ๋ฉด ์ฝ๋ฐฑ์ด ์คํ๋๋ค.
- ์ฝ๋ฐฑ ์ธ์๋ก ๋ฐ๋ [ResizeObserverEntry](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserverEntry)๋ฅผ ์ฌ์ฉํด ๋ณ๊ฒฝ๋ childNodes์ ๊ฐฏ์(= nodesRecord)์ ๋์ด(= scrollRecord)๋ฅผ ์ ์ฅํด์ฃผ์๋ค.
- ์ฑํ๋ฐฉ์ ์ฒ์ ์ง์ํ์ ๊ฒฝ์ฐ๋ nodeRecord๊ฐ ์ด๊ธฐ๊ฐ(= 0)์ธ ๊ฒ์ ํ์ฉํด ๊ตฌ๋ถํ๋ค.
- ์ฑํ์ ๋ฐ์ดํฐ๊ฐ ์ถ๊ฐ๋ ๊ฒฝ์ฐ๋ nodeRrecord์ ์ ์ฅ๋ ๊ฐ๊ณผ ํ์ฌ ๋ณ๊ฒฝ๋ childNodes์ ๊ฐฏ์๊ฐ ๋ค๋ฅผ ๋๋ง์ผ๋ก ํ์ ์ง์๋ค. (์ฑํ ๋ฐ์ดํฐ๋ฅผ ๋ถ๋ฌ์ค๋ ๊ณผ์ ์์ resize ์ด๋ฒคํธ๊ฐ ํ๋ฒ๋ง ๋ฐ์ํ์ง ์๊ธฐ ๋๋ฌธ์ด๋ค.)
  - ์ด๋ isLoadMore๊ฐ false์ธ ๊ฒฝ์ฐ๋ ์ถ๊ฐ๋ ๋ฐ์ดํฐ๊ฐ ์์ง๋ง trigger๋ก ๋ถ๋ฌ์จ ๋ฐ์ดํฐ๊ฐ ์๋๋ฏ๋ก ์๋ก์ด ๋ฉ์์ง๊ฐ ์จ ๊ฒ์ ๋ํ ๊ตฌ๋ถ์ ํ๋๋ฐ ์ฌ์ฉํ๋ค.
  - ๊ทธ ์ธ ๊ฒฝ์ฐ์ ์์์ ๋ณ๊ฒฝ๋ ๋์ด(= contentRect.height)์์ ์์ ์ ์ฅํด๋์๋ scrollRecord๋ฅผ ๋บ ๊ฐ๋งํผ ์คํฌ๋กค์ ๋ด๋ ค ์์น๋ฅผ ์ ์ง์ํฌ ์ ์์๋ค.

```js
const containerRef = useRef<HTMLDivElement | null>(null);
const chatListContainerRef = useRef<HTMLDivElement | null>(null);
const scrollRecord = useRef<number>(0);
const nodesRecord = useRef<number>(0);
/** loadMoreTrigger ์ํ ๊ด๋ฆฌ์ฉ */
const isloadMore = useRef<boolean>(false);

useEffect(() => {
  const container = containerRef.current!;
  const chatListContainer = chatListContainerRef.current!;

  const callback: ResizeObserverCallback = (entries) => {
    entries.forEach((entry) => {
      /** ์ฒ์ ์ง์ ์ ์คํฌ๋กค ๋งจ ์๋๋ก */
      if (!nodesRecord.current) {
        container.scrollTo({
        top: Number.MAX_SAFE_INTEGER,
      });
      isloadMore.current = false;

      /** ์ฑํ ๋ฐ์ดํฐ๊ฐ ์ถ๊ฐ๋  ๊ฒฝ์ฐ */
      } else if (nodesRecord.current !== entry.target.childNodes.length) {

      /** ์ถ๊ฐ๋ ๋ฐ์ดํฐ๊ฐ ์๋๋ฐ isLoadMore๊ฐ false์ธ ๊ฒฝ์ฐ๋ ์๋ก์ด ์ฑํ์ด๋ฏ๋ก ๋งจ ์๋๋ก ๋ด๋ฆผ */
        if (!isloadMore.current) {
          container.scrollTo({
            top: Number.MAX_SAFE_INTEGER,
            behavior: 'smooth',
          });

        /** ์ด ์ธ์๋ resized๋ ๋์ด์์ ์ด์ ์ ์ ์ฅํด๋์ ๋์ด ๋งํผ์ ๋ด๋ ค ์คํฌ๋กค์ ์์น๋ฅผ ์ ์ง์ํด */
        } else {
          isloadMore.current = false;
          container.scrollTo({
            top: entry.contentRect.height - scrollRecord.current,
          });
        }
      }

    /** ์ถ๊ฐ๋ ์ฑํ ๋ธ๋ ์ ๋ณด ์๋ฐ์ดํธ */
    nodesRecord.current = entry.target.childNodes.length;
    scrollRecord.current = entry.contentRect.height;
    });

  };

  const observer = new ResizeObserver(callback);
  observer.observe(chatListContainer, { box: 'border-box' });

  return () => {
    observer.disconnect();
  };
}, []);
```




```toc
```




