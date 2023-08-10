---
sidebar_position: 9
---

# Redirects

---
# A few notes on redirects
You can use any valid URI for your redirect URIs. At least one redirect URI is required for each or DEV, TEST and PROD. If you don't know the redirect URI for one or more of these environments, you may provide any valid URI for now and change it later. We suggest something like 'http://localhost:1000'

## Valid Redirect Format

In CSS app, the allowed URI syntax consists of two parts with `://` in the middle:
- `<scheme>://<path>`
- `scheme`: the following rules must be met:
    1. must be greater than one character.
    2. must start with an alphabet character followed by optional characters (`alphabets`, `hyphens(-)`, and `periods(.)`)
- `path`: a minimum of one character is required except for `white spaces` and `#`.
- For the `dev` and `test` redirect URIs please refer to the regular expression `/^[a-zA-Z][a-zA-Z-\.]*:\/\/\S+/`
- For `prod` URIs there are additional restrictions on wildcards (*) please refer to the regular expression `/^[a-zA-Z][a-zA-Z-\.]*:\/\/([^*\s]+\/\S*|[^*\s]*[^*\s]$)/`.  This prevents domain level wildcards like `https://www.example.com*` while accepting non-domain level wildcards `https://www.example.com/*`.
* We made an exception to allow wildcard (*) in the dev, and test environments to satisfy the various development processes.