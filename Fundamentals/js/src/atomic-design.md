# Design Atômico

```
├── index.html
├── main.js
└── src
    ├── html 
    │   └── templates
    │        └── home
    │            └── index.html
    ├── js 
    │   ├── components
    │   │    └── commons.js
    │   │    └── home
    │   │        └── index.js
    │   └── store
    │        └── index.js
    │        └── modules
    │            ├── in18n
    │            └── user
    │
    └── css
        ├── core
        │     ├── config.css
        │     ├── defaults.css
        │     ├── general.css
        │     └── mixins.css
        └── components
             └── home
                 └── index.css
```

## Exemplo JS importando html
**home/index.js**
```js
import template from '@/html/templates/home/index.html';

export default {
    template
}
```

**commons.js**
```js
import home from "@/js/components/home";

function register() {
    Vue.component("home", home);
}
```

**main.js**
```js
import commons from "@/js/components/commons";

commons.register();
```
