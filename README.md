## This repository is for a take home object detection challenge
This challenge required us to use transfer learning ml approach to solve the problem.
Task: It was to use images shared by the organisation as the training set and output the coordinates for the bounding boxes containing the twitter “following button”.

The output should be a list of arrays containing the bounding boxes of the following buttons for each picture:

[ymin, xmin, ymax, xmax]

## Hint: for validation, keep 1 picture away from the training data and then use it as the validation image.

The folder structure is as follows:
1. annotations - This folder stores all the .csv and tf.record files which contain a list of annotated images.
2. images - This folder stores all the train and validation images along with their .xml versions.
3. pre-trained model - This folder contains the pre-trained model checkpoint which is used as 
a starting checkpoint in training.
4. training - This folder contains the label_pbtext file as well pipeline training configuration file
generated during training.
5. trained-inference-graphs-1 - This folder contains inference graph which can be used to perform object detection.

Apart from these folders there are couple of files for entire set-up ans training purposes.
1. requirements.txt - file specifying the packages/libraries needed for the environment.
2. train.py - script to run the training job.
3. export_inference_graph.py - script to extract inference graph.

The entire process in brief is as follows:
1. Tensorflow=1.14 was used for this object detection task.
2. I created a workspace which contained the above folders. I segregated train and test images in their 
respective folders.
3. The images were annotated using labelimg package and .xml files were generated for each image.
4. Label Map was created with a single label for training and detection purpose and saved in the annotations folder.
5. Using .xml files training and validation images were converted to .csv file and these .csv files were then 
converted to tf.record file. All of the files are saved in the annotations folder.
6. For this task I used the ssd_inception_v2_coco model and downloaded the .tar.gz file as well as ssd_inception_v2_coco.config file and unzipped the contents in pretrained model folder.
7. Later the .config file for this model was edited using a code editor with num_classes set to 1, feature_extractor
type as ssd_inception_v2, batch_size to 1, learning_rate to 0.001, fine_tune_checkpoint : to ckpt file in pre-trained folder,
num_steps to 300 and input path of train files to tf.record file. This .config file was saved in the training folder.
8. The training was started with using the train.py script.
9. Once the training was done, inference graph was extracted using the script.

This model was tested with jupyter notebook provided in the notebook folder.
For more in depth information, kindly visit 
https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/training.html#configuring-a-training-pipeline

