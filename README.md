# Vehicle-Management-System
Complete Application with Spring Boot From the Scratch (Step by Step)

In this practical tutorial we would build a complete application. A Vehicle Management System. We would start from the scratch, take it step by step until the end.

What you will learn:

Java Programming
JavaScript programming
Spring Security – User Login
Spring Data Jpa
Hibernate ORM
MySQL Database – basic command
Thymeleaf Template Engine
HTML and Basic CSS
Debugging Skills
Bootstrap and JQuery
Source Control using GitHub
Hosting, publishing and marketing our application!
And more!
 

The tools you need:

Spring Tool Suit (STS). Get is free here https://spring.io/tools (download it, unzip it and run the SpringToolSuite4.exe file). No installation needed
MySQL Server 5.x. Get it free here https://dev.mysql.com/downloads/installer/
A computer with good internet connection!
Optionally, Any graphics application (Fireworks, Photoshop, CorelDraw etc)
Firefox or Google Chrome or Internet Explorer
 

Step 1: Prepare your tools and assets

(Optional): Prepare a brief paragraph and sketches of what your application is all about.

I’ll provide you with all the files for the completed project. So you can use it to check if you have any bugs in your code. Download and unzip them from the links below.

Models
Controller
Repositories
Services
HTML Files
JavaScript Files
Graphics
 

Step 2: Set up the project (a SpringBoot project)

Create the project in www.start.spring.io. Download it and open it in spring boot.

Ensure to add the following dependencies:

Dependency	Description
lombok	Helps to generate POJO codes
mysql-connector-java	Manages connection to MySQL Database
spring-boot-starter-web	Functionality for web applications created in Spring Boot
spring-boot-starter-data-jpa	Java Persistence API, helps handle data access
spring-boot-starter-thymeleaf	Template engine for rendering html pages
spring-boot-starter-security	Handles security, for instance user login, authentication and authorization (defer this till 10)
thymeleaf-extras-springsecurity5	from org.thymeleaf.extras. Helps you add logged-in username to the html page
Create the package structure: the controllers, repositories, models and services packages.

 

Step 3:  Configure MySQL database

Open MySQL command line and create a database called fleetdb.

Enter the database parameters in the application.properties file. The database parameters is given below:

spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.password=root
spring.datasource.username=root
spring.datasource.url=jdbc:mysql://localhost:3301/fleetdb?serverTimezone=UTC
spring.jpa.hibernate.ddl-auto=update
 

Step 4: Obtain and Setup the Template

Download the template from here. Then set it up. Adjust the links to make sure it works.

Add the ApplicationController file and write the method that serves in index page.

Test the application to make sure it’s ok

 

Step 5: Do the Object Oriented Design

Decide the objects that make up your application. Make a brief write-up of what roles they play.

Optionally, draw a relationship diagram.

I have identified the following objects for the Fleet Management System (FLEETMS) application

1. Auditable *	7. EmployeeType	13. State (Or Region or Province)	19. VehicleMaintenance
2. Client	8. Invoice	14. Supplier	20. VehicleMake
3. CommonObject *	9. InvoiceStatus	15.User	21. VehicleModel
4. Contact	10. JobTitle	16. UserPrincipal (defer till 10)	22. VehicleMovement
5. Country	11. Location	17.Vehicle	23. VehicleStatus
6. Employee	12. Person *	18. VehicleHire	24. VehicleType
Now based on these objects, plan the structure of your application.

 

Step 6: Create the models

Now you can create the entities you have identified from step 5.

You place the entities in the Models package.

You can find all the Models here (zip file with all the models)

 

Step 7: Create all the Controllers

It may be faster to create on controller and then copy across.

 

Step 8: Create all the Services

 

Step 9: Create all the Repositories

 

Step 10: Work on html Pages

First create and test the country.html page. It would be a blank page for now.

Then write the controller method to return this page. Test it.

Now create the link in the home page (index.html) to link to the country.html file. Test it

Create all the other html pages.

 

Step 11: Background image to the home page

You can get the backgroud image bg-11.jpg from here.

Open the index.html page.

Locate the panel-body-map div.

Delete it and replace it with this one below (Optional)

<div >
    <div style="background-image: url('img/bg-1.jpg'); background-size:100% 100%; height:400px;"></div>
</div>
Then go ahead to delete the headers of this panel.

Test the app to make sure.

 

Step 12: Plan the Navigation

Basically, you need to layout the navigation pattern to ensure that all object can be reached.

