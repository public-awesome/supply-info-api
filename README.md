# supply-info-api

An API for basic info about the STARS token supply.

Example response:

```json
{
  "circulatingSupply": "31511686.018182",
  "communityPool": "20008679.404121",
  "denom": "STARS",
  "totalSupply": "65336746.085331"
}
```

### How circulating supply is calculated

1. Get total supply.
2. Get community pool.
3. Subtract community pool from total supply.
4. Iterate through list of vesting amounts for large accounts and subtract the vesting amount from total supply.

This yields the circulating supply.

Vesting accounts are provided by an environment variable. See `.env.example` for an example.
