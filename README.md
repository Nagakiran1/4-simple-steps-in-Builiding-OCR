# 4_Simple_steps_in_Building_OCR-
Optical character recognition (OCR) is process of classifying opti- cal patterns contained in a digital image. The character recognition is achieved through segmentation, feature extraction and classification.

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

The Algorithm is built in a way to segment each individual character in a Image as individual images :-) , followed by recognition and consolidation to text in a Image.

 - to download the pre-trained Models [Pretrained Models](https://drive.google.com/file/d/1ckskSVzzFpkaMO7VyTZo0fz_m32q_S_C/view?usp=sharing)
 - to download sample labelled character Images data [Receipt Images](https://drive.google.com/drive/folders/1q4PjRX121lj6BGDAhnM8fh1TiC78-ylO?usp=sharing)


![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/OCR_Algorithm.PNG)


**1) Optical Scanning :scissors: from Image :**

 - Select any document or letter of having text information 
 ![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/sample.jpg) 
 -  ***Extract Character boundaries***
             Contours can be explained simply as a curve joining all the continuous points (along the boundary). The contours are a useful tool for shape analysis and object detection and recognition. Here Contours explained in differentiating each individual character in an image with using [contour dilation](https://docs.opencv.org/trunk/d9/d61/tutorial_py_morphological_ops.html) technique.
             Create a boundary to each character in an image with using [OpenCV Contours](https://docs.opencv.org/3.3.0/dd/d49/tutorial_py_contour_features.html) method. 
             Character recognition with the use ofOpenCV contours method

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/Countours.PNG)





- ***Pre-processing***
1) The raw data depending on the data acquisition type is subjected to a number of preliminary processing steps to make it usable in the descriptive stages of character analysis. The image resulting from scanning process may contain certain amount of noise

2) Smoothing implies both filling and thinning. Filling eliminates small breaks, gaps and holes in digitized characters while thinning reduces width of line.

            (a) noise reduction

            (b) normalization of the data and

            (c) compression in the amount of information to be retained.
            a. Noise Reduction
- ***Noise reduction***: The noise introduced by the optical scanning device or the writing instrument causes disconnected line segments, bumps and gaps in lines, filled loops, etc. The distortion including local variations, rounding of corners, dilation and erosion is a potential problem.

            (i) filtering
            (ii) morphological operations and 
            (iii) noise modeling.
            b. Normalization:
            The normalization methods aim to remove the variations of the writing and obtain standardized data. Some of the commonly used methods for normalization are

            (i) skew normalization and baseline extraction
            (ii) slant normalization 
            (iii) size normalization and 
            (iv) contour smoothing


***Naming Convention followed***
the extracted Text characters should be labelled with the Original character associated with it.

Here the Naming convention followed for the letters is last letter of file name should be the name associated with the character.
             
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![alt text](https://github.com/Nagakiran1/4-simple-steps-in-Builiding-OCR/blob/master/character%20Labelling.PNG)
 
 
 
 
**2) Build a ConvNet Model  :scissors:(Character Recognition Model):**


  Convolution Network of 8 layers with 2\*4 layers residual feedbacks used in remembering the Patterns  :scissors: of the Individual Character Images.
  
 
  ![alt text](https://github.com/Nagakiran1/Receipt_Image_Classification-/blob/master/ConvNet1.png)
  
  - Character Recognition Convolution Network is built to work as two models, 

- [x] 1st Model will train on the Receipt Images with direct Classification to predict the Images with softmax Classification of Receipt Categories.
- [ ] 2nd Model is same model with last before layer as predictor which will Calculate a Embedding of specified Flatten Neurons ( The Predicted flatten Values will have Feature Information of Receipt Images ).
            
  - Convolution Last before layer Embedding Output is considered as Pattern Feature of Image.

**2) Text Feature Extraction (OCR in Extracting Text):**

Receipt text information conveys much information in classifying the Receipt, but conventional Neural Networks cannot learn on the Text features in the Image. 

So to use the Text as Features, 2 stages of processing is needed.

- !) Recognizing the Text of Receipt or any Image. Here Tesseract Optical Recognition technique is used in recognizing the text and extracting from image.
- !!) Extracted Text of Receipt and Images are fed to the Sequential LSTM Classification Network. (In classifying the Text the ).

  ![alt text](https://github.com/Nagakiran1/Receipt_Image_Classification-/blob/master/OpticalCharacterRecognition.jpg)
  
  
  ![alt text](https://github.com/Nagakiran1/Receipt_Image_Classification-/blob/master/Models/BindingBox3.jpg)

  - LSTM Sequential models is also built to work as two models, 

- [x] 1st Model will train on the Receipt text with direct Classification to classify text with softmax Classification of Receipt Categories.
- [x] 2nd Model is same model with last before layer as predictor which will Calculate a Embedding of specified Flatten Neurons ( The Predicted flatten Values will have Feature Information Text key words).
            
            
            
**3) Receipt Classifier :**

Receipt Classifier is the main model in Classifying the Image either as Receipt or not.

- The Receipt Classifier is the Neural Network of having two 1 Dimensional convolution layers( to keep rememeber the Receipt Image pattern Information) and followed by 1 LSTM layer(to keep remember the Sequence of Receipt key words). 
- Input to the Network is given by the concatenated features of Pattern information Predicted Embedding values and Text Features extraction model Embedding output.

/play rimshot
