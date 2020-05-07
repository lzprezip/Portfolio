---
title: OriginECN 官方网站
date: 2020-03-01T15:00:00.000+00:00
hero: "/images/cover.jpeg"
excerpt: 金融经纪商OriginECN官方网站从0到1的建设过程，并经历3个大版本更迭。
timeToRead: 6
authors:
- Li Zhipeng

---
### 概要：

从0到1建设OriginECN官方网站，并随着公司品牌力提升，对网站进行三次版本的更迭。

### 目的：

让客户通过网站了解OriginECN这个外汇经纪商品牌，对公司留下较好印象，以提高销售人员信心，促进客户成交率。

### 效果：

从销售人员反馈得知，客户通过网站，表达出对公司较高的认可度。甚至公司官网被同行抄袭。

### 技能：

市场调研、竞品分析、UCD产品思维、原型制作、高保真设计图交付。

### 工具：

PS、AI

### 时长：

平均每个版本花费3周

***

# 01. 时间紧迫 V1.0

> 下个月初要开发布会，告诉媒体和客户我们进入中国市场，在那之前公司官网必须上线。 
>
> —— The boss

在这样时间紧迫的情况下，用最短的时间确保官网顺利上线才是重中之重，所以忽略了大量的前期调研工作，直接参考市面上的竞品，仿照其内容和网站框架进行搭建。

## 设计稿

***

# 02. 改头换面 V2.0

由于意识到V1.0版本目的是为了应付发布会的仓促之作，不管是框架内容还是设计都存在大量提升空间。所以在第一个版本上线仅2个月时，团队开始着手官网第二版的升级工作。

## 调研

初步的调研主要是与公司已有客户间接沟通，通过与销售人员聊天，去了解做在线外汇交易的客户特征，以及这样的客户在选择外汇平台时更看重哪些方面。

初次做在线外汇交易的客户，往往并不是拥有专业外汇知识的人，此类客户一般有大量资金存放于股票和期货账户中，通过朋友介绍了解到外汇交易这样更高风险更高收益的产品，遵循“不要把所有鸡蛋放在同一个篮子里”的原则，选择尝试外汇交易。

由于是未知产品且没有银行作为背书，初期客户在选择平台时更关注监管牌照，关心资金是否安全，出入金是否顺畅。所以此次更新的重点放在展示公司的荣誉资质和资金安全上。

## 竞品分析

由于在线外汇交易在西方国家非常流行，所以大量的同行都有欧洲背景或直接就是欧洲公司。我们通过浏览第三方媒体平台，查看了市面上交易量和知名度较为靠前的100多家外汇公司。

![](/images/cover.jpeg)

通过分析他们的官方网站，得出以下结论：

1. 41%的网站会将

```js live
const Wrapper = ({ children }) => (
  <div
    style={{
      background: "papayawhip",
      width: "100%",
      padding: "2rem"
    }}
  >
    {children}
  </div>
);

const Title = () => (
  <h2 style={{ color: "palevioletred", textAlign: "center" }}>
    Hello World!
    <br />
    Try Novela Gatsby Theme.
  </h2>
);

render(
  <Wrapper>
    <Title />
  </Wrapper>
);
```

One of the challenges I had when learning Gatsby was trying to understand the Gatsby lifecycle. React introduced me to the concept of a Component Lifecycle, but when I started learning Gatsby I felt at a loss again. I remember looking through example repositories and seeing Gatsby specific files in every project and thinking to myself, “What are these files for? Why are gatsby-node.js, gatsby-browser.js, and gatsby-ssr.js generated in the default starter kit? Can I really delete these files?”

## How does Gatsby work?

To understand what these files are for, we must first understand how Gatsby works. Gatsby is a static site generator that pulls data from sources you provide and generates a website/app for you.

Gatsby requires Node to be installed to run the Bootstrap and Build sequences. Under the hood, Gatsby uses Webpack to build and start a development server amongst other things.

### Step 1

During the Bootstrap sequence, which occurs every time you run $ gatsby develop, there are about 20 events that fire ranging from validating your gatsby-config.js to building the data schemas and pages for your site. For example, the Bootstrap sequence is where Gatsby will create pages. If you want an in depth look of all 20 Bootstrap steps Swyx shared a fantastic Gist that goes into more detail.

