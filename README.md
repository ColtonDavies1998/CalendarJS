This is the CalendarJS library created specifically for my personal capstone project. While looking through the internet for prebuilt Javascript calendars I came to the realization that in order for me to get what I truly wanted for my capstone project I would have to build my own calendar library. The purpose of this calendar library is to help display the tasks the user has, it is 1 tool in my application to keep the user organized. So you can have an empty calendar if you would like but there is also the ability to enter tasks and populate them with information. So through out this file, I will explain how you can set up CalendarJS in your project.



-> The data variable is just the array of data that you will be feeding into the table.
   The form of the data variable should be an array of objects [{}, {}], the properties show below are the properties
   that work in the program, you can customize the code if you want to add more properties but these were the ones i needed for my
   project
   <script>
    var data = [
      {
          Task_Id: "3",
          Task_Name: "Finish homework",
          Task_Description: "Do questions 1 - 4",
          Task_Start_Time: "8 am",
          Task_End_Time: "9 am",
          Task_Type: "education",
          Task_Start_Date: "September 21 2019",
          Task_End_Date: "September 21 2019",
          Task_priority: "4",
          Task_completed: "true"
      }
    ];
   </script>
    

-> tableHeaders is a property that is required for the program to work. This property must be an array
   of strings. These strings must be in the same order as the properties in your objects since they display
   from 0 index till the end of the array. Here is an example
   <script>
    var table = new Table(data, {
      tableHeaders: ["Id", "Name", "Start Time"]

    });

   </script>
  

-> tableId is the id of the element you wish to display the table in, this field is required in order for 
   the program to work.
   <script>
     var table = new Table(data, {
        tableHeaders: ["Id", "Name", "Start Time"],
        tableId: document.getElementById("mainTable"),
      });

   </script>
   

-> fields is the object fields that are inside the array of objects. This allows some items not to be displayed.
   This field is required in order for the program to work. 
   <script>
     var table = new Table(data, {
      tableHeaders: ["Id", "Name", "Start Time"],
      tableId: document.getElementById("mainTable"),
      fields: ["Id", "Name", "Start Time"],
      
    });
   </script>
    

-> numOfItemsDropdownDisplay is a object property that is not required in order for the program to work. 
   the object has 2 properties, the first is a boolean called "display", if set to true it will displayed
   the dropdown. the second property is the numbers you want in the dropdown, these numbers have to be
   full  numbers no negative or decimals allowed

   <div id="numOfItemsDisplay"></div>

   <script>
    var table = new Table(data, {
      tableHeaders: tableHeads,
      tableId: sourceId,
      fields: objectFields,
      numOfItemsDropdownDisplay: {
        display: true,
        numberList: ["5","10","15"]
      }
    });
   </script>

-> searchBarDisplay is a boolean property that is not required in order for the program to work. if
   the boolean is set to true then a search bar will be displayed. If nothing is inputed it will 
   automatically be set to false; Also if set to true, this property will require a div with the Id 
   named "searchBar". 

  <div id="searchBar"></div>

   <script>
      var table = new Table(data, {
      tableHeaders: tableHeads,
      tableId: sourceId,
      fields: objectFields,
      numOfItemsDropdownDisplay: true,
      searchBarDisplay: true,
    });
   </script>

-> specialButtons is a array of objects property thas is not required for the program to work.
   This property allows the user to put in special buttons at the end of their table, things like
   edit or delete, or anything since this is pretty customizable. The objects for this program
   have 3 properties. They are "btnName","btnClasses","text"
    <script>
    var table = new Table(data, {
        tableHeaders: tableHeads,
        tableId: sourceId,
        fields: objectFields,
        numOfItemsDropdownDisplay: true,
        searchBarDisplay: true,
        specialButtons: [
          {
            btnName: "edit",
            btnClasses: ["btn", "btn-warning"],
            text: "Edit"
          },
          {
            btnName: "delete",
            btnClasses: ["btn", "btn-danger"],
            text: "Delete"
          }
        ]
      });


  </script>

    

  Errors and issues:
    -> While working on this program, I realized once it was too late that if you have a task that starts on 1 day and ends on another day, that task will not display on the day or week calendar. Was not really sure how to fix this issue, my current solution will be to eliminate the tasks data from being able to start and end on different days.
  

  Future update ideas
    -> Fix the errors that come about having a task that starts and ends on different days
    ->For the custom buttons section, add the ability for users to add custom functions that the library attaches
    