Open the index.html file and locate the sidebar.

The redesign the sidebar using the navigation structure given below.

Navigation Structure
Navigation Structure
 

 

Step 13: Display list of Countries in the html page

We start with the Country model.

First complete the country model (Country.java)

Then open the CountryService.java file and write a method to return all the countries

Write the CountryController method to get all the countries (talking about Model.addAttribute());

Then insert a country manually in MySQL. The code for inserting a new country into MySQL database is given below. You can execute it a couple of time to add few records

 insert into country values (1, 'Washington', '01', 'North America', 'United States', 'American');
 

Then Open the country.html page, adjust the markup to display a list of countries

Test this page to see if it displays the country you inserted in MySQL

 

Step 14: Inserting a New Country

Then open the CountryService.java file and write a method to insert a country

Write the CountryController method to save a new country

Open the html page  and add the modal add form and button. Test it

 

Step 15: Updating a Country

Add the update button to the html table in country.html file

Add the edit modal form as well and remember to set the th:action attribute.. Then test it.

Set the th:href attribute to link to the findById() method in the controller

Then open the CountryService.java file and write a method to update a country

Write the CountryController method to update a country

 

Step 16: Deleting a Country

Add the delete button to the table

Then add the delete modal to the page.

Write the javascript code in the country.js file to display the delete modal

You can test it at this point

Write the delete function in the CountryService and CountryController

Write the code to assign the delete url to the “Yes, Delete” button

Now test the delete function and make sure a record is deleted.

Complete Application – Part 2 (Showing Image Thumbnails)

This Part follows from Part 1 where we build the basic application.

In this part, we are going to add image functionality. Showing image thumbnails.  So we’ll be able to do the following:

Display image thumbnail
Display an image popup
Write the JavaScript Code
Load image based on database field
Next Steps
 

This is what we would achieve. But we would start with static image thumbnails.



 

Let’s start with the first one.

 

1. Displaying Image Thumbnail
Step 1: First create a folder in the src directory. Name this folder, ‘photos’. It would be used to store employee photos.

Step 2: Now add any image into the photos folder (for now let’s display static thumbnail). Name this image avatar.jpg.

Step 3: Open the Employee.html page and add one additional column to the table. This column should be placed before the Id column.

This column would have the following markup:

<td>
    <a id="photoButton" th:href="@{'/img/photos/avatar.jpg'}">
           <img th:src="@{'/img/photos/avatar.jpg'}" width="40" height="40">
     </a>
 </td>	
 

2. Setup the Modal Form
Now, we want to display a modal popup, when the photoButton is clicked. So we would execute a javaScript code to display the modal and assign the image url

Step 1: Copy and paste the modal html markup to the Employee.html page

<div class="modal fade" tabindex="-1" role="dialog" id="photoModal">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Photo</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
      		<img id="employeePhoto" src="" width="90%" height="90%">
    </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div> 
 

3. Write the JavaScript Code
Now, we would write the JavaScript code to display this images.

So what happens, is that when the user clicks on the photoButton, the href attribute of the button is assigned to the src attribute of the image in the modal. Then the modal is displayed.

Step 1: Open the employee.js file and add the following code

$('.table #photoButton').on('click',function(event) {
   event.preventDefault();
   var href = $(this).attr('href');
   $('#photoModal #employeePhoto').attr('src', href);
   $('#photoModal').modal();		
});	
 

4. Display Dynamic Image based on Database field
This works in a very simple way. First, the name of the image has to be unique the the particular employee records. Therefore, the image name could either be:

username of employee
id of employee
We cannot use username since we are yet to discuss Spring Security in next section.

Step 1: So we would create and  save the images as 1.jpg, 2.jpg and 3.jpg inside the photos folder.

Step 2: Now, adjust the markup for the image column of the table. So it would look like this:

 <a id="photoButton" th:href="@{'/img/photos/' + ${employee.id} +'.jpg'}">
 <img th:src="@{'/img/photos/' + ${employee.id} +'.jpg'}" width="40" height="40">
 </a>
 

Now you can go ahead to test the application.

Then do exactly the same thing for the vehicles module. Let me know if you have any challenges. Also, watch the video lessons for clarifications.

 

5. Next Steps
We would now continue in the next part with 3 interesting topics:

Spring Security (adding user login)
Jpa Auditiong (adding LastUpdatedBy and LastUpdatedOn automatically)
Image upload (allowing a user to upload his profile image)
Remember to subscribe to my channel so you don’t miss any updates.
