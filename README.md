# dhis2-rtl

These are some notes / instructions to improve the support for Right To Left for DHIS2 data entry app.

1. Locally on your machine, create a file named style.css and add this CSS snippet to it

.formSection {
  direction: rtl !important;
}

or alternatively download [style.css](./style.css) from this repo which fixes many of 

2. Open a terminal, and navigate to where the style.css file is located. Then Run the curl command described in this documentation link. In your case, the command will be:

curl --data-binary @style.css "https://url_to_dhis_2_instance/api/files/style"  -H "Content-Type:text/css" -u user:password

3. In the browser, go to https://url_to_dhis_2_instance/api/files/style and you should be able to see the CSS file you uploaded.

4. Then go to a form, and do a hard refresh ("Empty cache and hard reload"  in Chrome), and the forms should then display right-to-left, with the styles applied to it. It's important to do a hard refresh, as otherwise the previous CSS will be cached and served instead.
