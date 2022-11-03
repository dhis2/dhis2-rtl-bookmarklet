# dhis2-rtl-bookmarklet

This bookmarklet improves support for right-to-left languages in DHIS2. For instructions on how to use it and install it, go to: https://dhis2.github.io/dhis2-rtl-bookmarklet/.

### Bookmarklet

To install the bookmarklet, go to https://dhis2.github.io/dhis2-rtl-bookmarklet/ then drag the link to your Bookmarks Bar. Then you can go to your DHIS2 instance, and click on the bookmarkelt. This will apply the RTL fixes, but the changes will be lost when you refresh.


If you are happy with the styles and want to apply them to your DHIS2 instance for all users, then you can run the following command:


```bash
curl -s https://dhis2.github.io/dhis2-rtl-bookmarklet/style.css | curl --data-binary @- "https://url_to_dhis_2_instance/api/files/style"  -H "Content-Type:text/css" -u user:password
```


https://user-images.githubusercontent.com/1014725/199788181-f6ecc26a-f4ec-4f47-ab57-d6c496973de1.mov


| Before | After |
| ---- | --- |
| <img width="1612" alt="image" src="https://user-images.githubusercontent.com/1014725/199567025-d5943ec1-c18f-4182-9a2c-bb43fff6c72f.png"> | <img width="1599" alt="image" src="https://user-images.githubusercontent.com/1014725/199566895-59acef94-96c8-4966-a014-e2ee8cfa4b89.png"> |


## Add Your own styles

If you prefer to not use the syles in this repo, and upload your own CSS fixes for RTL, then follow the steps below:

1. Locally on your machine, create a file named `style.css` and add - as an example - this CSS snippet to it:

```css
.formSection {
  direction: rtl !important;
}
```

or alternatively download [style.css](./style.css) from this repo which fixes many of the rtl issues, and change/add as you see fit.

2. Open a terminal, and navigate to where the style.css file is located. Then Run the curl command described in this documentation link. In your case, the command will be:

```bash
curl --data-binary @style.css "https://url_to_dhis_2_instance/api/files/style"  -H "Content-Type:text/css" -u user:password
```

changing `url_to_dhis_2_instance`, `user` and `password` to the values from your DHIS2 instance.

3. In the browser, go to `https://url_to_dhis_2_instance/api/files/style` and you should be able to see the CSS file you just uploaded.

4. Then go to a form, and do a hard refresh ("Empty cache and hard reload"  in Chrome), and the forms should then display right-to-left, with the styles applied to it. It's important to do a hard refresh, as otherwise the previous CSS will be cached and served instead.
