# SFC UI

> sfc-ui for Vue 2.0

- [ElemeFE / mint-ui](https://github.com/ElemeFE/mint-ui/)
（基于ElemeFE / mint-ui  2.2.0修改，纯属个人学习研究）

## Installation
```shell
npm i sfc-ui -S
```

## Usage

Import all components.

```javascript
import Vue from 'vue'
import Sfc from 'sfc-ui';

Vue.use(Sfc);
```

Or import specified component. (Use [babel-plugin-component](https://www.npmjs.com/package/babel-plugin-component))

```javascript
import { Cell, Checklist } from 'sfc-ui';

Vue.component(Cell.name, Cell);
Vue.component(Checklist.name, Checklist);
```


Equals to

```javascript
import Vue from 'vue';
import Sfc from 'sfc-ui';
import 'sfc-ui/lib/style.css';

Vue.use(Sfc);

// import specified component

import SfcRadio from 'sfc-ui/lib/radio';
import 'sfc-ui/lib/radio/style.css';

Vue.component(SfcRadio.name, SfcRadio);
```

## babel-plugin-component
- Auto import css file
- Modular import component

Installation
```shell
npm i babel-plugin-component -D
```

Usage

.babelrc
```json
{
  "plugins": ["other-plugin", ["component", [
    { "libraryName": "sfc-ui", "style": true }
  ]]]
}
```

## Development

```shell
npm run dev
```

## License
MIT
