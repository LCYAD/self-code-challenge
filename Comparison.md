# Comparison 
This is a comparison of this code challenge in different implementation (language, framework etc.)

_Last Updated: 2022-05-27_

## NestJS
* repository [here](https://github.com/LCYAD/self-core-challenge-nestjs)

### Pros
* Functionality well seperated
* Current Integration requires very few setup, like swagger generation
* Code can be easily maintained once the initial setup is done
* Everything is modularized so it is easy

### Cons
* Initial setup very tedious (eslint, prettier, pipes, guards, filters etc.)
* Out of the box stuff might not always be useful if more customization is required. An example is `ParseArrayPipe` which cannot extract all the Validation Error since it calls the exceptionFactory for each ValidationError performed
* Can have some useless data, such as swagger data, added to the meta data which you cannot seperate it in production.
* Too many `"black magic"` via reflect metadata, and if things doesn't work, investigation could take a while
* (More on NodeJS), dependency hell, and support for new standard like `esbuild` or `swc` are minimal and have to take the time to test out if it actually works on the repository or not.  As of this writing, the `swc/jest` does not work on the unit or integration test
