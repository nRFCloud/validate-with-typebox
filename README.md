# `@nrfcloud/validate-with-typebox`

<https://www.npmjs.com/package/@nrfcloud/validate-with-typebox>

Helper function to validate data with TypeBox schemas.

## Install with NPM

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
