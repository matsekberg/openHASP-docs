
# Image
**obj:`img`**

![lv_img](images/lv_ex_img_1.png)

| Property | Value        | Default | Description
|----------|--------------|---------|--------------------------
| src      | [string][10] | ""      | The name of the image file
| auto_size| [bool][2]    | true    | Automatically set the size of the image object to the image source
| offset_x | [int16][9]   | 0       | Shift the picture horizontally relative to the image object
| offset_y | [int16][9]   | 0       | Shift the picture vertically relative to the image object
| zoom     | [uint16][9]  | 256     | A larger value enlarges the images (e.g. `512` double size), a smaller value shrinks it (e.g. `128` half size). Fractional scale works as well. E.g. `281` for `10%` enlargement.
| angle    | [int16][9]   | 0       | Rotate the picture around its pivot point. Angle has `0.1` degree precision, so for `45.8°` use `458`.
| pivot_x  | [int16][9]   | H center| The pivot point of the rotation, by default centered
| pivot_y  | [int16][9]   | V center| The pivot point of the rotation, by default centered
| antialias| [bool][2]    | false   | The quality of the angle and zoom transformation. With enabled anti-aliasing the transformations has a higher quality but they are slower.

!!! note
    You can use `image_recolor` and `image_recolor_opa` from the [image styling][5] properties to apply a color overlay mask.

Either PNG or BIN image files are supported, from flash:

- PNG image are decoded and kept in memory, thus you'll be able to display full-screen images only if your microcontroller [has installed PSram memory](../../getting-started/#recommended-boards),
  else you will be limited to small icons or `BIN` files.

- BIN images are *not* stored in memory and are read from flash each time. This will be slower but allows the use of larger images even if your microcontroller doesn't have PSram.   

- BIN images from flash do not support `zoom` or `angle` transformations.

- Use the online [LVGL Image Converter][16]{target=_blank} to create BIN files. Set the output format to *Binary* or *Binary RGB565*.


???+ example "Example `jsonl`"
    ```json linenums="1"
    {"page":1,"id":34,"obj":"img","src":"L:/image.png","auto_size":0,"w":50}
    ```
   
[1]: ../../data-types/#colors
[2]: ../../data-types/#boolean
[3]: ../../../configuration/gpio/#groupid
[4]: ../../styling/#general
[5]: ../../styling/#image
[6]: ../../styling/#value
[7]: ../../styling/#line
[8]: ../../styling/#scale
[9]: ../../data-types/#integer
[10]: ../../data-types/#string
[11]: ../../data-types/#json-object
[12]: ../../styling/
[13]: ../../styling/#padding-and-margin
[14]: ../../styling/#text
[15]: ../../data-types/#variables
[16]: https://lvgl.io/tools/imageconverter
[17]: ../../../integrations/home-assistant/sampl_conf/#using-tags
[18]: ../../styling/#parts