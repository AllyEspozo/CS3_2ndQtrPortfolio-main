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

**Answer:** The difference between the default static positioning and the relative positioning is that for the default static positioning, the elements are placed in the normal document flow, ignoring `top`, `left`, `right`, or `bottom`. On the other hand, for the relative positioning, the element still occupies its original space in the flow, but you can sort of “nudge” it around using `top`, `left`, `right`, or `bottom`. 

### Step 2 (Fixed):

- Add in css ```position: fixed; bottom: 0; width: 100%;``` to .footer.

- Guided Question: What happens when you scroll the page? Why does the footer behave differently from position relative?

**Answer:** I noticed that when you scroll, the footer stays visible at the bottom of the screen. So, what's probably happening here is that the `.footer` is pinned to the viewport, not the document flow. For the behavior of the footer, applying relative moves within the flow, while applying fixed detaches from the flow and locks to the viewport.

### Step 3 (Absolute):

- Add in css ```position: absolute; top: 66px; left: 200px;``` to .content.

- Guided Question: What is the effect of position: absolute on an element? How is it different from fixed?

**Answer:** The `.content` is removed from the normal flow and positioned relative to its nearest positioned ancestor. It is different from fixed as for fixed, it is relative to the viewport, while absolute is relative to the parent container.

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
**Answer:** `.notice` appears above `.content` because it has a higher `z-index`. I also noticed that if you swap values (`.notice { z-index: 1; }` and `.content { z-index: 2; }`), then `.content` will overlap `.notice`.

- Challenge: 
    * What changes that you have to do on the code that will position .notice box on the top right corner of the .content box? Please write the code on paper as well (both html and css on the part of .notice and .content).
    - To place `.notice` at the **top-right corner of `.content`**, you need `.content` to be `position: relative;` so `.notice` can anchor to it.
    * Try to change the position of .content to relative then to fixed. What do you observed each time?
    - If `.content` is `relative`, `.notice` positions inside it.  
    - If `.content` is `fixed`, it locks to the viewport, and `.notice` follows that.
    * What do you observe on about the effect of z-index on .notice and .content boxes?
    - Changing z-index values determines which box visually stacks on top.

3. Please answer the following reflection questions (15 minutes)

    a. Could you summarize the differences between the CSS position values (static, relative, absolute, fixed)? 
    - **Static:** Default, follows normal flow, ignores offset properties.
    - **Relative:** Stays in flow but can be shifted around.
    - **Absolute:** Removed from flow, positioned relative to nearest positioned ancestor.
    - **Fixed:** Removed from flow, positioned relative to viewport, stays put when scrolling.

    b. How does absolute positioning depend on its parent element?
    - Absolute positioning depends on the nearest ancestor with `position: relative`, `absolute`, or `fixed`. Without one, it anchors to the page itself.

    c. How do you differentiate sticky from fixed (you can research on sticky)?
    - **Sticky:** Acts like relative until a scroll threshold is reached, then it “sticks” to a position until its parent is out of view.  
    - **Fixed:** Always pinned to the viewport regardless of scroll.

    d. If you were designing a webpage for a school event, how might you use positioning to highlight important information? Please give concrete examples.
    - I can use **fixed** for maybe a banner at the top with the event name so it’s always visible wherever you go on the webpage.  
    - I can use **absolute** for decorative elements and features like if the website is about a school party, there can be balloons positioned around some content regarding the details of the school party.  
    - I can use **sticky** for a clear and concise navigation bar that follows as you scroll through event details.  
    - I can use **relative** for making small adjustments to the spacing of sidebar announcements whenever there's a new urgent update regarding the event.