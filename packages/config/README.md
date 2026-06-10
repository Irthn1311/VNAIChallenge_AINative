# Config Package

## Purpose

Future shared configuration for linting, formatting, environment schema, or constants.

## What belongs here

* ESLint/Prettier shared config.
* Tailwind shared config if needed.
* Environment schema helpers.
* Non-secret constants.

## What does not belong here

* Real `.env` files.
* API keys.
* Deployment secrets.
* App-specific config that is not shared.

## Future examples

```text
eslint-config/
prettier-config/
env-schema/
constants/
```

## Notes for AI coding

Never place secrets here. Use `.env.example` for placeholder variable names only.

