# supply-info-api

An API for basic info about the STARS token supply.

The base route `/` returns all info in JSON:

```json
{
  "circulatingSupply": "834440089.553646",
  "communityPool": "165559530.412553",
  "denom": "STARS",
  "totalSupply": "999999619.9662"
}
```

## Other routes

- `/circulating-supply`: returns circulating supply in plain text
- `/total-supply`: returns total supply in plain text
- `/community-pool`: returns community pool size in plain text
- `/denom`: returns denom in plain text

### How circulating supply is calculated

1. Get total supply.
2. Get community pool.
3. Subtract community pool from total supply.
4. Iterate through list of vesting amounts for large accounts and subtract the vesting amount from total supply.

This yields the circulating supply.

Vesting accounts are provided by an environment variable. See `.env.example` for an example.
