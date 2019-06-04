# Deep-learning-based-selection-of-human-sperm-with-high-DNA-integrity

Relevant Code for manuscript: Deep learning-based selection of human sperm with high DNA integrity

All image data can be found here: https://figshare.com/articles/Deep_learning-based_selection_of_human_sperm_with_high_DNA_integrity/8124932

These notebooks provide guidance to help others understand the underlying model of the work

If you wish to reproduce all steps taken here, begin with 001_image_preprocessing. Otherwise, skip to step 4 to use the CNN.

One example is provided to demonstrate how to convert the large tif images with many cells into individual, cropped, DFI-labeled cells. 

1. The notebook "01_resort_brightfield_fluorescent_images_to_one_folder" will read in the tif images in "01_original_large_tifs" and output renamed images to the folder "01_renamed_and_sorted_large_tifs"

2. The next notebook "02_get_coordinates_and_crop_images" reads in the new tif images from the folder "01_renamed_and_sorted_large_tifs" and allows individual cells to be cropped. 

	To crop brighfield images: 

	0. begin program, large tif images pops up
	1. find a cell
	1a. 'draw a line' (no line visible) from the front of the head to the back
	1b. click and hold the tip of the head
	1c. drag cursor to the back of head
	1d. release left mouse buttom
    
	2. repeat this for each sperm in brightfield image
	3. click 'n' when done with image (once all cells have been selected)
	4. now new image pops up, go back to step 1, select cells, and click 'n' again when complete
	5. after it goes through all images, if it doesn't find the next one, it quits automatically

3. The next notebook "03_sort_images_into_sets_for_CNN" takes all of the images that you found and sorts them into different sets of training/validation/testing for use by the CNN

4. The notebook "CNN_pretrain_VGG_all_sets_with_post_analysis" will load in all images that have already been cropped and labeled with DFI values (under the figshare repository).

	1. Specific values of interest are output and stored as csv files in the same folder as sets1-7, including:

		a. the predicted DFI values
		b. the accuracy and loss values
		c. a saved .keras model file with weights and model architecture

	2. The post-processing also produces scatterplots and histograms (as given in the final manuscript) to show the predicted versus measured DFI values and model performance

	3. Finally, saliency maps of certain cells are given to highlight regions of interest
	
Thanks for checking out our work!
