# 2sxc-picture-helper
A helper utility to render a picture tag with all sizes.

## Usage
Copy the file `_Helper-Picture.cshtml` to the directory of your 2sxc app (or content). Then add the following code to the template where you want to setup a picture tag.

At the top:
```
@{
    var helper = CreateInstance("_Helper-Picture.cshtml");
}
```

Where the picture tag should be rendered:
```
@(helper.Picture(Content.Image, 4.0/3.0, 95, 85,"mode=crop&scale=both", Content.Title, new[] { 720, 464, 244, 290, 390 }))
```

The parameters are, in this order:
* `imageSrc`: the image source path
* `imageRatio`: the image ratio, e.g. for 4:3: `4.0/3.0` (attention: needs the .0 to be treated as double; use 0 to disable height restriction)
* `qualityDefault`: JPEG quality used for the 1x and fallback image; usually a higher value than qualityHighRes, e.g. 95
* `qualityHighRes`: JPEG quality used for sizes > 1, e.g. 85
* `defaultParameters`: define additional parameters like crop and scale
* `alternativeText`: the image alternate text
* `sizes`: the array which defines the sizes for each breakpoint, e.g. `new [] { xs, md, sm, md, lg }`

Note that the helper utility will pick up the current framework with [Koi](http://connect-koi.net/) and use its default breakpoints. If you want to change sizes or breakpoints, edit the corresponding lines in `_Helper-Picture.cshtml`. In most cases this won't be needed though.
