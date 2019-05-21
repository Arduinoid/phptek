# Day One
## PHP Internals
## How PHP Ticks: Under the hood

### PHP's innards
- C89/99
- C++98 in ext/intl

### overall shape
- extensions
- Zend engine
- main
- SAPI *(service application programming interface)*

### Zend Engine
- Script Enginge
- Datatype and structures

### SAPI
- entrypoint
- startup, request, shutdown

>sapi/cli/php_cli.c

### The compiler
- lexer (script.php)
- parser (tokens)
    - AST (expressions and statements)
- complier (op codes and byte code)

> statements have no output where expresions evaluate to a value

### tracking file changes for caching
- rdev
- inode
- mtime

### Compiler stage access
- tokens: token_get_all()
- AST
    - ext: astkit
    - userspace: PHP-Parser
- OPCODES: 
    - phpdbg
    - VLD
    - pecl/parsekit
