https://www.sitepoint.com/understanding-module-exports-exports-node-js/

[[ ## CommonJS (CJS)]]
This format is used in Node.js and uses `require` and `module.exports` to define dependencies and modules. The npm ecosystem is built upon this format.
```javascript
class User {
  constructor(name, age, email) {
    this.name = name;
    this.age = age;
    this.email = email;
  }

  getUserStats() {
    return `
      Name: ${this.name}
      Age: ${this.age}
      Email: ${this.email}
    `;
  }
}

module.exports = User;
```

And require (import) in `index.js`:
```javascript
const User = require('./user');
const jim = new User('Jim', 37, 'jim@example.com');

console.log(jim.getUserStats());
```


Exporting multiple thing from your source file:
```javascript
module.exports = {
	prop1: 'a value',
	function2: yourFunctionFromTheCode
}

// OR

module.exports.prop1 = 'a value';
module.exports.function2: yourFunctionFromTheCode;

// OR

exports.prop1 = 'a value';
exports.function2: yourFunctionFromTheCode;
```

And require (import) multiple things in `index.js`:
```javascript
const importedObject = require('./user');
const useTheImportedValue = importedObject.prop1;
const useTheImportedFunctionsReturnValur = importedObject.function2();
```
