Image file processing notes

```sh
cd ~/lab/vitessce/big-data/hubmap-arwg-2023

# File 1:
# Rename using .ome.tif rather than .ome.tiff
mv ./DON218-ND-52yM-T1A.ome.tiff ./DON218-ND-52yM-T1A.ome.tif

# Get OME-XML metadata
~/software/bftools/tiffcomment ./DON218-ND-52yM-T1A.ome.tif > ./DON218-ND-52yM-T1A.ome.xml

# Generate pyramidal OME-TIFF
~/software/bftools/bfconvert -tilex 512 -tiley 512 -pyramid-resolutions 5 -pyramid-scale 2 -compression LZW ./DON218-ND-52yM-T1A.ome.tif ./DON218-ND-52yM-T1A.pyramid.ome.tif

# Get OME-XML metadata for pyramidal file
~/software/bftools/tiffcomment ./DON218-ND-52yM-T1A.pyramid.ome.tif > ./DON218-ND-52yM-T1A.pyramid.ome.xml


# File 2:
# Convert QPTIFF to OME-TIFF
~/software/bftools/bfconvert ./Repeat_Test-2_Scan1.qptiff ./Repeat_Test-2_Scan1.ome.tif

# Get OME-XML metadata
~/software/bftools/tiffcomment ./Repeat_Test-2_Scan1.ome.tif > ./Repeat_Test-2_Scan1.ome.xml

# Generate pyramidal OME-TIFF
~/software/bftools/bfconvert -overwrite -tilex 512 -tiley 512 -pyramid-resolutions 5 -pyramid-scale 2 -compression LZW ./Repeat_Test-2_Scan1.ome.tif ./Repeat_Test-2_Scan1.pyramid.ome.tif

# Get OME-XML metadata for pyramidal file
~/software/bftools/tiffcomment ./Repeat_Test-2_Scan1.pyramid.ome.tif > ./Repeat_Test-2_Scan1.pyramid.ome.xml
```

Upload using `gsutil cp`