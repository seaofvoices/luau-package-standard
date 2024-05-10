# Sea of Voices Luau Package Standard

This standard aims to bridge the gaps between different Luau and Lua environments. By following this standard, Luau packages can be published on [`npm`](https://www.npmjs.com).

Additionally, [darklua](https://github.com/seaofvoices/darklua) can be used to transform module imports into environment specific imports, but also Luau code into Lua code.

## Must

- Define a `package.json` ([npm documentation](https://docs.npmjs.com/cli/v10/configuring-npm/package-json)).
- Use the `@pkg` alias to import dependent packages. This means that to import a package named `mypackage`, write the import statement as `require(“@pkg/mypackage”)`.

## Recommended

- Use the global variable `LUA_ENV` to branch for different environments.
- Put `luau` in the package `keywords` entry.
- For Roblox developers: avoid publishing Rojo configuration files (`*.project.json` files) into the package itself. Use `npm pack --dry-run` or `yarn pack --dry-run` to verify if the package will contain these files.

## Environments

Developers can define a global variable named `LUA_ENV` so that Luau packages can be used for different Luau (and even Lua) environments.

The next table shows the pair of environments and values recognized by the standard. *If an environment you would like to support is not defined here, open an issue to submit it.*

| Environment | Value    |
| ----------- | -------- |
| Roblox      | `roblox` |
| Lune        | `lune`   |

## Learn More

### Project Generator

For Luau users, the quickest way to setup a full project with the latest tooling is with [generator-luau](https://github.com/seaofvoices/generator-luau). It will create the necessary configuration files to analyse, auto-format, bundle to a single file, build a Roblox model, run tests with [jest](https://github.com/jsdotlua/jest-lua) and automate releases.
