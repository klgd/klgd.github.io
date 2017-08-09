---
title: how-to-use-tinymce-with-laravel-mix
tags:
  - null
categories:
  - null
date: 2017-08-09 15:37:54
---

安装tinymce

```
npm install tinymce --save
```

配置`webpack.mix.js`

```javascript

mix.autoload({
    'tinymce/tinymce': 'tinymce',
});

mix.webpackConfig({
        loaders: [
            {
                test: require.resolve('tinymce/tinymce'),
                loaders: [
                    'imports?this=>window',
                    'exports?window.tinymce'
                ]
            },
            {
                test: /tinymce\/(themes|plugins)\//,
                loaders: [
                    'imports?this=>window'
                ]
            }
        ]
    }
});
```

### vue 组件`demo.vue`

`style`

```css
    @import "~tinymce/skins/lightgray/skin.min.css";
```

```vue
import tinymce from 'tinymce/tinymce'

import 'tinymce/themes/modern/theme'

// Plugins
import 'tinymce/plugins/paste/plugin'
import 'tinymce/plugins/link/plugin'
import 'tinymce/plugins/autoresize/plugin'

// 注册一个自定义指令
Vue.directive('tinymce', {
    inserted() {
        tinymce.init({
            selector: '#tiny',
            theme: 'modern',
            skin: false,
            plugins: ['paste', 'link', 'autoresize'],
            setup: (editor)=> {
                // 初次化编辑器
                editor.on('init', ()=>{
                    // 设置默认值
                    editor.setContent('<p>Default Value!</p>');
                    // 注册事件
                    editor.on('input change undo redo', ()=>{
                        // 获得编辑结果
                        console.log(editor.getContent());
                    });
                });
            }
        });
    }
})
```

### 使用

```
<textarea id="tiny" v-tinymce></textarea>
```