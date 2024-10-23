# Text-Extraction

Project Title: Text Extraction from Images using EasyOCR and OpenCV
Objective:

The purpose of this project is to extract and recognize text from images using Optical Character Recognition (OCR) techniques. By leveraging the EasyOCR library, which supports multiple languages, we aim to detect text in an image, highlight it with bounding boxes, and display the results visually. This project demonstrates a simple, yet powerful, way to process images and retrieve textual information, which can be applied in fields like document scanning, image analysis, and more.
Libraries Used:

   - OpenCV: OpenCV (Open Source Computer Vision Library) is used for image processing and manipulation. We use it to load the image, process the image's coordinates, and draw rectangles around the detected text regions.

   - EasyOCR: EasyOCR is a Python-based OCR library that uses deep learning techniques to recognize text in various languages. It processes images and returns the detected text, along with the coordinates of the bounding boxes surrounding the text.

   - Google Colab Utilities: We use utilities like cv2_imshow and files.upload to upload images and display results within the Google Colab environment.


Explanation of Output Structure:

The EasyOCR output returns a list of detected text, where each entry contains:

    A set of four coordinates representing the corners of the bounding box around the text.
    The detected text itself.
    A confidence score indicating how certain the OCR model is about the detection.

Example output:

python

[
  ([[2364, 1502], [3703, 1502], [3703, 1760], [2364, 1760]], 'I SEE A LIGHT', 0.6275207746614941),
  ([[2660, 1837], [3376, 1837], [3376, 2084], [2660, 2084]], 'IN THE', 0.9295644309908175),
  ([[2487, 2158], [3592, 2158], [3592, 2423], [2487, 2423]], 'DARKNESS', 0.9997958741827272)
]

    Coordinates: [[2364, 1502], [3703, 1502], [3703, 1760], [2364, 1760]] These represent the four corners of the rectangle around the text in the image. The points correspond to:
       - Top-left corner
       - Top-right corner
       - Bottom-right corner
       - Bottom-left corner

    Detected Text: 'I SEE A LIGHT' This is the actual text that the OCR model detected within the bounding box.

    Confidence Score: 0.6275207746614941 This indicates the model's confidence in detecting the text. A score closer to 1.0 means higher confidence.


How the Code Works:

 1.  Image Upload: We begin by uploading an image using files.upload() in Google Colab. This allows us to choose an image file from the local device and load it into the project.

 2.   Reading the Image: The image is loaded using cv2.imread(), which reads the image into a matrix of pixel values.

 3.   Text Detection: The easyocr.Reader() object is initialized to detect text in English (or multiple languages). We pass the image to the readtext() function, which returns a list of detected text entries, each containing:
        The bounding box coordinates.
        The recognized text.
        A confidence score.

  4.   Drawing Bounding Boxes: Using OpenCV, we draw rectangles around the detected text by passing the top-left and bottom-right coordinates to cv2.rectangle(). We also display the detected text near each box using cv2.putText().

  5.   Displaying the Processed Image: Finally, we use cv2_imshow() to display the image with the text highlighted.

----------------------------------------

Why We Use OpenCV and Bounding Boxes:

  -  Why cv2.rectangle() and Bounding Boxes?
    OpenCV's cv2.rectangle() function is used to draw rectangles around the text regions. It requires two points: the top-left corner and the bottom-right corner. By extracting these from the list of coordinates returned by EasyOCR, we can visualize exactly where the text was detected on the image.

  -   Why cv2.putText()?
    After detecting the text, we want to label it directly on the image for clarity. cv2.putText() allows us to draw the text string at a specified location. The coordinates of the top-left corner of the bounding box are used as the starting point for placing the text.
