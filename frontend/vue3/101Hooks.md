## 使用 Hooks

- /src/hooks/useAuth.ts

```ts
function useAuth() {
  console.info('use Auth')

  const login = () => {
    console.info('login')
  }

  onMounted(() => {
    console.info('hook onMounted')
  })

  return {
    login
  }
}

export default useAuth
```

- /src/views/sys/user/index.vue

```vue
<script setup lang="ts">
import useAuth from '@/hooks/useAuth'

// ...

const { login } = useAuth()

login()

// ...
</script>
```
