
# mlz-eslint-config

eslint 统一规范配置，集成了 [eslint-plugin-import](https://github.com/import-js/eslint-plugin-import)、[eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier)、[eslint-plugin-promise](https://github.com/eslint-community/eslint-plugin-promise)、[eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react)、[eslint-plugin-react-hooks](https://github.com/facebook/react/tree/main/packages/eslint-plugin-react-hooks)

## Installation

`npm i -D @mlz/eslint-config`

## Usage

- typescript：在项目根目录新建 `tsconfig.json` 文件，并写入下面👇代码

```js
// tsconfig.json
{
  "extends": "@mlz/eslint-config/tsconfig.json",
  "compilerOptions": {
    "baseUrl": ".",
  }
}
```

- React 项目在根目录新建 `.eslintrc.json` 文件，并加入下面👇代码

```js
{
  "extends": "@mlz/eslint-config",
}
```

- 单纯 TypeScript 项目在根目录新建 `.eslintrc.json` 文件，并加入下面👇代码

```js
{
  "extends": ["@mlz/eslint-config:typescript"],
}
```

#### 不生效可能原因及解决方法：

- 1、eslint未启用或执行报错：

  调出eslint控制台（点击vscode右下角eslint打开控制台， 如找不到，则，点击左下角设置按钮 --> 选择setting --> 输入eslint --> 把 ```Eslint:Always Show Status``` 和 ```Eslint:Enable```勾选上 --> 点击任意js或ts文件则会出现，若还未出现请升级vscode版本），查看是否执行过程中出现错误


- 2、vscode版本过低（请升级到1.41.1或以上）

  mac中如果遇到无法升级，则确认```vscode```是否在应用程序中，如不在则手动把```vscode```移到应用程序中方可进行升级

---
## AutoFix

1、打开编辑器设置文件（以vscode为例）：
```js
command + P  -->  输入setting  --> 选择 settings.json文件
```

2、在文件中添加如下代码并保存：
```js
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.fixAll.stylelint": true,
  },
```
3、修改文件后保存，便会自动修复空格、顺序等风格问题

---
## 配置说明

++++++

该项目中的配置为公司前端统一配置，除一些标明可自定义的配置外，其他配置最好不要随意更改，以保持前端代码风格的统一

++++++
#### tsconfig  

详情请见：tsconfig.json

|  配置  | 值 | 原因 |
|  ----  | ----  | ---- |
| target  | ESNext | 保留所有特性，配合 `@babel` 或 `swc` 使用
| module | ESNext | 使用ES的方式组织代码
| lib | ["DOM", "DOM.Iterable", "ESNext"] | 把这些库文件包含进编译的过程中保证编译的正确快速执行
| allowJs  | true | 允许检查js文件，保证js文件的质量
| checkJs  | true | 允许ts检查js文件的错误，保证js文件的质量
| jsx  | preserve | 输出.jsx且dom编译后还是原dom方便后续babel等编译
| sourceMap  | true | 输出.map文件，方便调试
| outDir  | build | 指定输出目录为build
| removeComments  | true | 删除编译后的所有的注释（使代码安全简洁，减少代码量）
| noImplicitAny  | true | 类型安全更加严格（强制类型检验）
| strictNullChecks  | true | null 和 undefined检查，避免错误（严格空校验）
| noUnusedLocals  | true | 不需要不用的变量
| noImplicitReturns  | true | 函数的所有路径都必须有返回值
| moduleResolution  | node | 使用node的模块解析策略
| baseUrl | . | 把tsconfig所在的目录当成是解析非相对模块的基准目录
| paths | - | 模块名到基于 baseUrl 的路径映射的列表
| allowSyntheticDefaultImports | true | 允许从没有设置默认导出的模块中默认导入
| experimentalDecorators | true | 启用装饰器

#### eslint

详情请见 `index.js` 和 `typescript.js` 文件
