## Create realtime web-page index

#### Install
Use global variable
```
<script src = "https://cdn.jsdelivr.net/npm/foxql/build/foxql.min.js"></script>
```

``` javascript
const client = new foxql.client();
```
or
```
npm install foxql
```
``` javascript
import foxql from 'foxql';
const client = new foxql();
```

#### Push Data

``` javascript
client.database.useCollection('webPage').addDoc({
    title : document.title,
    description : document.querySelector('meta[name="description"]').content // change this selector on your using dom element.,
    url : window.location.href,
    domain : window.location.hostname
});

```


### Using 

``` html
    <html>
        <head>
            <title>Your web site</title>
            <meta name="description" content="Example page description">
        </head>
        <body>


            <!-- Javascripts -->
            <script src = "https://cdn.jsdelivr.net/npm/foxql/build/foxql.min.js"></script>
            <script>
                const client = new foxql.client();
                
                client.pushEvents([
                    'onSearch'
                ])

                client.openNativeCollections();

                client.open();

                client.database.useCollection('webPage').addDoc({
                    title : document.title,
                    description : document.querySelector('meta[name="description"]').content, // change this selector on your using dom element.
                    url : window.location.href,
                    domain : window.location.hostname
                });
            </script>
        </body>
    <html>
```


