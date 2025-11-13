### [IConify](https://www.radix-ui.com/icons)

[IconSets](https://icon-sets.iconify.design/?keyword=radix)

```bash
Monk@LuMonkdeMacBook-Pro blog-portal % yarn add -D @iconify/vue @iconify-json/lucide

yarn add v1.22.22
[1/4] 🔍  Resolving packages...

...

✨  Done in 9.53s.
```

* 验证

```vue
<template>
  <div>
    <UiButton variant="ghost" size="icon"  @click="toggleDark">
      <Icon
        icon="lucide:moon"
        class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
      />
      <Icon
        icon="lucide:sun"
        class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
      />
      <span class="sr-only">Toggle theme</span>
    </UiButton>
  </div>
</template>
<script setup lang="ts">
import { Icon } from "@iconify/vue";

const colorMode = useColorMode();

function toggleDark() {
  colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark';
}
</script>
```