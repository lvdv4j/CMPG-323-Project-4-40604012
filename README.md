# CMPG-323-Project-4-40604012

This UiPath Automation project made for EcoPower Logistics ensures that the website designed by the EcoPower Logistics team is well tested and is of proper quality and standard before it is deployed.

## Before you begin
Please ensure that you have the following installed:
- MS Excel
- Google Chrome
- UiPath Studio and/or UiPath Assistant

This project is only compatible with Windows Operating Systems.

## How to use this project
### Setting up the bot
This project can be used either by cloning the main repository to a file on your computer, opening the cloned files in UiPath Studio and running the main.xaml file. Alternativly, you can download the .nuget file from [this link](https://drive.google.com/file/d/1IM4v-yGRKm1j9iOHmTC9kHT79gcTyqih/view?usp=sharing). Once you have downloaded this file you need to place it into your ```C:/ProgramData/UiPath/Packages``` file, open UiPath Assistant, and run it from there.

This project has also been hosted on UiPath Orchestrator, you can contact the admin (me), providing your UiPath Orchestrator account name, and I will be able to grant you the needed roles to obtain access to the bot.

(Proof that I hosted the project on Orchestrator: )
![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/80a6c6aa-d600-4c56-ad7d-15af8d3a12d3)
![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/006f7282-b442-43f9-bacd-c6a4f6165d2a)
![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/3772e865-49be-4e71-bfa4-e787f74def72)

### Once the bot is running
#### Login Prompt
Before the bot begins testing, it will first ask you for your login information to log you onto the EcoPower Logistics website, to proceed further please provide it with your username and your password respectivly. If you are already logged in - the bot will skip this process and instead show you a messagebox confirming that you have already been logged in previously.

![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/4a70e443-a9ef-4cd8-8321-7e30e48c0257)
![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/47433f98-24d5-4b5e-b1a6-f1a6fd233879)

If the incorrect login details are provided, the bot will request for them again:

![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/f1b79667-8edc-460a-8487-69fea506ddcf)

#### File selection
The bot will then ask you to select an Excel file containing the data you wish to use to run your tests. You can use your own - or you can make use of the sample Excel file provided here on github. Please ensure that your Excel file is formatted correctly - otherwise the bot will not be able perform the tests properly.

![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/3f525b45-78a2-4183-8869-670ff8750da0)

#### Test selection
Once you have provided the bot with the relevant information it needs, you will be asked what you would like to test in the next input dialogue. 
You can choose from the following options:
- Customers ~ Tests the CRUD functionality for Customers
- Orders ~ Tests the CRUD functionality for Orders
- Products ~ Tests the CRUD functionality for Products
- Order Details ~ Tests the CRUD functionality for Order Details
- All ~ Tests the CRUD functionality for all of the above mentioned options
- Logout ~ End the testing process and log out of the website

Once you have selected an option, click ok and the bot will begin testing your chosen tab of the website with your data. This might take a while depending on your network connection as well as the general speed of your computer.

![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/074047a3-ff95-484e-930a-33c909ff366a)

If you choose to log out, the bot will log you out of the website and display a message box stating that you have been logged out.

![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/cee30e83-6328-43bc-83ab-8e9a0a4c1e1f)

#### During testing
You need not do anything to help or aid the bot during testing. You will be able to see how it interacts with the web browser as well as how it writes to your chosen Excel file. You'll notice that as a data record passes or fails the test cases defined within the bot, the bot will write TRUE or FALSE respectivly. If you have UiPath studio and are using that to run the bot, you will be able to get more information about why a certain data record failed a test by reading the output logs. 

``` *Please note that some tests may have a false fail ~ meaning that while the data record would and should have normally passed the test - due to a timeout or network error, the bot could not find the relevant UI elements or values needed to complete the test. It is recommended that you always run the test cases at least twice to confirm the status of the results. During the testing process, please refrain from entering values or pressing buttons on the web browser while the bot is still running, as this can also result in the same problem occuring.* ```

#### After testing
After the testing process is completed the bot will close the browser as well as the Excel spreadsheet. It will then present you with an option of performing another test. 
- if you click yes, you will return to the ```Select Option``` window to select what you would like to test.
- if you click no, the bot will stop running and the process will end.

![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/3f4a3fb1-7dba-4f74-b00a-f465423551c5)

### Stretch tasks for the project
The following stretch tasks were done for the project:
- Error handling: Although this was not requested in the brief or the rubric, I did error handling for the following:
  1. the login process - if the incorrect login details were given, I made sure that the bot would ask for the details again
  2. during the testing process for any of the entities - if there was a UI element not found error, my program will throw an exception message in a messagebox to ensure a good user experience.
  3. the log out process - if the user is already logged out, the program will notify the user with a messagebox.
- Log out function: This function was not requested in the project brief but I added it for some extra functionality.
- Dealing with multiple row entries on the website: Originally my project could only perform CRUD testing if there was only 1 row present in the website table at a time. If there were more than one, for example: ![image](https://github.com/lvdv4j/CMPG-323-Project-4-40604012/assets/104925498/a2954813-970a-4056-8210-cb8477d80a38)
 The bot would throw an error stating that multiple UI elements of the same type was found and this would result in the testing process not completing. To solve this error I made use of the concept of dynamic selectors, ensuring that the bot will only work on the last added record in the table.
- Doing multiple tests in one session: Also not something that was included in the rubric or brief - I allow the user to continue performing more tests after a test has been completed by making use of a Retry Scope activity. This ensures that the user will be able to run tests until they are satisfied/finished, without having to restart the bot each time.   

All the above mentioned tasks were completed ahead of the project milestone.

## References
