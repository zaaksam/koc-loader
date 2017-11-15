# ko-loader

Knockout component loader for webpack

You can write component file like Vue:

hello.ko

```html
<template>
    <div data-bind="text: info"></div>
</template>

<script lang="ts">
import ko from "knockout";

export default class Component {
    info: KnockoutObservable<string>;

    constructor(params: any) {
        this.info = ko.observable("hello ko-loader");
    }
}
</script>
```

Webpack.config.js:

```js
{
    module: {
        rules: [
            {
                test: /\.ko$/,
                loader: 'ko-loader'
            }
        ]
    }
}
```

app.ts (app.js)

```ts
import ko from 'knockout'
import Hello from './hello.ko'

ko.components.register('hello', Hello)

ko.applyBindings()
```

index.html

```html
<html>
    <body>
        <hello></hello>
    </body>
    <script src="http://host/app.js"></script>
</html>
```

Thanks:
* [san-loader](https://github.com/ecomfe/san-loader)
* [vue-loader](https://github.com/vuejs/vue-loader)