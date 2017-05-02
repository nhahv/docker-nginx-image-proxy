# docker-nginx-image-proxy
Image cropping with gravity, resizing and compressing on the fly with nginx image_filter module.  Docker container to build your own Cloudinary-like service.

For image crop offset, credit to: https://github.com/bobrik/nginx_image_filter
Crop gravity is very important to us.  We don't get why most image transformer default is set to Center.  Often, we find ourself using crop gravity NorthWest for large image teaser, especially in email.  This is why we have our default to NorthWest.  

# What does this solve?
You have a huge repository of images that need dynamic resize and cropping; which is the most common task of image transform.  You buy your own CDN so Cloudinary can be redundant and expensive.

# What does it not solve?
This does not have a lot of features.

1.  For more advance stuff, we recommend just using Cloudinary or similar service.
2.  There is no plan for SSL or other Caching methods.  We recommend putting a CDN in front, such as (MaxCDN/StackPath/KeyCDN), to provide caching and easy SSL.
3.  If you want thumbnail caching to s3, just write a lambda function and use this server to generate your thumbnail.  Then upload to s3 with the same function.

URL options:
-------------

```yml
code: name - valid values - default
  q: quality - 1-100 - 75 
  w: width - uint - null
  h: height - uint - null
  c: crop - null, 1 - null
  rz: resize - null, 1 - 1
  g: gravity - NorthWest, North, NorthEast, West, Center, East, SouthWest, South, SouthEast - NorthWest
  e: sharpen - 1..100 - 95
  r: rotate - 0, 90, 180, 270 - 0
```

Licence: MIT