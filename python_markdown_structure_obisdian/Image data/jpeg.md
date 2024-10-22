___
[[image_data]]
___
Bilder in der Regel aufgenommen mit einer Kamera oder einem Smartphone haben das Format der Joint Photographic Experts Group or JPEG.

Der Metadata Standard für .jpeg Bilder ist Exif (Exchangeable Image File Format). JPG speichert grundlegende Metadata wie Datum, Einstellungen und Ort.

In Python kann Metadata extrahiert werden:
```python

import pprint

import PIL.ExifTags

from PIL import Image

  

# Open the image

image = Image.open('C:/Users/olean/Pictures/RICOH_ZBAR_2019/RIMG0212.jpg')

  
# Extract the EXIF metadata

exif_data = image.getexif()

print(exif_data, type(exif_data)) # <class 'PIL.Image.Exif'> also ein Exif-Objekt

  

for key, value in exif_data.items():

    print(key, value)


# Dictionary comprehension

exif = {

    PIL.ExifTags.TAGS[k]: v

    for k, v in image._getexif().items()

    if k in PIL.ExifTags.TAGS

}

  

pprint.pp(exif)

# {'ResolutionUnit': 2,
 # 'ExifOffset': 220,
 # 'Make': 'RICOH IMAGING COMPANY, LTD.',
 # 'Model': 'RICOH WG-50',
 # 'Software': 'RICOH WG-50 Ver. 1.00',
 # 'Orientation': 1,
 # 'DateTime': '2023:07:03 18:24:24',
 # 'XResolution': 72.0,
 # 'YResolution': 72.0,
 # 'ExifVersion': b'0230',
 # 'ComponentsConfiguration': b'\x01\x02\x03\x00',
 # 'ColorSpace': 1,
 # 'DateTimeOriginal': '2020:01:28 16:58:32',
 # 'ExposureBiasValue': 0.0,
 # 'ExifImageWidth': 2068,
 # 'ExifImageHeight': 2514,
 # 'MeteringMode': 5,
 # 'ExposureMode': 0,
 # 'Flash': 16,
 # 'FocalLength': 6.1,
 # 'WhiteBalance': 0,
 # 'DigitalZoomRatio': 1.0,
 # 'FocalLengthIn35mmFilm': 34,
 # 'SceneCaptureType': 0,
 # 'Contrast': 0,
 # 'Saturation': 0,
 # 'Sharpness': 0,
 # 'SubjectDistanceRange': 2,
 # 'ExposureTime': 0.005,
 # 'FNumber': 3.8,
 # 'ISOSpeedRatings': 400}
```