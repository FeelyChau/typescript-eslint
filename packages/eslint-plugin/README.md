<h1 align="center">ESLint Plugin TypeScript</h1>

<p align="center">An ESLint plugin which provides lint rules for TypeScript codebases.</p>

<p align="center">
    <img src="https://github.com/typescript-eslint/typescript-eslint/workflows/CI/badge.svg" alt="CI" />
    <a href="https://www.npmjs.com/package/@typescript-eslint/eslint-plugin"><img src="https://img.shields.io/npm/v/@typescript-eslint/eslint-plugin.svg?style=flat-square" alt="NPM Version" /></a>
    <a href="https://www.npmjs.com/package/@typescript-eslint/eslint-plugin"><img src="https://img.shields.io/npm/dm/@typescript-eslint/eslint-plugin.svg?style=flat-square" alt="NPM Downloads" /></a>
</p>

## Getting Started

- **[You can find our Getting Started docs here](../../docs/getting-started/linting/README.md)**
- **[You can find our FAQ / Troubleshooting docs here](../../docs/getting-started/linting/FAQ.md)**

These docs walk you through setting up ESLint, this plugin, and our parser. If you know what you're doing and just want to quick start, read on...

## Quick-start

### Installation

Make sure you have TypeScript and [`@typescript-eslint/parser`](../parser) installed:

```bash
$ yarn add -D typescript @typescript-eslint/parser
$ npm i --save-dev typescript @typescript-eslint/parser
```

Then install the plugin:

```bash
$ yarn add -D @typescript-eslint/eslint-plugin
$ npm i --save-dev @typescript-eslint/eslint-plugin
```

It is important that you use the same version number for `@typescript-eslint/parser` and `@typescript-eslint/eslint-plugin`.

**Note:** If you installed ESLint globally (using the `-g` flag) then you must also install `@typescript-eslint/eslint-plugin` globally.

### Usage

Add `@typescript-eslint/parser` to the `parser` field and `@typescript-eslint` to the plugins section of your `.eslintrc` configuration file, then configure the rules you want to use under the rules section.

```json
{
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint"],
  "rules": {
    "@typescript-eslint/rule-name": "error"
  }
}
```

You can also enable all the recommended rules for our plugin. Add `plugin:@typescript-eslint/recommended` in extends:

```json
{
  "extends": ["plugin:@typescript-eslint/recommended"]
}
```

