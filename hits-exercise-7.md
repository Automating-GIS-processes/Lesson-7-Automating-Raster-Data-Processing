
#HINTS FOR EXERCISE 7

###PROBLEM 1:
- make sure you 
- When downloading the data, pay attention to the parameters you insert for the `urllib.request.urlretrieve( , )` -function. You need to specify the download link and the LOCAL FILE NAME (full path to the final downloaded file with extension .tif) for the function to work correctly. So, something like this:

`urllib.request.urlretrieve( DOWNLOADLINK, LOCALFILEPATH )` # insert here the correct filepaths

- There is a tiny mistake on the last line for printing the info, can you spot it (cannot concatenate str and int) : 
`print("Download completed. Number of tiles downloaded: " + DownloadCount) # add str() around the DownloadCount -variable for printing the correct info message`


###PROBLEM 2:

####DELINEATING FOREST AREAS 

Correct syntax for one file with `gdal_calc.py`

`gdal_calc.py -A Hansen_GFC2015_treecover2000_10S_040E.tif --calc="A>=50" --outfile=tresholded.tif --co="COMPRESS=LZW"`

Note also that the processing takes a few moments!
If running the command with `os.system()` does not work after you made sure the syntax is correct, you can complete the exercise from the command line.


####MERGING FILES AND REDUCING THE OUTPUT RESOLUTION

You might have noticed that the input data is projected in WGS84. Consequently the units of the 
input files are in decimal degrees. 1km at the equator equals approximately 0.0083 decimal degrees and you can use this as the output resolution.

In order to merge files with gdalwarp you need to list all input files after calling the name of the tool. 

`gdalwarp forestlayer1.tif forestlayer2.tif -tr 0.0083 0.0083 mergedForest.tif`


Again, if running the command with `os.system()` in Python does not work after you made sure the syntax is correct, you can complete the exercise from the command line.


