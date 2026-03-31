# Seatwork #2 - Getting to know CSS Position and z-index.
### This seatwork will ask you to implement the different CSS position on a given code.
### short link to this .md file is: https://bit.ly/4c61P9K
#### Resources (also found in Khub week 5)
- [4 Minute Youtube Video on CSS Position](https://www.youtube.com/watch?v=YEmdHbQBCSQ)
- [CSS Position Tutorial](https://roycan.github.io/CssPositioningZIndexLab/)

### Instructions: 
1. This is individual submission in khub, but you can work with a partner.  When you submit in khub please place both your names in the submission bin.
2. Guided Activity (30 minutes), please follow what is being required.  

    - Make a copy of this .md file to your Q4 repository and name it as **SectionLNseatwork2.md** example **9LiCruzSeatwork2.md**. Place it in your q4 repository vscode local computer. Committing frequently to your Github repository.  
    - Copy the code below and paste it inside a new file (name it as SectionLNseatwork2.html). Place this file in the same location where the .md file is saved. 
    - Change the content values of the meta tags to your names for author/s and the date today for revised.
    - Please do the following tasks that will ask you to reposition HTML elements then answer the guided question for each task on the .md file. Commit changes to the .md file and to the .html file as well.
    **- This seatwork is worth 20pts and should be submitted by the end of the period** The link to [KHub submission bin](https://khub.mc.pshs.edu.ph/mod/assign/view.php?id=15481).
      - Submit the links to your .md file and .html file.

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="author" content="<your names>" />
  <meta name="revised" content="<date today>" />
  <style>
    body { font-family: Arial, sans-serif; }
    .header, .footer {
      background: lightblue;
      padding: 10px;
    }
    .footer {
       opacity: 0.5;
    }
    .sidebar {
      background: lightgreen;
      width: 150px;
      height: 200px;
    }
    .content {
      background: lightyellow;
      width: 300px;
      height: 200px;
    }    
  </style>
</head>
<body>
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">Main Content</div>
  <div class="footer">Footer</div>
</body>
</html>
```
### Step 1 (Static vs Relative):

- Add in css ```position: relative; top: 20px; left: 20px;``` to .sidebar.

- Guided Question: What changed compared to the default static positioning? Try to give different values to top and left or you can change it to bottom, right.

- Answer: The sidebar changed positions relative to its original position when it was static. When you change the values of top and bottom, the figure shifts as well correspondingly.

### Step 2 (Fixed):

- Add in css ```position: fixed; bottom: 0; width: 100%;``` to .footer.

- Guided Question: What happens when you scroll the page? Why does the footer behave differently from position relative?

- Answer: When you try to scroll, it won't move from its position. It will always remain in the same position of the viewpoint of the user. When i try to zoom in, it will also enlarge itself but remains in the same position.

### Step 3 (Absolute):

- Add in css ```position: absolute; top: 66px; left: 200px;``` to .content.

- Guided Question: What is the effect of position: absolute on an element? How is it different from fixed?

- Answer: `position: absolute` removes the element from the normal document flow and positions it relative to the nearest positioned ancestor or the page if none exists. Unlike `fixed`, the absolute element is not pinned to the viewport; it can still move when the page scrolls and is positioned relative to its containing block, not necessarily the screen.

### Step 4 : (Absolute)

- Add in html ```<div class="notice">Notice!</div>``` and include the css below:

```css
.notice {
    position: absolute;
    top: 60px;
    left: 400px;
    background: orange;
    padding: 10px;
    z-index: 2;
}
```

- Give .content a z-index: 1.

- Guided Question: Why does the notice appear on top of the content? What happens if you swap the z‑index values?

- Answer: The figure with the larger z-index value will be placed on a layer above the other figure with the lower index.

- Challenge: 
    * What changes that you have to do on the code that will position .notice box on the top right corner of the .content box? Please write the code on paper as well (both html and css on the part of .notice and .content).
      - Answer: Place the notice inside the content box and make the content positioned, for example:
        HTML Part:
        <div class="content">
          Main Content
          <div class="notice">Notice!</div>
        </div>
       
       CSS Part:
        .content {
          position: relative;
          z-index: 1;
        }
        .notice {
          position: absolute;
          top: 0;
          right: 0;
          z-index: 2;
        }
        
        So to make the .notice part appear on the top right corner of .content, we have to set the z-index of .content to be less than the z-index of .notice, and we have to put the div tag of .notice into the div tag of .content. Just set the top and right values of the css of .notice to zero so that it really appears on the top right corner.

    * Try to change the position of .content to relative then to fixed. What do you observed each time?
      - Answer: The position of .notice changes relative to the position of .content. Whenever I change the position of .content, the .notice box seems to follow it as well.
    * What do you observe on about the effect of z-index on .notice and .content boxes?
      - Answer: If I put a smaller z-index on .content, then the .notice box will overlap the .content box, and when .notice has a smaller z-index, the .content box will overlap the .notice box.

3. Please answer the following reflection questions (15 minutes)

    a. Could you summarize the differences between the CSS position values (static, relative, absolute, fixed)? 

    - Answer: static is the default position and follows normal document flow. relative keeps the element in flow but allows offset from its normal position. absolute removes the element from flow and positions it relative to the nearest positioned ancestor or the viewport. fixed also removes the element from flow but positions it relative to the viewport so it stays visible while scrolling.

    b. How does absolute positioning depend on its parent element?

    - Answer: Absolute positioning is relative to the nearest ancestor that has a position other than static (relative, absolute, fixed). If no such ancestor exists, it is positioned relative to the initial containing block (usually the page). This means the parent’s positioning can change where the absolutely positioned element appears.

    c. How do you differentiate sticky from fixed (you can research on sticky)?

    - Answer: fixed keeps an element locked to the viewport at all times, even when the page is scrolled. sticky behaves like a normal element until scrolling reaches its threshold, then it just sticks in place within its parent container (usually the viewport).

    d. If you were designing a webpage for a school event, how might you use positioning to highlight important information? Please give concrete examples.

    - Answer: I would use fixed for an event banner or a navigation bar that SHOULD NOT move when I scroll the page so the navigation links and important dates-to-remember stay visible. I would use absolute inside a section box to place a “Register Now” button or countdown badge at the top-right corner of a featured announcement. I could use relative to arrange event images and captions into the layout I want.
