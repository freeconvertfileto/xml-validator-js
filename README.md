# XML Validator

Check XML well-formedness instantly using the native DOMParser API and report element count or the first parse error, entirely in the browser.

**Live Demo:** https://file-converter-free.com/en/developer-tools/xml-validator-online

## How It Works

The input string is passed to `DOMParser.parseFromString(text, 'application/xml')`. All major browsers insert a `<parsererror>` element when parsing fails — the code checks for this with `doc.querySelector('parsererror')` and extracts the first line of the error message for display. On success, `document.getElementsByTagName('*').length` counts the total number of elements in the parsed document, and `documentElement.nodeName` retrieves the root tag name. The validator checks structural well-formedness only (properly nested tags, balanced open/close pairs, valid attribute syntax as per XML 1.0); it does not perform DTD or XSD schema validation.

## Features

- Well-formedness validation via `DOMParser` `parsererror` detection
- Reports root element name and total element count on success
- Displays first parse error line on failure
- Synchronous, no network access after page load

## Browser APIs Used

- DOMParser (`parseFromString` with `application/xml`)

## Code Structure

| File | Description |
|------|-------------|
| `index.html` (inline script) | `DOMParser.parseFromString`, `doc.querySelector('parsererror')` check, `getElementsByTagName('*').length` count, `documentElement.nodeName` root name |

## Usage

| Element ID / Selector | Purpose |
|----------------------|---------|
| XML input textarea | XML document to validate |
| Validate button | Run validation |
| Result display | Valid (element count + root) or Invalid (error message) |

## License

MIT
