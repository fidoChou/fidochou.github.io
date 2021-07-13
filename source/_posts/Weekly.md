---
layout: post
title: Weekly
date: 2021-06-19 21:20:31
categories: Weekly
---
#### 2021.07.20 - 2021.07.27

* [React: 五种不好的编程方式](https://betterprogramming.pub/5-code-smells-react-beginners-should-avoid-480c97799162)
* [ES2021](https://javascript.plainenglish.io/es12-is-going-to-make-your-life-easier-6be8d131e117)
	* replaceAll 已经用上了
	* &&=，||=，和??=
* [react-virtual](https://github.com/tannerlinsley/react-virtual)
* [视频防盗链技术方案研究与讲解](https://www.xiaoheidiannao.com/213903.html)
* [v8-release-92](https://v8.dev/blog/v8-release-92)


#### 2021.07.12 - 2021.07.19

* [JS Is Weird](https://jsisweird.com/)
	* 我挺讨厌这个网站的

* [Encoding data for POST requests](https://jakearchibald.com/2021/encoding-data-for-post-requests/)
	* URLSearchParams
		* URLSearchParams 做为请求体的 body，Content-Type 头部会自动设置为「application/x-www-form-urlencoded」
	
	* FormData
		* 最主要的是文件的传递
		* formData 做为请求体：Content-Type 头部会自动设置为「multipart/form-data」
		* FormData 可以转换为 URLSearchParams， 但含有文件时会抛错：application/x-www-form-urlencoded 不能代表文件数据

	* Other Fetch bodies
		* Blobs
		* Strings：Content-Type：「text/plain;charset=UTF-8」
		* Buffers：需要自己设置 Content-Type 的值
		* Streams：不要试图处理 multipart/form-data或application/x-www-form-urlencoded，使用 FormData 和 URLSearchParams
	* Bonus round: Converting Form Data to JSON

* [React — 5 Things That Might Surprise You](https://medium.com/geekculture/react-5-things-that-might-surprise-you-ddefd9fbac0f)
	* previous state is unpredictable
	* use useRef to store a static variable
	* 使用 key 强制重新挂载一个组件
	* Context API 会导致所有的的组件重新渲染，可以使用第三方库：[use-context-selector](https://github.com/dai-shi/use-context-selector)
	* 关于 Children 的 api：toArray、map、forEach、count、only


#### 2021.07.05 - 2021.07.11
* [How to useContext in React](https://www.robinwieruch.de/react-usecontext-hook)
* [You have to start using this CSS property in your websites](https://bootcamp.uxdesign.cc/you-have-to-start-using-this-css-property-in-your-websites-7353f46def79)
	* 我们的项目一直都有「safe-area」但我一直以为是通过 postCSS 定义的。其实在 iOS 上是原生的，安卓上可能有的手机有（我除了菜一无所有）

* [Writing memory efficient software applications in Node.js](https://medium.com/dev-bits/writing-memory-efficient-software-applications-in-node-js-5575f646b67f#id_token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjFiZjhhODRkM2VjZDc3ZTlmMmFkNWYwNmZmZDI2MDcwMWRkMDZkOTAiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL2FjY291bnRzLmdvb2dsZS5jb20iLCJuYmYiOjE2MjU3MTQyMjIsImF1ZCI6IjIxNjI5NjAzNTgzNC1rMWs2cWUwNjBzMnRwMmEyamFtNGxqZGNtczAwc3R0Zy5hcHBzLmdvb2dsZXVzZXJjb250ZW50LmNvbSIsInN1YiI6IjEwMzkxNDcyODA1ODg3NDA4MDA4NyIsImVtYWlsIjoiaW5remhvdUBnbWFpbC5jb20iLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwiYXpwIjoiMjE2Mjk2MDM1ODM0LWsxazZxZTA2MHMydHAyYTJqYW00bGpkY21zMDBzdHRnLmFwcHMuZ29vZ2xldXNlcmNvbnRlbnQuY29tIiwibmFtZSI6IuWRqOmiliIsInBpY3R1cmUiOiJodHRwczovL2xoMy5nb29nbGV1c2VyY29udGVudC5jb20vYS9BQVRYQUp4YmhlVVJOWUlWNVlZNVpiUk8xQW9jMzgtSl9WVUViSUVRal9DYT1zOTYtYyIsImdpdmVuX25hbWUiOiLpopYiLCJmYW1pbHlfbmFtZSI6IuWRqCIsImlhdCI6MTYyNTcxNDUyMiwiZXhwIjoxNjI1NzE4MTIyLCJqdGkiOiI4MjdmMzY4OGEyYWQ4NjViYjhjNGNmOGE3OGUyMzY2ZjI2MTI4MjZiIn0.wMiYJApJEbHbF-sg_7tPXHZ9ZzoSR8V3yBlQeCjGYKVCOSfvKIBkugRqmMX96oVyqdFz5tU849Yx0hkGZHfif_ExtAzYcdmiyxs1eV5DiLZ3ieI_yDwaWrtpvdrkHfvT-3iE1ahsd_wrs6S2CGJB2H6gupBKmrtKrBFC1jfTz9DlrsJk88YFJyvLydoPxit8s1gc4nRa3xQt2VyMW4IMUjqbNyhx4yNjWaXuYbJ8J2eMKv8hBdOOx80sVRPEHDzOmM7GqV1iewgrUS3nBKFCJlGxaEV4HuIOuqyGeUx3fcG2E9HUEQJGXRcQRF7-O-cFEoxSkFUKDzg2kSieVjoGsQ)
	* RAM（Random Access Memory）对于大文件的操作一不小心就 OOM，可以从 Node.js 提供的「流」和「缓冲」进行优化

#### 2021.06.28 - 2021.07.04

* [Temporal：JavaScript’s new date time API](https://2ality.com/2021/06/temporal-api.html)
* [JavaScript: The First 20 Years](https://dl.acm.org/doi/pdf/10.1145/3386327)
* [Super Simple Start to ESModules in Node.js](https://kentcdodds.com/blog/super-simple-start-to-es-modules-in-node-js)
* [SolidJS Official Release: The long road to 1.0](https://dev.to/ryansolid/solidjs-official-release-the-long-road-to-1-0-4ldd)
* [How to use Throttle or Debounce with React Hook](https://javascript.plainenglish.io/how-to-use-throttle-or-debounce-with-react-hook-776e402a5fac)
* [Disabling a link](https://www.scottohara.me/blog/2021/05/28/disabled-links.html?utm_source=CSS-Weekly&utm_campaign=Issue-464&utm_medium=web)
* [Using Performant Next-Gen Images in CSS with image-set](https://css-tricks.com/using-performant-next-gen-images-in-css-with-image-set/?utm_source=CSS-Weekly&utm_campaign=Issue-464&utm_medium=web)

#### 2021.06.21 - 2021.06.27

* [关于 React 18 你所需要知道的](/2021/06/23/前端-React-18-所需要知道的/)
* [ES2021 Features!](https://h3manth.com/ES2021/)
*  [Node v16.4.0 (Current) Released ](https://nodejs.org/en/blog/release/v16.4.0/)
	* AsyncLocalStorage 作用，使用场景？
* [28 (And Counting) Node CLI App Best Practices](https://github.com/lirantal/nodejs-cli-apps-best-practices)
* [How to Dynamically Import ECMAScript Modules](https://dmitripavlutin.com/ecmascript-modules-dynamic-import/)
* [PDF generation with Serverless + AWS Lambda and Puppeteer.](https://shubham-pandey.medium.com/pdf-generation-with-serverless-aws-and-puppeteer-cac3442b1c95)

#### 2021.06.14 - 2021.06.20

[JS 内存使用的基准测试](https://blog.webpagetest.org/posts/benchmarking-javascript-memory-usage/)
1. 根据v8 团队的研究：网络上 35% 的内存分配与 JavaScript 相关；10% 用于表示内存中的 DOM 元素；剩下的 55% 是图像。[measureUserAgentSpecificMemory](https://web.dev/monitor-total-page-memory-usage/) API 目前仅限于 JS 和 DOM 相关信息，但确实也占据页面实际内存使用量的很大一部分（约 45%）。

总结
1. 内存仍然是 Web 性能的一个尚未开发的主要领域，但这可能需要改变。随着发布的 JavaScript 数量不断增加，内存使用量也在增加。
2. 我们仍然需要更多信息来完善全貌。在任何时间点，浏览器实际可用的内存有多少？内存与关键业务和用户参与度指标有何关联？什么是内存的使用不与JavaScript和DOM的复杂性？
3. 虽然今天使用真实用户监控为您的站点获取这些数据可能存在挑战，但我在此处进行测试所采用的相同方法（一些 Chrome 标志与自定义指标配对）使您可以开始将内存相关数据提取到您的测试结果今天，我也喜欢看到人们这样做只是所以我们可以更多地了解我们是如何做的今天，其意义是什么，以及如何开始好转。


[memory-inspector for chrome](https://developer.chrome.com/blog/memory-inspector/)

#### 2021.06.07 - 2021.06.11

[Making JavaScript run fast on WebAssembly](https://bytecodealliance.org/articles/making-javascript-run-fast-on-webassembly)
https://jsonmatic.com/
https://domevents.dev/
