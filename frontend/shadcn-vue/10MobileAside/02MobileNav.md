## MobileNav

* components/layout/mobile/NavItem.vue

```vue
<template>
  <div>
    Menu
  </div>
</template>
<script setup lang="ts">
const props = defineProps<{
  item: any;
  index: number;
}>()
</script>
```

* components/layout/mobile/Nav.vue

```vue
<template>
  <div>
    <LayoutMobileNavItem v-for="(item, i) in nav" :key="i" :item="item" :index="i">
    </LayoutMobileNavItem>
  </div>
</template>
<script setup lang="ts">
const nav = ref([
  {
    title: 'Links',
    links: [{
      title: 'Getting Started',
      to: '/getting-started',
      description: 'Start building your document with shadcn-docs-nuxt',
      icon: 'lucide:rocket',
    }, {
      title: 'Baidu',
      to: 'https://www.baidu.com/',
      description: 'Move to Baidu',
      target: '_blank',
    }]
  },
  {
    title: 'Use This Template',
    to: '/getting-started/installation',
    target: '_self',
    showLinkIcon: true,
  }
])
</script>
```

* components/layout/aside/index.vue

```vue
<template>
    <UiScrollArea orientaion="vertical" class="relative h-full overflow-hidden py-6 pr-6 text-sm md:pr-4" type="hover">
        <LayoutMobileNav v-if="isMobile" class="mb-5 border-b pb-2" />
    </UiScrollArea>
</template>
<script setup lang="ts">
defineProps<{ isMobile: boolean }>();
</script>
```