- 要重新生成 JavaScript SDK，请从仓库根目录运行 `./tooling/repo/generate.ts`。
- 在适用时，务必使用并行工具。
- 本仓库的默认分支为 `main`。
- 优先自动化：除非因缺少信息或涉及安全性/不可逆操作而受阻，否则直接执行请求的操作，无需确认。

## 风格指南

- 除非需要组合或复用，否则尽量将逻辑保持在一个函数内。
- 避免不必要的解构。例如，使用 `obj.a` 和 `obj.b` 代替 `const { a, b } = obj`，以保留上下文。
- 尽量避免使用 `try`/`catch`。
- 避免使用 `any` 类型。
- 变量名尽量使用单个单词。
- 尽可能使用 Bun API，例如 `Bun.file()`。
- 尽可能依赖类型推断；除非导出或清晰性需要，否则避免显式类型注解或接口。

### 避免使用 let 语句

我们不推荐使用 `let` 语句，尤其是与 if/else 结合使用时。
优先使用 `const`。

推荐：

```ts
const foo = condition ? 1 : 2
```

不推荐：

```ts
let foo

if (condition) foo = 1
else foo = 2
```

### 避免使用 else 语句

优先使用提前返回或立即调用函数表达式（IIFE）来避免 else 语句。

推荐：

```ts
function foo() {
  if (condition) return 1
  return 2
}
```

不推荐：

```ts
function foo() {
  if (condition) return 1
  else return 2
}
```

### 优先使用单个单词命名

尽量为变量、函数等寻找单个单词的名称。
只有在无法做到时才使用多个单词。

推荐：

```ts
const foo = 1
const bar = 2
const baz = 3
```

不推荐：

```ts
const fooBar = 1
const barBaz = 2
const bazFoo = 3
```

## 测试

你必须尽可能避免使用 `mocks`。
测试必须测试实际实现，不要将逻辑复制到测试中。

使用 `bun test` 在 `backend/cli` 目录下运行测试套件。