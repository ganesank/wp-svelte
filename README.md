# Netlify Identity Demo in Svelte

## Introduction

**Features:**

- [Svelte v3](https://svelte.dev/)
- [svelte-routing](https://github.com/EmilTholin/svelte-routing) (A declarative Svelte routing library with SSR support)
- [Netlify Identiy Widget](https://github.com/netlify/netlify-identity-widget/)
- [Netlify](https://www.netlify.com) (hosting)

This project was bootstrapped with the starter Svelte template by running `npx degit sveltejs/template <PROJECT_NAME>` and uses Netlify Identity for authentication. It was influenced by the the [React example](https://github.com/netlify/netlify-identity-widget/tree/master/example/react) by [@sw-yx](https://github.com/sw-yx) and the [Vue example](https://github.com/whizjs/netlify-identity-demo-vue) by [@medmin](https://github.com/medmin)

### Local Storage

This example uses the `gotrue.user` key in Local Storage to determine if a user is already signed in and then stores that in a Svelte store. Since Netlify Identity does that already it means we don't have to maintain our own Local Storage info.

## Redirects

The functionality of redirecting a user after logging in to whichever protected page they were coming from is mocked up in the Protected route by storing a redirect URL stored in a Svelte store. 

## Gotchas

If you are developing with the Netlify Identity Widget locally you will be prompted for a deployed Netlify Identity site (more info in the [Localhost section](https://github.com/netlify/netlify-identity-widget#localhost) of the Netlify Identity Widget README). Sometimes this causes issues with email verification or confirmation and you may need to reset the site.

To clear the locally stored Netlify Identity site you previously entered, execute `localStorage.removeItem('netlifySiteURL');` in your window.