**Note: Make sure to use `eslint --ext .js,.ts` since by [default](https://eslint.org/docs/user-guide/command-line-interface#--ext) `eslint` will only search for `.js` files.**

### Recommended Configs

You can also use [`eslint:recommended`](https://eslint.org/docs/rules/) (the set of rules which are recommended for all projects by the ESLint Team) with this plugin:

```json
{
  "extends": ["eslint:recommended", "plugin:@typescript-eslint/recommended"]
}
```

As of version 2 of this plugin, _by design_, none of the rules in the main `recommended` config require type-checking in order to run. This means that they are more lightweight and faster to run.

Some highly valuable rules simply require type-checking in order to be implemented correctly, however, so we provide an additional config you can extend from called `recommended-requiring-type-checking`. You would apply this _in addition_ to the recommended configs previously mentioned, e.g.:

```json
{
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:@typescript-eslint/recommended-requiring-type-checking"
  ]
}
```

Pro Tip: For larger codebases you may want to consider splitting our linting into two separate stages: 1. fast feedback rules which operate purely based on syntax (no type-checking), 2. rules which are based on semantics (type-checking).

**[You can read more about linting with type information here](../../docs/getting-started/linting/TYPED_LINTING.md)**

## Supported Rules

<!-- begin base rule list -->

**Key**: :heavy_check_mark: = recommended, :wrench: = fixable, :thought_balloon: = requires type information

| Name                                                                                                                  | Description                                                                                                             | :heavy_check_mark: | :wrench: | :thought_balloon: |
| --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------ | -------- | ----------------- |
| [`@typescript-eslint/adjacent-overload-signatures`](./packages/eslint-plugin/docs/rules/adjacent-overload-signatures.md)                     | Require that member overloads be consecutive                                                                            | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/array-type`](./packages/eslint-plugin/docs/rules/array-type.md)                                                         | Requires using either `T[]` or `Array<T>` for arrays                                                                    |                    | :wrench: |                   |
| [`@typescript-eslint/await-thenable`](./packages/eslint-plugin/docs/rules/await-thenable.md)                                                 | Disallows awaiting a value that is not a Thenable                                                                       | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/ban-ts-comment`](./packages/eslint-plugin/docs/rules/ban-ts-comment.md)                                                 | Bans `// @ts-<directive>` comments from being used or requires descriptions after directive                             | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/ban-tslint-comment`](./packages/eslint-plugin/docs/rules/ban-tslint-comment.md)                                         | Bans `// tslint:<rule-flag>` comments from being used                                                                   |                    | :wrench: |                   |
| [`@typescript-eslint/ban-types`](./packages/eslint-plugin/docs/rules/ban-types.md)                                                           | Bans specific types from being used                                                                                     | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/class-literal-property-style`](./packages/eslint-plugin/docs/rules/class-literal-property-style.md)                     | Ensures that literals on classes are exposed in a consistent style                                                      |                    | :wrench: |                   |
| [`@typescript-eslint/consistent-type-assertions`](./packages/eslint-plugin/docs/rules/consistent-type-assertions.md)                         | Enforces consistent usage of type assertions                                                                            |                    |          |                   |
| [`@typescript-eslint/consistent-type-definitions`](./packages/eslint-plugin/docs/rules/consistent-type-definitions.md)                       | Consistent with type definition either `interface` or `type`                                                            |                    | :wrench: |                   |
| [`@typescript-eslint/explicit-function-return-type`](./packages/eslint-plugin/docs/rules/explicit-function-return-type.md)                   | Require explicit return types on functions and class methods                                                            |                    |          |                   |
| [`@typescript-eslint/explicit-member-accessibility`](./packages/eslint-plugin/docs/rules/explicit-member-accessibility.md)                   | Require explicit accessibility modifiers on class properties and methods                                                |                    | :wrench: |                   |
| [`@typescript-eslint/explicit-module-boundary-types`](./packages/eslint-plugin/docs/rules/explicit-module-boundary-types.md)                 | Require explicit return and argument types on exported functions' and classes' public class methods                     | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/member-delimiter-style`](./packages/eslint-plugin/docs/rules/member-delimiter-style.md)                                 | Require a specific member delimiter style for interfaces and type literals                                              |                    | :wrench: |                   |
| [`@typescript-eslint/member-ordering`](./packages/eslint-plugin/docs/rules/member-ordering.md)                                               | Require a consistent member declaration order                                                                           |                    |          |                   |
| [`@typescript-eslint/method-signature-style`](./packages/eslint-plugin/docs/rules/method-signature-style.md)                                 | Enforces using a particular method signature syntax.                                                                    |                    | :wrench: |                   |
| [`@typescript-eslint/naming-convention`](./packages/eslint-plugin/docs/rules/naming-convention.md)                                           | Enforces naming conventions for everything across a codebase                                                            |                    |          | :thought_balloon: |
| [`@typescript-eslint/no-base-to-string`](./packages/eslint-plugin/docs/rules/no-base-to-string.md)                                           | Requires that `.toString()` is only called on objects which provide useful information when stringified                 |                    |          | :thought_balloon: |
| [`@typescript-eslint/no-confusing-non-null-assertion`](./packages/eslint-plugin/docs/rules/no-confusing-non-null-assertion.md)               | Disallow non-null assertion in locations that may be confusing                                                          |                    | :wrench: |                   |
| [`@typescript-eslint/no-dynamic-delete`](./packages/eslint-plugin/docs/rules/no-dynamic-delete.md)                                           | Disallow the delete operator with computed key expressions                                                              |                    | :wrench: |                   |
| [`@typescript-eslint/no-empty-interface`](./packages/eslint-plugin/docs/rules/no-empty-interface.md)                                         | Disallow the declaration of empty interfaces                                                                            | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/no-explicit-any`](./packages/eslint-plugin/docs/rules/no-explicit-any.md)                                               | Disallow usage of the `any` type                                                                                        | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/no-extra-non-null-assertion`](./packages/eslint-plugin/docs/rules/no-extra-non-null-assertion.md)                       | Disallow extra non-null assertion                                                                                       | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/no-extraneous-class`](./packages/eslint-plugin/docs/rules/no-extraneous-class.md)                                       | Forbids the use of classes as namespaces                                                                                |                    |          |                   |
| [`@typescript-eslint/no-floating-promises`](./packages/eslint-plugin/docs/rules/no-floating-promises.md)                                     | Requires Promise-like values to be handled appropriately                                                                | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-for-in-array`](./packages/eslint-plugin/docs/rules/no-for-in-array.md)                                               | Disallow iterating over an array with a for-in loop                                                                     | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-implied-eval`](./packages/eslint-plugin/docs/rules/no-implied-eval.md)                                               | Disallow the use of `eval()`-like methods                                                                               | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-inferrable-types`](./packages/eslint-plugin/docs/rules/no-inferrable-types.md)                                       | Disallows explicit type declarations for variables or parameters initialized to a number, string, or boolean            | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/no-invalid-void-type`](./packages/eslint-plugin/docs/rules/no-invalid-void-type.md)                                     | Disallows usage of `void` type outside of generic or return types                                                       |                    |          |                   |
| [`@typescript-eslint/no-misused-new`](./packages/eslint-plugin/docs/rules/no-misused-new.md)                                                 | Enforce valid definition of `new` and `constructor`                                                                     | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/no-misused-promises`](./packages/eslint-plugin/docs/rules/no-misused-promises.md)                                       | Avoid using promises in places not designed to handle them                                                              | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-namespace`](./packages/eslint-plugin/docs/rules/no-namespace.md)                                                     | Disallow the use of custom TypeScript modules and namespaces                                                            | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/no-non-null-asserted-optional-chain`](./packages/eslint-plugin/docs/rules/no-non-null-asserted-optional-chain.md)       | Disallows using a non-null assertion after an optional chain expression                                                 | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/no-non-null-assertion`](./packages/eslint-plugin/docs/rules/no-non-null-assertion.md)                                   | Disallows non-null assertions using the `!` postfix operator                                                            | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/no-parameter-properties`](./packages/eslint-plugin/docs/rules/no-parameter-properties.md)                               | Disallow the use of parameter properties in class constructors                                                          |                    |          |                   |
| [`@typescript-eslint/no-require-imports`](./packages/eslint-plugin/docs/rules/no-require-imports.md)                                         | Disallows invocation of `require()`                                                                                     |                    |          |                   |
| [`@typescript-eslint/no-this-alias`](./packages/eslint-plugin/docs/rules/no-this-alias.md)                                                   | Disallow aliasing `this`                                                                                                | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/no-throw-literal`](./packages/eslint-plugin/docs/rules/no-throw-literal.md)                                             | Disallow throwing literals as exceptions                                                                                |                    |          | :thought_balloon: |
| [`@typescript-eslint/no-type-alias`](./packages/eslint-plugin/docs/rules/no-type-alias.md)                                                   | Disallow the use of type aliases                                                                                        |                    |          |                   |
| [`@typescript-eslint/no-unnecessary-boolean-literal-compare`](./packages/eslint-plugin/docs/rules/no-unnecessary-boolean-literal-compare.md) | Flags unnecessary equality comparisons against boolean literals                                                         |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/no-unnecessary-condition`](./packages/eslint-plugin/docs/rules/no-unnecessary-condition.md)                             | Prevents conditionals where the type is always truthy or always falsy                                                   |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/no-unnecessary-qualifier`](./packages/eslint-plugin/docs/rules/no-unnecessary-qualifier.md)                             | Warns when a namespace qualifier is unnecessary                                                                         |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/no-unnecessary-type-arguments`](./packages/eslint-plugin/docs/rules/no-unnecessary-type-arguments.md)                   | Enforces that type arguments will not be used if not required                                                           |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/no-unnecessary-type-assertion`](./packages/eslint-plugin/docs/rules/no-unnecessary-type-assertion.md)                   | Warns if a type assertion does not change the type of an expression                                                     | :heavy_check_mark: | :wrench: | :thought_balloon: |
| [`@typescript-eslint/no-unsafe-assignment`](./packages/eslint-plugin/docs/rules/no-unsafe-assignment.md)                                     | Disallows assigning any to variables and properties                                                                     | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-unsafe-call`](./packages/eslint-plugin/docs/rules/no-unsafe-call.md)                                                 | Disallows calling an any type value                                                                                     | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-unsafe-member-access`](./packages/eslint-plugin/docs/rules/no-unsafe-member-access.md)                               | Disallows member access on any typed variables                                                                          | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-unsafe-return`](./packages/eslint-plugin/docs/rules/no-unsafe-return.md)                                             | Disallows returning any from a function                                                                                 | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/no-unused-vars-experimental`](./packages/eslint-plugin/docs/rules/no-unused-vars-experimental.md)                       | Disallow unused variables and arguments                                                                                 |                    |          |                   |
| [`@typescript-eslint/no-var-requires`](./packages/eslint-plugin/docs/rules/no-var-requires.md)                                               | Disallows the use of require statements except in import statements                                                     | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/prefer-as-const`](./packages/eslint-plugin/docs/rules/prefer-as-const.md)                                               | Prefer usage of `as const` over literal type                                                                            | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/prefer-for-of`](./packages/eslint-plugin/docs/rules/prefer-for-of.md)                                                   | Prefer a ‘for-of’ loop over a standard ‘for’ loop if the index is only used to access the array being iterated          |                    |          |                   |
| [`@typescript-eslint/prefer-function-type`](./packages/eslint-plugin/docs/rules/prefer-function-type.md)                                     | Use function types instead of interfaces with call signatures                                                           |                    | :wrench: |                   |
| [`@typescript-eslint/prefer-includes`](./packages/eslint-plugin/docs/rules/prefer-includes.md)                                               | Enforce `includes` method over `indexOf` method                                                                         |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/prefer-literal-enum-member`](./packages/eslint-plugin/docs/rules/prefer-literal-enum-member.md)                         | Require that all enum members be literal values to prevent unintended enum member name shadow issues                    |                    |          |                   |
| [`@typescript-eslint/prefer-namespace-keyword`](./packages/eslint-plugin/docs/rules/prefer-namespace-keyword.md)                             | Require the use of the `namespace` keyword instead of the `module` keyword to declare custom TypeScript modules         | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/prefer-nullish-coalescing`](./packages/eslint-plugin/docs/rules/prefer-nullish-coalescing.md)                           | Enforce the usage of the nullish coalescing operator instead of logical chaining                                        |                    |          | :thought_balloon: |
| [`@typescript-eslint/prefer-optional-chain`](./packages/eslint-plugin/docs/rules/prefer-optional-chain.md)                                   | Prefer using concise optional chain expressions instead of chained logical ands                                         |                    |          |                   |
| [`@typescript-eslint/prefer-readonly`](./packages/eslint-plugin/docs/rules/prefer-readonly.md)                                               | Requires that private members are marked as `readonly` if they're never modified outside of the constructor             |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/prefer-readonly-parameter-types`](./packages/eslint-plugin/docs/rules/prefer-readonly-parameter-types.md)               | Requires that function parameters are typed as readonly to prevent accidental mutation of inputs                        |                    |          | :thought_balloon: |
| [`@typescript-eslint/prefer-reduce-type-parameter`](./packages/eslint-plugin/docs/rules/prefer-reduce-type-parameter.md)                     | Prefer using type parameter when calling `Array#reduce` instead of casting                                              |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/prefer-regexp-exec`](./packages/eslint-plugin/docs/rules/prefer-regexp-exec.md)                                         | Enforce that `RegExp#exec` is used instead of `String#match` if no global flag is provided                              | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/prefer-string-starts-ends-with`](./packages/eslint-plugin/docs/rules/prefer-string-starts-ends-with.md)                 | Enforce the use of `String#startsWith` and `String#endsWith` instead of other equivalent methods of checking substrings |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/prefer-ts-expect-error`](./packages/eslint-plugin/docs/rules/prefer-ts-expect-error.md)                                 | Recommends using `// @ts-expect-error` over `// @ts-ignore`                                                             |                    | :wrench: |                   |
| [`@typescript-eslint/promise-function-async`](./packages/eslint-plugin/docs/rules/promise-function-async.md)                                 | Requires any function or method that returns a Promise to be marked async                                               |                    |          | :thought_balloon: |
| [`@typescript-eslint/require-array-sort-compare`](./packages/eslint-plugin/docs/rules/require-array-sort-compare.md)                         | Requires `Array#sort` calls to always provide a `compareFunction`                                                       |                    |          | :thought_balloon: |
| [`@typescript-eslint/restrict-plus-operands`](./packages/eslint-plugin/docs/rules/restrict-plus-operands.md)                                 | When adding two variables, operands must both be of type number or of type string                                       | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/restrict-template-expressions`](./packages/eslint-plugin/docs/rules/restrict-template-expressions.md)                   | Enforce template literal expressions to be of string type                                                               | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/strict-boolean-expressions`](./packages/eslint-plugin/docs/rules/strict-boolean-expressions.md)                         | Restricts the types allowed in boolean expressions                                                                      |                    |          | :thought_balloon: |
| [`@typescript-eslint/switch-exhaustiveness-check`](./packages/eslint-plugin/docs/rules/switch-exhaustiveness-check.md)                       | Exhaustiveness checking in switch with union type                                                                       |                    |          | :thought_balloon: |
| [`@typescript-eslint/triple-slash-reference`](./packages/eslint-plugin/docs/rules/triple-slash-reference.md)                                 | Sets preference level for triple slash directives versus ES6-style import declarations                                  | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/type-annotation-spacing`](./packages/eslint-plugin/docs/rules/type-annotation-spacing.md)                               | Require consistent spacing around type annotations                                                                      |                    | :wrench: |                   |
| [`@typescript-eslint/typedef`](./packages/eslint-plugin/docs/rules/typedef.md)                                                               | Requires type annotations to exist                                                                                      |                    |          |                   |
| [`@typescript-eslint/unbound-method`](./packages/eslint-plugin/docs/rules/unbound-method.md)                                                 | Enforces unbound methods are called with their expected scope                                                           | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/unified-signatures`](./packages/eslint-plugin/docs/rules/unified-signatures.md)                                         | Warns for any two overloads that could be unified into one by using a union or an optional/rest parameter               |                    |          |                   |

