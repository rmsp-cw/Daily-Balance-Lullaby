# Daily Balance Lullaby

### intro

It´s a project for **Money Makes Music challenge** - creating music from money.

This code generates a peacefull lullaby melody by converting the transactions amount of an especific choosen date into piano notes.

The project is made in Python running on Google Colab notebook.

## About the project

### Concept definition

>A melody is born when a sequence of sounds happens along the timeline. For that, we need to have at least two basic parameters, one to define the sounds, and other to define the timeline.

>A transaction is born when someone needs to pay for something.

That´s simple, Isn´t it? 

It´s true, but working with payments doesn´t always sound like music…
There´s a lot of information running wild through a huge complex system, a lot of problems to be fixed, a lot of processes to be designed, tons of numbers coming in and going out connecting millions of people.

It´s so fkn stressful! 

How could we transform this chaotic scenario into a peaceful music?

What about a clean and calm piano melody to make you sleep as a child?

So, let´s do it...

### Parameters definition

A transaction file holds a bunch of information, both numerical - id, amount, fees, card number, installments, etc. - and non-numerical - cardholder name, merchant name, card brand,etc., so the first decision was to choose the most suitable parameters to be converted in musical notes.


The choice should satisfy some rules, it should allow random pick-up and also an easy codification methodology, so I´ve decided to work with the transaction amount column data because: 

- it happens randomly
- it has a wide range, allowing correlation with a large range of notes
- It´s numerical and allows easy manipulation
- It happens frequently along the time


### First Manipulations

The transaction amount is a float number. To produce piano notes we need to covert it in integers.


![image](https://user-images.githubusercontent.com/71954914/176128437-787a71b4-5cd8-442d-9542-cbc900950f1d.png)

### Selecting a sound project

To make music we need to have an audio engine code to generate a sound output. I chose the Music21 project because it allows to play notes from a single sequence string.

https://web.mit.edu/music21/doc/index.html#

### Creating relationship between transaction amount and musical notes

The challenge now is to convert the transaction amount column in a readable string.
The Music21 music note string is composed by the music note plus it´s duration:

`note.Note('A2 ' , quarterLength = .25)`


And it´s possible to give it an object name alias:


`n1 = note.Note('A2 ' , quarterLength = .25)`

`n2 = note.Note('A2 ' , quarterLength = .5)`

`n3 = note.Note('A2 ' , quarterLength = .75)`


So this way we can create a relationship between the transactions query results and the notes by formatting the result column, adding a 'n' before the number:

![image](https://user-images.githubusercontent.com/71954914/176133623-1f0ecc18-c06c-4e14-8a36-0ee4892875b0.png)
![image](https://user-images.githubusercontent.com/71954914/176141144-cb434b29-2d6f-4b95-ae08-92ab0c5c1c7e.png)


Now we need to create a table of notes from which the code will compare the result string of the transactions query to generate a melody line.
I´ve used Google Sheets to write a big table with 350 notes of `C major` natural scale from `A2` to `G6` with different duration combinations in order to have a wider range of possibilities.

![image](https://user-images.githubusercontent.com/71954914/176138105-110dc3b1-5818-4121-92e8-de7b6f4cf368.png)


### Final settings

The amount range is very wide, we have transactions from cents to thousand hundreds, it´s impossible to take one piano note to each transaction amount value.
To solve this we need to limit the transactions range, or make the relationship by amount ranges. 

For the first version I´ve only filtered by transactions with amount between 1 and 350 , producing notes from n1 to n350 that is our table notes range. I´ve also added a filter to limit the string length to 100 notes, resulting in a melody of about 1 minute.

To make things more fun, I´ve added a custom date filter, so you can select a date you want and each date will generate one different melody.

![image](https://user-images.githubusercontent.com/71954914/176145242-f7fb4287-a163-4eb1-b50c-764c5b0302de.png)









## How to run:

#### 1-Run "General Setup"
This cell install everything is needed to to run the code properly. 

*In this step your CW´s credentials will be requested to give access to the database to run the query that will fetch de transactions data. 

**You need to have permission to access the project `infinitepay-production` on Big Query database.
![image](https://user-images.githubusercontent.com/71954914/176036444-2e6a2ef0-8ad6-4b2c-85d7-1f31478d9405.png)



#### 2-Run "Load Notes Table"
![image](https://user-images.githubusercontent.com/71954914/176036558-15a0aec4-d980-4da6-9985-efbe2b917946.png)




#### 3-Run "Select the date interval from which your song will be generated:"
Here you can select any date > '2019-06-01'. In this step a query will be executed and the transactions of the selected date will be converted to an coded string
![image](https://user-images.githubusercontent.com/71954914/176036624-94be1a70-33cd-4b10-aac4-482c59794602.png)




#### 4-Run "Listen to your song and have a good night!"
this section generates the melody by crossing the query´s encoded string and the notes table. Press the play button and enjoy your song!
![image](https://user-images.githubusercontent.com/71954914/176036699-c2064db3-60df-4f76-ab5b-32acf0604214.png)

![image](https://user-images.githubusercontent.com/71954914/176036820-fe563147-c7ef-429a-bc54-ff0cf1884573.png)

![image](https://user-images.githubusercontent.com/71954914/176145596-19592539-f99f-4536-ba7d-2d1839e7e6c0.png)

