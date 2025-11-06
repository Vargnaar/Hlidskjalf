A very lightweight, single-file JavaScript bookmarklet designed to instantly display media; built to make open directory enumeration a little smoother.

# Features

Image Extraction: Automatically scans the current page for links ending in common image extensions (.jpg, .png, .gif, etc.).

Responsive Gallery: Displays extracted images in a clean, scrollable, and responsive grid layout.

Lazy Loading: Uses the Intersection Observer API for performance, only loading images as they scroll into the viewport.

Image Count: Shows a sticky footer displaying the total number of images found.

Scroll to Top: Includes a "Back to Top" button in the footer for easy navigation.

# Installation & Usage

This script is intended to be used as a Bookmarklet in your web browser.

1. Copy the Minified Code

The code must be minified and URL-encoded to work correctly as a bookmarklet. Copy the complete string below:
```
javascript:(function(){var baseUrl=location.href;var newWindow=window.open("","Gallery","width=900,height=700");var placeholder='data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==';var sHTML='<!DOCTYPE html><html lang="en"><head><meta charset="UTF-8"><title>Hlidskjalf | v1.5.3</title><base href="'+baseUrl+'"><style>body{margin:0;background-color:#1a1a1a;}.gallery{display:flex;flex-wrap:wrap;justify-content:center;margin-bottom:200px;}.gallery-item{width:250px;margin:10px;text-align:center;}img{max-width:100%;height:auto;}.footer{position:fixed;bottom:0;left:0;width:100%;z-index:1000;display:flex;justify-content:center;align-items:flex-end;}.footer .card,.footer .back-to-top{margin-left:10px;padding:5px 10px;background-color:#1a1a1a;border:1px solid #d0d0d0;border-top-left-radius:10px;border-top-right-radius:10px;box-shadow:0 0 10px rgba(0,0,0,0.3);font-family:Arial,sans-serif;font-weight:bold;text-align:center;color:white;}.footer .back-to-top{cursor:pointer;}</style></head><body><div class="gallery">';var imageCount=0;for(var x=0;x<document.links.length;x++){var a=document.links[x].href;if(a.match(/\.(jpeg|jpg|png|gif|bmp|tiff|tif|webp)$/i)){sHTML+='<div class="gallery-item"><a href="'+a+'" target="_blank"><img data-src="'+a+'" src="'+placeholder+'" alt="Image"></a></div>';imageCount++;}}sHTML+='</div><div class="footer"><div class="card">Total Images: '+imageCount+'</div><div class="back-to-top" onclick="window.scrollTo({top:0,behavior:\'smooth\'});">Back to Top</div></div><script>(function(){var images=document.querySelectorAll(\'img[data-src]\');var observer=new IntersectionObserver(function(entries){entries.forEach(function(entry){if(entry.isIntersecting){var img=entry.target;img.src=img.dataset.src;observer.unobserve(img);}});});images.forEach(function(img){observer.observe(img);});})();</script></body></html>';newWindow.document.write(sHTML);newWindow.document.close();})();

```
2. Create the Bookmark

Open your browser's Bookmark Manager.

Create a new bookmark.

Set the Name to something memorable (e.g., Image Gallery).

Paste the minified code (from Step 1) into the URL or Location field.

Save the bookmark.

3. Run the Script

Navigate to any webpage that contains image links.

Click the newly created Image Gallery bookmark.

A new window will open displaying all discovered images.

