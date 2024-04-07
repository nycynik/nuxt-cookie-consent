# Getting started

This Nuxt module offers a straightforward and convenient way to engage with cookie consent platforms, utilizing a unified and simple interface.

Its goal is to serve as a simple and accessible foundation for integrating cookie policies into your Nuxt application.


## Why this package?
Why not leverage Google Tag Manager to conditionally load scripts based on consent?

That's a valid question! One of the primary reasons was the slow loading of scripts 🐌. For returning users, we had to first serve the site, then load Google Tag Manager, and finally load the Cookie Consent scripts. Google Tag Manager then listens to init events on consent and loads the scripts.

This chain of events needs to occur before you can enable analytics or showcase YouTube videos. Moreover, we faced challenges in maintaining a reactive state when a user's consent changes. For example, should we render the YouTube player when a user accepts statistics? Or allow Algolia to collect insights when consent is given?

With this module, we aim to address these issues while providing a small and easy-to-use interface for interaction.

## SSR
So, what about SSR?
This module parses the cookies on the server and populates the consent state and loads your scripts directly on the ssr response for faster loading.

This means that your scripts are loaded initially by the client if the consent is given.

## Installation

You have two ways of installing the module – see options below.

### 1.0) Install using nuxi module add

Install using nuxi module add, wich automatically adds it tot the modules option in `nuxt.config`.

::: code-group
```bash [npm]
npx nuxi@latest module add @weareheavy/nuxt-cookie-consent
```

```bash [bun]
bunx nuxi@latest module add @weareheavy/nuxt-cookie-consent
```
:::

### 2.1) Install manually

Install the `@weareheavy/nuxt-cookie-consent` module using your favorite package manager.

::: code-group
```bash [npm]
npm install @weareheavy/nuxt-cookie-consent
```

```bash [yarn]
yarn add @weareheavy/nuxt-cookie-consent
```

```bash [bun]
bun install @weareheavy/nuxt-cookie-consent
```
:::

### 2.2) Initialize module
Add the module to your `nuxt.config.ts` file.

```typescript
export default defineNuxtConfig({
    modules: ['@weareheavy/nuxt-cookie-consent']
    // ...
})
```

## Configure your provider
Setup the supported provider in the `cookieConsent` option.

::: code-group
```typescript [CookieBot]
export default defineNuxtConfig({
    modules: ['@weareheavy/nuxt-cookie-consent']
    cookieConsent: {
        provider: 'cookiebot',
        cbid: '00000000-0000-0000-0000-000000000000' // Replace with you "cbid" from CookieBot
    }
})
```

```typescript [CookieInformation]
export default defineNuxtConfig({
    modules: ['@weareheavy/nuxt-cookie-consent']
    cookieConsent: {
        provider: 'cookieinformation',
        culture: 'EN' // Replace with the culture you want to apply
    }
})
```
:::