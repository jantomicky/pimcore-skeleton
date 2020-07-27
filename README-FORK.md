# Pimcore Skeleton Fork

## Usage
Clone the repository:
```
git clone git@github.com:youruser/pimcore-skeleton.git
```
Add the original repository as "upstream" remote:
```
git remote add upstream https://github.com/pimcore/skeleton
```
Verify:
```
git remote -v
```
Fetch:
```
git fetch upstream
```
**Update the original code from upstream:**
```
git checkout master && git rebase upstream/master
```

## Patching
See <https://github.com/cweagans/composer-patches> for details.

Copy the original file in the same location, add a postfix (modified, fixed,…):
```
cp ./vendor/path/to/your/file.php ./vendor/path/to/your/file-modified.php
```
Create a diff file, save it as a patch:
```
diff -u ./vendor/path/to/your/file.php ./vendor/path/to/your/file-modified.php > ./patches/file.php.patch
```
Open the patch file and change the paths on the first two lines from `vendor/org/package/src` to just `../src`, for example from
```
vendor/pimcore/pimcore/bundles/AdminBundle/…
```
to
```
../bundles/AdminBundle/…
```
Finally, reference the patch in the `composer.json` file grouped by `organization/package`:
```
"extra": {
    "patches": {
        "pimcore/pimcore": {
            "basepage option for staticroutes 1/4": "./patches/file.php.patch"
        }
    }
}
```
