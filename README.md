# `@nrfcloud/validate-with-typebox`

<https://jsr.io/@nrfcloud/validate-with-typebox>

Helper function to validate data with TypeBox schemas.

## Install with NPM

```bash
npx jsr add (--save-prod|--save-dev) @nrfcloud/validate-with-typebox
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
