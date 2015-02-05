# PyTN
This started as a talk on the tools of data science in python for the PyTN 2015 conference. I give a description of the data and the tools I used below.

## Python tools

### iPython notebook (Project Jupyter)
I did this presentation in iPython notebook. The notebook, now called Project Jupyter, is a great tool for mixing code and notes in one file that you can pass around to other people. You can find instructions for downloading the notebook here:
http://ipython.org/install.html

### pandas
pandas is a great library for munging and analyzing data. The library uses two main data structures, a Series, which is a one dimensional array, and a Dataframe, a two dimensional array much like a spreadsheet. 
These data structures let you easily shift your data around, fill in missing values, create pivot tables, plot your data and run numerical analysis

### numpy 
pandas data structures are built on top of numpy ndarrays, which are very fast, very efficient n dimensional arrays which let you perform incredibly fast calculations on array data, specifically linear algebra and Fourier transforms.  You can see how to install numpy here:
http://www.scipy.org/scipylib/download.html

### matplotlib
matplotlib helps you make pretty pictures with you data. It's an easy to use library of plotting functions that works closely with both numpy and pandas. You can see how to install it here:
http://matplotlib.org/users/installing.html

## scikit-learn or sklearn
sklearn is a machine learning package. It has many of the standard ML algorithms that you would use in data analysis and data mining, many of which are  built on top of numpy's efficient ndarrays. Install it from here:
http://scikit-learn.org/stable/install.html

## Anaconda
If you don't want to download all these packages individually and you don't already have a python distribution that you are happy with, you might want to checkout Anaconda, a free python distro that has a huge number of libraries for various scientific endeavors. You can check it out here:
http://continuum.io/downloads

# The data we'll be looking at

The data for this project all came from https://www.govtrack.us/developers which collects and stores all the voting records for Congress all the way back to the first Congress. They have well documented API that lets you grab bills, votes and Congress members, committee members, etc. You can also bulk load data, which is the recommended way if you need a lot of their data spanning many years.

This project started out in response to the popularly held opinion that Congress is so partisan that it is almost impossible for anything to get accomplished, so I asked  the question: "Can we train a machine to properly predict Congressional votes baased on the party of the sponsor?" Political scientists have a deep affinity for statistical analysis, but there are very few cases where anyone has applied modern machine learning to political science and I wanted to see if it was worthwhile to try to do so. This first attempt will ultimately use a very small set of inputs, just the party of the sponsor of a bill and the party of the Congressional voter. This is an introductory attempt to train a simple machine, in our case the Perceptron, to learn voting patterns based soley on these two inputs. 

In order to get this data, I had to look in three sets of files:
* The vote files, which stores the information specific to a vote on a bill. Each bill could have several votes so the vote has a unique id along with an id of the bill it is attached to. There is also a list of the Congress-people voting yes or no, along with those that voted present or not voting.
* The bill file holds the specific information on a bill, such as the sponsor(s) the committees, the house of Congress, the outcome of all the votes, etc.
* The current and former Congress members. While the other files are in json format, these files are csv. They hold various pieces of information such as the state, office, party, youtube channel, twitter handle, etc for each member of Congress. 

At various times I had to cross reference these files to build to final dataset. The vote contains a bill id to get the bill information. The bill contains the thomas id of the sponsor, which you can find in the legislators csv file. If you're so inclined, I'm sure you can dig deeper into the files and find all manner of connections. Just remember the warning from Otto von Bismarck "Laws are like sausages, it is better not to see them being made". 

I hope you find this useful.  Please give me feedback!

Derik
@\_gignosko\_
