## Final Project Publishing with markdown

The final projects from this class will be presented and compiled as a web publication.

You will each compose your final project using a langauge called markdown and then contribute to a class website that is hosted on Github.

This tutorial contains everything you need to know in order to successfully format and submit your final project. It should be your first go-to reference for any issues you encounter while you are working on this.

The class website you will collectively contribute to is built using a static site generator called [Jekyll](https://jekyllrb.com/). For more on what Jekyll is or how to use it to build your own website please refer to this great tutorial from the [Programming Historian](https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages).

Jekyll websites are primarily composed of `posts`. Each group will contribute their final project as a post to the collective website.

This tutorial accomplishes two things:
  - you will become familiar with editing and composing documents using markdown syntax.
  - you will create a template document for your final project with you group that you can edit to publish your final project.


To successfully complete this mandatory tutorial you must:
- create a Github account [here](https://github.com/) if you haven't already
- submit a pull request in the Github repository for the class website to create a new 'post'
- wait to be invited as a contributor to the repository for the class site
- then, with your final project group, create a new post which you will continue to edit and update as you work on your final project.


#### Step 1: create a Github account
1. Visit [github.com](https://github.com/) and sign up for a Github account if you do not already have one

#### Step 2: Get familiar with the structure of the class website
1. Use a web browser to navigate to the live website that you will each contribute to at [https://centerforspatialresearch.github.io/puerto_rico_now/](https://centerforspatialresearch.github.io/puerto_rico_now/). It's not very interesting yet because it doesn't have your final projects.
2. This website is being powered by the content contained in this [Github repository](https://github.com/CenterForSpatialResearch/puerto_rico_now). Visit this repository. The repository looks something like this:
![github repo]
  - Each page on the website is made by producing a new file in the `_posts` folder of the repository.
  - Any images that are being shown are contained in folders in the `images` folder.
  - **Note** `_posts` and `images` are the only two folders you will need to interact with.

3. Open the `_posts` folder and then the `2019-03-20-template.markdown` file.  
  - select `Raw`  
  ![raw mode]  

This will open a new browser window. This is text written in markdown. It what you are viewing when you are at this link.
![markdown html comparison]

#### Step 3: Practice writing text in markdown
1. Open the text editor of your choice (we suggest either [Atom](https://atom.io/) or [Sublime Text](https://www.sublimetext.com/), download one of these if you haven't already)
2. Create a new empty file in your text editor.
3. **Copy** all of the raw markdown from 2019-03-20-template.markdown and **paste** it in to this empty file.
4. Save the file in the following format `2019-03-29-lastname.markdown`
5. Once you save the file your text editor will recognize you are writing in markdown and will start highlighting the special syntax of this language:
![syntax highlight]
6. Now we'll each customize this layout and post it to the class website by submitting something called a pull request.

7. Edit the document's header (the area highlighted in yellow above).
    - layout should stay labeled as post: `layout: post`
    - change the date to today's date
    - leave the image as-is `image: "/puerto_rico_now/images/groupname/csr_thumbnail.png"`
    - change the title to your uni:  `title:  "xyz2222"`
    - change the author to your name: `author: "Jane Adams"`

8. Edit the document to practice formatting text and including links. Write in the document so you have:
    - a paragraph of text (use your final project proposal)
    - a word in bold,
    - a word in italics
    - a link to the github repository for the tutorials for this class
    - (optional) an iframe with the webmap you created in tutorial 4 or 5 embedded

#### Step 4: submit a pull request to add your post to the class website
You do not yet have permission to edit the class website. Thus to add your post to the site you will need to create a 'pull request' the TAs will then add you as a collaborator to the site so you can upload new posts without needing permission in the future.
1. Navigate to the `_posts` folder of the `puerto_rico_now` github repository.
2. Select `Create New File`
![new file]
3. Enter the name of the markdown file you have been creating as the file's name. (i.e. `2019-03-29-lastname.markdown`)
4. Copy all of the text from your markdown file and paste it into the `Edit new file` window
![edited]
5. Scroll to the bottom of the page and click the green `Propose new file` button.
6. On the next page that opens select `Create pull request`.
![pull request]
You'll be prompted to enter a message, and then select `Create pull request` again.


One of the class instructors or TAs will `merge` your pull request and invite you to be a collaborator on the class website. You should receive this invitation within 24 hours of submitting your pull request. If you don't, send an email to one of the TAs. You will receive an email when you have been invited to contribute to the repository, you must click on the link in this email to accept the invitation. Once you accept this invitation you will be able to make changes to the website without submitting a pull request.

### Part two: to be completed with your final project group

Once you have received an invitation to collaborate on the class website repository you will now create the base document that you will use to publish your final project.

#### Step 5: Creating your final project post
1. Open your text editor, create a new blank file.

2. Create a yaml header for your post at the top of the file. Replace the **date, title,** and **author** fields to match your group. (Don't change the **layout** or **image**) fields.


```
---
layout: post
date:   2019-03-20
image: "/puerto_rico_now/images/groupname/csr_thumbnail.png"
title:  "Provisional Title of Your Final Project"
author: "Names Of Everyone In Your Group"
---

```  
3. Save the file using the following format `2019-03-29-lastname1-lastname2.markdown`. (Follow this format exactly but replace with your group member last names and today's date)

4. **Practice embedding an image in your post:**

This is a two step process.
**Step one:** you must upload your image to a folder in the class website Github repository.
**Step two:** you must link to that image from within your post.

All of your group's images should be uploaded in the folder with your group name (these have been pre-created for you, please refer to the list of group names and group members at the bottom of this document).

  5.  Find an image relevant to your project's topic that is in the [public domain](https://en.wikipedia.org/wiki/Public_domain) or for which you have image rights.  
  6. save the image with a reasonable file name
  7. upload the image to the `images` >  `your-last-names` folder in the class site Github repository
  ![image upload]
  8. After dragging the image file you have chosen into the uploader, enter a descriptive caption for your commit, and select `Commit Changes`
  9. Check the folder to verify that the image was uploaded.

**Now we'll embed the image in to the body of your post.**

  10. You'll use the following syntax:  `![description of image](/puerto_rico_now/images/groupname/test2-.png)` you can see that there is an example of this in the [template document](https://github.com/CenterForSpatialResearch/puerto_rico_now/blob/master/_posts/2019-03-20-template.markdown).
    - the information between the [ ] contains a description of the image
    - the information in the () contains the path to the image within our website.
  b. replace the description with a description of your image
  c. replace the file path with the path to the image you just uploaded
      **Note** the file path must start with a `/` i.e. it must be `/puerto_rico/images/` if you do not include the `/` then the link will not work.

11. **Save your post.**

12. Now let's replace the thumbnail image that appears on the course website landing page. This image, currently a placeholder, is defined in the header of your post. To change it you will need to first choose and upload an image, and then change the link in the yaml header. Okay, lets do it:

13. Choose an image that is representative of your project, crop it to have a square aspect ratio that is at least 300px wide.

14. Just like you did in step 7 above upload this image to your group's folder within the `images` folder.

15. Update the yaml header of your post, replace the path in the `image` field to match the folder and file name of the square image you just uploaded to github.
```
---
layout: post
date:   2019-03-20
image: "/puerto_rico_now/images/groupname/csr_thumbnail.png"
title:  "Provisional Title of Your Final Project"
author: "Names Of Everyone In Your Group"
---

```

16. **Save your post**

17. Commit your post to the repository. Navigate to the `_posts` folder. And select `Upload Files`. Drag the markdown file containing your post to the window. Write a commit message, and commit your post.

18. Wait 1-2 minutes, then visit the class website URL at [https://centerforspatialresearch.github.io/puerto_rico_now/](https://centerforspatialresearch.github.io/puerto_rico_now/). Your post should have appeared.

#### Step 6: Making changes to your post

To update your post after you have made changes to your markdown file:
1. Navigate to the `_posts` folder in the `puerto_rico_now` Github repository.
2. Select `Upload Files` as you did in number 6 above.. **Note** make sure that you did not change the name of your file. Drag the markdown file containing your post to the window. Write a commit message, and commit your post.

3. Wait 1-2 minutes, then visit the class website URL at [https://centerforspatialresearch.github.io/puerto_rico_now/](https://centerforspatialresearch.github.io/puerto_rico_now/). The updates to your post should have appeared.

## Deliverables
(due by April 5)  

Submit links via courseworks to:
- your individual post
- the post you created with your group


## For reference: project group image folder names
`andrey`: Andrey Prigov

`food_soverignty`: Crystal Herrera Pereira, Kevin Nick Borja, Shiori Osakata


`infra_power`: Caitlin Sills, Alexander Odom

`migration`: Isabella Lajara, Isaac Kim, Sanggyu Shin, Jinsook Lee, Chenyan Zhou, Simone Hasse Stavnsbo

`outage`: Lorena Galvao, Richard Chou

`future_scenarios`: Aline F. Estefam, Ge Guo, Esteban Vanegas Jr, Qi Yang

`decision_model`: Pauline Claramunt, Madeline Entrikin, Caitlin Bone, Tyrene Calvesbert

`debt`: Don Chen, Alicia French, Ran Ma, Maria Moersen, Jaal Alston

`recovery`: Gloria Serra Coch, Ashley Louie

`infrastructure`: Junyu Cao, Shuo Yang

`public_art`: Daniel Bernal, Jean-Pierre Villafane, Aris Minaretzis Tsionos, Tim Battelino


## For reference: post template
```
---
layout: post
date:   2019-03-20
image: "/puerto_rico_now/images/groupname/csr_thumbnail.png"
title:  "Template: Title of Your Final Project"
author: "Names Of Everyone In Your Group"
---
This is a document that is written in markdown. What is markdown? It is a 'markup language' that allows you to format plain text in a way that is easily converted to many different formats. For example, this document was written in markdown but will be used as an webpage and converted into HTML.  

To present and turn in your final projects for Conflict Urbanism: Puerto Rico Now you will be editing this template. You will include all of the text of your paper here, along with any and all images, maps, videos, or other materials that you produce.  

[This webpage](https://guides.github.com/features/mastering-markdown/) provides a comprehensive guide to markdown syntax. But to make things easier for you we are including a cheat sheet of the main things you need to know here.  

#### Please use level 4 headings for major section divisions

Write **words in bold** like this.  

Italics are *similar* and are formatted like this.  

To make a paragraph break you need to add two spaces at the end of your line before going to the next line.  

See this is now a new paragraph.  

Lists are easy:
1. they can be ordered
1. like this
1. notice that the numbers are automatically ordered
  1. use two spaces in front to indent

Or they can just be bullet points:
- like this
* or like this
  - use two spaces
  - to have nested lists

Use Author-Date parenthetical citations following Chicago Manual of Style conventions throughout your document, and add a works cited at the bottom of your post. See Author-Date quick guide [here](https://www-chicagomanualofstyle-org.ezproxy.cul.columbia.edu/tools_citationguide/citation-guide-2.html) for citation conventions.  

To include hyperlinks format them like this [text of link](http://c4sr.columbia.edu/).  

To embed images first ensure that the file is at least 740px wide. Then place the image file in a folder named for your group in the images folder. Then link to that image using the format here, but replace the file path with the name of your group's folder and appropriate image file name:  

![description of image](/puerto_rico_now/images/groupname/test2-.png)

If you want to include html files (i.e. an interactive map) host these via your personal github page, and then you can embed them in your document with a iframe. The format looks like this:  

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/290575503?title=0&byline=0&portrait=0" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0"></iframe></div>  

All you need to do to use one is replace the url that is between the two " ". Here is an iframe of mapbox tiles:  


<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://api.mapbox.com/styles/v1/mapbox/satellite-v9.html?title=true&access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NDg1bDA1cjYzM280NHJ5NzlvNDMifQ.d6e-nNyBDtmQCVwVNivz7A#2/0/0" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0"></iframe></div>```
______________________________________________________________________________________________________________


Tutorial written by Dare Brawley, for *Conflict Urbanism: Puerto Rico Now*, a spring 2019 seminar offered by the [Center for Spatial Research](http://c4sr.columbia.edu). More information about the course is available [here](http://c4sr.columbia.edu/courses/conflict-urbanism-puerto-rico-now).


[github repo]: Images/publishing_1.png
[raw mode]: Images/publishing_2.png
[markdown html comparison]: Images/publishing_3.png
[syntax highlight]: Images/publishing_4.png
[new file]: Images/publishing_5.png
[edited]: Images/publishing_6.png
[pull request]: Images/publishing_7.png
[image upload]: Images/publishing_8.png
