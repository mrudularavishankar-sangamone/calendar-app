# Calendar Display

A simple React application that displays a calendar with the ability to navigate between previous and next months.

## Technologies Used:
- ReactJS - UI framework and interactivity
- HTML - Markup structure
- CSS - Styling

## Setup/Installation

### Prerequisites:
- Node.js (v14 or higher) and npm installed on your machine
- Git (to clone the repository)

### Steps:
1. Verify if npm is installed in your device/workspace(for Windows):
    - Before running the project, ensure that npm is installed on your system.
    - Open the Terminal in VSCode.
    - Run the following command:
      ```
      npm -v
      ```
    - If a version number is displayed (for example, 10.4.1), npm is already installed. You can skip Step 2.
    - If you see an error such as: ```'npm' is not recognized as an internal or external command```, then npm is not installed. Proceed to Step 2

2. Installing npm:
    - Download Node.js from 'https://nodejs.org/'.
    - Install Node.js by running the installer and follow the prompts.
    - Verify the installation by running the npm -v command in terminal.

3. Install the React package and its dependencies:
    ```
    npx create-react-app <app-name>
    ```
    P.S: The AppName should only contain lowercase alphabets

4. Changing the directory to the AppName:
    ```
    cd <app-name>
    ```

5. Start the development server:
    ```
    npm start
    ```
    The app will open in your browser at http://localhost:3000

6. Modify App.js file:
    - Delete the logo.svg import statement
    - Delete all the lines of code between the return() in App function
    - Add the following statements in the return()
      ```
      return(
        <div>
          <h1> Calendar </h1>
        </div>
      );
      ```
    - Verify the output at http://localhost:3000. Now, the React Application is ready.

7. Grouping the jsx file:
    - Create a folder called pages under src.
    - Create a file called pages/Page1.jsx.
    - Add the ```export default function Page1(){ }``` statement.
    - Add an empty return statement within Page1() function.
      ```
      return(
        <div>
        </div>
      );
      ```
    - Create a table with weekdays as the column headers within div-tag inside return():
      ```
      <table>
        <tr>
          <th>Sun</th>
          <th>Mon</th>
          <th>Tue</th>
          <th>Wed</th>
          <th>Thu</th>
          <th>Fri</th>
          <th>Sat</th>
        </tr>
      </table>
      ```

8. Including Page1.jsx reference in App.js:
    - Add ```import Page1 from './pages/Page1.jsx'``` statement
    - Add React tag within the return() so that the contents of Page1.jsx shows up on the screen.
      ```
      return(
        <div className = "App">
          <h1> Calendar </h1>
          <Page1 />
        </div>
      );
      ```
    - Verify the output at http://localhost:3000.

9. Adding Dates to the table:
    - Hard code the dates into the table using td-tag:
      ```
      <tr>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td>1</td>
        <td>2</td>
        <td>3</td>
      </tr>
      <tr>
        <td>4</td>
        <td>5</td>
        <td>6</td>
        <td>7</td>
        <td>8</td>
        <td>9</td>
        <td>10</td>
      </tr>
      <tr>
        <td>11</td>
        <td>12</td>
        <td>13</td>
        <td>14</td>
        <td>15</td>
        <td>16</td>
        <td>17</td>
      </tr>
      <tr>
        <td>18</td>
        <td>19</td>
        <td>20</td>
        <td>21</td>
        <td>22</td>
        <td>23</td>
        <td>24</td>
      </tr>
      <tr>
        <td>25</td>
        <td>26</td>
        <td>27</td>
        <td>28</td>
        <td>29</td>
        <td>30</td>
        <td>31</td>
      </tr>
      ```
    - Verify the output at http://localhost:3000.

10. Adding the logic to dynamically display Weekdays:
    - Create an array whose values are days of the week:
      ```
      const daysOfWeek = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
      ```
    - Create a function to dynamically render the values of daysOfWeek array:
      ```
      function displayDaysOfWeek() {
        let weekdays = [];
        for(let i = 0; i < daysOfWeek.length; i++) {
          weekdays.push(<span key = {"Days" + i}> {daysOfWeek[i]} </span>);
        }
        return weekdays;
      }
      ```
      PS: The above lines of code are to be placed within Page1() before the return().
    - Add the following lines of code inside the return():
      ```
      <div className = 'days-container'>
        {displayDaysOfWeek()}
      </div>
      ```
    - Verify the output at http://localhost:3000.

