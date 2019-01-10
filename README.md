# MvcCore - Example - Pig-Latin Translator [portable]

[![Latest Stable Version](https://img.shields.io/badge/Stable-v5.0.0-brightgreen.svg?style=plastic)](https://github.com/mvccore/example-translator-portable/releases)
[![License](https://img.shields.io/badge/Licence-BSD-brightgreen.svg?style=plastic)](https://github.com/mvccore/example-translator-portable/blob/master/LICENCE.md)
[![Packager Build](https://img.shields.io/badge/Packager%20Build-passing-brightgreen.svg?style=plastic)](https://github.com/mvccore/packager)
![PHP Version](https://img.shields.io/badge/PHP->=5.4-brightgreen.svg?style=plastic)

Skeleton for MvcCore [Pig-Latin Translator (`mvccore/example-translator`)](https://github.com/mvccore/example-translator) example portable packing/building.

## Instalation
```shell
# load translator portable project skeleton
composer create-project mvccore/example-translator-portable

# go to portable project skeleton directory
cd example-translator-portable

# load translator project
composer create-project mvccore/example-translator ./development

# go to translator project directory
cd ./development

# update dependencies for translator development sources
composer update
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
- go to `example-translator-portable/development`
- clear everything in `./Var/Tmp/`
- change `$app->Run();` to `$app->Run(1);` in `./index.php`
- visit all application routes where are different JS/CSS bundles 
  groups to generate `./Var/Tmp/` content for result app
- run build process

### 2. Run Build Process

#### Linux:
```shell
# go to project build dir
cd example-translator-portable/build
# run build process into single PHP file
sh make.sh
```

#### Windows:
```shell
# go to project build dir
cd example-translator-portable/build
# run build process into single PHP file
make.cmd
```

#### Browser:
```shell
# visit script `make-php.php` in your project build directory:
http://localhost/example-translator-portable/build/make-php.php
# now run your result in:
http://localhost/example-translator-portable/release/
```
