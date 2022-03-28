Zappen Server - Pastec
======

Introduction
------------

Zappen image recognition server, forked from Pastec with image processing enhancements, to be used with Zappen camera app functionality (https://github.com/yesexactly/zappen-camera-app). Server URL and port should be entered into zappen-camera-app/app/components/ZappenCamera.js to connect. 

Zapp image URL should be stored in the image TAGS JSON as 'url': 
curl -X PUT -d "{'url':'https://www.foo.com'}"  http://ZAPPEN_SERVER:4212/index/images/1/tag


### Presentation

[Pastec](http://www.pastec.io) is an open source index and search engine for image recognition based on [OpenCV](http://www.opencv.org/). It can recognize flat objects such as covers, packaged goods or artworks. It has, however, not been designed to recognize faces, 3D objects, barcodes, or QR codes.

Pastec can be, for example, used to recognize DVD covers in a mobile app or detect near duplicate images in a big database.

Pastec does not store the pixels of the images in its database. It stores a signature of each image thanks to the technique of [visual words](http://en.wikipedia.org/wiki/Visual_Word).

Pastec offers a tiny HTTP API using JSON to add, remove, and search for images in the index.

### Intellectual property

Pastec is developed by [Visualink](http://www.visualink.io) and licensed under the [GNU LGPL v3.0](http://www.gnu.org/licenses/lgpl.html).
It is based on the free packages of [OpenCV](http://www.opencv.org/) that are available for commercial purposes; you should therefore be free to use Pastec without paying for any patent license.

More precisely, Pastec uses the [patent-free ORB descriptor](https://www.willowgarage.com/sites/default/files/orb_final.pdf) and not the well-known SIFT and SURF descriptors that are patented.

Setup
-----

See [here](http://pastec.io/doc#setup).

API
---

See [here](http://pastec.io/doc#api)

