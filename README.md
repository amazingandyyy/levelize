<h1 align="center">
🎁 levelize
</h1>
<p align="center">
Use leveldb just like mongo.
</p>

<p align="center">
   <a href="https://github.com/amazingandyyy/levelize/blob/master/LICENSE">
      <img src="https://img.shields.io/badge/License-MIT-green.svg" />
   </a>
   <a href="https://circleci.com/gh/amazingandyyy/levelize">
      <img src="https://circleci.com/gh/amazingandyyy/levelize.svg?style=svg" />
   </a>
   <a href="https://www.npmjs.com/package/@amazingandyyy/levelize">
      <img src="https://badge.fury.io/js/%40amazingandyyy%2Flevelize.svg" />
   </a>
</p>

> open source!


## Installation

```shell
$ npm i --save @amazingandyyy/levelize
# or
$ yarn add @amazingandyyy/levelize
```

## Usage

```javascript
const process = require('process')
const level = require('level')
const Levelize = require('@amazingandyyy/levelize')

const levelize = new Levelize(level)

levelize.connect('levelize-demo-2019', {
  location: process.cwd()
})

const UserShema = levelize.schema({
  username: String,
  password: String,
  email: String
})

const userModel = levelize.model('User', UserShema)

for (let i = 0; i < 10; i++) {
  userModel.createOne({
    username: `amazingandyyy-${i}@gmail.com`, password: `xx${i}xx`
  })
}
userModel.getAll()

userModel.getOne({
  username: `amazingandyyy-3@gmail.com`
}, (err, user) => {
  console.log(err, user)
})

```

## License

MIT
