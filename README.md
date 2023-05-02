# dontusesystemruby.com

## What is this?

This is the source for the website [Don't Use System Ruby](https://dontusesystemruby.com/).

## How to run locally

Install [docsify-cli](https://github.com/docsifyjs/docsify-cli) to enable the local server:

```shell
npm install -g docsify-cli
```

Then run docsify:

```shell
docsify serve public
```

## How to contribute

* Fork this repository
* Run `corepack prepare yarn@stable --activate` to install Yarn
* Run `yarn install` to install dependencies
* Edit [`public/README.md`](public/README.md)
* Use a JSON-LD generator like <https://saijogeorge.com/json-ld-schema-generator/faq/> to generate the JSON-LD
* Replace the JSON-LD in [`public/index.html`](public/index.html) with the generated JSON-LD
* Submit a pull request

## How to deploy

Deploy a preview site:

```shell
firebase hosting:channel:deploy preview --expires 1h
```

Deploy the production site:

```shell
firebase deploy --only hosting
```

## License

Licensed under CC-BY-SA-4.0. See [LICENSE](LICENSE) for details.
