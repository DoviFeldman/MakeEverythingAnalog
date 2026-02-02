# How to Set Up Your Interactive Image Website

## Step 1: Prepare Your Files

1. Rename your image file to something simple like `your-image.jpg` (or .png, .gif, etc.)
2. Place the image in the same folder as `index.html`
3. Update line 28 in `index.html` to match your image filename:
   ```html
   <img src="your-image.jpg" alt="Interactive Image" usemap="#image-map">
   ```

## Step 2: Find the Coordinates for Your Clickable Areas

You need to find the exact pixel coordinates of the items you want to make clickable.

### Method 1: Using an Online Tool (Easiest)
1. Go to https://www.image-map.net/
2. Upload your image
3. Draw rectangles over the items you want to be clickable
4. Copy the coordinates it generates

### Method 2: Using Image Editing Software
1. Open your image in any image editor (Paint, Photoshop, GIMP, etc.)
2. Hover over the top-left corner of an item - note the X,Y coordinates
3. Hover over the bottom-right corner of the same item - note the X,Y coordinates
4. Your coordinates are: `x1,y1,x2,y2`

### Method 3: Using Your Browser
1. Open the HTML file in Chrome/Firefox
2. Right-click the page → Inspect
3. In the Console tab, paste this code:
   ```javascript
   document.querySelector('img').addEventListener('click', function(e) {
       console.log('X: ' + e.offsetX + ', Y: ' + e.offsetY);
   });
   ```
4. Click the corners of items to get coordinates

## Step 3: Update the Coordinates in index.html

Each clickable area looks like this:
```html
<area shape="rect" coords="100,100,200,200" href="https://example.com" alt="Link 1" target="_blank">
```

The `coords` format is: `x1,y1,x2,y2`
- `x1,y1` = top-left corner of the clickable rectangle
- `x2,y2` = bottom-right corner of the clickable rectangle

**Example:** If your first clickable item is located:
- Top-left corner at X: 150, Y: 80
- Bottom-right corner at X: 300, Y: 200

Change the coords to: `coords="150,80,300,200"`

## Step 4: Set Your Links and Pages

### For External Links (3 areas):
Update the `href` to your actual URLs:
```html
<area shape="rect" coords="100,100,200,200" 
      href="https://yourlink.com" 
      alt="Description" 
      target="_blank">
```
- `target="_blank"` makes it open in a new tab
- Replace `https://yourlink.com` with your actual link

### For Internal Pages (3 areas):
```html
<area shape="rect" coords="100,300,200,400" 
      href="page1.html" 
      alt="Page 1">
```
- Keep `page1.html`, `page2.html`, `page3.html` as is
- You'll create these HTML files later
- Remove `target="_blank"` so they open in the same tab

## Step 5: Upload to GitHub Pages

1. Create a new repository on GitHub
2. Upload `index.html` and your image file
3. Go to Settings → Pages
4. Under "Source", select "main" branch
5. Click Save
6. Your site will be live at: `https://yourusername.github.io/repositoryname`

## Quick Reference: All 6 Areas

```
AREA 1 (External Link): coords="x1,y1,x2,y2" href="https://link1.com"
AREA 2 (External Link): coords="x1,y1,x2,y2" href="https://link2.com"
AREA 3 (External Link): coords="x1,y1,x2,y2" href="https://link3.com"
AREA 4 (Internal Page): coords="x1,y1,x2,y2" href="page1.html"
AREA 5 (Internal Page): coords="x1,y1,x2,y2" href="page2.html"
AREA 6 (Internal Page): coords="x1,y1,x2,y2" href="page3.html"
```

## Testing

1. Open `index.html` in your browser
2. Hover over the clickable areas - your cursor should change to a pointer
3. Click to test if links work

## Troubleshooting

- **Clicks don't work?** Check that your coordinates are correct
- **Image doesn't show?** Make sure the image filename matches exactly (case-sensitive)
- **Wrong area clickable?** Double-check your x1,y1,x2,y2 coordinates
- **Link doesn't open?** Make sure URLs start with `https://`

Need help? The image-map.net tool is the easiest way to get perfect coordinates!
