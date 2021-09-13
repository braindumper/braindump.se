---
title: "Importing products in to woocommerce"
published: true
date: 2021-09-13
categories:
- blog
- woocommerce
---
One of the startups I'm a co-founder off is an e-commerce site, selling physical products.
We have our own warehouse and distribution chain.

The e-commerce site is running on Woocommerce.
Today the CEO & CMO contacted me regarding a new brand they have signed a deal with. And now they need to get the products up on our site.
As input I got a spreed sheet with the necessary information for adding the products, and a folder containing images for all products.

The industry we are operating in, are not that digitalized, so the images usually comes in different qualities and sizes.
To make them look good I use [ImageMagick](https://imagemagick.org/) to convert all images to the same size, and if the source image is lesser than the output I wan't, it adds a white background and put the image in the center.
[ImageMagick](https://imagemagick.org/) is free and a very competent product that I can highly recommend.

#### Shell script
Run the following commands in the folder where your images are stored.
It will then create a subfolder called output and then convert and store all jpg files in the output folder.
The original images are untouched.
```
mkdir output
for i in *.jpg ; do
convert "$i" -resize 1200x1200 -gravity center -background white -extent 1200x1200  "output/${i%.jpg}.jpg"
done

for i in *.JPG ; do
mv $i ${i%.jpg}.jpg
done
```
Upload all the converted images to a proper path on your site.
Create a csv file with all the necessary data and the path to the image for each product.
Here you can find the documentation and example on how to [create and import the file](https://docs.woocommerce.com/document/product-csv-import-suite-importing-products/)

Good luck!