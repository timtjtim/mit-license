# A permalink for your MIT License

I always forget to add an MIT-license.txt file to my projects, so I wanted to link to a single resource that would always be up to date and would always have my details online.

Why keep this to myself, there's two ways to create your *own* MIT license page:

1. Make a request to the API (details below)
2. Fork this project and send a pull request

Now I can always include http://rem.mit-license.org in all my projects which links `rem` (the cname) against my copyright holder name `Remy Sharp` - all stored in the `users` directory.

## Requesting your own MIT license page

You can fork this project, send me a pull request and wait for me to pull (which I'll do as quickly as possible) or if the user is still available you can do it yourself from the command line:

```bash
curl -d'{ "copyright": "Remy Sharp" }' https://rem.mit-license.org
```

If the `rem` user isn't taken already, then this will create the new user file on the fly and the url will be immediately available.

You can send a full JSON file to the API, not *just* the copyright, so this works too:

```bash
curl -d'{ "copyright": "Remy Sharp", "url": "http://remysharp.com", "email": "me@mysite.com", "format": "txt" }' https://rem.mit-license.org
```

If there's any problems in the automated creation, send me a pull request and it'll go live soon after.

Equally if you need to update the user file to include more details that you didn't initially include (extra fields in the next section) you will need to send a pull request on that `user.json` file via GitHub.

## The user.json file

The `users` directory contains a list of files, each representing a host on mit-license.org. The minimum requirement for the JSON is that is contains a `copyright` field - everything else is optional. Remember to ensure the `user.json` file is [valid JSON](http://jsonlint.com/).

Available fields:

* copyright (required)
* url
* email
* format
* gravatar
* version
* theme

### copyright

Create a new file and give it the name of the CNAME you want (in my case it's `rem.json`). This file contains a JSON object containing at least a `copyright` property:

```json
{
  "copyright": "Remy Sharp, http://remysharp.com"
}
```

Means I can now link to: http://rem.mit-license.org and it will show my license name (note that the date will always show the current year).

### url

In addition to the `copyright` property, if you want to make a link from the copyright text, you can include a `url` property:

```json
{
  "copyright": "Remy Sharp, http://remysharp.com",
  "url": "http://remysharp.com"
}
```

### email

You can also include a link to your email which is displayed after the copyright notice using the `email` property (note the `mailto:` is automatically added):

```json
{
  "copyright": "Remy Sharp, http://remysharp.com",
  "url": "http://remysharp.com",
  "email": "me@mysite.com"
}
```

### format

And if you want your license to appear as plain text, just add the `format` property (currently only `txt` and `html` are supported):

```json
{
  "copyright": "Remy Sharp, http://remysharp.com",
  "url": "http://remysharp.com",
  "format": "txt"
}
```

### gravatar

And if you want to show your gravatar, just add the `gravatar` boolean property:

```json
{
  "copyright": "Remy Sharp, http://remysharp.com",
  "url": "http://remysharp.com",
  "email": "me@mysite.com",
  "gravatar": true
}
```

Note that the gravatar requires the email property. You also need to check the compatibility of the chosen theme. Currently, only the default theme supports Gravatar.

### License version targeting

License version targeting allows you to link your MIT license to a specific revision in this project - therefore fixing it permanently to a specific license text.

Though I don't expect the license text to change ever, this is just some extra assurance for you.

Targeting requires the [sha from the license commit](https://github.com/remy/mit-license/commits/master/LICENSE.html). This can be specified on the URL (in your permalink) or in the JSON file.

For example: http://rem.mit-license.org/a526bf7ad1 (make sure to view-source) shows an older version of the LICENSE.html file (compared to the [latest version](http://rem.mit-license.org) - the older version didn't have the new themes).

This can also be targeted in my JSON file:

```json
{
  "copyright": "Remy Sharp, http://remysharp.com",
  "url": "http://remysharp.com",
  "version": "a526rbf7"
}
```

Note that if no version is supplied, the latest copy of the LICENSE.html will be displayed with your information included.

### Themes

If you've got an eye for design (or like me: not): you can contribute a theme by adding a CSS file to the `themes` directory. The default theme is simple and clean, but you can add your own as you like.

To use a theme, add the `theme` property to your `user.json` file, for example:

```json
{
  "copyright": "Remy Sharp, http://remysharp.com",
  "url": "http://remysharp.com",
  "theme": "flesch"
}
```

Current available themes:

* default - [preview](http://mit-license.org) (by
  [@remy](https://github.com/remy),
  [@raphaelbastide](https://github.com/raphaelbastide) &
  [@evertton](https://github.com/evertton))
* flesch - [preview](http://jsbin.com/ufefid/3) (by
  [@flesch](https://github.com/flesch))
* eula-modern - [preview](http://jsbin.com/ExiVida/1/) (by [@sauerlo](https://github.com/lsauer))
* afterdark - [preview](http://jsbin.com/ivufon/4) (by [@rmartindotco](https://github.com/rmartindotco))
* orange - [preview](http://jsbin.com/uzubos/2) (by [@kirbylover4000](https://github.com/kirbylover4000))
* plaintext - [preview](http://jsbin.com/uzubos/4) (by [@barberboy](https://github.com/barberboy))
* double-windsor - [preview](http://jsbin.com/uzubos/5/) (by [@desandro](https://github.com))
* cherry - [preview](http://jsbin.com/ufefid/5/) (by [@mustafa-x](https://github.com/mustafa-x))
* white cherry - [preview](http://jsbin.com/uzezas/2/) (by [@mustafa-x](https://github.com/mustafa-x))
* blackwood - [preview](http://jsbin.com/uzezas/) (by [@mustafa-x](https://github.com/mustafa-x))
* hipster-gray - [preview](http://jsbin.com/ivufon/10) (by [@noformnocontent](https://github.com/noformnocontent))
* xtansia - [preview](http://jsbin.com/ereren/1/) (by [@tomass1996](https://github.com/tomass1996))
* magic-mint - [preview](http://jsbin.com/obibot/1/) (by [@ekhager](https://github.com/ekhager))
* default-dark - [preview](http://jsbin.com/uhagaw/10) (by
  [@remy](https://github.com/remy),
  [@raphaelbastide](https://github.com/raphaelbastide) &
  [@evertton](https://github.com/evertton))
* black-beauty - [preview](http://jsbin.com/dovivu) (by [@evertton](https://github.com/evertton))
* silver-style - [preview](http://jsbin.com/erezijI/2) (by [@dev-dipesh](https://github.com/Dev-Dipesh))
* friendly - [preview](http://jsbin.com/hilula) (by [@evertton](https://github.com/evertton))
* opensans - [preview](http://jsbin.com/UfepUvah) (by [@pburtchaell](https://github.com/pburtchaell))
* solarized - [preview](http://jsbin.com/yimax/1) (by [@anmoljagetia](https://github.com/anmoljagetia))
* willpower - [preview](http://jsbin.com/piheyicoyi/1) (by [@willpowerart](https://github.com/willpowerart))
* rokkitt - [preview](http://jsbin.com/zudayiqeco/1) (by [@luizpicolo](https://github.com/luizpicolo))
* material - [preview](http://ahaasler.github.io/mit-license-material-theme/) (by [@ahaasler](https://github.com/ahaasler)). *Available colours: blue gray (default), red, pink, purple, deep purple, indigo, blue, light blue, cyan, teal, green, light green, lime, yellow, amber, orange, deep orange, brown and grey. To use a specific colour, add it as a dash-separated suffix on the theme name, such as `material-deep-orange`.*

## Formats & URLs

The following types of requests can be made to this project:

* [http://rem.mit-license.org/](http://rem.mit-license.org/) HTML, or the default format specified in
the json file (currently none specified on `rem`)
* [http://rem.mit-license.org/license.html](http://rem.mit-license.org/license.html) HTML
* [http://rem.mit-license.org/license.txt](http://rem.mit-license.org/license.txt) Text
* [http://rem.mit-license.org/a526bf7ad1](http://rem.mit-license.org/a526bf7ad1) a526bf7ad1 version, HTML, or the
default format specified in the json file (again, none specified for
`rem` so defaults to HTML)
* [http://rem.mit-license.org/a526bf7ad1/license.html](http://rem.mit-license.org/a526bf7ad1/license.html) a526bf7ad1 version,
HTML
* [http://rem.mit-license.org/a526bf7ad1/license.txt](http://rem.mit-license.org/a526bf7ad1/license.txt) a526bf7ad1 version,
text

The url also supports including a start year:

* [http://rem.mit-license.org/2009/](http://rem.mit-license.org/2009/) will
  show a license year range of 2009-2016 (2016 being the current year)
* [http://rem.mit-license.org/2009-2010](http://rem.mit-license.org/2009-2010/)
  allows me to force the year range
* [http://rem.mit-license.org/a526bf7ad1/2009-2010/license.txt](http://rem.mit-license.org/a526bf7ad1/2009-2010/license.txt) a526bf7ad1 version, with year range of 2009-2010 in plain text

Finally, the url also supports pinning the year

* [http://rem.mit-license.org/@2009](http://rem.mit-license.org/@2009)
  this is useful for when your software copyright should expire ([as discussed here](https://github.com/remy/mit-license/issues/771))

## Ways to contribute

Aside from code contributions that make the project better, there are a few other specific ways that you can contribute to this project.

Development contributions from:

* [remy](https://github.com/remy)
* [batuhanicoz](https://github.com/batuhanicoz)
* [georgebashi](https://github.com/georgebashi)
* [mathiasbynens](https://github.com/mathiasbynens)
* [evertton](https://github.com/evertton)

**SSL and wildcard DNS is supported by [CloudFlare](https://www.cloudflare.com) - thank you 🙏💙**

### 1. Donate domain years

I host the domain with namecheap.com and yearly renewal is $9.69 per year. If you want to contribute a year, send me a message and I'll add the years on.

Of course I'll do my best to continue running the domain and hosting, but this is your chance to contribute to the community project.

Domain contributions:

* [remy](https://github.com/remy) - 2011-2012
* [barberboy](https://github.com/barberboy) - 2012-2013
* [paulirish](https://github.com/paulirish) - 2013-2014
* [batuhanicoz](https://github.com/batuhanicoz) - 2014-2015
* [buritica](https://github.com/buritica) - 2015-2016
* [adamstrawson](https://github.com/adamstrawson) - 2016-2018 (2 years)
* [keithamus](https://github.com/keithamus) - 2018-2026 (8 years)
* [pmuellr](https://github.com/pmuellr) - 2026-2027
* [danielknell](https://github.com/danielknell) - 2027-2029 (2 years)
* [barberboy](https://github.com/barberboy) - 2029-2030
* [mostly-magic](https://github.com/mostly-magic) - 2030-2032

*Please note that the whois says 2032 as you can only have 10 active registered years with ICANN - but the domain is set to auto-renew, so it's all good :)*

### 2. Hosting

For the first 5 years mit-license.org was hosted on my own dedicated server, but I've now moved to Heroku and am paying a monthly fee. If you would like to donate **[please donate here](https://www.paypal.me/rem)** include a message and I will add your name to the credit. Hosting is currently costs $7 per month, if you want to donate in months or years, it's gratefully received ❤

Hosting contributions:

* [remy](https://github.com/remy) - 2011-2016 Apr...
* [therebelrobot](https://github.com/therebelrobot) 1 month
* [you?](https://www.paypal.me/rem)

### 3. A lick of paint

I'm a developer, I seem only capable of *grey*! If you're a designer and want to contribute a decent lick of paint on the project that would be super. Just create a new theme and send me a pull request.

## License

And of course:

MIT: http://rem.mit-license.org
