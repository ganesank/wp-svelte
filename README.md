# Svelte with WordPress API
 
Example of Svelte application with WordPress REST API

## [Live Demo](https://react-with-wordpress.netlify.com/)


Svelte Svelte with WordPress API of a Single Page Application which built over Svelte, Bootstrap using Wordpress Rest API.
This code can Be used as boilerplate for Svelte Application Development and as ready use Web development.


## Getting Started
- Install Nodejs from [Nodejs Official Page](https://nodejs.org/en/)
- Clone this repo in `git clone https://github.com/ganesank/wp-svelte`
- Open your terminal
- Navigate to the project and `git checkout branchname`
- Run `npm install` or `yarn install` if you use [Yarn](https://yarnpkg.com/en/)
- Run `npm run dev` or `yarn dev` to start a local development server
- Navigate to `http://localhost:5000` or - A new tab will be opened in your browser

You can also run additional npm tasks such as
- `npm run build` to build your app for production
- `npm run lint` to run linting.

## Prerequisites

You must have Node.js and npm installed on your machine. This project was built against the following versions:

- Node v12.6.0
- npm v6.9.0

## Advantages!

  - SPA based on Counter Component Developemnt 
  -  reactive declarations with variables which automatically computes the changes
  -  executes statements reactively when a value changes
  -  feasibility of multiple logic and conditional statements
  -  No Virtual DOM
  -  Significantly less boilerplate and better performance
  -  Options to utilize the data using  **props**, **Contexts**, **Stores** & **Module Scope**
  -  Lifecycle functions to performe before and after mount, after update and on destroy
## Features and RoadMap

- [x] CRUD operation with WordPress REST API
- [x] Accessing public and private routes
- [x] Handing WordPress REST API custom end points
- [x] Pagination for blog and other post types
- [ ] Authentication with JWT ( Login Logout )
- [ ] User Login and Managment


## Configuration

Add your wordPress siteUrl in `src/client-config.js`

```ruby
const clientConfig = {
	siteUrl: 'http://localhost:8888/wordpress'
};

export default clientConfig;
``` 


## License

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

