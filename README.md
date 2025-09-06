
# 🚀 React + TypeScript + Webpack + Babel Setup

This is a simple setup to get **React**, **TypeScript**, **Webpack**, and **Babel** working together.

---

## 🛠 Steps to Add TypeScript Support

### 1. Install TypeScript and Dependencies

```bash
npm install --save-dev typescript ts-loader @babel/preset-typescript @types/react @types/react-dom
```

---

### 2. Create `tsconfig.json`

Create a `tsconfig.json` file in the project root with the following content:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "ESNext",
    "lib": ["DOM", "ESNext"],
    "jsx": "react-jsx",
    "moduleResolution": "node",
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true
  },
  "include": ["src"]
}
```

---

### 3. Update `webpack.config.js`

Modify your `webpack.config.js` to handle `.ts` and `.tsx` files:

```javascript
const path = require("path");

module.exports = {
  entry: "./src/index.tsx",
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "bundle.js",
    clean: true,
  },
  module: {
    rules: [
      {
        test: /\.(ts|tsx)$/,
        exclude: /node_modules/,
        use: "ts-loader" // or babel-loader with @babel/preset-typescript
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"],
      },
    ],
  },
  resolve: {
    extensions: [".ts", ".tsx", ".js", ".jsx"],
  },
};
```

---

### 4. Update `.babelrc` (Optional)

If you want to use Babel for TypeScript (skip type checking):

```json
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react",
    "@babel/preset-typescript"
  ]
}
```

**Note:** You can choose either:

✅ **`ts-loader` only** – Uses TypeScript compiler for type-checking.  
✅ **`babel-loader` with `@babel/preset-typescript`** – Transpiles without type-checking.

---

### 5. Rename Files

Rename your files to use TypeScript extensions:

```
src/index.js → src/index.tsx
src/App.js → src/App.tsx
```

---

### 6. Example TypeScript Component

**`src/App.tsx`**

```tsx
import React from "react";

type Props = {
  name: string;
};

const App: React.FC<Props> = ({ name }) => {
  return <h1>Hello {name}, React + Webpack + TypeScript 🚀</h1>;
};

export default App;
```

**`src/index.tsx`**

```tsx
import React from "react";
import { createRoot } from "react-dom/client";
import App from "./App";

const root = createRoot(document.getElementById("root") as HTMLElement);
root.render(<App name="Karthick" />);
```

---

### 7. Update `package.json` Scripts

```json
"scripts": {
  "start": "webpack serve --mode development",
  "build": "webpack --mode production"
}
```

---

### 8. Run the Project 🚀

```bash
npm start
```

You now have a fully working **React + TypeScript + Webpack + Babel** setup!

---

Happy coding! 🎉
