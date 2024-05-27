# Currency-Converter
Here's a README file for your GitHub repository containing the `index.html` and `app.js` files for the Currency Converter project:

```markdown
# Currency Converter

This repository contains the code for a simple Currency Converter web application. The application allows users to convert amounts between different currencies using real-time exchange rates.

## File Structure

- `index.html`: The main HTML file that contains the structure and layout of the Currency Converter web page.
- `app.js`: The JavaScript file that handles the functionality of fetching exchange rates and performing the currency conversion.

## Features

- **Currency Selection**: Users can select the currencies they want to convert from and to using dropdown menus.
- **Real-Time Conversion**: The application fetches real-time exchange rates from an external API and performs the conversion instantly.
- **User Input**: Users can enter the amount they want to convert, and the converted amount is displayed immediately.

## Usage

To use the Currency Converter, follow these steps:

1. **Clone the Repository**: Clone this repository to your local machine using the following command:
   ```sh
   git clone https://github.com/yourusername/currency-converter.git
   ```
   
2. **Open the HTML File**: Navigate to the repository folder and open the `index.html` file in your web browser.

3. **Select Currencies**: Use the dropdown menus to select the currencies you want to convert from and to.

4. **Enter Amount**: Enter the amount you want to convert in the input field.

5. **Convert**: Click the "Convert" button to see the converted amount.

## Dependencies

- The application relies on the [Frankfurter API](https://www.frankfurter.app/) to fetch real-time currency exchange rates.

## Example

Here's how the Currency Converter works:

1. Select the currency you want to convert from (e.g., USD).
2. Select the currency you want to convert to (e.g., EUR).
3. Enter the amount you want to convert (e.g., 100).
4. Click "Convert" to see the converted amount.

## Code Overview

### index.html

The HTML file provides the structure of the Currency Converter web page, including the input fields and buttons.

### app.js

The JavaScript file contains the following key functions:

- **displayDropDown**: Fetches the list of available currencies and populates the dropdown menus.
- **convert**: Fetches the exchange rate for the selected currencies and calculates the converted amount.

```javascript
let select = document.querySelectorAll('.currency')
let btn = document.getElementById('btn')
let input = document.getElementById('input')

fetch('https://api.frankfurter.app/currencies')
.then(res => res.json())
.then(res => displayDropDown(res))

function displayDropDown(res) {
  let curr = Object.entries(res)
  for (let i = 0; i < curr.length; i++) {
    let opt = `<option value="${curr[i][0]}">${curr[i][0]}</option>`
    select[0].innerHTML += opt
    select[1].innerHTML += opt
  }
}

btn.addEventListener('click', () => {
  let curr1 = select[0].value
  let curr2 = select[1].value
  let inputVal = input.value
  if (curr1 === curr2)
    alert("Choose different currencies")
  else
    convert(curr1, curr2, inputVal)
});

function convert(curr1, curr2, inputVal) {
  const host = 'api.frankfurter.app';
  fetch(`https://${host}/latest?amount=${inputVal}&from=${curr1}&to=${curr2}`)
  .then(resp => resp.json())
  .then((data) => {
    document.getElementById('result').value = Object.values(data.rates)[0]
  });
}
```

## License

This project is licensed under the MIT License. See the LICENSE file for more details.

## Contact

For any questions or suggestions, please open an issue or contact the repository owner.

---

This project was created to provide a simple and easy-to-use currency converter. Feel free to contribute by submitting pull requests or opening issues.
```

Make sure to update the repository URL in the clone command and any other placeholders (like your username) with the actual information specific to your repository.
