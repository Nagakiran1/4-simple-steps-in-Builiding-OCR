# 4_Simple_steps_in_Building_OCR-
[Optical character recognition (OCR) is process of classifying opti- cal patterns contained in a digital image. The character recognition is achieved through segmentation, feature extraction and classification.](https://medium.com/datadriveninvestor/4-simple-steps-in-building-ocr-1f41c66099c1)

OCR (optical character recognition) is the recognition of printed or written text characters by a computer. This involves photoscanning of the text character-by-character, analysis of the scanned-in image, and then translation of the character image into character codes, such as ASCII, commonly used in data processing.

In OCR processing, the scanned-in image or bitmap is analyzed for light and dark areas in order to identify each alphabetic letter or numeric digit. When a character is recognized, it is converted into an ASCII code. Special circuit boards and computer chips designed expressly for OCR are used to speed up the recognition process.


Steps involved in Optical Character recognition:-
```

            Steps in Optical Character Recognition :-

              1)      Extract Character boundaries from Image,

              2)      Build a Convolutional Neural Network(ConvNet) in remembering the Character images,

              3)      Load trained Convolutional Neural Network(ConvNet) Model,
              
              4)      Consolidate ConvNet predictions of characters.



```

[The Algorithm is built in a way to segment each individual character in a Image as individual images :-) , followed by recognition and consolidation to text in a Image.](https://medium.com/datadriveninvestor/4-simple-steps-in-building-ocr-1f41c66099c1)

 - to download the pre-trained Models [Pretrained Models](https://drive.google.com/file/d/1ckskSVzzFpkaMO7VyTZo0fz_m32q_S_C/view?usp=sharing)
 - to download sample [labelled character Images](https://drive.google.com/drive/folders/1q4PjRX121lj6BGDAhnM8fh1TiC78-ylO?usp=sharing)


![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/OCR_Algorithm.PNG)


**1) Optical Scanning :scissors: from Image :**

 - Select any document or letter of having text information 
 ![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/sample.jpg) 
 -  ***Extract Character boundaries***
             Contours can be explained simply as a curve joining all the continuous points (along the boundary). The contours are a useful tool for shape analysis and object detection and recognition. Here Contours explained in differentiating each individual character in an image with using [contour dilation](https://docs.opencv.org/trunk/d9/d61/tutorial_py_morphological_ops.html) technique.
             Create a boundary to each character in an image with using [OpenCV Contours](https://docs.opencv.org/3.3.0/dd/d49/tutorial_py_contour_features.html) method. 
             Character recognition with the use ofOpenCV contours method

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/Countours.PNG)


            
***Naming Convention followed***
the extracted Text characters should be labelled with the Original character associated with it.

Here the Naming convention followed for the letters is last letter of file name should be the name associated with the character.
             
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/character%20Labelling.PNG)
 


- ***Pre-processing***
1) The raw data depending on the data acquisition type is subjected to a number of preliminary processing steps to make it usable in the descriptive stages of character analysis. The image resulting from scanning process may contain certain amount of noise

2) Smoothing implies both filling and thinning. Filling eliminates small breaks, gaps and holes in digitized characters while thinning reduces width of line.

            (a) noise reduction

            (b) normalization of the data and

            (c) compression in the amount of information to be retained.

            

 
 
 
**2) Build a ConvNet Model  :scissors:(Character Recognition Model):**


  Convolution Network of 8 layers with 2\*4 layers residual feedbacks used in remembering the Patterns  :scissors: of the Individual Character Images.
  
 
  ![alt text](https://github.com/Nagakiran1/Receipt_Image_Classification-/blob/master/ConvNet1.png)
 
- [x] 1st Model will train on the Individual Character Images with direct Classification to predict the Images with softmax Classification of Character Categories.
- [ ] 2nd Model is same model with last before layer as predictor which will Calculate a Embedding of specified Flatten Neurons ( The Predicted flatten Values will have Feature Information of Receipt Images ).
            
  - Convolution Last before layer Embedding Output is considered as Pattern Feature of Image.

**3) Load Trained ConvNet OCR model:**

Optical Character recognition last step involves preprocessing of image into specific word related contours and letter contours, followed by prediction and consolidating according to letter and word related contours in an image.


once affter training the model loading the pre-trained Optical character recognition model.

- !) Once after training the OCR model on labelled names data, load the pre trained model in recognising the specific character. .
- !!) Predict each character image and label it with the prediction associated with the Optical character recognition technique.


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/OCR%20workflow.PNG)




            
**4) Test and Consolidate Predictions of OCR :**

Consolidate predicitons involves, assigning specific ID to each word related contour with the line associated with the word in image, Consolidating all predictions in a sorted series of specific word related contour and letters associated word.
![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/Word_contour.PNG)

- Predict each character image and label it with the prediction associated with the Optical character recognition technique.
- Fix the word associated with the prediction with the use of word contour and line through line related contour and consolidate all together.


/play rimshot
