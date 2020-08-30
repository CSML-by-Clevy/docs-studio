# Studio CLI

CSML Studio comes with a CLI \(command-line interface\) tool that helps you develop your chatbot locally before deploying it. With the [CSML Studio CLI](https://www.npmjs.com/package/@csml/studio-cli), you can update your flows using your favorite code editor on your local machine and publish it on CSML Studio. For larger projects, we recommend using the CSML Studio CLI over the online interface as it makes it easier to manage many flows.

### Setting up CSML Studio CLI

To setup CSML Studio CLI, simply install the tool with `npm install -g @csml/studio-cli` \(requires nodejs 12+\). Then, using your bot's API keys \(see the [Studio API](introduction.md) section to learn more about creating API keys\), you can now run `csml-studio init -k MYKEY -s MYSECRET -p path/to/project`.

This command will setup a local development environment where you will be able to manage your chatbot entirely from the comfort of your machine!

### Get started with the CSML Studio CLI:

* [github](https://github.com/CSML-by-Clevy/CSML-Studio-CLI)
* [npm](https://www.npmjs.com/package/@csml/studio-cli)

