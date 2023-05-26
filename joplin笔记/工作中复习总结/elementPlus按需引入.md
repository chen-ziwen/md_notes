# elementPlus按需引入各项配置

## 1.vite.config.js

```js
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import Components from "unplugin-vue-components/vite"
import { ElementPlusResolve } from "unplugin-vue-components/resolvers"

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue(),

    Components({
      resolvers: [ElementPlusResolver()],
    }),
  ]
})
```

## 2.mian.js

```js

import { createApp } from 'vue'
import App from './App.vue'
// import router from './router.js'
const app = createApp(App)
//遍历注册组件
import { components } from "./assets/ts/element";
for (const cpn of components) {
    app.component(cpn.name, cpn);
  }

app.mount('#app')

```

## 3.element.ts

```js
//按需要引入
import {
    ElButton, ElRow,
   
  } from "element-plus";
   
  export const components = [
    ElButton,
    ElRow
  ];
  
```

