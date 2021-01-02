# Freshworks-Engineering-Assignment
FILE BASED KEY-VALUE DATA STORE

All the code I have tested on a file named as “example.json”.

File Directory : First the code will ask for the directory in which user want to create the file and perform operations. If the directory is not provided, then the file will be created in the current directory.

User Input: User will provide the key, time to live for the key, and the json object. I have used a manually created json object named as “js_object”.

Functions:

1.	Create(): 
It will take three arguments key, json object and time to live(in seconds). It will take care of the key is string or not and length of the key(less than 32). 
It will also check the size of the json object (less than 16KB). 
After writing this json object into the file "example.json", it will further check the size of the “example.json” file. If the size exceeds 1GB it will then create a new file named as “example_new.json” and write that particular key-value pair in this new file. At the same time it will delete this key-value pair from the original file. And it will again check its size and if size is still greater, then it will remove that key-value pair and put it into the newly created file.

2.	Read():
It will take the key as an argument. It will check if the key is expired or not by comparing the current time with the time that the value contains for that particular key(current time + time to live) during the creation.
If it is expired then Read() will simply delete it. Otherwise it will return the value corresponding to that particular key.

3.	Delete():
It will take the key as an argument and simply deletes the corresponding key-value pair from the file.


Security and Threading :
For making it a safe data store I have used mutex lock. So that at any time only one user can access any of theses functions. So before using any of these functions first i am doing mutex.acquire_lock() and after performing all opretations i am doing mutex.release_lock(). 



