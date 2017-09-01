Zappen - Testing Notes
======

Initial testing of the open source Pastec image recognition platform (http://pastec.io/) proved successful, and we were able to match an image to itself, similar graphic content between two images, and a photo to graphic images. These tests were performed using computer images and real-world graphics such as CD and LP album covers, book covers, posters, packaging, photographs - any 2-D image of sufficiently complexity could be indexed and successfully matched. 

Once our Zappen mobile camera app was completed, we began testing on a larger set of approximately 3000 images, using the profile pictures from the Zappen team’s personal Facebook liked Pages. These images were processed into a pastec feature detection database, with the camera app pointing to that server’s IP address to use the pastec API as a search engine for smartphone photos (‘Zapping’). We created a webpage to display the full image set for testing photos of these images zapped off a computer screen - https://go.zappen.co/grid. 

Sample search request using Pastec API (http://pastec.io/doc/oss/) :  

curl -X POST --data-binary @/home/test/img/request.jpg http://localhost:4212/index/searcher

When images are processed for features and indexed, it is given two numerical scores: the number of Visual Words found (‘hits’) and the number of features extracted using those words. The higher the number, the more complex an image is. 

curl -X PUT --data-binary @img_123.jpg http://localhost:4212/index/images/123
Image 123 added: 738 hits.
{"image_id":123,"nb_features_extracted":1956,"type":"IMAGE_ADDED"}

Over the course of development, we found that low contrast or very simple images cannot be matched as they do not have enough distinguishing features, which is calculated by contrasting pixels, to be extracted. Using the OpenCV library, we were able to apply additional processing to the input zapped image to enhance the detection of features and increase our rate of success.

Currently, an image file can be successfully matched to itself with as low as 20 hits / 25 features extracted. When matching a Zappen app photo to an indexed image (‘a zapp’), the threshold needs to be higher to take into account photo distortion, focus and noise, with a successful matches occurring around the 50 hit / feature mark and greater. The more complex an image is, the more feature descriptors can be extracted, and thus a more exact match can be found. 
