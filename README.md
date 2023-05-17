# MvcCore - Example - Pig-Latin Translator For Portable Packing

[![Latest Stable Version](https://img.shields.io/badge/Stable-v5.2.0-brightgreen.svg?style=plastic)](https://github.com/mvccore/example-translator-portable/releases)
[![License](https://img.shields.io/badge/License-BSD%203-brightgreen.svg?style=plastic)](https://mvccore.github.io/docs/mvccore/5.0.0/LICENSE.md)
[![Packager Build](https://img.shields.io/badge/Packager%20Build-passing-brightgreen.svg?style=plastic)](https://github.com/mvccore/packager)
![PHP Version](https://img.shields.io/badge/PHP->=5.4-brightgreen.svg?style=plastic)

Skeleton for MvcCore [Pig-Latin Translator (`mvccore/example-translator`)](https://github.com/mvccore/example-translator) example portable packing/building.

## Instalation
```shell
# load translator portable project skeleton
composer create-project mvccore/example-translator-portable ./my-translator

# go to portable project skeleton directory
cd my-translator

# load translator project
composer create-project mvccore/example-translator ./development
```

## Packed Result Features

- **Result** is **completelly portable** - `./example-translator-portable/release/index.php`
- Result application is **currently packed in strict package mode**
- All packing configurations are included in `./build/configs` directory
- Packed with [**Packager library - mvccore/packager**](https://github.com/mvccore/packager)), all packing ways possible:
  - **PHAR file**
    - standard PHAR package with whole development directory content
  - **PHP file**
    - **strict package**
      - everything is contained in result `index.php`
      - only `.htaccess` or `web.config` are necessary to use mod_rewrite
    - **preserve package**
      - result `index.php` file contains PHP files, 
        PHTML templates but no CSS/JS/fonts or images
      - all wrapped file system functions are looking inside 
        package first, then they try to read data from HDD
    - **preserve hdd**
      - result `index.php` file contains PHP files, 
        PHTML templates but no CSS/JS/fonts or images
      - all wrapped file system functions are looking on HDD first, 
        then they try to read data from package itself
    - **strict hdd**
      - result `index.php` file contains only PHP files, 
        but PHTML templates, all CSS/JS/fonts and images are on HDD
      - no PHP file system function is wrapped

## Build

### 1. Prepare Application
- go to `./my-translator/development`
- clear everything in `./Var/Tmp/`
- uncomment `->SetCompiled(\MvcCore\Application::COMPILED_SFU)` in `./index.php`
- visit all application routes where are different JS/CSS bundles 
  groups to generate `./Var/Tmp/` content for result app
- run build process

### 2. Run Build Process

#### Linux:
```shell
# go to project build dir
cd ./my-translator/build
# run build process into single PHP file
sh make.sh
```

#### Windows:
```shell
# go to project build dir
cd ./my-translator/build
# run build process into single PHP file
make.cmd
```

#### Browser:
```shell
# visit script `make-php.php` in your project build directory:
http://localhost/my-translator/build/make-php.php
# now run your result in:
http://localhost/my-translator/release/
```
