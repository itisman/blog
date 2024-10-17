# How to set Cache-Control header?

## For the index.html file

> always need to get the latest.
> `Cache-Control: no-cache`

## For the chuck js file

> always need to get the cache.
> `Cache-Control: max-age=2592000`

## For the frequently updated images

> always have short term cache and must revalidate
> `Cache-Control: max-age=3600, must-revalidate`

## For the barely updated images

> always have long term cache and stale while revaldiate
> stale while revalidate: if the cache is expired, it will still use the cache while revalidate the cache.
> `Cache-Control: max-age=2592000, stale-while-revalidate=2592000`
