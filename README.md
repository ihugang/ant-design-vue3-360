# ant-design-vue3 360浏览器兼容
ant-design-vue3 360浏览器兼容性 

# CSS 错乱更正 
## App.vue
```vue
 import { StyleProvider } from 'ant-design-vue';
 <StyleProvider hash-priority="high" :transformers="[legacyLogicalPropertiesTransformer]">
      <router-view #="{ Component }">
        <component :is="Component" />
      </router-view>
      <LockScreen />
    </StyleProvider>
```

# JS兼容性
## vite.config代码
```js
import legacy from '@vitejs/plugin-legacy';
import topLevelAwait from 'vite-plugin-top-level-await';

plugins:[
      legacy({
        targets: ['chrome 78'],
        additionalLegacyPolyfills: ['regenerator-runtime/runtime'],
        modernPolyfills: true,
      }),
      topLevelAwait({
        promiseExportName: '__tla',
        promiseImportName: (i) => `__tla_${i}`,
      })
  ...
]
```

测试目标是：360企业安全浏览器 Windows版本 78.0.3904.108

