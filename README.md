# Daily Balance Lullaby - How to run
It´s a project for Money Makes Music challenge - creating music from money.

This code generates a peacefull lullaby melody by converting the transactions amount of an especific choosen date into piano notes.

So, after a really chaotic work day, you can transform a bunch of money-related numbers to help you fall asleep totally relaxed.

The project is made in Python running on Google Colab notebook.


How to run:

1-Run "General Setup"
(This cell install everything is needed to to run the code properly. In this step your CW´s credentials will be requested to give access to the database to run the query that will fetch de transactions data.) 
![image](https://user-images.githubusercontent.com/71954914/176036444-2e6a2ef0-8ad6-4b2c-85d7-1f31478d9405.png)



2-Run "Load Notes Table"
![image](https://user-images.githubusercontent.com/71954914/176036558-15a0aec4-d980-4da6-9985-efbe2b917946.png)




3-Run "Select the date interval from which your song will be generated:"
(Here you can select any date > '2019-06-01'. In this step a query will be executed and the transactions of the selected date will be converted to an coded string)
![image](https://user-images.githubusercontent.com/71954914/176036624-94be1a70-33cd-4b10-aac4-482c59794602.png)




4-Run "Listen to your song and have a good night!"
(this section generates the melody by crossing the query´s encoded string and the notes table. Press the play button and enjoy your song!"
![image](https://user-images.githubusercontent.com/71954914/176036699-c2064db3-60df-4f76-ab5b-32acf0604214.png)

![image](https://user-images.githubusercontent.com/71954914/176036820-fe563147-c7ef-429a-bc54-ff0cf1884573.png)
