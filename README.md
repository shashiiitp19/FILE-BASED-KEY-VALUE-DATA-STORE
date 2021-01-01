# Freshworks-Engineering-Assignment
FILE BASED KEY-VALUE DATA STORE

All the code I have tested on a file named “example.json”.

File Path : First the code will ask for the path of the file. If the file path is not provided it will use a provided default path.

User Input: User will provide the key, time to live for the key, and the json object. I have used a manually created json object named as “js_object”.

Functions:

1.	Create(): 
It will take three arguments key, json object and time to live. It will take care of the key is string or not and length of key(<32). 
It will also check the size of the json object (<16KB). 
After writing this json object, it will check the size of the “example.json” file. If the size exceeds 1GB it will then create a new file named as “example_new.json” and write that key value pair in this file. At the same time it will delete this key value pair from original file. And it will again check its size.

2.	Read():
It will take the key as an argument. It will check if the key is expired or not by comparing the current time with the added time(current time + time to live) during the creation.
If it is expired then Read() will simply delete it. Otherwise it will return the value corresponding to that particular key.

3.	Delete()
It will take the key and simply deletes the corresponding key value pair.


Threading :
For making it a safe data store I have used mutex lock. So that at any time only one user can access any of theses functions.



