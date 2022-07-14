# Yarn berry eslint-import-resolver-typescript error

I encountered an error with yarn berry after upgrading `eslint-import-resolver-typescript` to `>=3.2.2`.

```sh
# yarn dedupe                                                                                                                                                                                                          ─╯
➤ YN0000: ┌ Deduplication step
➤ YN0001: │ Error: Assertion failed: The package (a293018a10e9ce0aa8d85029a0159483af721a57359dd0534b9aac89fa081b358e02fea978a486b91358e63c916a7e26dd6ed4cb7056f2a4397bd9f7cfc2666c) should have been registered
    at ./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:474:1519
    at processTicksAndRejections (node:internal/process/task_queues:96:5)
    at async Promise.all (index 87)
    at async ./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:474:2181
    at async Je.startSectionPromise (./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:414:3303)
    at async qN (./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:474:1983)
    at async ./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:474:3699
    at async Function.start (./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:414:2373)
    at async um.execute (./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:474:3595)
    at async um.validateAndExecute (./bug-yarn-3-eslint-import-resolver-typescript/.yarn/releases/yarn-3.2.1.cjs:350:673)
➤ YN0000: └ Completed
```

This repository is a minimal reproduction.

## Steps to produce

```sh
yarn install
yarn dedupe
```

## Problem

This package depends on `get-tsconfig@^4`. `eslint-import-resolver-typescript` uses this as dependency.

```json
{
  "dependencies": {
    "get-tsconfig": "npm:@unts/get-tsconfig@^4.1.1"
  }
}
