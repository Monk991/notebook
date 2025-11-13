## [Nuxt Server](https://nuxt.zhcndoc.com/docs/guide/directory-structure/server)


### HelloWorld

* server/api/user.get.js

```js
export default defineEventHandler(async (event) => {
  return {
    hello: "world",
  };
});
```

* [验证](http://localhost:3000/api/user)

### 页面调用

* app.vue

```vue
<template>
  <div :class="{ dark: darkMode }">
    <div class="bg-white text-gray-900 dark:bg-gray-800 dark:text-white">
      <div class="h-screen">
        {{ data }}
      </div>
    </div>
  </div>
</template>
<script setup>
const darkMode = ref(true);

const { data } = await useFetch("/api/user");
</script>
```

* [验证](http://localhost:3000/)
