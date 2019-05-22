# network_pos_printer

<div align="center"><p>A dart/flutter package to send texts silently (with simple styles like underline, bold, justification, etc.) to a network POS printer.</p></div><br>

<div align="center">
	<a href="https://flutter.io">
        <img src="https://img.shields.io/badge/Platform-Flutter-yellow.svg" alt="Platform" />
    </a>
  
   [![Pub Package](https://img.shields.io/pub/v/network_pos_printer.svg)](https://pub.dev/packages/network_pos_printer)
</div>
<br />


It lets you send the data to the printer without previewing a document (it is usually used as a receipt print).

Here an example on how to send texts and cut the ticket:
```
    NetworkPOSPrinter.connect('192.168.81.80', 9100).then((printer) {

      printer.setBold(true);
      printer.writeLine('Test bold');

      printer.resetToDefault();

      printer.setInverse(true);
      printer.writeLine('Test inverse');

      printer.resetToDefault();

      printer.setUnderline(NetworkPOSPrinterUnderline.single);
      printer.writeLine('Test underline');

      printer.resetToDefault();

      printer.setJustification(NetworkPOSPrinterJustification.center);
      printer.writeLine('Test justification');

      // space blanks before cut
      for (int i = 0; i <= 5; i++) {
        printer.writeLine();
      }

      printer.cut();

      printer.close().then((v) {
        printer.destroy();
      });
    }).catchError((error) {
      print('error : $error');
    });
```

Some printers will not accept NetworkPOSPrinterUnderline.double, only a single weight will be printed.

## TODO

* method documentation

## Support
If this package was helpful to you in delivering on your project or you just wanna to support this project, a cup of tea would be highly appreciated ;-)

[![Buy me a tea](https://www.buymeacoffee.com/assets/img/custom_images/purple_img.png)](https://buymeacoff.ee/benverstraete)