# jellyseer-request-removal-script
Jellyseerr remove all content requests automatically.

Just paste the following script into the browser console and it will automatically remove all the requests 1 by one. However if your request count exceeds the max page-length, you might need to run this several times.


```js
var elements = $("span").filter(function() {
    return $(this).text() === "Delete Request"; // Filter span elements containing the text "Delete Request"
});

function clickSpanAtIndex(index) {
    if (index < elements.length) {
        var span = elements.eq(index);
        span.click(); // Click on the span
        setTimeout(function() {
            span.click(); // Click again after 1 second
            clickSpanAtIndex(index + 1); // Move to the next span
        }, 1000);
    }
}

clickSpanAtIndex(0); // Start the process by clicking the first filtered span
```