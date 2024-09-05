
# Worldwide Currencies with Details in JSON

This repository contains a JSON file (`currencies.json`) with detailed information about worldwide currencies, including their ISO 2-character country codes, symbols, names, exchange rates, and more.

## File Contents

The `currencies.json` file includes an array of objects, each representing a currency. Each object has the following properties:

- `name`: The full name of the currency (e.g., "United States Dollar").
- `name_plural`: The plural form of the currency name (e.g., "United States dollars").
- `symbol`: The currency symbol (e.g., "$").
- `symbol_native`: The native symbol used in the respective country.
- `decimals`: The number of decimal digits used in the currency.
- `rounding`: The rounding convention used (if any).
- `flag`: The path to the flag image of the country associated with the currency.
- `code`: The ISO 3-character currency code.
- `country`: The ISO 2-character code of the country where the currency is used.
- `country_name`: The full name of the country.
- `exchange_rate`: The current exchange rate of the currency relative to a base currency (e.g., USD).

If you need the flags, they can be found here: https://github.com/HthSolid/flags-worldwide-svg

### Example entry:
```json
{
    "name": "United Arab Emirates Dirham",
    "name_plural": "UAE dirhams",
    "symbol": "د.إ",
    "symbol_native": "د.إ.‏",
    "decimals": 2,
    "rounding": 0,
    "flag": "/assets/paymoi/Flags/ae.svg",
    "code": "AED",
    "country": "AE",
    "country_name": "United Arab Emirates",
    "exchange_rate": 1.16
}
```

## How to Use

### Loading the JSON File

You can load and use the JSON file in various programming languages. Below are examples in JavaScript and Python.

## JavaScript

Using Node.js to read and parse the JSON file:

```javascript
const fs = require('fs');

// Read the JSON file
fs.readFile('currencies.json', 'utf8', (err, data) => {
    if (err) {
        console.error(err);
        return;
    }

    // Parse JSON data
    const currencies = JSON.parse(data);

    // Example: Print all currencies and their exchange rates
    currencies.forEach(currency => {
        console.log(`Currency: ${currency.name}, Exchange Rate: ${currency.exchange_rate}`);
    });
});
```

## Python

Using Python to read and parse the JSON file:

```python
import json

# Read the JSON file
with open('currencies.json', 'r') as file:
    currencies = json.load(file)

# Example: Print all currencies and their exchange rates
for currency in currencies:
    print(f"Currency: {currency['name']}, Exchange Rate: {currency['exchange_rate']}")
```

### Integrating with Your Application

You can integrate this JSON file into your application to display or calculate currency conversion values, display currency symbols, or provide localized currency formatting.

## Example Usage

### JavaScript

```javascript
function formatCurrency(amount, currencyCode) {
    // Find the currency object by ISO currency code
    const currencyInfo = currencies.find(c => c.code === currencyCode);
    if (!currencyInfo) {
        throw new Error('Currency not found');
    }

    const { symbol_native, decimals } = currencyInfo;

    // Format the number using the currency's decimal digits
    return `${symbol_native}${amount.toFixed(decimals)}`;
}

// Example: Format an amount for the Australian Dollar
const formattedAmount = formatCurrency(1234.56, 'AUD');
console.log(formattedAmount); // "AU$1234.56"
```

### Python

```python
def format_currency(amount, currency_code):
    # Find the currency object by ISO currency code
    currency_info = next((c for c in currencies if c['code'] == currency_code), None)
    if not currency_info:
        raise ValueError('Currency not found')

    symbol_native = currency_info['symbol_native']
    decimals = currency_info['decimals']

    # Format the amount using the currency's decimal digits
    formatted_amount = f"{symbol_native}{amount:.{decimals}f}"
    return formatted_amount

# Example: Format an amount for the Australian Dollar
formatted_amount = format_currency(1234.56, 'AUD')
print(formatted_amount)  # "AU$1234.56"
```

# Contributing
If you find any inaccuracies or want to add more currencies, feel free to open a pull request. Contributions are welcome!

# License
This project is licensed under the MIT License.

# Acknowledgements
The data in this JSON file is compiled from various sources to provide accurate and up-to-date information on worldwide currencies.
