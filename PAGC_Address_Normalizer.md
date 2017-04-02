#Using the PAGC Address Normalizer with PostGIS

Much of what is written here is excerpted from
*PostGIS in Action, 2nd Edition
Chapter 8*

Go buy a copy right now.

## A Note about Performance

`pagc_normalize_address` is an inefficient wrapper around `standardize_address`.  For the sake of speed, it is better to call `standardize_address` directly and do the extra work of mapping `staddr` results to `norm_addy` if you need to pass the results to the PostGIS geocoder.

## Install the Extension
```sh
CREATE EXTENSION address_standardizer;
```

##Testing the `pagc_normalize_address` Function
```sh
WITH A AS (
    SELECT pagc_normalize_address(a) As addy
    FROM (
        VALUES
        	('1116 Killian Blvd SE, Saint Cloud, MN'),
        	('ONE E PIMA ST STE 999, TUSCON, AZ'),
        	('4758 E Reno Road, DC 20017'),
        	('1021 New Hampshare Avenue, Washington, DC 20010'),
        	('1731 New Hamspire Ave Northwest, Washington, DC 20010'),
        	('1 Palisades, Denver, CO')
        ) X(a)
    )
    SELECT
    	(addy).address AS num,
        (addy).predirabbrev As pre,
        (addy).streetname || ' ' || (addy).streettypeabbrev As street,
        (addy).location As city,
        (addy).stateabbrev As st
	FROM A;
```
To see all the fields of the `addy` object as separate columns, replace the selected fields with `(addy).*`.