/*    JavaScript 6th Edition

 *    Filename: tt.js
 */

// global variables
var daysOfWeek = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

var opponents = ["","", "", "", "", "", "", "Jacksonville", "", "", "", "", "", "", "Oakland", "", 
				 "", "", "", "", "", "Baltimore","", "", "", "", "", "", "Detroit", ""];
				 
var gameLocation = ["", "", "", "", "", "", "", "away", "", "", "", "", "", "", "away", "", "", "", "", "", "", "home", "",
					"", "", "", "", "", "away", ""];
					
var gameTimes = ["", "", "", "", "", "", "", "1:00 PM", "", "", "", "", "", "", "4:05 PM", "", "", "", "", "", "", "1:00 PM", "",
				 "", "", "", "", "", "1:00 PM", ""];
				 
var tvStation = ["", "", "", "", "", "", "", "CBS", "", "", "", "", "", "", "CBS", "", "", "", "", "", "", "CBS", "",
				 "", "", "", "", "", "FOX", ""];
	
// functions to place the daysOfWeek in header row cells

// function to add column headers
function addColumnHeaders()
{
	var i = 0;
	
	while(i < 7)
	{
		document.getElementsByTagName("th")[i].innerHTML = daysOfWeek[i];
		i++;
	}
}//end addColumnHeaders function

//function to add day of month value in the first 'p' element within each table data cell that has an id
function addCalendarDates()
{
	var i = 1;
	var paragraph = "";
	
	do
	{
		var tableCell = document.getElementById("09-" + i);
		
		paragraphs = tableCell.getElementsByTagName("p");
		paragraphs[0].innerHTML = i;
		i++
	}while(i <= 30); // number of days in month
	
	
}//end addCalendarDates function

//function to place opponents and gameLocation values in second element within each table data cell that has an id
function addGameInfo()
{
	var paragraphs = "";
	for (var i = 0; i < 30; i++)
	{
		var date = i + 1;
		var tableCell = document.getElementById("09-" + date);
		paragraphs = tableCell.getElementsByTagName("p");
		
		switch(gameLocation[i])
		{
			case "away":
				paragraphs[1].innerHTML = "@ ";
				break;
				
			case "home":
				paragraphs[1].innerHTML = "vs ";
				break;
				
			case "":
				paragraphs[1].innerHTML = "";
				break;
		}//end gameLocation switch
		
		paragraphs[1].innerHTML += opponents[i];
		
	}//end for loop paragraphs 1
	
	for (var j = 0; j < 30; j++)
	{
		var date = j + 1;
		var tableCell = document.getElementById("09-" + date);
		paragraphs = tableCell.getElementsByTagName("p");
		
		switch(gameTimes[j])
		{
			case "4:05 PM":
				paragraphs[2].innerHTML = "4:05 PM";
				break;
				
			case "1:00 PM":
				paragraphs[2].innerHTML = "1:00 PM";
				break;
				
			case "":
				paragraphs[2].innerHTML = "<img src=\"images/helmet.png\" width=\"90px\" height=\"90px\">";
			break;
		}//end gameTime switch
		
	}//end for loop paragraphs 2
	
		for (var n = 0; n < 30; n++)
	{
		var date = n + 1;
		var tableCell = document.getElementById("09-" + date);
		paragraphs = tableCell.getElementsByTagName("p");
		
		switch(tvStation[n])
		{
			case "CBS":
				paragraphs[3].innerHTML = "On CBS";
				break;
				
			case "FOX":
				paragraphs[3].innerHTML = "On FOX";
				break;
				
			case "":
				paragraphs[3].innerHTML = "";
			break;
		}//end tvStation switch
		
	}//end for loop paragraphs 3
	
}//end function addGameInfo

//fucntion to populate the calendar
function setUpPage()
{
	addColumnHeaders();
	addCalendarDates();
	addGameInfo();
}//end function setUpPage

//runs setUpPage function when page loads
if(window.addEventListener)
{
	window.addEventListener("load", setUpPage, false);
}
else if (window.attachEvent)
{
	window.attachEvent("onload", setUpPage);
}
//end of page load 