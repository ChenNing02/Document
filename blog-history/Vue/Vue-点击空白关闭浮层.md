---
title: Vue 点击空白关闭浮层
---

案例

```vue
<template>
    <div>
        <p v-if="open" @click.stop> 显示的浮层 </p>
        <button @click.stop="autoFloat">开/关</button>
    </div>
</template>
<script>
export default {
    data () {
        return {
            open: false
        }
    },
    methods: {
        autoFloat () {
            this.open = !this.open
        },
        closeFloat () {
            this.open = false
        }
    },
    mounted () {
        document.addEventListener('click', this.closeFloat)
    },
    destroyed () {
        document.removeEventListener('click', this.closeFloat)
    }
}
</script>
```

