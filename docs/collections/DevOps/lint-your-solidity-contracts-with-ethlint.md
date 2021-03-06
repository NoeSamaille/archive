---
title: Lint your Solidity contracts with Ethlint
summary: Ethlint (Formerly Solium) analyzes your Solidity code for style & security issues and fixes them. Installnpm install -g ethlint solium -V For backward-compatibility, you can still use npm install -g solium. If youre currently using the solium package for npm install, it is highly recommended that you move to ethlint. The solium package will not receive updates after December, 2019. There are no differences between the updates pushed to ethlint and solium packages. Usage In the root directory of
authors:
  - Kauri Team (@kauri)
date: 2019-05-28
some_url: 
---

# Lint your Solidity contracts with Ethlint

![](https://ipfs.infura.io/ipfs/QmdB7bqHShAvbtpEeg8L57FW4t1BA7kHKu2cHhUhbH6Lcr)


Ethlint (Formerly Solium) analyzes your Solidity code for style & security issues and fixes them.

### Install

```bash
npm install -g ethlint
solium -V
```

For backward-compatibility, you can still use `npm install -g solium`.

If you're currently using the `solium` package for `npm install`, it is highly recommended that you move to `ethlint`. The `solium` package will not receive updates after December, 2019. There are no differences between the updates pushed to `ethlint` and `solium` packages.

### Usage

In the root directory of your DApp:

```bash
solium --init
```

This creates 2 files for you:
- `.soliumignore` - contains names of files and directories to ignore while linting
- `.soliumrc.json` - contains configuration that tells Solium how to lint your project. You should modify this file to configure rules, plugins and sharable configs.

`.soliumrc.json` looks like:

```json
{
  "extends": "solium:recommended",
  "plugins": ["security"],
  "rules": {
    "quotes": ["error", "double"],
    "indentation": ["error", 4],
    "linebreak-style": ["error", "unix"]
  }
}
```

To know which lint rules Solium applies for you, see [Style rules](http://ethlint.readthedocs.io/en/latest/user-guide.html#list-of-style-rules) and [Security rules](https://www.npmjs.com/package/solium-plugin-security#list-of-rules).

---
**NOTE**

Solium does **not** strictly adhere to the Solidity [Style Guide](http://solidity.readthedocs.io/en/latest/style-guide.html). It aims to promote coding practices agreed upon by the community at large.

---

#### Lint

```bash
solium -f foobar.sol
solium -d contracts/
```

#### Configure with comments

**Comment Directives** can be used to configure Solium to ignore specific pieces of code.
They follow the pattern `solium-disable<optional suffix>`.

If you only use the directive, Solium disables all rules for the marked code. If that's not desirable, specify the rules to disable after the directive, separated by comma.

- Disable linting on a specific line

```
contract Foo {
	/* solium-disable-next-line */
	function() {
		bytes32 bar = 'Hello world';	// solium-disable-line quotes

		// solium-disable-next-line security/no-throw, indentation
						throw;
	}
}
```

- Disable linting on entire file

```
/* solium-disable */

contract Foo {
	...
}
```

#### Fix

Solium automatically fixes your code to resolve whatever issues it can.

```bash
solium -d contracts/ --fix
```

### Next steps

- Read the [Documentation](https://ethlint.readthedocs.io/).
- [IDE and Editor Integrations](http://solium.readthedocs.io/en/latest/user-guide.html#index-9)
- [Demo Video](https://www.youtube.com/watch?v=MlQ6fzwixpI)



---

- **Kauri original title:** Lint your Solidity contracts with Ethlint
- **Kauri original link:** https://kauri.io/lint-your-solidity-contracts-with-ethlint/1cf59f73db9948cf89019e59abb93146/a
- **Kauri original author:** Kauri Team (@kauri)
- **Kauri original Publication date:** 2019-05-28
- **Kauri original tags:** linting, ethlint, best-practise-
- **Kauri original hash:** QmNXkG1fEnMboYXPqJ7fabSo3rkHakvLt1hkc427pbmbZE
- **Kauri original checkpoint:** QmYRYAA1TRyDiXS6uLXdt6qS8AnW63tqJHYpUQKrdyNz7h



