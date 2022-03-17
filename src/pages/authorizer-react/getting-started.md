---
title: Authorizer React Getting Started
layout: ../../layouts/Main.astro
---

Authorizer React SDK allows you to implement authentication in your [React](https://reactjs.org/) application quickly. It also allows you to access the user profile.

Here is a quick guide on getting started with `@authorizerdev/authorizer-react` package.

<div class="video-container">
  <iframe class="frame" width="560" height="315" src="https://www.youtube.com/embed/2aOTuwkfYvM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Step 1: Get Authorizer Instance

Deploy production ready Authorizer instance using one click deployment options available below

| **Infra provider** |                                                                                                                **One-click link**                                                                                                                |               **Additional information**               |
| :----------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------: |
|    Railway.app     | <a target="_blank" href="https://railway.app/new/template?template=https://github.com/authorizerdev/authorizer-railway&amp;plugins=postgresql,redis"><img src="https://railway.app/button.svg" style="height: 44px" alt="Deploy on Railway"></a> | [docs](https://docs.authorizer.dev/deployment/railway) |
|       Heroku       |             <a target="_blank" href="https://heroku.com/deploy?template=https://github.com/authorizerdev/authorizer-heroku"><img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy to Heroku" style="height: 44px;"></a>             | [docs](https://docs.authorizer.dev/deployment/heroku)  |
|       Render       |                     <a target="_blank" href="https://render.com/deploy?repo=https://github.com/authorizerdev/authorizer-render"><img alt="render button" src="https://render.com/images/deploy-to-render-button.svg" /></a>                      | [docs](https://docs.authorizer.dev/deployment/render)  |

For more information check [docs](https://docs.authorizer.dev/getting-started/)

## Step 2: Setup Instance

- Open authorizer instance endpoint in browser
- Sign up as an admin with a secure password
- Configure environment variables from authorizer dashboard. Check env [docs](/core/env) for more information

> Note: `DATABASE_URL`, `DATABASE_TYPE` and `DATABASE_NAME` are only configurable via platform envs

## Step 3 - Install package

Install `@authorizerdev/authorizer-react` library

```sh
npm i --save @authorizerdev/authorizer-react
OR
yarn add @authorizerdev/authorizer-react
```

## Step 4 - Configure Provider and use Authorizer Components

Authorizer comes with [react context](https://reactjs.org/docs/context.html) which serves as `Provider` component for the application

```jsx
import {
  AuthorizerProvider,
  Authorizer,
  useAuthorizer,
} from "@authorizerdev/authorizer-react";

const App = () => {
  return (
    <AuthorizerProvider
      config={{
        authorizerURL: "http://localhost:8080",
        redirectURL: window.location.origin,
        clientID: "YOUR_CLIENT_ID", // obtain your client id from authorizer dashboard
      }}
    >
      <LoginSignup />
      <Profile />
    </AuthorizerProvider>
  );
};

const LoginSignup = () => {
  return <Authorizer />;
};

const Profile = () => {
  const { user } = useAuthorizer();

  if (user) {
    return <div>{user.email}</div>;
  }

  return null;
};
```

## Examples

Please check the [example repo](https://github.com/authorizerdev/examples) to see how to use this component library.
