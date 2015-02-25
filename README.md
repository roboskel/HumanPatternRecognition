# Human-Pattern-Recognition
Real time recongition of humans through laser scans

a)Convert R.O.S. bagfiles to suitable .mat files using 'bag2mat.py':

	Enter desired destination with file ending in .mat

b)Annotate with annotate.py (offline_train is no longer used):

Either provide command line arguments with the same order as below, or run the script without arguments and provide them when prompted

	*Enter timewindow (int)
	
	*Enter frames to set wall (int)
	
	*Enter max range scanned (float)
	
	*Enter filename (string, no quotes)
	
	trained data will be saved as : <input>.<trainingdata>
	
	!!!When asked for max laser range, input the maximum range scanned 
	during the recording, not the maximum range at which you want to train

	$python annotate.py <time_window> <wall_set_frames> <max_scan_range> <mat_file_to_use>

c)create classifier with merge_train.py:

merge_train will create a classifier in the specified folder

	$python merge_train <folder of annotated .mat files>
	
d)Test on live data with hpr.py:

	Publish laser scans on topic /scan, enable intensities, set min_angle, max_angle to -45,45 degrees
	respectively (to be changed).
	
	$rosrun <package_name> hpr.py <classifier path> <.p file with annotated data for validation>

RECOMMENDATION:

	Use same timewindow, and wall set time for each training set, and use the same values when
	evaluating
    
