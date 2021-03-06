---
title: Image Comparison
page_title: Image Comparison
description: "Test Studio is an innovative and easy-to-use automated web, WPF and load testing solution. Test Studio tests support essential technologies like ASP.NET AJAX, Silverlight, PHP and MVC. HTML5, Testing framework, functional testing, performance testing, load testing, exploratory testing, manual testing."
previous_url: /user-guide/code-samples/html/image-comparison.aspx, /user-guide/code-samples/html/image-comparison
position: 1
---
#Perform an Image Comparison in Code#

*I would like to compare a specific image from the browser to one stored on disk.*

##Solution##

Here is sample code showing how to perform an image comparison:

```C#
HtmlImage img = Find.ById<HtmlImage>("myImageId");
System.Drawing.Bitmap actualbmp = img.Capture();
  
ArtOfTest.Common.PixelMap expected = ArtOfTest.Common.PixelMap.FromBitmap(expectedbmp);
ArtOfTest.Common.PixelMap actual = ArtOfTest.Common.PixelMap.FromBitmap(actualbmp);
 
Assert.IsTrue(expected.Compare(actual, 5.0));
```
```VB
Dim img As HtmlImage = Find.ById(Of HtmlImage)("myImageId")
Dim actualbmp As System.Drawing.Bitmap = img.Capture()

Dim expected As ArtOfTest.Common.PixelMap = ArtOfTest.Common.PixelMap.FromBitmap(expectedbmp)
Dim actual As ArtOfTest.Common.PixelMap = ArtOfTest.Common.PixelMap.FromBitmap(actualbmp)

Assert.IsTrue(expected.Compare(actual, 5.0))
```

In the above code I am getting the image of the "myImageId" element from the browser and comparing it to the expected image stored on disk named "myExpected.png". The comparison is allowing a 5% tolerance, meaning there may be up to a 5% difference in the image or else the Assert fails and the test aborts.