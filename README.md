# Redux Promise Middleware

[![Build Status](https://travis-ci.org/pburtchaell/redux-promise-middleware.svg?branch=master)](https://travis-ci.org/pburtchaell/redux-promise-middleware) [![npm downloads](https://img.shields.io/npm/dm/redux-promise-middleware.svg?style=flat)](https://www.npmjs.com/package/redux-promise-middleware)

Redux Promise Middleware enables simple, yet robust handling of async action creators in [Redux](http://redux.js.org). 

```js
const asyncAction = () => ({
  type: 'PROMISE',
  payload: new Promise(...),
})
```

Given a single action with an async payload, the middleware transforms the action to a separate a pending action and a separate fulfilled/rejected action, representing the states of the async action.

The middleware can be combined with [Redux Thunk](https://github.com/gaearon/redux-thunk) to chain action creators.

```js
const secondAction = (data) => ({
  type: 'SECOND',
  payload: {...},
})

const firstAction = () => {
  return (dispatch) => {
    const response = dispatch({
      type: 'FIRST',
      payload: new Promise(...),
    })

    response.then((data) => {
      dispatch(secondAction(data))
    })
  }
}
```

## Documentation and Help
- [Introduction](/docs/introduction.md)
- [Guides](/docs/guides/)
- [Examples](/examples)

## Issues
For bug reports and feature requests:
- [File an issue]()

For help:
- [Ask a question on StackOverflow](https://stackoverflow.com/questions/tagged/redux-promise-middleware)

## Releases
- [Releases](https://github.com/pburtchaell/redux-promise-middleware/releases)
- [Version Upgrading Guide](/docs/upgrading.md)

For older versions:
- [4.x](https://github.com/pburtchaell/redux-promise-middleware/tree/4.4.0)
- [3.x](https://github.com/pburtchaell/redux-promise-middleware/tree/3.3.0)
- [2.x](https://github.com/pburtchaell/redux-promise-middleware/tree/2.4.0)
- [1.x](https://github.com/pburtchaell/redux-promise-middleware/tree/1.0.0)

## Maintainers
Please reach out to us if you have any questions or comments.

Patrick Burtchaell (pburtchaell):
- [Twitter](https://twitter.com/pburtchaell)
- [GitHub](https://github.com/pburtchaell)

Thomas Hudspith-Tatham (tomatau):
- [GitHub](https://github.com/tomatau)

## License

[Code licensed with the MIT License (MIT)](/LICENSE). 

[Documentation licensed with the CC BY-NC License](https://creativecommons.org/licenses/by-nc/4.0/).
