#What to do if you have problems publishing to RPubs

You may be getting the following error (or a variant thereof):
>Error in function (type, msg, asError = TRUE)  : 
>  SSL certificate problem, verify that the CA cert is OK. Details:
>error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
>Calls: rpubsUpload ... <Anonymous> -> .postForm -> .Call -> <Anonymous> -> fun
>Execution halted

1.  Make sure you have an [RPubs](http://rpubs.com/) account.

1.  Check your RProfile.site file.  You might need to have one in the working directory, it might need to be in the directory with your RStudio executable.  Close RStudio and make sure that, as a minimum, the file has these  lines in it:
> options(rpubs.upload.method = "internal")  
options(RCurlOptions = list(verbose = FALSE, capath = system.file("CurlSSL", "cacert.pem", package = "RCurl"), ssl.verifypeer = FALSE))  

1. Make sure that the packages knitr, RCurl, and bitops have been enabled via a `library()` call or by selecting them in the Packages window in RStudio.

3.  Finally, RPubs seems to not like file names with spaces or underscores.  So if you wanted to call your RPub RR_Project_02 or something similar, why not go with RRProject02 instead.

That's all the things that I found to be troublesome, and generally all the problems seem to be fixed with the above steps.  With the above you ought to be able to publish to RPubs.



Good luck!

