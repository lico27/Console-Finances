- initialise variables for monthCount, netchangeProfits, averageChangeProfits, greatestProfit, greatestLoss
- loop for each month add 1 to monthCount variable
- loop through array, compare finances[i][1] to finances[i -1][1]



Greatest Increase in Profits/Losses: Feb-2012 ($1926159)
Greatest Decrease in Profits/Losses: Sep-2013 ($-2196167)


// * The average of the **changes** in Profit/Losses over the entire period.
//   * You will need to track what the total change in Profit/Losses are from month to month and then find the average.
//   * (`Total/(Number of months - 1)`)
var totalchange=0
var averagechange=0
// to get total change between months
// loop through the finaces array at index 1, instead of 0,
// var difference for change between the current month and past month
// current month = finances[i][0]
// current revenue = finances[i][1]
for(var i=1;i<finances.length;i++){
  var difference = finances[i][1] - finances[i -1][1]
  totalchange = totalchange + difference
}
 var averagechange=totalchange / (count-1)
 console.log('Average of the changes in Profit/Loss over period: $' + averagechange.toFixed(2))


 // Calculating and displaying the total number of months included in the dataset:

var count=finances.length
console.log('Total number of months: ' + count)

// Defines the formatting for the display of monetary values calculated
var profit = { 
  style: "currency", 
  currency: "USD", 
  minimumFractionDigits: 2, 
  maximumFractionDigits: 2
};

// Calculating and displaying the net total amount of Profit/Losses over the entire period.
var total=0
for(var i=0;i<finances.length;i++){
    // console.log(finances[i]);
    total += finances[i][1];
}

// Formats the net total to make it easier to read

console.log('Net total: ' + total.toLocaleString(undefined, profit));

// Calculating and displaying the average of the **changes** in Profit/Losses over the entire period.

var totalchange=0
var averagechange=0

// to get total change between months, loop through the finaces array at index 1, instead of 0, 
// define var 'difference' to represent change between the current month and past month
// current month = finances[i][0]
// current revenue = finances[i][1]

for(var i=1;i<finances.length;i++){
  var difference = finances[i][1] - finances[i -1][1]
  totalchange = totalchange + difference
}
 var averagechange=totalchange / (count-1)

 console.log('Average of the changes in Profit/Loss over the period was:' + averagechange.toLocaleString(undefined, profit))

// Calculating and displaying the greatest increase in Profit/Losses (date and amount) over the entire period.

var greatestmonthlydifference = ['',0]
var monthlydifference = 0

for(var i=1;i<finances.length;i++){
  var currentmonth = finances[i][0]
  var monthlydifference = finances[i][1] - finances[i -1][1] // calculates the POSITIVE change month-on-month

  if (monthlydifference >= greatestmonthlydifference[1]){
    // checks if difference if greater than greatestmonthlydifference, if so updates greatest monthly difference to the current monthly difference
    greatestmonthlydifference = [currentmonth, monthlydifference]
  }
}

// Displays the entire greatestmonthlydifference array:
// console.log('The greatest month-on-month increase in profit is: ' + greatestmonthlydifference)

// Splits the greatestmonthly difference into the date and value for ease of reading
console.log('The greatest month-on-month increase in profit was in ' + greatestmonthlydifference[0] + ' with ' + greatestmonthlydifference[1].toLocaleString(undefined, profit))

// sum the difference onto the netChangeProfits variable: netChange = netChange + difference


// Calculating and displaying the greatest decrease in Profit/Losses (date and amount) over the entire period.
var greatestmonthlydifference = ['',0]
var monthlydifference = 0

for(var i=1;i<finances.length;i++){
  var currentmonth = finances[i][0]
  var monthlydifference = finances[i -1][1] - finances[i][1] // calculates the NEGATIVE change month-on-month

  if (monthlydifference >= greatestmonthlydifference[1]){
    // checks if difference if greater than greatestmonthlydifference, if so updates greatest monthly difference to the current monthly difference
    greatestmonthlydifference = [currentmonth, monthlydifference]
  }
}

// Displays the entire greatestmonthlydifference array:
// console.log('The greatest month-on-month decrease in profit is: ' + greatestmonthlydifference)

// Splits the greatestmonthly difference into the date and value for ease of reading
console.log('The greatest month-on-month decrease in profit was in ' + greatestmonthlydifference[0] + ' with ' + greatestmonthlydifference[1].toLocaleString(undefined, profit))







// Objective: The total number of months included in the dataset.
// Solution: Each element in the finance array represents a month so the length of the array will be the total number of months.
let totalMonths = financesArr.length;


// Objective: The net total amount of Profit/Losses over the entire period.
// Solution: This requires accumulating the number values in every element.
let netProfitLoss = 0;
for(let i = 0; i < totalMonths; i++)
{
    netProfitLoss += financesArr[i][1];
}


// Objective: The average of the changes in Profit/Losses over the entire period.
/* You will need to track what the total change in Profit/Losses are from month to month and then find the average.
(Total/(Number of months - 1)) */
// Solution: This difference of the profit/loss of every following month to calculate the total then be divided by the number of differences used to get that total.
let avg = 0; //Average Change: -2315.12
let avgArr = [];
for (let i = 1; i < totalMonths; i++) 
{
    let difference = financesArr[i][1]-financesArr[i-1][1];
    avg += difference;
    avgArr.push(difference);
}
avg = avg/avgArr.length;


// Objective: The greatest increase in Profit/Losses (date and amount) over the entire period.
// Solution: The greatest increase by default is -Infinity. If there is no increase, then the greatest increase will remain -Infitiny otherwise will show the greatest increase found by the end of the loop.
let monthIncrease = [];
let greatestIncrease = -Infinity;
for (let i = 1; i < totalMonths; i++){
    let month = financesArr[i][0];
    let difference = financesArr[i][1] - financesArr[i-1][1];
    if(greatestIncrease < difference){
        greatestIncrease = difference;
        monthIncrease = [month, difference];
    }
}


//Objective: The greatest decrease in Profit/Losses (date and amount) over the entire period.
// Solution: The greatest decrease by default is Infinity. If there is no decrease, then the greatest decrease will remain Infitiny otherwise will show the greatest decrease found by the end of the loop.
let monthDecrease = [];
let greatestDecrease = Infinity;
for (let i = 1; i < totalMonths; i++){
    let difference = financesArr[i][1] - financesArr[i-1][1];
    if(greatestDecrease > difference){
        greatestDecrease = difference;
        monthDecrease = [financesArr[i][0], difference];
    }
}


// Objective: Your final code should print the analysis to the console.
 /*
Financial Analysis 
----------------
Total Months: 86
Total: $38382578
Average Change: -2315.12
Greatest Increase in Profits/Losses: Feb-2012 ($1926159)
Greatest Decrease in Profits/Losses: Sep-2013 ($-2196167)  
*/
var options = {
    style: "currency", 
    currency: "USD", 
    minimumFractionDigits: 0, 
    maximumFractionDigits:2
}//https://www.joshmcarthur.com/til/2018/04/11/til-tolocalestring.html

console.log(
`Financial Analysis
----------------
Total Months: ${totalMonths}
Total: ${netProfitLoss.toLocaleString("en-US", options)}
Average Change: ${avg.toLocaleString("en-US", options)}
Greatest Increase in Profits/Losses: ${monthIncrease[0]} (${monthIncrease[1].toLocaleString("en-US", options)})
Greatest Decrease in Profits/Losses: ${monthDecrease[0]} (${monthDecrease[1].toLocaleString("en-US", options)})`
);