### Step 2

The Build sequence is very similar to the Bootstrap sequence, except it’s run with production optimizations and will output static files ready for deployment. Think of it as building your React application in production mode vs development.

### Step 3

And finally, once the generated files are deployed, Gatsby lives in the browser. Gatsby cleverly generates a static website that turns into a web app after initial load, which extends the lifecycle to the browser.

What’s important to remember is that Gatsby’s lifecycle can be aggregated into 3 main sequences:

* Bootstrap
* Build
* Browser
* These three sequences makeup the Gatsby lifecycle.

***

## What are the Gatsby specific files for?

gatsby-config.js
A place to put all your site configurations such as plugins, metadata, and polyfills. This file is the blueprint of your application and is where Gatsby really shines with its plugin system. When you run $ gatsby develop or $ gatsby build gatsby-config.js is the first file to be read and validated.

Most of your time spent in gatsby-config.js will likely revolve around source plugins, image plugins, offline support, styling options, and site metadata.

```jsx
function MDX({ content, children, ...props }) {
  const [colorMode] = useColorMode();

  return (
    <MDXProvider components={components}>
      <MDXBody>
        <MDXRenderer isDark={colorMode === "dark"} {...props}>
          {content}
        </MDXRenderer>
        {children}
      </MDXBody>
    </MDXProvider>
  );
}
```

### gatsby-node.js

Gatsby runs a Node process when you develop or build your website and uses Webpack under the hood to spin up a development server with hot reloading. During the Node process Gatsby will load plugins, check the cache, bootstrap the website, build the data schema, create pages, and deal with some configuration and data management.

Everything that occurs during the Bootstrap and Build sequences occurs in gatsby-node.js. This means it’s the perfect place to create pages dynamically based off data from a source plugin or modify Gatsby’s Webpack or Babel configs.

For example, if you want to move some files manually, such as a Netlify _redirects file, a good place to do it is in your gatsby-node.js file at the onPostBuild lifecycle hook.

From experience, most of my time has revolved around handling data and building pages in gatsby-node.js. This file quickly becomes the piping of your entire website.

### Examples of gatsby-node.js hooks:

* createPages
* onCreateBabelConfig
* onCreateWebpackConfig
* onPostBuild
* gatsby-ssr.js

When you think Server Side Rendering you think of a server that takes in requests and dynamically builds pages and sends it to the client. Gatsby doesn’t do that, but it does server side render — it generates all the pages during build time.

Naturally, gatsby-ssr.js allows developers to hook into that lifecycle. In my experience, most use cases revolve around injecting CSS, HTML, or Redux state information into the generated output. For example, if you need to insert third party scripts such as Analytics Tracking or a Pixel it can be done on the onRenderBody gatsby-ssr.js hook.

### Examples of gatsby-ssr.js hooks:

* onPreRenderHTML
* onRenderBody
* replaceRenderer
* gatsby-browser.js

Gatsby is a static site that loads a dynamic application after initial load, which means you get the benefits of a static site in a web application. gatsby-browser.js provides convenient hooks to deal with app loading, route updates, service worker updates, scroll positioning, and more.

Everything that occurs after your static site has loaded can be hooked in gatsby-browser.js. For apps that I’ve built, gatsby-browser.js was mostly used for keeping track of routes, scroll positioning, and sending analytics events.

### Examples of gatsby-browser.js hooks:

* onClientEntry
* onRouteUpdate
* onServiceWorkerInstalled
* registerServiceWorker
* shouldUpdateScroll

## Conclusion

Gatsby is built with React at its core and shares a common API pattern, the lifecycle. This lifecycle gives developers access to key moments in their website’s process through specific hooks. For example, adding analytics can be achieved through the Browser lifecycle hook onClientEntry. Gatsby reserves specific filenames as an entry point to access every lifecycle; these files are named gatsby-node.js, gatsby-ssr.js and gatsby-browser.js.

Without the Gatsby lifecycle, it would be impossible to customize and modify your project beyond the base configuration, leaving developers with a rigid and poor developer experience. This power and flexibility has helped us build amazing web projects for clients like Hopper!

Gatsby is a staple within our engineering process at Narative, helping us help our clients build the products they’ve always dreamed of, and the ones they’re yet to dream up.