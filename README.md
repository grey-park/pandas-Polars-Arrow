# DataFrames with pandas, Polars and Arrow

302 Data infrastructures, topic 16.

## The topic
- pandas and Polars are two engines that run filter, join and aggregate on a DataFrame.
- A DataFrame is a typed table stored in memory.
- Arrow is how the table sits in memory under both.

## The question I answer
- Why the same query read the whole file in pandas and a small part of it in Polars?
- How can the result move between pandas and Polars without a copy?

## The demo shows

1. The MeteoSwiss aggregation in pandas and in Polars.
2. The timing of the same query in both.
3. How a table is passed from Polars to pandas through Arrow, without a copy.

## The demo: "1_demo.ipynb"

```bash
git clone https://github.com/grey-park/pandas-Polars-Arrow
cd pandas-Polars-Arrow
pip install -r requirements.txt
jupyter lab 1_demo.ipynb
```

## The data loader: "0_make_data.ipynb"

The data comes from SwissMetNet with one value every 10 minutes per station. 
The two Parquet files are already in the repo:

- `data/measurements.parquet`: station_abbr, ts, temperature, humidity, pressure. Sorted by station, then by time.
- `data/stations.parquet`: station_abbr, station_name, canton, height_masl.

`0_make_data.ipynb` downloads the data again and rebuilds these two files.
It keeps the last 180 days.

## the operations benchmark: "2_benchmark.py"

`benchmark.py` times the query step by step to compare pandas and Polars.

