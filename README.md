# apatch.sh
apatch was created for use in the [EmpireMinecraft](https://fork.emc.gs) and [PaperMC](https://papergit.emc.gs) projects, to help
with managing a large list of patches on top of upstream changes.

When upstream makes large changes, such as method name changes (due to deobfuscated source code), patches will begin to completely
fail to apply.

[wiggle](https://linux.die.net/man/1/wiggle) is a linux utility that can take patch file rejections and 'try harder' to apply them.

apatch first tries to apply your patch using `git am -3`. If that fails, it resets, and applies the file with `--rej` causing it to
save rejections.

Then git metadata is stripped, and wiggle is used to apply the rejections.

If wiggle can successfully apply all of the changes, all files wil be staged.
If wiggle could not apply any of the changes, the file will be left unstaged, and wiggle conflict markers added.

Now, you can focus only on the difficult parts of the patch to apply, instead of having to manually apply the entire patch by hand.

## Source
 * [apatch.sh](apatch.sh)

## Dependencies
`sed` and `wiggle` are both used

### Debian/Ubuntu
`sudo apt install wiggle`

### centos
`yum install wiggle`

### Windows
[wiggle for windows](https://github.com/neilbrown/wiggle)

### MacOS
`brew install wiggle`

### other OS
find how to obtain wiggle for your distro 

## License
Copyright Daniel Ennis (Aikar) 2015-2018

apatch.sh is licensed [MIT](LICENSE)