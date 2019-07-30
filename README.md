Simple extension to read barcodes from images

## Basic usage:

    <?php
    /* Create new image object */
    $image = new ZBarCodeImage("test.jpg");

    /* Create a barcode scanner */
    $scanner = new ZBarCodeScanner();

    /* Scan the image */
    $barcode = $scanner->scan($image);

    /* Loop through possible barcodes */
    if (!empty($barcode)) {
    	foreach ($barcode as $code) {
    		printf("Found type %s barcode with data %s\n", $code['type'], $code['data']);
    	}
    }
    ?>

The EAN13 image in the tests/ directory is from 
http://en.wikipedia.org/wiki/File:Ean-13-5901234123457.png

## Since 
For some reason C-API of zbar (/usr/include/zbar.h) now requires PATCH argument in the `zbar_version` function and needs to be accomodated:

```c
extern int zbar_version(unsigned *major,
                        unsigned *minor,
                        unsigned *patch);
```


## Dependencies:

ZBar 
http://zbar.sourceforge.net/

ImageMagick
http://www.imagemagick.org/