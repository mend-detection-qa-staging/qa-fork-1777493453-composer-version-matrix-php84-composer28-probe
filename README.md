# version-matrix-php84-composer28

## Feature exercised

Verifies that Mend SCA correctly detects Composer dependencies when the project is resolved under PHP 8.4 and Composer 2.8, exercising the lockfile-driven detection path against a minimal two-package graph.

## Probe metadata

| Field | Value |
|---|---|
| Pattern | version-matrix-php84-composer28 |
| PHP version | 8.4 (8.4.14 actual) |
| Composer version | 2.8 (2.8.12 actual) |
| Docker image used | `composer:2.8` |
| Note on image | `composer:2.8-php8.4` does not exist as a published tag; `composer:2.8` already bundles PHP 8.4.14 |
| plugin-api-version | 2.6.0 |
| lockfile content-hash | 2e4e654c92e88d1a7590bf23f7e74233 |

## Toolchain note

The requested tag `composer:2.8-php8.4` is not published on Docker Hub. The canonical `composer:2.8` image already ships PHP 8.4.14 (verified: `docker run --rm composer:2.8 php --version`). Use `composer:2.8` for any CI matrix that targets this probe.

Expected `.whitesource` versioning hint (for scanner config, not committed here):

```json
{
  "php": "8.4",
  "composer": "2.8"
}
```

## Expected dependency tree

- `monolog/monolog` 3.10.0 — direct production dependency, sourced from Packagist
  - `psr/log` 3.0.2 — transitive production dependency, sourced from Packagist

Platform package `php` (>=8.4) appears only in `composer.lock`'s `platform` section and must NOT appear as a detected library in Mend output.

Total installable packages: 2 (1 direct, 1 transitive). No dev packages.