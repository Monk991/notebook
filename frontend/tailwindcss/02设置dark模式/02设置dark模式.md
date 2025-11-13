
### 设置Dark mode

* app.vue

```vue
<template>
  <div :class="{ dark: darkMode }">
    <div class="bg-white text-gray-900 dark:bg-gray-800 dark:text-white">
      <div class="h-screen">Home</div>
    </div>
  </div>
</template>
<script setup>
const darkMode = ref(true);
</script>
```

* assets/css/main.css
```css
@import "tailwindcss";

@custom-variant dark (&:where(.dark, .dark *));
```