<!-- end base rule list -->

### Extension Rules

In some cases, ESLint provides a rule itself, but it doesn't support TypeScript syntax; either it crashes, or it ignores the syntax, or it falsely reports against it.
In these cases, we create what we call an extension rule; a rule within our plugin that has the same functionality, but also supports TypeScript.

<!-- begin extension rule list -->

**Key**: :heavy_check_mark: = recommended, :wrench: = fixable, :thought_balloon: = requires type information

| Name                                                                                            | Description                                                                    | :heavy_check_mark: | :wrench: | :thought_balloon: |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | ------------------ | -------- | ----------------- |
| [`@typescript-eslint/brace-style`](./packages/eslint-plugin/docs/rules/brace-style.md)                                 | Enforce consistent brace style for blocks                                      |                    | :wrench: |                   |
| [`@typescript-eslint/comma-spacing`](./packages/eslint-plugin/docs/rules/comma-spacing.md)                             | Enforces consistent spacing before and after commas                            |                    | :wrench: |                   |
| [`@typescript-eslint/default-param-last`](./packages/eslint-plugin/docs/rules/default-param-last.md)                   | Enforce default parameters to be last                                          |                    |          |                   |
| [`@typescript-eslint/dot-notation`](./packages/eslint-plugin/docs/rules/dot-notation.md)                               | enforce dot notation whenever possible                                         |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/func-call-spacing`](./packages/eslint-plugin/docs/rules/func-call-spacing.md)                     | Require or disallow spacing between function identifiers and their invocations |                    | :wrench: |                   |
| [`@typescript-eslint/indent`](./packages/eslint-plugin/docs/rules/indent.md)                                           | Enforce consistent indentation                                                 |                    | :wrench: |                   |
| [`@typescript-eslint/init-declarations`](./packages/eslint-plugin/docs/rules/init-declarations.md)                     | require or disallow initialization in variable declarations                    |                    |          |                   |
| [`@typescript-eslint/keyword-spacing`](./packages/eslint-plugin/docs/rules/keyword-spacing.md)                         | Enforce consistent spacing before and after keywords                           |                    | :wrench: |                   |
| [`@typescript-eslint/lines-between-class-members`](./packages/eslint-plugin/docs/rules/lines-between-class-members.md) | Require or disallow an empty line between class members                        |                    | :wrench: |                   |
| [`@typescript-eslint/no-array-constructor`](./packages/eslint-plugin/docs/rules/no-array-constructor.md)               | Disallow generic `Array` constructors                                          | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/no-dupe-class-members`](./packages/eslint-plugin/docs/rules/no-dupe-class-members.md)             | Disallow duplicate class members                                               |                    |          |                   |
| [`@typescript-eslint/no-empty-function`](./packages/eslint-plugin/docs/rules/no-empty-function.md)                     | Disallow empty functions                                                       | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/no-extra-parens`](./packages/eslint-plugin/docs/rules/no-extra-parens.md)                         | Disallow unnecessary parentheses                                               |                    | :wrench: |                   |
| [`@typescript-eslint/no-extra-semi`](./packages/eslint-plugin/docs/rules/no-extra-semi.md)                             | Disallow unnecessary semicolons                                                | :heavy_check_mark: | :wrench: |                   |
| [`@typescript-eslint/no-invalid-this`](./packages/eslint-plugin/docs/rules/no-invalid-this.md)                         | disallow `this` keywords outside of classes or class-like objects              |                    |          |                   |
| [`@typescript-eslint/no-loss-of-precision`](./packages/eslint-plugin/docs/rules/no-loss-of-precision.md)               | Disallow literal numbers that lose precision                                   |                    |          |                   |
| [`@typescript-eslint/no-magic-numbers`](./packages/eslint-plugin/docs/rules/no-magic-numbers.md)                       | Disallow magic numbers                                                         |                    |          |                   |
| [`@typescript-eslint/no-unused-expressions`](./packages/eslint-plugin/docs/rules/no-unused-expressions.md)             | Disallow unused expressions                                                    |                    |          |                   |
| [`@typescript-eslint/no-unused-vars`](./packages/eslint-plugin/docs/rules/no-unused-vars.md)                           | Disallow unused variables                                                      | :heavy_check_mark: |          |                   |
| [`@typescript-eslint/no-use-before-define`](./packages/eslint-plugin/docs/rules/no-use-before-define.md)               | Disallow the use of variables before they are defined                          |                    |          |                   |
| [`@typescript-eslint/no-useless-constructor`](./packages/eslint-plugin/docs/rules/no-useless-constructor.md)           | Disallow unnecessary constructors                                              |                    |          |                   |
| [`@typescript-eslint/quotes`](./packages/eslint-plugin/docs/rules/quotes.md)                                           | Enforce the consistent use of either backticks, double, or single quotes       |                    | :wrench: |                   |
| [`@typescript-eslint/require-await`](./packages/eslint-plugin/docs/rules/require-await.md)                             | Disallow async functions which have no `await` expression                      | :heavy_check_mark: |          | :thought_balloon: |
| [`@typescript-eslint/return-await`](./packages/eslint-plugin/docs/rules/return-await.md)                               | Enforces consistent returning of awaited values                                |                    | :wrench: | :thought_balloon: |
| [`@typescript-eslint/semi`](./packages/eslint-plugin/docs/rules/semi.md)                                               | Require or disallow semicolons instead of ASI                                  |                    | :wrench: |                   |
| [`@typescript-eslint/space-before-function-paren`](./packages/eslint-plugin/docs/rules/space-before-function-paren.md) | Enforces consistent spacing before function parenthesis                        |                    | :wrench: |                   |

<!-- end extension rule list -->

## Contributing

[See the contributing guide here](../../CONTRIBUTING.md).
