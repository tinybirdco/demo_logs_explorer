# Tinybird project

This folder contains all of the resources to build the Tinybird project for this demo.

## Project structure

This project contains:

```
├── datasources
│   ├── accounts.datasource
│   ├── fixtures
│   │   └── accounts.csv
│   ├── logs.datasource
│   └── mv_ts_range.datasource
├── pipes
│   ├── log_explorer_brute_force.pipe
│   ├── log_explorer_with_map.pipe
│   └── mat_ts_range.pipe
```

In the `/datasources` folder:
- `accounts.datasource` is dimensional data. This example is for a multitenant application, where `accounts.id` is the ID of each end user. The data for this Data Source is in `/datasources/fixtures/accounts.csv`.
- `logs.datasource` is the raw logs data.
- `mv_ts_range.datasource` is a Materialized View used to create the "map".

In the `/pipes` folder:
- `log_explorer_brute_force.pipe` is the original query using the "brute force" approach.
- `log_explorer_with_map.pipe` is the optimized query.
- `mat_ts_range.pipe` is the Materializing Pipe to create the "map".

> 🚧 Warning
> 
> The query in `/pipes/log_explorer_with_map.pipe` does not guarantee that you will get exactly N results, or that results are unique per page (it depends on the "map" time interval defined in `mat_ts_range.pipe`). If that is required, you will need to add additional logic to calculate the last results from the previous page.


> ℹ️ Note
> 
> You may not notice a huge difference in performance at small scale. This approach is designed to optimize queries at huge data volumes.

## Deploying the Tinybird resources

To deploy to Tinybird, you need to have the [Tinybird CLI installed](https://www.tinybird.co/docs/cli/overview). Then, you can run the following commands:

```sh
tb auth --token <your user admin token>
tb push --force --fixtures
```
