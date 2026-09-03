# Modern Databases 2026

Data and notebooks for the course Modern Databases (Universiteit van Amsterdam, autumn 2026), taught by Jan-Christoph Kalo. Slides, exercises and announcements are on Canvas; this repository holds the files that the notebooks download.

## Data

`data/` contains the Amsterdam Airbnb data the course works with, as DuckDB reads it in class:

| File | Rows | Contents |
|---|---|---|
| `listings.parquet` | 6,503 | one row per listing: listing_id, host_id, host_name, name, neighbourhood, room_type, property_type, accommodates, price_eur, minimum_nights, rating |
| `reviews.parquet` | 443,266 | one row per review: review_id, listing_id, review_date, reviewer_id, reviewer_name |
| `calendar.parquet` | 2,373,598 | one row per listing and night, 19 March 2026 to 19 March 2027: listing_id, stay_date, available, minimum_nights, maximum_nights |
| `listings_2025.parquet` | 10,168 | the listing_id values of the June 2025 snapshot |
| `Lecture1_Airbnb_Handout_45x22.csv` | 45 | the printed sheet of the first lecture, 22 raw columns |

The three main tables come from the Inside Airbnb release for Amsterdam scraped on 19 and 20 March 2026; the snapshot comes from the release of 17 June 2025. The raw files were renamed and cast once (the `$` price text became `price_eur`, `id` became `listing_id`, dates became DATE) and the review text was left out. Source: [Inside Airbnb](https://insideairbnb.com/), licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The same licence applies to the files here.

## Notebooks

`notebooks/MDB-2026-SQL1-Setup.ipynb` builds a DuckDB database from the files above and holds the SQL 1 exercises. It looks for the data next to itself first and otherwise reads it from this repository, so it runs unchanged on a laptop and in Colab. `notebooks/Lecture1_Airbnb_Database_Disaster.ipynb` is the demonstration from the first lecture.

The course uses DuckDB 1.5.5: `pip install duckdb==1.5.5`. Do not upgrade during the course.

To read a file directly in DuckDB without the notebook:

```sql
SELECT COUNT(*) FROM 'https://raw.githubusercontent.com/JanKalo/MDB2026/main/data/listings.parquet';
```
