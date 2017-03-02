# sfc-spinner
> spinner.

## Install
```shell
npm i sfc-spinner -S
```

## Required
```shell
npm i babel-plugin-component -D
```

## Usage
import all spinner
```javascript
import Vue from 'vue';
import Spinner from 'sfc-spinner';

Vue.use(Spinner);
```

```html
<sfc-spinner></sfc-spinner>
```

import one spinner

```javascript
import Vue from 'vue';
import { DoubleBounce } from 'sfc-spinner';

Vue.component(DoubleBounce.name, DoubleBounce);
```

```html
<double-bounce></double-bounce>
```

.babelrc
```json
{
  "plugins": [
    "xxx",
    ["component", [
        {
          "libraryName": "sfc-spinner",
          "style": true
        }
      ]
    ]
  ]
}
```

**`import Spinner from 'sfc-spinner'` and `import { DoubleBounce } from 'sfc-spinner'` can not be used together.**.

## Spinner
- snake
- double-bounce
- triple-bounce
- fading-circle

## API

### color
- type: String

### size
- type: Number

### type
- type: String|Number

```html
<sfc-spinner :type="0"></sfc-spinner>
<sfc-spinner type="snake"></sfc-spinner>

<sfc-spinner :type="1"></sfc-spinner>
<sfc-spinner type="double-bounce"></sfc-spinner>

<sfc-spinner :type="2"></sfc-spinner>
<sfc-spinner type="triple-bounce"></sfc-spinner>

<sfc-spinner :type="3"></sfc-spinner>
<sfc-spinner type="fading-circle"></sfc-spinner>
```

## Development

```shell
make dev
```

## Production
```
make dist
```

## License
MIT
