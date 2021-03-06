![Imgur](http://i.imgur.com/gwjpUqe.png "logo")


[![npm version](https://badge.fury.io/js/ng2-easy-table.svg)](https://badge.fury.io/js/ng2-easy-table)
[![Build Status](https://travis-ci.org/ssuperczynski/ng2-easy-table.svg?branch=master)](https://travis-ci.org/ssuperczynski/ng2-easy-table)

Proudly powered by [![Imgur](http://i.imgur.com/qbbb6ah.png)](http://espeo.eu/)

Beta version. Component may contains some issues, but feel free to add it to your page!

<h3><a href="http://angular2-table.espeo.pl/" target="_blank">DEMO</a></h3>

This table always will be easy to add to every page.

#Installation

1. `npm install ng2-easy-table`
2. component

```typescript
import {Component}     from 'angular2/core';
import {bootstrap}     from 'angular2/platform/browser';
import {AppComponent}  from 'ng2-easy-table/app/app.component';
import {ConfigService} from "./config-service";

@Component({
  selector: 'app',
  directives: [AppComponent],
  providers: [ConfigService],
  template: `
    <ng2-table [configuration]="configuration"></ng2-table>
  `
})
export class App {
  constructor(private configuration:ConfigService) {}
}

bootstrap(App, [ConfigService]);
```

3. config service:

```typescript
import {Injectable} from "angular2/core";
@Injectable()
export class ConfigService {
    public searchEnabled = true;
    public orderEnabled = true;
    public globalSearchEnabled = false;
    public footerEnabled = false;
    public paginationEnabled = false;
    public exportEnabled = false;
    // etc
}
```
![table](http://i.imgur.com/yqlYtVR.png "table")

###Available config settings:

| field               |      type      |  options   | example                                     |
|---------------------|:--------------:|:----------:|---------------------------------------------|
| searchEnabled       | bool           | true false | public searchEnabled = true;                |
| exportEnabled       | bool           | true false | public exportEnabled = true;                |
| orderEnabled        | bool           | true false | public orderEnabled = true;                 |
| paginationEnabled   | bool           | true false | public paginationEnabled = true;            |
| globalSearchEnabled | bool           | true false | public globalSearchEnabled = true;          |
| resourceUrl         | string         |            | public resourceUrl = "api/v1/persons.json"; |


If you have problem with display table, add this to `System.config`
```html
<script>
        System.config({
            map: {
                'ng2-easy-table': 'node_modules/ng2-easy-table/dist'
            },
            packages: {
                app: {
                    format: 'register',
                    defaultExtension: 'js'
                },
                'ng2-easy-table': {
                    format: 'register',
                    defaultExtension: 'js'
                }
            }
        });
        System.import('app/index.component')
                .then(null, console.error.bind(console));
    </script>

```
run tests by typing:
`node_modules/karma/bin/karma start karma.conf.js --single-run`