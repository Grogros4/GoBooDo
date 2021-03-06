# GoBooDo
### A google books downloader with proxy support.


     .88888.           dP                               dP
    d8'   `88          88                               88
    88        .d8888b. 88d888b. .d8888b. .d8888b. .d888b88 .d8888b.
    88   YP88 88'  `88 88'  `88 88'  `88 88'  `88 88'  `88 88'  `88
    Y8.   .88 88.  .88 88.  .88 88.  .88 88.  .88 88.  .88 88.  .88
     `88888'  `88888P' 88Y8888' `88888P' `88888P' `88888P8 `88888P'
    oooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo


GoBooDo is a python3 program which downloads the books which are available for preview at Google Books. It downloads high resolution image of those pages and combines them to save the file as a PDF. Since Google limits the amount of pages accessible to each individual majorly on the basis of IP address, GoBooDo uses proxies for circumventing that limit and maximizing the number of pages that can be accessed in the preview.

# Usage
For downloading a book GoBooDo requires the book id which can be fetched from the url of the book. For instance consider the example below:
~~~
https://books.google.co.in/books?id=XUwOtdcIWdkC&printsec=frontcover#v=onepage&q&f=false
~~~
in this url the id=XXX is the part we are interested in.

To start downloading:
~~~
python GoBooDo.py --id=XUwOtdcIWdkC
~~~

The configuration can be done in the settings.json and the description is as follows:
~~~
{
  "country":"co.in", //The TLD for the service that is being used.
  "proxy_links":0,   //0 to not allow proxy while fetching page links when current ip is banned otherwise 1.
  "proxy_images":0,  //0 to not allow proxy while fetching page images when current ip is banned otherwise 1.
  "max_retry_links":1, // max retries for fetching a link using proxies.
  "max_retry_images":1 // max retries for a fetching a image using proxies.
}
~~~

The output will be saved as a folder named the 'id' of the book which was given as input. The final PDF will be in the output folder inside it.
Proxies may be added in proxies.txt (a sample proxy has been added already). After the program has finished running once, it will keep the state of the book saved and any subsequent runs will resume from the previous state of links and images.

# Dependencies
~~~
requests
bs4
Pillow
fpdf
html5lib
~~~

# Todo
1. Add proxy integration with a checker.
2. Make the system more robust from being detected by google.
