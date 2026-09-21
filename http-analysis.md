# HTTP Analysis

## Request #1 - HTML Document

- **Method:** GET
- **URL:** https://en.wikipedia.org/wiki/Fitchburg_State_University
- **Status:** 304 Not Modified

### Response Headers: 
1. **Content-Type:** text/html; charset=UTF-8
    - Tells the browser that the response is an HTML document and the text uses UTF-8 character encoding.

2. **Cache-Control:** private, s-maxage=0, max-age=0, must-revalidate, no-transform
    - Helps ensure the page is current because it tells the browser not to use a stored copy before validating it with the server.

## Request #2 - JPEG

- **Method:** GET
- **URL:** https://upload.wikimedia.org/wikipedia/en/1/11/Fitchburg_State_University_Seal.jpg?utm_source=en.wikipedia.org&utm_campaign=parser&utm_content=thumbnail_unscaled 
- **Status:** 200 OK

### Response Headers: 
1. **Content-Type:** image/jpeg 
    - Tells the browser that the response is a JPEG image so it knows how to display the file.

2. **Content-Length:** 142875
    - Size of the response body 

## Request #3 - Stylesheet

- **Method:** GET
- **URL:** https://en.wikipedia.org/w/load.php?...
- **Status:** 200 OK

### Response Headers: 
1. **Content-Type:** text/css; charset=utf-8
    - Tells the browser that the response contains CSS code and that the text uses UTF-8 character encoding.

2. **Cache-Control:** public, max-age=300, s-maxage=300, stale-while-revalidate=60 
    - Tells the browser that the stylesheet can be cached for 300 seconds (max age) and can temporarily use an older copy while checking for an updated version.

## Analysis
Based on the loading times provided in the Network column of the Fitchburg State Wikipedia page, the HTML document took the longest to load. It took 120ms, while the stylesheet was only 25ms and the JPEG was 0ms. The HTML may have taken longer because it is the main page resource and contains the structure as well as the information that the browser needs before it can fully display the page. The other two may have loaded more quickly because they are smaller or because some of their data was already available in the browser’s cache. 

The status codes and response headers also gave the browser information about how to handle each response. The HTML returned a status code of 304 Not Modified, which tells the browser that the version that was already stored in its cache is still current. This means that downloading the entire document again is unnecessary. The Cache-Control header also provides instructions about how the browser should handle caching. The Content-Type headers tell the browser what type of content it received, such as HTML, CSS, or JPEG.

Something that surprised me was how many requests are necessary for a website to load. I think it’s interesting to see all of the different resources a browser requests in order to load the full web page.
