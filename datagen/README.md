# Data Generator

This folder contains code to generate data for this demo.

## How to generate data

To generate data, you need to have [Mockingbird Library installed](https://mockingbird-docs.tinybird.co/library).

Update the `.env` to include the correct endpoint (region), Data Source name, and token (with 'append' scope to your Data Source). If you'd like, you can customize the schema and settings in `mockingbird.js`.

Then, you can run the following from this directory:

```sh
node mockingbird.js
```
