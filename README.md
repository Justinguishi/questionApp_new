# Question setting App
- This is the Technical Guide of Question App
	>In this section, the function of the question setting App is to create a new question by clicking on 
	a point on a Leaflet map and adding the question and four possible answers. The question should be stored
	in a database on the web server.
## Requirements
#### Hardware: 	
- A computer with positioning function
	 >Since the question setting app is based on the browser and needs to track the location, 
a computer or laptop with a location function is required.

#### Software:
- Bitvise SSH Client 8.29 in computers 
	 >Applying this SSH Server to provide remote access to the UCL server.As this app doesn't specify a requirement to run on an Android phone, we do not 
need to download PhoneGap like the quizApp.

####  Browser: 
- Google Chrome 73 
- Microsoft Edge
- Internet Explorer 11
	>Running questionApp on these browsers. Besides, if you want to debug the wrong part of the code, a browser with a console 
window is a good choice.In this way the user can clearly see where the error occurred and effectively correct it, although it is not necessary.



## Deployment
The Question Setting App is developed by HTML5 and Javascript. All the functions developed here are basically using Javascript and the solution 
is mainly the JavaScript and XML (AJAX) which is used  to create multiple web applicationson the client side. According to the AJAX, for the function 
of uploading questions, writing a function to get every value by using the programming statement getElementById entered by clients and processing it to 
send the data through the way postString to the server to save. As for loading existing quiz points automatically, the app needs to send the request to 
acquire each value from the server when opening the app. For getting the detailed coordinates from the leaflet map, onMapClick and getElementById can be used here.

- This App uses github submodules. Therefor, the deloyment process is as follows:

1: check the local directory
	
	 >pwd
	 /home/studentuser/code/questionApp_new

2: connect to deployment branch in GitHub
	 
	 >git clone https://github.com/ucl-geospatial/uczl374-questions.git--recurse-submodules

	(Before deploying anything, it has to be in the deployment branch. After ever step is over, the newly uploaded data is merged into the master. Only by doing this 
	preparation can the data be safely protected and no data will be lost for the user. And, doing so will make the data more organized, and every step of the work can be 
	shown in GitHub)
	
3: Make the change

	 >cd uczl374_questions/uczl374/www
	
	In this process, I mainly carried out three steps. First, the entire map page is loaded, and many basic functions of the practicle are completed. The implementation
	of these functions lays a good foundation for the subsequent load question. Second,the function of clicking the map to return the coordinate point is completed, and a
	form web page can be newly loaded in the menu. Third, it is the most important part of the whole project. Get the form data added by the user, use AJAX to request the 
	server, and then upload all the data (coordinate points and text data) to the database for use by the quizApp. 
		
## Testing 
The test code is divided into two parts. First, we need to check whether the entire app can run normally. The main function of the whole questionApp can be realized: 
track the user's location and display it on the map, display the coordinates of quiz points which have been already loaded.In addition, user need to fill in the appropriate
values in the corresponding fields in the table and test whether you can upload the data to the database, and the web page reflects the correct alert. At the same time, we can access 
the data that the user has uploaded by directly entering the URL in the browser. This is also a way to check whether the function of the questionApp is intact.Finally, it is 
tested whether each function in the app can run successfully, such as get earthquakes, show map, etc. These functions do not play a major role in this quizApp, but a successful 
mobile app should guarantee each function can run smoothly as well.


- For testing the code, the tester can select random points on the map and then set random questions on it then submit it, opening the server to see whether the information has already been saved.
	
	 >1.Opening the question setting app in the browser( http://developer.cege.ucl.ac.uk:30314/). Clicking on the map to select different points and setting different questions, it is better if there is a certain distance between
	 points since there is 5 to 10 meters error in the Global Navigation Satellite System (GNSS). That is also the major reason that set 50 meter as the certain distance to require the closest quiz point.

	 >2.After submitting the questions, tester can refresh the page to check whether the quiz points are displayed on the map.

	 >3.If there is any question about the app, tester can click the left-hand side menu to click the 'help document' to check the user guide.	


## Functionalities
| Directory  |  File  | Functions  |
| :------------: | :------------: | :------------: |
|uczl374-questions |index.html| Foundation of this web-base questionApp|
|uczl374-questions|createForm.html|the function of creating a simple form|
|uczl374-questions|LeafletGeoJSON2.html|Insert a basic map in the right-hand menu|
|uczl374-questions |question.html| the question setting form to build the quiz points|	 
|uczl374-questions |helpDocument_question.html| link the help document|	 
|uczl374-questions |leaflet.js| provide a simple empty map|	
|uczl374-questions |leafletFunction.js| add polygon and the earthquakes data on that map|	
|uczl374-questions |AJAX.js| process the AJAX request|	
|uczl374-questions |getData.js| load the quiz points from database and show them on map|	
|uczl374-questions |rhMenu.js| UCL logo function|	
|uczl374-questions |startup.js| trigger the function when running the web page |	
|uczl374-questions |uploadData1.js| upload the question form to the database|	
|uczl374-questions |userTracking.js| Positioning the user|	
|uczl374-questions |utilities.js| get the port number|	
