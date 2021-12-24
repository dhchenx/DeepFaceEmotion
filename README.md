# DeepFaceEmotion
A revised DeepFace to have callback function for saving emotion inside program

## Background
Although the [DeepFace](https://github.com/serengil/deepface) project has an amazing abilities to retrieve facial attriburtes in realtime video analysis, the library is not able to provide a callback function so developers can obtain the identified attributes inside their codes. This limits the developer to write automated programs for data mining, for example, automatically retrive the attributes and save the attributes to a csv plain text file. 

Hence, I revised the `deepface` class in the library to fulfile the needs. 

## Usage 
Replace the attached `deepface.py` and `commons/realtime.py` inside the installed deepface lib in python package directory and perform the below example code:

```python
from deepface import DeepFace

count=0

# this function ensures we can write codes to save the timestamp-based facial attributes during processing video
def call_back_func(emotions,age,gender,ts):
    global count
    count+=1
    print(emotions)
    print(age)
    print(gender)
    print()

DeepFace.stream(
    # db_path="../doctor_images",
                # source=0,
                source="video/test2.mp4",
                enable_face_recognition=False, call_back_func=call_back_func,time_threshold=2) # pass call_back_func to the stream function

# do some work based on the retrieved attributes in time series
print("Total Emotions Identification: ",count)


```

## Credit
Say thanks to the [DeepFace](https://github.com/serengil/deepface) project. 

## Note
This revised feature may be unnecessary if the deepface library team adds new features to their library. 

