# LabelEdit
仿照vue devtools修改data的交互方式，做的一个即时修改文本的组件。鼠标移入显示编辑按钮，点击后文本变成可输入的input。


### 引入组件
```js
import LabelEdit from './components/LabelEdit.vue'
```
## 用法
```html
<LabelEdit placeholder="placeholder" :text="text" @updateText="textUpdateCallback" />
```

### 参数

| Props | 描述 |
| --------- |:----- |
| :text | 需要修改的文本 |
| v-on:updateText | 点击保存的回调函数 |
| placeholder | (可选) 提示信息 |

## Example

```html
<template>
	<div>
		<LabelEdit placeholder="placeholder" :text="text" @updateText="textUpdateCallback" />
	</div>
</template>
```

```js
<script>
import LabelEdit from './components/LabelEdit.vue'
export default {
  name: 'App',
  data () {
    return {
      text: '安徒生童话',
    }
  },
  components: {
    LabelEdit,
  },
  methods: {
    textUpdateCallback(val) {
      console.log('更新后的文本：' + val)
      window.alert('更新后的文本：' + val)
    },
  }
}
</script>
```

## Demo
请参考vue devtools