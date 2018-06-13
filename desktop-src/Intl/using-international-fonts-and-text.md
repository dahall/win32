---
Description: In each major release of Windows, there are fonts added to support international languages and scripts.
ms.assetid: 77b8c200-2682-4651-855a-602f768edc9b
title: International Font Enumeration and Selection
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# International Font Enumeration and Selection

In each major release of Windows, there are fonts added to support international languages and scripts. Please reference [Script and Font Support in Windows](http://msdn.microsoft.com/en-us/goglobal/bb688099.aspx) for the fonts that have been added in each Windows version since Windows 2000, as well as their supported scripts, regions, and languages.

## EnumFontFamiliesEx

To enumerate international fonts in your application, you can use the [**EnumFontFamiliesEx**](https://msdn.microsoft.com/4d70906d-8005-4c4a-869e-16dd3e6fa3f2) function. **EnumFontFamiliesEx** allows you to enumerate fonts based on typeface name and charset by passing in a pointer to a [**LOGFONT**](https://msdn.microsoft.com/57658a03-0a6d-4a28-a7c1-c65ec145beb4) structure that contains the typeface name and charset information. To call **EnumFontFamiliesEx**, you can either specify a typeface name or a charset, or you can ask for whatever is available. Setting the typeface name of the **LOGFONT** to **NULL** enumerates all typeface names. Setting the charset field to **DEFAULT\_CHARSET** enumerates all charsets.

Note that charsets are a legacy notion corresponding to pre-Unicode character sets. At this time, there is no mechanism to enumerate fonts supporting arbitrary scripts or character ranges in Unicode. The [**NEWTEXTMETRICEX**](https://msdn.microsoft.com/b85ff705-2dd4-4877-9905-d4c2a0894e24) structure passed by [**EnumFontFamExProc**](https://msdn.microsoft.com/a4adad4c-ab6a-4adb-a1d3-fea3cfdbaf73) includes the [**FONTSIGNATURE**](/windows/desktop/api/Wingdi/ns-wingdi-tagfontsignature) structure, which includes more detailed declarations provided by the font developer as to what code pages and what Unicode ranges the font supports. To determine more precisely what character ranges a given font supports, select the font into a device context and call [**GetFontUnicodeRanges**](https://msdn.microsoft.com/51b0ab12-c467-4a89-8173-fdc513868aae). Note that this API does not support Unicode supplementary planes.

## ChooseFont

You can use the [**ChooseFont**](https://www.bing.com/search?q=**ChooseFont**) function to display a common dialog box that allows the user to select international fonts based on charset. You can specify one of three flags to determine, based on charset, which fonts are displayed in the ChooseFont dialog: **CF\_SCRIPTSONLY**, **CF\_SELECTSCRIPT**, or **CF\_NOSCRIPTSEL**.

The **CF\_SCRIPTSONLY** flag tells the API to list fonts for all character sets that are not Symbol or OEM.

If you want to display only fonts that cover a particular charset, you need to specify the flag **CF\_SELECTSCRIPT**. Before calling [**ChooseFont**](https://www.bing.com/search?q=**ChooseFont**), initialize the *lfCharSet* field of the [**LOGFONT**](https://msdn.microsoft.com/57658a03-0a6d-4a28-a7c1-c65ec145beb4) structure. If you are interested in specifying only the charset, set the other fields of the **LOGFONT** structure to **NULL**. To have **ChooseFont** look at the **LOGFONT** structure, you also need to specify the **CF\_INITTOLOGFONTSTRUCT** flag.

Finally, as with any other field in the Font dialog box, you might choose to display a blank script list box. This capability is useful if the user has highlighted several different fonts spanning several charsets. In this case, you would call [**ChooseFont**](https://www.bing.com/search?q=**ChooseFont**) with the **CF\_NOSCRIPTSEL** flag.

Starting with Windows 7, [**ChooseFont**](https://www.bing.com/search?q=**ChooseFont**) implements support for the hiding of fonts from font selection lists. **ChooseFont** will only list the shown fonts and filter out the hidden fonts while displaying fonts in the list box. The additional flag (**CF\_INACTIVEFONTS**) in the flags member of the [**CHOOSEFONT**](https://www.bing.com/search?q=**CHOOSEFONT**) structure is added to allow you to display all the installed fonts in the font list, the same as **ChooseFont** behaved before Windows 7. For the details of behavior differences in Windows 7 for the **ChooseFont** function, please see [**ChooseFont() Win32 Common Dialog**](https://msdn.microsoft.com/ee1df9f2-585f-4208-ad49-a0f6ba76f53a) in the [Windows 7 Application Quality Cookbook](https://msdn.microsoft.com/68fe0b82-b6b3-4766-9699-3f2892d3f8e5). Please reference **ChooseFont** function and **CHOOSEFONT** structure for the end user experience differences in Windows 7.

Note that charsets are a legacy notion corresponding to pre-Unicode character sets. At this time, there is no mechanism to filter fonts based on Unicode scripts or character ranges.

## Font Controls in Windows Scenic Ribbon

Windows 7 introduces the Windows Scenic Ribbon which comes with a set of controls targeted to font selection. These font controls support the new Windows 7 font hiding behavior. You can use those font controls to list only shown fonts and allow the user to select the font.

> [!Note]  
> Support for hiding fonts is not available when the Windows Scenic Ribbon is running on any platform prior to Windows 7.

 

## Related topics

<dl> <dt>

[**EnumFontFamiliesEx**](https://msdn.microsoft.com/4d70906d-8005-4c4a-869e-16dd3e6fa3f2)
</dt> <dt>

[**ChooseFont**](https://www.bing.com/search?q=**ChooseFont**)
</dt> <dt>

[**CHOOSEFONT structure**](https://www.bing.com/search?q=**CHOOSEFONT+structure**)
</dt> <dt>

[**Font Controls in Windows Scenic Ribbon**](https://msdn.microsoft.com/windows/desktop/98eddab5-28cb-4b9d-a788-ee28dd6055b1)
</dt> <dt>

[**ChooseFont() Win32 Common Dialog**](https://msdn.microsoft.com/ee1df9f2-585f-4208-ad49-a0f6ba76f53a)
</dt> </dl>

 

 


