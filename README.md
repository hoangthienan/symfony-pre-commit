# A Symfony pre commit hook
==========================
Checks in our pre-commit hook 

* Syntax check with php lint (“php -l”): We check every committed file has a valid PHP syntax.
* Sync check of composer.json and composer.lock files: We check these two files are committed together in order to avoid committing the json but not the lock and generate some issue to another developers.
* PHP CS Fixer check: With the –dry-run parameter it does not fix, just say what the problems are. With the –fixers parameter you can control what fixers you want to execute.
* PHP Code Sniffer check: Same as before, but another rule that checks another rules.
* PHPMD: We have enabled the controversial rules.
* Unit Testing check: We run around 3.000 tests right now.

**INSTALLATION:**

[![Latest Stable Version](https://poser.pugx.org/hgtan/symfony-pre-commit/v/stable.svg)](https://packagist.org/packages/hgtan/symfony-pre-commit) [![Total Downloads](https://poser.pugx.org/hgtan/symfony-pre-commit/downloads.svg)](https://packagist.org/packages/hgtan/symfony-pre-commit) [![Latest Unstable Version](https://poser.pugx.org/hgtan/symfony-pre-commit/v/unstable.svg)](https://packagist.org/packages/hgtan/symfony-pre-commit) [![License](https://poser.pugx.org/hgtan/symfony-pre-commit/license.svg)](https://packagist.org/packages/hgtan/symfony-pre-commit)

[![SensioLabsInsight](https://insight.sensiolabs.com/projects/77614f76-617a-4288-8e75-2ad38037ed89/big.png)](https://insight.sensiolabs.com/projects/77614f76-617a-4288-8e75-2ad38037ed89)

This library is available on [Packagist](https://packagist.org/packages/hgtan/symfony-pre-commit). 
The recommended way to install this library is through [Composer](http://getcomposer.org):

add hgtan/symfony-pre-commit as a composer dependency.

composer.json
```bash
"require-dev": {
    ...
    "hgtan/symfony-pre-commit": "dev-master"
}
php composer.phar update hgtan/symfony-pre-commit
```
**USAGE:**

When a developer clones the project, it just needs to:

```
-- linux
cd [project]
rm -rf .git/hooks
ln -s ../vendor/hgtan/symfony-pre-commit/hooks .git/hooks

-- windows
cd [project]
rd .git\hooks
mklink /D /J .git\hooks vendor\hgtan\symfony-pre-commit\hooks
```

Remembering to set up the hooks

```
"scripts": {
    "pre-update-cmd": "Hgtan\\Composer\\Script\\Hooks::checkHooks",
    "pre-install-cmd": "Hgtan\\Composer\\Script\\Hooks::checkHooks"
}
```

Have a look at [Write your git hooks in PHP and keep them under git control](http://bit.ly/git-hooks-in-php) for more usage information.
