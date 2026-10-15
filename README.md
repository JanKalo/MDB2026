# Modern Databases 2026

Data and notebooks for the course Modern Databases (Universiteit van Amsterdam, autumn 2026), taught by Jan-Christoph Kalo. Slides and announcements are on Canvas; this repository holds the files that the notebooks download, and practice exercises.

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

`data/cinema/` holds the fictional data of the cinema practice notebook: six CSV exports from the spreadsheets of an invented cinema chain with three cinemas.

| File | Rows | Contents |
|---|---|---|
| `seats.csv` | 747 | one row per seat: cinema, cinema_name, city, screen, seat_row, seat_no, seat_type |
| `films.csv` | 23 | one row per film: title, release_year, runtime_min, min_age, genres, sequel_of_title, sequel_of_year |
| `programme.csv` | 476 | one row per screening, 3 to 16 September 2026: cinema, screen, start_time, title, release_year, base_price |
| `customers.csv` | 1,205 | one row per registered customer: email, name, birth_date, member_since, home_cinema |
| `tickets.csv` | 9,316 | one row per ticket: cinema, screen, start_time, seat_row, seat_no, email, price_paid, sold_at |
| `ratings.csv` | 802 | one row per rating: email, title, release_year, stars, rated_on |

The cinemas, films and people are invented, and the email addresses use the reserved example domains.

## Notebooks

`notebooks/MDB-2026-SQL1-Setup.ipynb` builds a DuckDB database from the files above and holds the SQL 1 exercises. It looks for the data next to itself first and otherwise reads it from this repository, so it runs unchanged on a laptop and in Colab. `notebooks/Lecture1_Airbnb_Database_Disaster.ipynb` is the demonstration from the first lecture. `notebooks/MDB-2026-Cinema-Practice.ipynb` is a practice notebook on the cinema data, from an EER diagram to SQL queries; it has no model solution and shows the expected result of every query.

The course uses DuckDB 1.5.5: `pip install duckdb==1.5.5`. Do not upgrade during the course.

To read a file directly in DuckDB without the notebook:

```sql
SELECT COUNT(*) FROM 'https://raw.githubusercontent.com/JanKalo/MDB2026/main/data/listings.parquet';
```

## Relational algebra practice

`relational-algebra/` holds seventeen exercises on the rental platform from Lecture 6 (Host, Listing, Guest, Booking), in the style of the exam questions, with the expected result and a solution for each, in the lecture notation and in RelaX. Write the answers on paper and check them in [RelaX](https://dbis-uibk.github.io/relax/calc); `rental-platform.txt` is the data to paste into RelaX. Instructions are in [relational-algebra/README.md](relational-algebra/README.md).
