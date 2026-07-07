# @deb0shic/tsconfig

Shared TypeScript compiler configurations. Five presets, all extending `base.json`:

| Preset | Extends | For |
|--------|---------|-----|
| [`base.json`](base.json)         | —              | Strict defaults for any project. Not usable directly — it does not set `target` / `module`. |
| [`node.json`](node.json)         | `base`         | Node 20+, ESM, `node_modules` resolution. |
| [`library.json`](library.json)   | `base`         | Publishable library. Emits declarations + declaration maps + source maps. |
| [`next.json`](next.json)         | `base`         | Next.js 14/15 App Router; JSX preserve, path aliases, `noEmit`. |
| [`strict-plus.json`](strict-plus.json) | `base`   | Every extra safety flag TypeScript ships. Slower to build; catches more. |

## Install

```bash
pnpm add -D @deb0shic/tsconfig
```

## Use

Point your `tsconfig.json` at the preset that fits:

```jsonc
{
  "extends": "@deb0shic/tsconfig/next.json",
  "include": ["**/*.ts", "**/*.tsx", ".next/types/**/*.ts"]
}
```

Or extend more than one — later entries win:

```jsonc
{
  "extends": ["@deb0shic/tsconfig/library.json", "@deb0shic/tsconfig/strict-plus.json"]
}
```

## What the presets set

**`base.json`** — `strict: true`, `noUncheckedIndexedAccess`, `noImplicitOverride`, `exactOptionalPropertyTypes`, `verbatimModuleSyntax`, `skipLibCheck`. Nothing about output; those go in the concrete presets.

**`node.json`** — `target: ES2022`, `module: NodeNext`, `moduleResolution: NodeNext`, `types: ["node"]`. ESM-first.

**`library.json`** — `declaration`, `declarationMap`, `sourceMap`, `emitDeclarationOnly` off, `stripInternal`. Also `composite` for project references.

**`next.json`** — `jsx: preserve`, `module: esnext`, `moduleResolution: bundler`, `noEmit`, path alias `"@/*": ["./*"]`, plus the standard set for Next's plugin.

**`strict-plus.json`** — `noUnusedLocals`, `noUnusedParameters`, `noFallthroughCasesInSwitch`, `noImplicitReturns`, `useUnknownInCatchVariables`. Turns compile time up; catches more real bugs.

## License

MIT


