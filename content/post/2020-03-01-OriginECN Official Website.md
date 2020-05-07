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

# 01.背景

> 下个月初我们就要开发布会，告诉媒体和客户我们进入中国市场了，在那之前公司中文官网必须上线。 —— The boss

这是我刚进入公司就接到的第一个任务，以为是把英文网站翻译成中文就行，哪想到连英文网站都没有。于是便从研究这个未知的行业开始

<div class="Image__Medium">
<img src="/images/medium.jpg" alt="alt text for medium image" />
</div>

But it takes more than good ideas to build and grow a business. It takes people to bring them into reality. Are those people collaborating and sharing their expertise, or are they in conflict and keeping it to themselves? But it takes more than good ideas to build and grow a business. It takes people to bring them into reality. Are those people collaborating and sharing their expertise, or are they in conflict and keeping it to themselves? But it takes more than good ideas to build and grow a business. It takes people to bring them into reality. Are those people collaborating and sharing their expertise, or are they in conflict and keeping it to themselves? But it takes more than good ideas to build and grow a business. It takes people to bring them into reality. Are those people collaborating and sharing their expertise, or are they in conflict and keeping it to themselves?

<div class="Image__Large">
<img src="/images/large.jpg" alt="alt text for large image" />
</div>

But it takes more than good ideas to build and grow a business. It takes people to bring them into reality. Are those people collaborating and sharing their expertise, or are they in conflict and keeping it to themselves?

## This is a secondary heading

But it takes more than good ideas to build and grow a business. It takes people to bring them into reality. Are those people collaborating and sharing their expertise, or are they in conflict and keeping it to themselves?

```js {5-6}
import React from "react";
import { graphql, useStaticQuery } from "gatsby";
import styled from "@emotion/styled";

import SocialIcons from "@icons";
import mediaqueries from "@styles/media";

const icons = {
  dribbble: SocialIcons.DribbbleIcon,
  linkedin: SocialIcons.LinkedinIcon,
  twitter: SocialIcons.TwitterIcon,
  facebook: SocialIcons.FacebookIcon,
  instagram: SocialIcons.InstagramIcon,
  github: SocialIcons.GithubIcon
};

function SocialLinks({ fill = "#73737D" }: { fill: string }) {
  const result = useStaticQuery(socialQuery);
  const socialOptions = result.allSite.edges[0].node.siteMetadata.social;

  return (
    <>
      {socialOptions.map(option => {
        const Icon = icons[option.name];

        return (
          <SocialIconContainer
            key={option.name}
            target="_blank"
            rel="noopener"
            data-a11y="false"
            aria-label={`Link to ${option.name}`}
            href={option.url}
          >
            <Icon fill={fill} />
          </SocialIconContainer>
        );
      })}
    </>
  );
}
```

At Narative, we’ve been fans of Gatsby from day one, using it to build performant and flexible products for both clients and ourselves. With the growing community interest in Gatsby, we hope to create more resources that make it easier for anyone to grasp the power of this incredible tool.

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