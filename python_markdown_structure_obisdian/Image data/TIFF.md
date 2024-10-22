___
[[image_data]]
___
Tagged Image File Format ist ein komplexes Bilddatenformat ist ein verlustfreies Format für Bilder mit hohen Qualitätsansprüchen.

Metadaten in .tiff oder .tif werden in der Image File Directory (IFD) gespeichert. Verschiedene Metadaten in dem IFD sind unter bestimmten TagIDs gespeichert und die Rohdaten für jeden Tag sind Teil der .tiff Datei, neben dem TagType, Count und Offset.
___
TIFF-Tags:
https://www.loc.gov/preservation/digital/formats/content/tiff_tags.shtml
___


```python
import tifffile


with tifffile.TiffFile("file_path") as tiff:

    metadata = tiff.pages[0].tags

    for tag in metadata.values():

        print(tag.name, tag.value)


# NewSubfileType FILETYPE.UNDEFINED
# ImageWidth 29626
# ImageLength 8148
# BitsPerSample (8, 8, 8)
# PhotometricInterpretation PHOTOMETRIC.RGB
# ImageDescription ImageJ=1.52p
# unit=cm
# StripOffsets (214,)
# SamplesPerPixel 3
# RowsPerStrip 8148
# StripByteCounts (724177944,)
# XResolution (14812645, 1000000)
# YResolution (14812645, 1000000)
# ResolutionUnit RESUNIT.CENTIMETER
```