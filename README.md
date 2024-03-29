# randomall

Simple and elegant generation of random data.

## Installtion

```sh
npm i @liting-yes/randomall
```

## Hello Random

```js
const random = require('@liting-yes/randomall')
```

### random number

#### simple to use

```js
random.number()
// output: 88
// return an integer between [0, 100)

random.number.DEFAULT
// default parameter value
```

#### use with args

Function random.number has 5 params as follows:

- **min** *number*

> mininum random number isn't less than it

- **max** *number*

> maxinum random number doesn't exceed it

- **radix** *number*

> base of return value (2-36)
>
> **notice**: when radix != 10, the return value will be the string value of the corresponding random number

- **isInteger** *boolean*

> whether the return value is integer

- **decimal** *number*

> max number of decimal places returned

```js
random.number(1, 10, 10, false, 5)
// output: 1.58
// return a float between [1, 10) with no more than 5 decimal places


// support object passing
random.number({ isInteger: false })
// output: 62.664065
```

### random string

#### simple to use

```js
random.string()
// output: Z1Qdvk
// return a random string whose characters are letters and numbers

random.string.DEFAULT
random.string.CHARACTAR
// default parameter value
```

#### use with args

Function random.stringhas 6 params as follows:

- **len** *number*

  > length of random string

- **banNum** *number*

  > random string without numbers*

- **banLowercase** *boolean*

  > random string without lowercase letters

- **banUppercase** *boolean*

  > random string without uppercase letters*

- **add** *array*

  > special characters that random string contains

- **remove** *array*

  > special characters that random string must never contain

```js
random.string(10, true, false, true, ['@', '#', '?'], ['a', 'b', 'c'])
// output: #sr#u?ljsv
// return a random string that contain possibly the characters '@', '#', '? ' and no digits, uppercase letters, 'a', 'b', 'c'


// support object passing
random.string({ banNum: true, banLowercase: true })
// output: ODMZPO
```

### random boolean

#### simple to use

```
random.boolean()
// output: true
// return a random boolean value
```

### random array

#### simple to use

```js
random.array()
// output: [45, 71,  8, 20, 79, 17, 73, 16, 85, 44]
// return an array of length 10 and each element has a value greater than 0 and less than 100
```

#### use with args

- **len** *number*

  > length of random array

- **fn** *function* 

  > the function to generate random value

- **args** *remain parameters*

  > function arguments of fn

```js
random.array(5, random.number, 1, 10)
// output: [ 9, 5, 2, 5, 5 ]
// return an array with 5 number element which is greater than 1 less than 10
```

### random image

#### simple to use

```js
random.image().then(imgUrl => console.log(imgUrl))
// returns a configurable random image address

random.image.DEFAULT_CONFIG
random.image.DEFAULT_LOCATION
// default parameter value
```

#### use with args

- **userConfig** *object*

> same as axios request configuration

- **userLocation** *array*

> nested position of target data

```js
random.image({ baseURL:'https://api.ixiaowai.cn', url: '/mcapi/mcapi.php' }, ['imgurl']).then(imgUrl => console.log(imgUrl))
// return an random image url about the api
```

#### statement

the image API the repo is using is [小歪API](https://api.ixiaowai.cn/)

**in order to avoid some unforeseen problems, it is recommended to configure the API yourself**