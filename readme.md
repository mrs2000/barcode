# Barcode coder

[Documentation](http://barcode-coder.com/en/)

### Installation
The preferred way to install this extension is through [composer](http://getcomposer.org/download/).
Either run
```
php composer.phar require --prefer-dist mrssoft/barcode "*"
```
or add
```
"mrssoft/barcode": "*"
```
to the require section of your `composer.json` file.

### Usage
```php
    public function actionBarcode($ean13 = null, $width = 250, $height = 100)
    {
        $im = imagecreatetruecolor($width, $height);
        $black = imagecolorallocate($im, 0x00, 0x00, 0x00);
        $white = imagecolorallocate($im, 0xff, 0xff, 0xff);
        imagefilledrectangle($im, 0, 0, $width, $height, $white);

        if (!empty($ean13)) {
            Barcode::gd($im, $black, $width / 2, $height / 2, 0, 'ean13', $ean13, 2, $height);
        }

        header('Content-Type: image/png');
        imagepng($im);
        imagedestroy($im);
        eixt();
    }
```