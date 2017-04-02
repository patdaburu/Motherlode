#Normalizing Addresses Using `standardize_address`



Go buy a copy right now.

The `standardize_address` function allows you to specify the *lexicon*, *gazetteer*, and *rules* table to use when standardizing addresses.

To read more about this function, check out *PostGIS in Action, 2nd Edition, Section 8.4*.

For more details about the *rules* table, refer to [Address Standardizer Rules Table Structure](<http://postgis.net/docs/manual-dev/rulestab.html>) in the PostGIS manual.

##Install the Extension
```sh
CREATE EXTENSION address_standardizer;
```

##Testing the `standardize_address` Function
```sh
WITH A(a) AS (
    VALUES
    	('1116 Killian Blvd SE, Saint Cloud, MN'),
       	('ONE E PIMA ST STE 999, TUSCON, AZ'),
        ('4758 E Reno Road, DC 20017'),
        ('1021 New Hampshare Avenue, Washington, DC 20010'),
        ('1731 New Hamspire Ave Northwest, Washington, DC 20010'),
        ('1 Palisades, Denver, CO')
    )
SELECT (s).house_num, (s).name, (s).predir, (s).suftype, (s).sufdir
FROM (
	SELECT standardize_address(
		'pagc_lex', 'pagc_gaz', 'pagc_rules', a
	) AS s FROM A
) AS X;
```
The output of the function is a composite type object called `staddr`, which is similar to the `norm_addy` composte type.  If you want to see all the fields, don't itemize but substitute in `(s).*`.

## References

Much of what is written here is excerpted from
*PostGIS in Action, 2nd Edition
Chapter 8*