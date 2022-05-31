# Comparison 
This is a comparison of this code challenge in different implementation (language, framework etc.)

_Last Updated: 2022-05-31_

## NestJS (_NodeJS_)
* repository [here](https://github.com/LCYAD/self-core-challenge-nestjs)

### Pros
* Functionality well seperated
* Certain Integration requires very few setup, like swagger generation
* Code can be easily maintained once the initial setup is done
* Everything is modularized so it is easy to remove current dependency

### Cons
* Initial setup very tedious (eslint, prettier, pipes, guards, filters etc.)
* Out of the box stuff might not always be useful if more customization is required. An example is `ParseArrayPipe` which cannot extract all the Validation Error since it calls the exceptionFactory for each ValidationError performed
* Can have some useless data, such as swagger data, added to the meta data which you cannot seperate it in production.
* Too many `"black magic"` via reflect metadata, and if things doesn't work, investigation could take a while
* (More on NodeJS), dependency hell, and support for new standard like `esbuild` or `swc` are minimal and have to take the time to test out if it actually works on the repository or not.  As of this writing, the `swc/jest` does not work on the unit or integration test

### When to use
* if your team is very focused on the NodeJS ecosystem and want to build something that will need to be maintainable when the project goes big


## Oak (_Deno_)
* repository [here](https://github.com/LCYAD/self-code-challenge-deno)

### Pros
* Works with minimal effort. Almost half the time took to get most functionality done when compared to the NestJS attempt.
* Very little setup (no eslint, prettier setup etc.) since everything is opinionated with options for customization
* Simple architecture, all middlewares with proper typing
* Can bundle code together in single file with bundle size very small (compared to NodeJS and its node modules)
    * It should be noted that the bundled JS file will only work on Deno only
* Fast testing
* Much less dependency issue

### Cons
* Deno is still young, a lot of useful library in NodeJS isn't available in Deno
* The simple nature of the framework can create issues if not setup properly which can be hard to maintain if it gets big
* IDE support for Deno still require workaround, cannot `autoattch`
* Testing library is quite limited in functionality compared to Jest
    * lacking snapshot testing etc.
    * cannot spy inside method during integration test
    * testing is not as comprehensive when compared to NestJS attempt
    * need to rewrite the whole imported library rather than having methods like `jest.mock`
* Most of the time you will need to allow all the security options to get a server running so not really as useful as claimed

### WHen to use it
* smaller projects and want to access the benefit of Typescript but don't want to deal with NodeJS shit
* build small executable natively

