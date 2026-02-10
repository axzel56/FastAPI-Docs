
# JSON/JSONB functions 

| PostgreSQL function       | SQLAlchemy                       |
| ------------------------- | -------------------------------- |
| `jsonb_build_object`      | `func.jsonb_build_object()`      |
| `jsonb_build_array`       | `func.jsonb_build_array()`       |
| `jsonb_extract_path`      | `func.jsonb_extract_path()`      |
| `jsonb_extract_path_text` | `func.jsonb_extract_path_text()` |
| `jsonb_set`               | `func.jsonb_set()`               |
| `jsonb_array_elements`    | `func.jsonb_array_elements()`    |
| `jsonb_array_length`      | `func.jsonb_array_length()`      |
| `to_jsonb`                | `func.to_jsonb()`                |
- jsonb_build_object: Creats JSON objects from key-value pairs.
- jsonb_set()

# Aggregate functions

|PostgreSQL|SQLAlchemy|
|---|---|
|`count`|`func.count()`|
|`sum`|`func.sum()`|
|`avg`|`func.avg()`|
|`min`|`func.min()`|
|`max`|`func.max()`|
|`array_agg`|`func.array_agg()`|
|`jsonb_agg`|`func.jsonb_agg()`|

# Date and time

|PostgreSQL|SQLAlchemy|
|---|---|
|`now()`|`func.now()`|
|`current_date`|`func.current_date()`|
|`age()`|`func.age()`|
|`date_trunc()`|`func.date_trunc()`|
|`extract()`|`func.extract()`|

# String

|PostgreSQL|SQLAlchemy|
|---|---|
|`lower()`|`func.lower()`|
|`upper()`|`func.upper()`|
|`length()`|`func.length()`|
|`concat()`|`func.concat()`|
|`substring()`|`func.substring()`|
|`trim()`|`func.trim()`|

# Conditional & logical functions

|PostgreSQL|SQLAlchemy|
|---|---|
|`coalesce()`|`func.coalesce()`|
|`nullif()`|`func.nullif()`|
|`greatest()`|`func.greatest()`|
|`least()`|`func.least()`|

# String / text functions

|PostgreSQL|SQLAlchemy|
|---|---|
|`lower()`|`func.lower()`|
|`upper()`|`func.upper()`|
|`length()`|`func.length()`|
|`concat()`|`func.concat()`|
|`substring()`|`func.substring()`|
|`trim()`|`func.trim()`|

# Conditional & logic functions
|PostgreSQL|SQLAlchemy|
|---|---|
|`coalesce()`|`func.coalesce()`|
|`nullif()`|`func.nullif()`|
|`greatest()`|`func.greatest()`|
|`least()`|`func.least()`|

# Math functions

| PostgreSQL | SQLAlchemy      |
| ---------- | --------------- |
| `round()`  | `func.round()`  |
| `ceil()`   | `func.ceil()`   |
| `floor()`  | `func.floor()`  |
| `abs()`    | `func.abs()`    |
| `random()` | `func.random()` |
