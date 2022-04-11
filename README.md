## Readme

Hello. I here decided to share a script that I did not write. I just found 2 scripts and connected them in place. 
First, I'll tell you what they do. Part 1 of the script creates the time in the next column when you write or replace something 
(for example: You wrote something in A2 and the date appears in B2).
The second part Creates and replaces the date separately.
What does it mean?
If you write something in A2, then it will create a date in both B2 and C2, but the next time you replace the text with A2, the date will only change to B2.


Here's how it looks.

<a href="https://imgur.com/lJMRhxE"><img src="https://i.imgur.com/lJMRhxE.gif" title="source: imgur.com" /></a>


Below is the code itself. You yourself will find how to use it, but I finished here.


Here are links to the authors of both scripts:
1 part: https://bit.ly/3hg8wJ5
2 part: https://bit.ly/3zRPMrI

## Code

```js
function onEdit(e) {

addTimestamp(e);

var s = SpreadsheetApp.getActiveSheet();

if( s.getName() == "test" ) { //checks that we're on the correct sheet

var r = s.getActiveCell();

if( r.getColumn() == 2 ) { //checks the column

var nextCell = r.offset(0, 1);

nextCell.setValue(new Date());

}

}

}

function addTimestamp(e){

//variables

var startRow = 8;

var targetColumn = 1;

var ws = "test";

//get modified row and column

var row = e.range.getRow();

var col =e.range.getColumn();

if(col === targetColumn && row >= startRow && e.source.getActiveSheet().getName() === ws){

var currentDate = new Date();

e.source.getActiveSheet().getRange(row,3).setValue(currentDate);

if(e.source.getActiveSheet().getRange(row,6).getValue() == ""){

e.source.getActiveSheet().getRange(row,6).setValue(currentDate);

}

}

}
```
