# Raw printing for Chrome

This is a Chrome app to allow browser-based Javascript code to pass raw data to a supported printer. It is aimed at developers of web-based point-of-sale systems where server-side printing is not feasable.

This has been developed for use with a USB receipt printer, with an ESC/POS command generator ([escpos-php](https://github.com/mike42/escpos-php)) providing the binary data.

## The problem

Web-based and cloud-based point-of-sale systems have their benefits, but adding printing is difficult.

- Using system printing and a vendor driver produces terrible output
- Server-side printing and 'cloud' do not mix well

This app bridges the gap, by exposing a websocket on localhost. A web-page can then retrieve binary print data from the server, and pass it to the app for printing.

## Compatibility

### Printer types

Only USB receipt printers are currently supported.

- **Networked printers** may be supported in future.
- **Serial/Parallel printers** may be accessed via a USB adaptor.
- **CUPS/IPP/Windows** shared printers are out of scope at this stage, please hook in directly via USB.

### Supported printers

Raw printing for Chrome is loaded with vendor/product ID's for the following printers:

- Epson TM-T20
- PL2305 Parallel Port
- Winbond Virtual Com Port.

If your USB printer is not listed, please create a new issue to request support. Because of the way Chrome app permissions work, please include the USB vendor ID and product ID.

### Page Description Languages

This app is simply a connector. In theory, any page description language is supported, provided that you are able to generate it, and your printer can understand it.

## Installation

This application is not yet available in the Chrome store, so the installation steps are a bit unusual:

- Under `chrome://extensions`, tick developer mode, and 'load unpacked extension', and locate this folder.
- Launch the extension, select your printer
 - If not listed, find the USB product, vendor ID, add it to `manifest.md`, and restart.
- Click print
 - If it doesn't print, check the error log and see the notes within the app for the basic things to check.
 - In particular, unload the `usblp` kernel module if applicable as it will claim the USB interface to the printer.

## Demo

A small example web-page available under `example/`, which will print a "Hello World" receipt in ESC/POS if the raw printint app is running, with an ESC/POS printer configured. Steps to try it out:

- Run the app
- Add a printer
- Open the example web page
- Click a few buttons and hope for output.

This was tested on an Epson TM-T20. 

## Contribute

Pull requests are welcome and appreciated. This project is quite new, please see the issue tracker for ideas of things to work on.

# Screenshot
![screenshot](https://github.com/receipt-print-hq/chrome-raw-print/raw/master/assets/screenshot.png)

