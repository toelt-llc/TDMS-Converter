# TDMS-Converter
This repository contains the code for a package that converts TDMS files into pandas data frame for easy usage. 

## Help

You can always get the up to date documentation with

from tdmsUtils import tdmsConverter as tdmsc
help(tdmsc)

## Example usage

The package can be easily used. An example of usage is

    from tdmsUtils import tdmsConverter as tdmsc
    tc = tdmsc.tdmsConverter('./ExampleData/')
    df , total_number_of_channels = tc.convertToDf(debug = False)
    df_avg = tc.averageFiles(df, debug = False)
    
In the ```df``` pandas dataframe you will find all the measurements. An example of how it looks like is

        data	groupName	channelName	filename
    0	x y 0 0.970000 -2.358...	PD_Signal_0	Avg_Data_20190405 09:28:53.72	./ExampleData/0_cold_next_day.tdms
    0	x y 0 0.970000 -2.359...	PD_Signal_0	Avg_Data_20190405 09:29:08.93	./ExampleData/0_cold_next_day.tdms
    0	x y 0 0.970000 -2.359...	PD_Signal_0	Avg_Data_20190405 09:29:24.14	./ExampleData/0_cold_next_day.tdms
    0	x y 0 0.970000 -2.358...	PD_Signal_0	Avg_Data_20190405 09:29:39.35	./ExampleData/0_cold_next_day.tdms
    0	x y 0 0.970000 -2.358...	PD_Signal_0	Avg_Data_20190405 09:29:54.56	./ExampleData/0_cold_next_day.tdms



## Documentation as of 7.4.2019 20:58

Help on module tdmsUtils.tdmsConverter in tdmsUtils:

NAME
    tdmsUtils.tdmsConverter

CLASSES
    builtins.object
        tdmsConverter
    
    class tdmsConverter(builtins.object)
     |  tdmsConverter(path)
     |  
     |  Methods defined here:
     |  
     |  __init__(self, path)
     |      Constructor for the converter
     |  
     |  averageFiles(self, df, debug=False)
     |      This function evaluate the average of all channels for all files.
     |      
     |      Input parameters:
     |      df: dataframe with all the files as obtained by the function
     |      convertToDf() in this package.
     |      
     |      Return Values:
     |      A DataFrame that contains as many records as number of files. The
     |      Dataframe contains two columns: 'filemname' that contains the name
     |      of the file with the path, and 'average' that contains a pandas
     |      dataframe with two columns 'x' and 'y'.
     |  
     |  convertToDf(self, debug=False)
     |      This function convert the content of the Files
     |      into a list. Each element of the list is a pandas
     |      dataframe with two columns: x,y.
     |      
     |      Input parameters:
     |      debug: a boolean. If False no debug text is printed. If
     |      True then debug informations are printed.
     |      data_files: a list with the list of the file names.
     |      Typically this is the value returned by the function
     |      generateFileList().
     |      
     |      Return Value:
     |      1. A pandas dataframe with 3 columns:
     |          'data', 'groupName', and 'channelName'.
     |      2. the number of channels as integer.
     |  
     |  generateFileList(self, debug=False)
     |      Returns the list of file in the folder given as input
     |      as a list.
     |      
     |      Input parameters:
     |      path: a string with the folder name. If the data is in the same folder
     |      as the file, you can use "./"
     |      debug: a boolean variable (can be True or False). If False then
     |      no output is printed. If True then the list of files is printed.$
     |  
     |  getChannelName(self, channelName)
     |      This is a helper function that from the output of the
     |      tdms package for the channel name like
     |      
     |      <TdmsObject with path /'PD_Signal_0'/'Avg_Data_20190404 15:30:45.93'>
     |      
     |      extract the actual channel name. In this case
     |      
     |      Avg_Data_20190404 15:30:45.93
     |      
     |      Input Parameters:
     |      channelName: a channelName as returned, for example, from a loop
     |      like This
     |      
     |      for channel in tdms_file.group_channels(group):
     |          ......
     |      
     |      Return Value:
     |      a string with the channel name, that can be used in the function
     |      
     |      tdms_file.object(str(group), channelName).data
