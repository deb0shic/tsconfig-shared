# Changelog

## 0.4.0

- Split `strict-plus.json` out of the base so projects can opt in without paying the extra check-time cost.
- Base now sets `verbatimModuleSyntax: true`. This lines up ambient imports with the runtime shape and prevents a whole class of unused-import surprises.
- `node.json` bumped to `target: ES2022` and `module: NodeNext`.

## 0.3.0

- Renamed `next-app.json` → `next.json`. Only App Router is supported anyway.
- Added `noPropertyAccessFromIndexSignature` to strict-plus.

## 0.2.0

- Introduced `library.json` with `composite` for project references.
- Base config now sets `exactOptionalPropertyTypes: true`. Breaking for callers that relied on `T | undefined` being equivalent to an optional property.

## 0.1.0

- Initial split from a single monolithic `tsconfig.json` used across my projects.
