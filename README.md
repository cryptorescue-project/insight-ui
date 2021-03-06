# Insight UI

A CryptoRescue blockchain explorer web application service for [CryptoRescueCore Node](https://github.com/cryptorescue-project/cryptorescuecore-node) using the [Insight API](https://github.com/cryptorescue-project/insight-api).

## Quick Start

Please see the guide at [https://bitcore.io/guides/full-node](https://bitcore.io/guides/full-node) for information about getting a block explorer running. This is only the front-end component of the block explorer, and is packaged together with all of the necessary components in [CryptoRescueCore](https://github.com/cryptorescue-project/cryptorescuecore).

## Getting Started

To manually install all of the necessary components, you can run these commands:

```bash
npm install -g cryptorescuecore-node
cryptorescuecore-node create mynode
cd mynode
cryptorescuecore-node install insight-api
cryptorescuecore-node install insight-ui
cryptorescuecore-node start
```

Open a web browser to `http://localhost:3001/insight/`

## Development

To run Insight UI locally in development mode:

Install bower dependencies:

```
$ bower install
```

To compile and minify the web application's assets:

```
$ grunt compile
```

There is a convenient Gruntfile.js for automation during editing the code

```
$ grunt
```

## Multilanguage support

Insight UI uses [angular-gettext](http://angular-gettext.rocketeer.be) for multilanguage support.

To enable a text to be translated, add the ***translate*** directive to html tags. See more details [here](http://angular-gettext.rocketeer.be/dev-guide/annotate/). Then, run:

```
grunt compile
```

This action will create a template.pot file in ***po/*** folder. You can open it with some PO editor ([Poedit](http://poedit.net)). Read this [guide](http://angular-gettext.rocketeer.be/dev-guide/translate/) to learn how to edit/update/import PO files from a generated POT file. PO file will be generated inside po/ folder.

If you make new changes, simply run **grunt compile** again to generate a new .pot template and the angular javascript ***js/translations.js***. Then (if use Poedit), open .po file and choose ***update from POT File*** from **Catalog** menu.

Finally changes your default language from ***public/src/js/config***

```
gettextCatalog.currentLanguage = 'es';
```

This line will take a look at any *.po files inside ***po/*** folder, e.g.
**po/es.po**, **po/nl.po**. After any change do not forget to run ***grunt
compile***.


## Note

For more details about the [Insight API](https://github.com/cryptorescue-project/insight-api) configuration and end-points, go to [Insight API GitHub repository](https://github.com/cryptorescue-project/insight-api).

## Contribute

Contributions and suggestions are welcomed at the [Insight UI GitHub repository](https://github.com/cryptorescue-project/insight-ui).

## PSA for Pool Hosts
```PSA for Pool Operators:

Yiimp Pool operators:
You can customize your coinbase value to identify your pool on the blockchain!
Why? this will allow block explorers to drive traffic to your pool!
Open up */stratum/coinbase.cpp in your favorite editor
Edit the  hex value from this line: "char script2[32] = "7969696d7000"; // "yiimp\0" in hex ascii"
https://github.com/tpruvot/yiimp/blob/next/stratum/coinbase.cpp#L82

Procedure:
1)the name MUST be no more than 15 ASCII characters in length
2)convert your name to hex with https://www.rapidtables.com/convert/number/ascii-to-hex.html
	for example: hextestforpool becomes 68 65 78 74 65 73 74 66 6f 72 70 6f 6f 6c
3)You MUST append 00 to the number you recieved in step 2
	for example: 68657874657374666f72706f6f6c becomes 68657874657374666f72706f6f6c00
4)replace 7969696d7000 with your number on line(82): "char script2[32] = "7969696d7000"; // "yiimp\0" in hex ascii"
5) recompile yiimp source code
6) DM me(Mafalate) on discord, the (up to) 15 ASCII characters you chose, and I'll add it to the explorer
7)profit!


NOMP Pool operators:
You can customize your coinbase value to identify your pool on the blockchain!
Why? this will allow block explorers to drive traffic to your pool!
open up */node_modules/stratum-pool/lib/transactions.js in your favorite editor
Edit the string from this line: "var scriptSigPart2 = util.serializeString('/nodeStratum/');
https://github.com/foxer666/node-stratum-pool/blob/master/lib/transactions.js#L185

Procedure:
1)replace /nodeStratum/ with the name(any length) of your pool. The forward slashes are optional, but improve readability
2)Be sure to leave the leave the single quotation marks in place
	for example: change ('/nodeStratum/') to ('/CPR Pool/')
3)Restart NOMP 
4)DM me(Mafalate) on discord, what you changed the value to, and I'll add it to the explorer
5)Profit!
```

## License
(The MIT License)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
