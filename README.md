[![xtypejs Logo](http://xtype.js.org/assets/img/xtypejs-logo.png)](http://xtype.js.org/) <a href="https://travis-ci.org/lucono/xtypejs"><img align="right" src="https://travis-ci.org/lucono/xtypejs.svg?branch=master"></a>
#### Elegant, highly efficient data validation for JavaScript

---

### Overview

- Provides concise, performant, readable, data and type validation for JavaScript, using close to 40 highly efficient, data-validating pseudo types.
- Improves application efficiency and readability by unifying the most basic but common data and type validations in JavaScript apps, into single, concise, highly optimized operations.
- Employs bitwise operations, data pre-processing, and memory-efficient memoization for fast, robust performance in small and large apps and libraries.
- Ready for nodejs, requirejs, and regular script tag.
- Website &ndash; **[xtype.js.org](http://xtype.js.org)**

### Go from this:

```js
function searchEmployees(value) {
    if (typeof value === 'string') {
         if (value.trim().length > 1) {
            return EmployeeDB.searchByName(value);
        } else if (value.trim().length === 1) {
            return EmployeeDB.searchByMiddleInitial(value);
        } else {
            return { error: 'Invalid search value supplied' };
        }
    } else if (typeof value === 'object' && value !== null) {
        if (Object.keys(value).length === 1) {
            return EmployeeDB.searchByFieldValuePair(value);
        } else if (Object.keys(value).length > 1) {
            return { error: 'Search by multiple fields not supported' };
        } else {
            return { error: 'Invalid search value supplied' };
        }
    } else if (typeof value === 'number') {
        if (!isNaN(value) && isFinite(value) && value > 0 && value % 1 === 0) {
            return EmployeeDB.searchByEmployeeNumber(value);
        } else {
            return { error: 'Invalid employee number supplied' };
        }
    } else if (typeof value === 'undefined' || value === null) {
        return { error: 'No search value supplied' };
    } else {
        return { error: 'Invalid search value supplied' };
    }
}
```

### To concise, performant, readable, data validation:

```js
function searchEmployees(value) {
    switch (xtype.which(value, 'str2+ str1 int+ obj1 obj2+ num nil')) {
        case 'str2+':
            return EmployeeDB.searchByName(value);
        case 'str1':
            return EmployeeDB.searchByMiddleInitial(value);
        case 'int+':
            return EmployeeDB.searchByEmployeeNumber(value);
        case 'obj1':
            return EmployeeDB.searchByFieldValuePair(value);
        case 'obj2+':
            return { error: 'Search by multiple fields not supported' };
        case 'num':
            return { error: 'Invalid employee number supplied' };
        case 'nil':
            return { error: 'No search value supplied' };
        default:
            return { error: 'Invalid search value supplied' };
    }
}
```

## &nbsp;

#### Links

- [Website](http://xtype.js.org)
- [Examples And Guide](http://xtype.js.org/?doc=guide)
- [API Docs](http://xtype.js.org/?doc=api)

#### Installation

See [here](http://xtype.js.org/?doc=getit).

#### Dependencies

None.


#### Build / Test

See [here](https://github.com/lucono/xtypejs/tree/master/test).


#### License

MIT license.


#### Website

Visit the website for usage guide, examples, API docs, and installation.

#### **[xtype.js.org](http://xtype.js.org/)**
