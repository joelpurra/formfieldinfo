# [FormFieldInfo](https://github.com/joelpurra/formfieldinfo)

A javascript plugin used to collect information about forms in a page. This information is then used to filter out potential form problems, like missing values for radio buttons etcetera.



## Usage

```javascript
// Get fields
var fields = JoelPurra.FormFieldInfo.getFields(selector, $context);


// Gets fields based on their name.
var group = fields.group(name);

// Removes fields with empty names.
var withName = fields.removeEmptyNames();

// Gets an array of unique fields names.
var uniqueNames = fields.uniqueNames();

// Merges fields based on the array convention fieldName[0], fieldName[1], ..., fieldName[n] to fieldName[i]. The merge keeps the first instance of each unique fieldName[i] and discards the rest.
var mergedArrays = fields.mergeArrays();


// Groups fields based on their name.
var fieldGroups = fields.groups();

// Gets field names with a list of all corresponding values.
var nameValues = fieldGroups.nameValues();

// Gets field groups that have mismatched attributes within the groups. Attributes checked for mismatches are tag and type.
var withMismatches = fieldGroups.withMismatches();

```



## Examples

```javascript
// All field info
var fields = JoelPurra.FormFieldInfo
	.getFields();

// Array of field groups (excluding fields with empty names)
var fieldGroups = JoelPurra.FormFieldInfo
	.getFields()
	.removeEmptyNames()
	.mergeArrays()
	.groups()
	.toArray();

// Array of names and values only (excluding fields with empty names)
var fieldSummaries = JoelPurra.FormFieldInfo
	.getFields()
	.removeEmptyNames()
	.mergeArrays()
	.groups()
	.nameValues()
	.toArray();
```



## See also

- [extract-fields](https://github.com/joelpurra/extract-fields), scripts to extract HTML form field information from one or several webpages. Uses FormFieldInfo and runs in a phantomjs script, for automated extraction.



## Runtime dependencies
- [jQuery](http://jquery.com/)
- [underscore](http://underscorejs.org/)



## Todo
- Normalize `<select>` with options to match `<input type="checkbox" />` and type `radio`? Both are similar in form functionality, but selects only appear once in the `getFields()` results. Select fields could be expanded with each `<option>`.
- Write/fix inline documentation with [JSDoc-Toolkit](http://code.google.com/p/jsdoc-toolkit/w/list).



## License
Copyright (c) 2012, 2013 Joel Purra <http://joelpurra.com/>
All rights reserved.

When using FormFieldInfo, comply to at least one of the three available licenses: BSD, MIT, GPL.
Please see the LICENSE file for details.
