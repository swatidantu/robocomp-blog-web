# Problems + Solutions

23rd August, 2019

After testing the component thoroughly for a number of real test cases, I faced a few challenges and here are the ways I tackled them.

### Problem 1:

The component was predicting the second nearest neighbour as the output in a few cases.

Solution: In order to tackle this, I used a weighted distance which gives more weightage to the the labels with larger number of images above the threshold. This ensures that the test image is closest to the output label cluster.

### Problem 2:

Ability to add images directly from camera feed.

Solution: Earlier new people in the database could be added only through images which was very cumbersome. But now I have added a feature which allows user to add images directly from the video feed. It stores all the people's faces in a folder for a fixed number of frames and then user can select the image of the face and the label to be added in the database.

### Problem 3:

Error while adding the new people in the database.

Solution: Sometimes while adding new people in the database, the component was getting confused with the previously stored embeddings. In order to tackle this I adjusted the threshold values and then tested it on a bunch of test cases.

* * *
Aditya Aggarwal
