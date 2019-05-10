## DESCRIPTION

Fork of Shancarter's Mr-Data-Converter project, to be edited for DMS specific config file creation.  Will take excel with custom field mappings and generate the associated XML to be used within dmsconfig.xml

## How to use
* [Download](https://github.com/laszlo462/DMSConfigBuilder-Electron/releases) and run the portable .exe to open the Config Builder tool.
    * If cloning this repo, you can build the .exe following the Dev and Build steps further below.
* Copy the 3 columns (including the header columns) from the factorymap.xls and paste into the top box.
* The output below can then be pasted into dms-config.xml after the initial Powerscribe connectivity has been verified within the DMS web UI.

### To update dms-config.xml:
* Open IIS and stop the DataMappingService web site.
* Open C:\DataMappingService\config\dms-config.xml within a text editor.
* If initial PowerScribe connectivity has been established, there should be XML elements populated for
~~~ xml
<ConnectionAttributes>
~~~
as well as a hashed password.
* Paste the Config Builder XML output (likely beginning with <DataMaps>) and overwrite the current
~~~ xml
<DataMaps>


</DataMaps>
~~~
tags.
* Save the changes and restart the DataMappingService website.
* Log into the DataMappingService webiste and verify population of the customer specific PS360 Custom Fields.

## NOTE
Whitespacing may not be accurate upon pasting into dms-config.xml file.  Be sure to verify this as it may affect how the software will pick these up.  Will look to resolve the issue upon initial live testing if this occurs.


## Dev
Requires node.js to be installed.
```
$ npm install
```

### Run

```
$ npm start
```

### Build

```
$ npm run-script dist
```

Builds Windows portable .exe distribution, using [electron-builder](https://github.com/electron-userland/electron-builder).


## License

MIT © [Steve Szabo](https://github.com/laszlo462)
