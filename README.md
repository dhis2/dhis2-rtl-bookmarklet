# dhis2-rtl

These are some notes / instructions on how to improve the support for Right To Left for DHIS2 data entry app.

## Use the styles fixes in this repo

[style.css](./style.css) contains some fixes for RTL support for DHIS2 data entry app. To test these fixes, there is a bookmarklet that allow you to apply the styles on the fly without installing them on your system.

### Bookmarklet

To install the bookmarklet, go to https://kabaros.github.io/dhis2-rtl/ then drag the link to your Bookmarks Bar. Then you can go to your DHIS2 instance, and click on the bookmarkelt. This will apply the RTL fixes, but the changes will be lost when you refresh.

If you are happy with the styles and want to apply them to your DHIS2 instance for all users, then you can run the following command:


```bash
curl -s https://kabaros.github.io/dhis2-rtl/style.css | curl --data-binary @- "https://url_to_dhis_2_instance/api/files/style"  -H "Content-Type:text/css" -u user:password
```

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

3. In the browser, go to `https://url_to_dhis_2_instance/api/files/style` and you should be able to see the CSS file you uploaded.

4. Then go to a form, and do a hard refresh ("Empty cache and hard reload"  in Chrome), and the forms should then display right-to-left, with the styles applied to it. It's important to do a hard refresh, as otherwise the previous CSS will be cached and served instead.
