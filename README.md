sql-countries
=============

The `countries.sql` file is an SQL script which creates a table containing
a list of countries, their ISO codes, an indicator of using the metric system,
ordering of fields in date strings and if they are using the 24 hour time
system.

This is a somewhat "lazy" list, mostly with regards to date and time formats,
created using the following guidelines:

 * Use a relatively common-sense list of countries, not necessarily very
   official (e.g. this list contains Taiwan, Hong Kong and Myanmar...).
 * Use DMY as the default date format, even for countries which officially
   offer a choice of other formats (i.e. if a country standardizes both
   DMY and YMD, use DMY).
 * Use 24 as the default if a country standardizes on both 24h and 12h time.

The rest of the data are official and unambigous.

The table definition is as follows:

```SQL
CREATE TABLE countries (
  name varchar(50) NOT NULL,
  iso2 varchar(2) NOT NULL PRIMARY KEY,
  iso3 varchar(3) NOT NULL,
  msystem char(1) NOT NULL DEFAULT 'M',         -- Metric system: M for Metric, I for imperial
  dformat char(3) NOT NULL DEFAULT 'DMY',       -- Date format: DMY or MDY or YMD
  tformat char(2) NOT NULL DEFAULT '24'         -- Time format: 24 or 12
);
```

The 2-letter ISO code is the primary key, and it should be used when storing
country data in other tables.
