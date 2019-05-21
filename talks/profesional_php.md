# OOP
## collaboration 

### Interfaces
this is the contract to interacting with things

### Polymorphism
something that can be used in different contexts.

---------------------

## Dependency Management
**Composer**

### what is dependency Management?
- it handles packages your application uses directly as well as the packages it use

### Finding and using packages
- use *[packagist](https://packagist.org)*

### Versioning

- semver: **1.2.1** (*major*.*minor*.*patch*)

### Consitent Environments
- `composer.lock`

### Autoloading
[PSR-4](https://www.php-fig.org/psr/psr-4/), [PSR-0](https://www.php-fig.org/psr/psr-0/), classmap and files

**[Auto Loading Basics](https://getcomposer.org/doc/01-basic-usage.md)**

- **PSR-4** uses a *src* directory that will automatically make available your files that get installed there
- **PSR-0** uses a map that requires you to add locations and reload with each new addition

### Create your own Package
> every project is a package

**structure of the library**
- src
    - hello-world
        - Greeting.php
- composer.json
- composer.lock

**composer.json**
```json
{
    "name": "acme/blog",
    "repository": [
        "type": "vcs",
        "url": "github.com/blah/hello-world"
    ]
}
```