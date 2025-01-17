## Summary

**-> [Back to Index](./README.md)**

* [Incrementing Version Numbers](#incrementing-version-numbers)
* [Pre-release and Build Metadata](#pre-release-and-build-metadata)
* [Version Comparison](#version-comparison)

Semantic Versioning follows the format of `MAJOR.MINOR.PATCH`, with optional pre-release and build metadata.

## Incrementing Version Numbers

---

### ****Major Version (MAJOR)****

- Indicates incompatible API changes.
- Increment when you make incompatible changes in the public API.
- Reset MINOR and PATCH to 0.
- Example: `1.0.0` -> `2.0.0`

### Minor Version (MINOR)

- Indicates added functionality in a backward-compatible manner.
- Increment when you add new features or enhance functionality in a backward-compatible manner.
- Reset PATCH to 0.
- Example: `1.0.0` -> `1.1.0`

### ****Patch Version (PATCH)****

- Indicates backward-compatible bug fixes.
- Increment when you make backward-compatible bug fixes.
- Example: `1.0.0` -> `1.0.1`

[Back to top](#summary)

## ****Pre-release and Build Metadata****

---

### ****Pre-release Version****

- Allows for indicating pre-release versions.
- Use a hyphen followed by a series of dot-separated identifiers.
- Example: `1.0.0-alpha`, `1.0.0-beta.2`

### ****Build Metadata****

- Provides additional build information.
- Use a plus sign followed by a series of dot-separated identifiers.
- Example: `1.0.0+20130313144700`

[Back to top](#summary)

## Version Comparison

---

### ****Precedence Order****

- Precedence is determined by comparing individual components from left to right.
- Numeric components are compared numerically, and alphanumeric components are compared lexically.
- Example: `1.0.0-alpha` < `1.0.0-beta` < `1.0.0`

[Back to top](#summary)