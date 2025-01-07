# A require() style import is forbidden.eslint@typescript-eslint/no-require-imports

> [!NOTE]
>
> ### Definition
>
> The eslint@typescript-eslint/no-require-imports rule is part of the ESLint plugin for TypeScript (@typescript-eslint). This rule disallows the use of CommonJS require() imports in favor of ES Module import statements, which are preferred in TypeScript and modern JavaScript projects.

### Why You See This Error:

- Code Consistency: TypeScript encourages the use of ES Module syntax for imports (import ... from '...'), which is more consistent with modern JavaScript.
- Type Safety: ES Modules provide better type safety and are more compatible with TypeScript's static type checking.

### How to Fix the Error:

Replace require() with import:
Convert your require() imports to import statements.

Before:

```javascript
const fs = require("fs");
const path = require("path");
```

after

```typescript
import fs from "fs";
import path from "path";
```

For Named Exports:
If the module exports specific named exports, you need to adjust the import accordingly.
Before

```javascript
const { readFile } = require("fs");
```

After

```typescript
import { readFile } from "fs";
```

### Additional Notes:

Default Exports: If a module uses module.exports, you may need to handle it differently because TypeScript might not recognize it as a default export. In such cases, use import \* as.

Example:

```typescript
import * as someModule from "./someModule";
```

Dynamic Imports: If you need to dynamically import a module, use the import() function.

Example:

```typescript
const module = await import("./module");
```

ESLint Configuration: If you have legacy code that must use require(), you can temporarily disable the rule for specific lines using comments:

javascript
Copy code

```javascript
// eslint-disable-next-line @typescript-eslint/no-require-imports
const fs = require("fs");
```

Transitioning to import statements is beneficial for modern TypeScript projects, ensuring better compatibility and type safety.

Encountered Date: 2025.01.05
