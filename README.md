# Image swapping technique to improve LCP

The default method of lazy loading high resolution images does not work because :
-  In addition to late-loading images and fonts, a page may add new elements to the DOM as new content becomes available. If any of these new elements is larger than the previous largest contentful element, a new PerformanceEntry will also be reported.
- If an element that is currently the largest contentful element is removed from the viewport (or even removed from the DOM), it will remain the largest contentful element unless a larger element is rendered

The "Catch"
- The browser will stop reporting new entries as soon as the user interacts with the page (via a tap, scroll, or keypress),

Probable Solution:
- Load the low res image by default.
- Add the high resolution image to the DOM, but set display:none,
  This is important, otherwise the image will be downloaded on scroll and users will see a "flicker"
- On scroll/click/tap set display:none to lowres and display:block to high resolution.  
