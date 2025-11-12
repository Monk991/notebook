## [Normalize](http://necolas.github.io/normalize.css/)

### 安装

```bash
$ yarn add normalize.css

yarn add v1.22.4
...
$ curl --compressed -o- -L https://yarnpkg.com/install.sh | bash
success Saved 1 new dependency.
info Direct dependencies
└─ normalize.css@8.0.1
info All dependencies
└─ normalize.css@8.0.1
✨  Done in 2.05s.
```

### 使用

- /src/main.ts

```ts
import { createApp } from 'vue'

import 'normalize.css/normalize.css'
import './style.css'
// ...
```
