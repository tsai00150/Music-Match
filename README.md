# Music-Match
A simple program that uses dejavu to check how songs are alike to each other. 

## Prerequisite
Download dejavu [here](https://github.com/worldveil/dejavu)<br />
Follow the steps provided in the tutorial. For simplicity, we will use the "Quickstart with Docker" option to setup the program. Input the following commands in terminal below: <br />
```
$ docker-compose build
$ docker-compose up -d
$ docker-compose run python /bin/bash
```
Then, put the python file inside the dejavu file, then you can execute the program via docker: <br />
```
root@a0015abb31d7:/code# python Music_Match.py
```
You are in the program!<br />
## Functions
There are four commands that you can use:
1. Enter 'a' to input songs to be fingerprinted <br />
2. Enter 'b' to input songs you want to recognize <br />
3. Enter 'x' to exit the system <br />
4. Enter 'h ' to check out the commands <br />

### Input songs to be fingerprinted
These songs will be collecting "fingerprints" in order to compare with other songs later. You need to have a folder that has the same file type (ex. mp3, wav). For example, I have three songs by Taylor Swift inside the folder "Fingerprinted". The folder has the same hierarchy as Music_Match.py. The commands are as follows: 
```
Input a command to use this system (enter 'h' for help):
a
Input the directory that stores all the songs to be fingerprinted:
Fingerprinted
Input '.mp3' or '.wav', which is the file type of all the songs to be fingerprinted:
.wav
Fingerprinting channel 1/2 for Fingerprinted/06 Mine [US Version].wav
Fingerprinting channel 1/2 for Fingerprinted/09 Love Story.wav
Fingerprinting channel 1/2 for Fingerprinted/01 Mine.wav
Finished channel 1/2 for Fingerprinted/06 Mine [US Version].wav
Fingerprinting channel 2/2 for Fingerprinted/06 Mine [US Version].wav
Finished channel 1/2 for Fingerprinted/01 Mine.wav
Finished channel 1/2 for Fingerprinted/09 Love Story.wav
Fingerprinting channel 2/2 for Fingerprinted/01 Mine.wav
Fingerprinting channel 2/2 for Fingerprinted/09 Love Story.wav
Finished channel 2/2 for Fingerprinted/09 Love Story.wav
Finished channel 2/2 for Fingerprinted/06 Mine [US Version].wav
Finished channel 2/2 for Fingerprinted/01 Mine.wav
```
### Input songs you want to recognize
Next, we need to select a song and compare the song to songs that are fingerprinted previously. Select the song "Mine" by Taylor Swift in folder "MusicMatchTests":
```
Input a command to use this system (enter 'h' for help):
b
Input the directory that stores the song you want to recognize:
MusicMatchTests/01 Mine.wav
Song Name                 Match Percentage
01 Mine                       1.00
06 Mine [US Version]          0.14
09 Love Story                 0.09
```
In this case, because the song "Mine" is the same as the one in "Fingerprinted", it is no suprise that the Match Percentage is 1.00. However, with a slight change in instrumentals, "Mine [US Version]" dropped to 0.14 significantly. Let's move on to test a completely song:
```
Input a command to use this system (enter 'h' for help):
b
Input the directory that stores the song you want to recognize:
MusicMatchTests/12 You Belong With Me.wav
Song Name                 Match Percentage
01 Mine                       0.09
06 Mine [US Version]          0.08
09 Love Story                 0.08
```
Looks like dejavu is better at comparing songs that are identical, rather than covers or alternate versions. 
