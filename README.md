# `@nrfcloud/validate-with-typebox`

<https://github.com/nRFCloud/validate-with-typebox/pkgs/npm/validate-with-typebox>

Helper function to validate data with TypeBox schemas.

## Installation

The package is published to the
[GitHub Packages registry](https://github.com/nRFCloud/validate-with-typebox/pkgs/npm/validate-with-typebox).
Releases are also published to
[npm](https://www.npmjs.com/package/@nrfcloud/validate-with-typebox).

To install it, point the `@nrfcloud` scope to it in your project's `.npmrc` and
[authenticate](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry#authenticating-to-github-packages)
with a token that has the `read:packages` scope:

```
@nrfcloud:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

```bash
npm i (--save-prod|--save-dev) @nrfcloud/validate-with-typebox
```

## Usage

```typescript
import { fetchWithDebug } from "@nrfcloud/validate-with-typebox";
import assert from "node:assert/strict";

const validateInput = validateWithTypeBox(
  Type.Object({
    email: Type.RegExp(/.+@.+/),
  }),
);

assert.equal(
  formatTypeBoxErrors(
    (
      validateInput({
        email: "f",
      }) as any
    ).errors,
  ),
  `/email: Expected string to match regular expression`,
);
```

## TypeScript 6 and 7

This repo
[runs TypeScript 6 and 7 side by side](https://devblogs.microsoft.com/typescript/announcing-typescript-7-0/#running-side-by-side-with-typescript-6.0),
[so that eslint works](https://github.com/typescript-eslint/typescript-eslint/issues/10940#issuecomment-4922812181).
