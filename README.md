# One Page Calendar Program

The Calendar Program is an application that displays a calendar view for a specific year.

## Usage
- Open the index.html file in your browser.
- Enter the desired year in the input field with the ID year-input and press the Enter key.
- The calendar view will automatically update to display the selected year.

## Functions
The Calendar Program includes the following functions:

### populateMonthNamesByWeekday()
This function calculates the names of the months for each week of the year and stores them in the monthNamesByWeekday array. It is called each time the year is changed to ensure that the month names are displayed correctly.

### resetMonthNamesByWeekday()
This function clears the monthNamesByWeekday array to ensure that it is correctly initialized for each new year.

## Technologies
The One Page Calendar program was developed using the Svelte JavaScript framework and the TypeScript programming language. The view is formatted using HTML and CSS.

## Author
Hauke Konrad - hauke.konrad.coding@gmail.com

## License
This project is licensed under the MIT License. See the LICENSE file for more information.