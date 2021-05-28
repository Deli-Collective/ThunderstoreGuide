# Putting Deli 0.3 Mods on Thunderstore and r2modman
A short, step-by-step guide on how to properly package Deli 0.3 mods to be uploaded to [Thunderstore](https://h3vr.thunderstore.io/) and consumed by [r2modmanPlus](https://github.com/ebkr/r2modmanPlus) (hereafter r2modman).

# File Structure
File structure required for Deli 0.3 mods is simple. You can place the files in whatever folders you please, but the easiest is:

```
MyAuthor-MyMod.zip/
  icon.png
  manifest.json
  MyMod.deli
  README.md
```

Directory mods still exist, but using them requires a more complicated file structure:
```
MyAuthor-MyMod.zip/
  files/
    plugins/
      manifest.json
      ...
  icon.png
  manifest.json
  README.md
```

I personally recommend sticking with `.deli` files still, unless the loader you use has optimizations ready for files on disk.

## `manifest.json`
Depending on your purpose, you need to choose between 2 different manifests. I recommend starting with v2, and rewriting to v1 before uploading.

In either case, your mod name can only use:
- `a-z`
- `A-Z`
- `0-9`
- `_` (this gets rendered as a space in Thunderstore and r2modman)

### v2 (local testing)
Manifest v2 is a WIP manifest format that cannot be used with Thunderstore, but required to install mods locally via r2modman. Most of your users will be using r2modman, so you should ensure that your mod installs properly through it.

Use this template:
```json
{
    "ManifestVersion": 2,
    "AuthorName": "ChangeMe",
    "Name": "ChangeMeAuthor-ChangeMeName",
    "DisplayName": "ChangeMe",
    "Version": "ChangeMe",
    "Licence": "",
    "WebsiteURL": "",
    "Description": "",
    "GameVersion": "N/A",
    "Dependencies": [],
    "OptionalDependencies": [
		"DeliCollective-Deli-0.4.1"
	],
    "Incompatibilities": [],
    "NetworkMode": "both",
    "PackageType": "mod",
    "InstallMode": "managed",
    "Loaders": [
        "bepinex"
    ],
    "ExtraData": {}
}
```


### v1 (Thunderstore listing)
Use this template
```json
{
    "name": "ChangeMe",
    "version_number": "ChangeMeSemverOnly",
    "website_url": "ChangeMe",
    "description": "ChangeMe250CharactersMax",
    "dependencies": [
        "DeliCollective-Deli-0.4.1"
    ]
}
```

If you do not have a website URL, simply leave it blank.  
If you already have a v2 manifest, just copy the properties from it. The v1 name is *purely* the name, not including the author like v2 does.

## `README.md`
Your Thunderstore `README.md` is like your BoneTome description. Unlike BoneTome descriptions though, Thunderstore READMEs support Markdown! If you are not familiar with Markdown, it's like an easy markup language that gives your text some flavor. You can use [GitHub's guide](https://guides.github.com/features/mastering-markdown) to learn the ins and outs, but do not use GitHub Flavored Markdown (GFM) features.

If you already had a README file, make sure you remove any old installation instructions. It's confusing to users if you keep them in.

## `icon.png`
The icon must simply be 256x256, and it can (but does not need to) have transparency. If you do not have an icon, and easy fix is to use white text with your project name over a transparent background.

# Final Checklist
Ensure all of the following *before* uploading your mod to Thunderstore:

## First Release
- Your `.deli` file is up to date
- Your manifest
  - has accurate information
  - does not have a typo in the name
- Your readme
  - does not have old installation instructions
  - has accurate information
- Your icon
  - is 256x256
  - is transparent (if desired)

## Updates
- Your `.deli` file is up to date
- Your manifest
  - has a newer `version_number`

Do not be worried if you upload a manifest of the wrong format, because it will spit out an error.  
In the case that it successfully uploads but you messed up badly, you can contact a Thunderstore moderator to remove it. However, this should happen rarely.

# Examples
I've included examples of 2 of my mods in [the examples directory](examples/), unzipped for your viewing pleasure. As you can see, nothing is different between the V1 and V2 versions, except that the V2 version has a stripped down, V2 manifest.

# Sources
- [The ror2modman wiki](https://github.com/ebkr/r2modmanPlus/wiki/)
  - [Structuring your Thunderstore package](https://github.com/ebkr/r2modmanPlus/wiki/Structuring-your-Thunderstore-package)
  - [What does a ManifestV2 look like](https://github.com/ebkr/r2modmanPlus/wiki/Installing-mods-locally#what-does-a-manifestv2-look-like).
- [The Thunderstore upload page](https://h3vr.thunderstore.io/package/create/)