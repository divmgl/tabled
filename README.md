# tabled

Data-driven HTML tables with vanilla JavaScript

## Usage

```html
<table>
  <thead>
    <th>
      <td>First Name</td>
      <td>Last Name</td>
      <td>Age</td>
    </th>
  </thead>
  <tbody>
    <tr>
      <td>John</td>
      <td>Smith</td>
      <td>29</td>
    </tr>
    <tr>
      <td>Jane</td>
      <td>Doe</td>
      <td>26</td>
    </tr>
  </tbody>
</table>

<script>
  tabled.create(document.getElementByTag("table")[0]);
</script>
```

### UMD

```bash
$ npm install html-tabled
```

```javascript
var tabled = require('html-tabled');
tabled.create(document.getElementByTag("table")[0]);
```

### Schema specification

While it's very easy to specify a body for your table, you may want to
dynamically populate it using JavaScript. For this, you will need to specify
a schema.

At minimum, you will need to provide a `<thead></thead>` tag in your table.

```html
<table>
  <thead>
    <th>First Name</th> <!-- Column index 0 -->
    <th>Last Name</th>  <!-- Column index 1 -->
    <th>Age</th>        <!-- Column index 2 -->
  </thead>
</table>
```

`tabled` will use these tags to create an initial schema for the table. By
default, it will read these tags and convert them to camel case when creating
your schema. Assuming your table looks like the latter, your schema now looks
like this:

```javascript
table.headers = [ "firstName", "lastName", "age" ]
```

The table can now be populated.

```javascript
var tabled = require('html-tabled');
var table  = tabled.create(document.getElementByTag("table")[0], {
  data: [
    { firstName: "John", lastName: "Doe", age: "28" }
  ]
});
```

You can also update the table and it will adjust automatically.

```javascript
table.data = [
  { firstName: "Jane", lastName: "Doe", age: "26" }
]
```

## Tests

The test suite is on Node.js and uses PhantomJS with Mocha.

```bash
$ npm install -g
$ npm test
```