11. Adding the logic to dynamically display the dates:
    - Create an array whose values are months in a year:
      ```
      const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
      ```
    - Add the following lines of code to extract the current date, current month, current year, days in a month:
      ```
      const currentDate = new Date();
      const [currentMonth, setCurrentMonth] = useState(currentDate.getMonth());
      const [currentYear, setCurrentYear] = useState(currentDate.getFullYear());
      const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();
      ```
    - Add ```import { useState } from 'react';``` in order to use the useState function.
    - Create a function to dynamically render the values of daysOfWeek array:
      ```
      function displayDatesInMonth (){
        let dates = [];
        for(let i = 1; i <= daysInMonth; i++){
          dates.push(<span key = {"Date" + i}> {i} </span>);
        }
        return dates;
      }
      ```
      PS: The above lines of code are to be placed within Page1() before the return().
    - Add the following lines of code inside the return():
      ```
      <div className = 'dates-container'>
        {displayDatesInMonth()}
      </div>
      ```
    - Verify the output at http://localhost:3000.

12. Displaying the month and year dynamically as headings:
    - Add the following lines of code to display the month and year as heading:
      ```
      <h2> Calendar {currentYear} </h2>
      <h3> {months[currentMonth]}, {currentYear} </h3>
      ```
    - Verify the output at http://localhost:3000.

13. Adding CSS to the page in order to display the calendar properly:
    - Open the App.css file and add the following:
      ```
      .App {
        text-align: center;
      }

      .App-header {
        background-color: #282c34;
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-size: calc(10px + 2vmin);
        color: white;
      }

      .days-container {
        width: 100%; 
        display: flex;
      }

      .days-container span {
        width: calc(100% / 7);
        font-weight: bold;
        text-transform: uppercase;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 10px 0px 10px 0px;
      }

      .dates-container {
        width: 100%; 
        display: flex;
        flex-wrap: wrap;
      }

      .dates-container span {
        width: calc(100% / 7);
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 10px 0px 10px 0px;
      }

      div i {
        margin: 10px;
        padding: 10px 20px;
        font-size: 16px;
        gap: 10px;
        cursor: pointer;
        font-weight: bold;
      }
      ```

14. Adding empty spaces to align the first day of the month
    -  Create a function to dynamically render the empty spaces until start of the the first day:
      ```
      const firstDayOfMonth = new Date(currentYear, currentMonth, 1).getDay();

      function emptySpace(){
        let emptySpaces = [];
        for(let i = 0; i < firstDayOfMonth; i++){
          emptySpaces.push(<span key = {"empty" + i}> </span>);
        }
        return emptySpaces;
      }
      ```
      PS: The above lines of code are to be placed within Page1() before the return().
    - Add the following line of code within dates-container div tag inside the return():
      ```
      <div className = 'dates-container'>
        {emptySpace()}
        {displayDatesInMonth()}
      </div>
      ```
    - Verify the output at http://localhost:3000.

15. Adding next and previous buttons to Page1.jsx file
    - Add the following piece of code within return() statement:
      ```
      <div>
        <button> &lt; </button>
        <button> &gt; </button>
      </div>
      ```

16. Adding a previous function to navigate to previous month
    - Add the following lines of code to handle backward month navigation:
      ```
      function previous () {
        if (currentMonth === 0) {
          setCurrentMonth(11);
          setCurrentYear(currentYear - 1);
        } else {
          setCurrentMonth(currentMonth - 1);
        }
      }
      ```
      This function updates the month and year correctly when moving from January to December of the previous year.
    - Adding onclick attribute to previous button:
      ```
      <button onClick={previous}> &lt; </button>
      ```

17. Adding a next function to navigate to next month
    - Add the following lines of code to handle forward month navigation:
      ```
      function next (){
        if(currentMonth === 11){
          setCurrentMonth(0);
          setCurrentYear(currentYear + 1);
        }else{
          setCurrentMonth(currentMonth + 1);
        }
      }
      ```
      This function updates the month and year correctly when moving from December to January of the next year.
    - Adding onclick attribute to next button:
      ```
      <button onClick={next}> &gt; </button>
      ```