# Audioscrobbler-Data
UCLA Master of Applied Economics Econ 423 Assignment
Go to 
http://www-etud.iro.umontreal.ca/~bergstrj/audioscrobbler_data.html 
and download the file

      profiledata_06-May-2005.tar.gz
This archive has the following files:

      user_artist_data.txt: user_id artist_id play_count => user_id played artist_id play_count times
      artist_data.txt: artist_id artist_name => artist_id is for artist/group arist_name
      artist_alias.txt: where artist names are misspelled. artist_id1 artist_id2 => artist_id1 is same as artist_id2
      README.txt: A file describing the dataset
 
### PART 1: Audioscrobbler Data: Display Artists and Times Play for a Given User ID - 10 points

Note: In this assignment you can ignore the file artist_alias.txt. 

Write a function that will take a User ID and print names of artists that the user has played together with number of times each artist was played. The function will look like the following (in pseudo code):

      def printListenersTimesPlayed(userID):
         from file user_artist_data.txt find all artists IDs and number of times that the user with userID has played
         from file artist_data, find names of artists that the user has played
         print list of artists and times that the user (with userID) has played
 
Note that the above is just pseudo code. You will need a number of steps for reading, processing, searching, and displaying the data. 
Your program (to be submitted as notebook named ascrob.ipynb) should be written in such a way that it produces output for any user ID that is provided to the program. So I should be able to call your program for any user ID  such as:

      printListenersTimesPlayed(1000208)
and get the list of all artists the user has played together with times the artists has been played by the user. Something similar to the following:

      Great Artist - 34
      Prince - 6
      Abba -12
      BoneyM - 43
Write your program assuming that your data files are in the same directory/folder where the program is being run (use no path). I'll simply put your file in a directory/folder where the data files from audioscrobbler exists and run your file and expect to see the result. You do not get points otherwise.
 
### PART 2: Audioscrobbler Data: Create User-Artist Interaction Matrix - 5 points

Write a function (in notebook named gettimes.ipy) that will read user_artist_data.txt file and build User-Artist Interaction Matrix which is a matrix with as many rows as number of users and as many columns as number of artists. Entries in this matrix are times listened. So for user i and artist j, the entry will give number of times listened. 

The code will look like the following:

      read user_artist_data.txt file
      build user-artist interaction matrix as a two dimension list called userArtistsTime

      def getTimesforUserXArtistY(userID, artistID):
         timesListened = userArtistsTime[userID, artistsID]
         return timesListened 
 
Only external library that you can use is NumPy. You are not allowed to use other external libraries (such as Pandas). Note that you should build a matrix in the function to return timesListened instead of search from the source datafile.
  
PSEUDO CODE 1:

      create an empty list called users
      create an empty list called artists
      open file
      For all lines in the file:
        Read the next line of the file to determine userid and artistid
        append userid to users
        append artistid to artists
      close file
      turn users into a set
      turn artists into a set
      create lisartim, a numpy array of zeros of type int and with as many rows as users and as many columns as artists)
      convert listeners to a numpy array (for the purpose of index lookup)
      convert artists to a numpy array (for the purpose of index lookup)
 
      open file
      For all lines in the file:
        Read the next line of the file to determine userid, artistid, and times.
        determine index i of the artist using artists
        determine index j of the user using users
        put times in lisartim at indices i,j
      close file
#### Now lisrtim has all the entries. 
 
Now define your function:
 
      def getTimesforUserXArtistY(userID, artistID):
         timesListened = lisrtim[userID, artistsID]
         return timesListened 
 
Now write a test program:
 
      uid = 10009
      aid = 10065
      times = getTimesforUserXArtistY(uid, aid)
      print(uid listened to aid for times times)
