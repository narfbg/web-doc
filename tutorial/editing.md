# Editing manual sources

## Introduction
When editing or translating the manual, you have to remember some things:
- use only UTF-8 encoding
- follow the project's [style guidelines](style.php)

## Editing existing documentation
Simply open the files and edit them.

## Adding new documentation
When adding new functions or methods, there are a couple of options.

### Option A: Generating files using docgen
This is preferred way to generate files for new extensions, classes, functions
or methods using [`docgen`][docgen]. The script is found in the [doc-base][doc-base]
repository and uses reflection to generate documentation (DocBook) files.

### Option B: Copy skeleton files
This involves copying the skeleton files into the correct location:
```
cp /phpdoc/RFC/skeletons/method.xml classname/methodname.xml   #for new methods
cp /phpdoc/RFC/skeletons/function.xml functions/functionname.xml #for new functions
```

Note: *classname*, *methodname* and *functionname* are lowercased names of the
class, method, or function, respectively, not a literal file name.

Remember the extension folder [structure](structure.php) when copying those files.

## Translating documentation
The translation process is described in the [translating chapter](translating.php).

## Validating your changes
Every time you make changes to documentation sources (both English or translation),
you have to validate your changes to ensure that the manual still builds without error.
The necessary [configure.php][configure.php] script is distributed with the
[doc-base][doc-base] repository, so you should already have it. All you have
to do to validate changes is run configure.php:
```
$ cd phpdoc
$ php configure.php --with-lang={LANG}
```
If your language is English you can omit the `with-lang` argument. When the above
outputs something like "All good. Saving .manual.xml… done." then you know it validates.
You can commit your changes now.

## Commit changes
If you have the appropriate [commit karma][karma], you can commit your modified files.

## Viewing changes online
Documentation is built every night, at around 23:00 CST, then synced out to the
website mirrors. However, there is a special mirror at [docs.php.net][docs] - where
the manual is updated from sources every six hours. If any errors occured, a message
will be delivered to the appropriate mailinglist (`doc-{LANG}@lists.php.net`).

Read more about manual builds in the [builds appendix](builds.php).

The next chapter contains [style guidelines](style.php) that you are obliged to
follow. Read them carefully.

[docgen]: http://svn.php.net/viewvc/phpdoc/doc-base/trunk/scripts/docgen/
[doc-base]: http://svn.php.net/viewvc/phpdoc/doc-base/
[configure.php]: http://svn.php.net/viewvc/phpdoc/doc-base/trunk/configure.php?view=markup
[karma]: http://svn.php.net/viewvc/SVNROOT/global_avail?view=markup
[docs]: http://docs.php.net/
