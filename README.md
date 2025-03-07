# Hosting a Markdown Resume on a Website
Hi Marvin,  
I've seen you reading _Modern Technical Writing_ in the lunch room, so I decided to write up some documentation that teaches some key principles from the book. Consider this my birthday gift to you!  

The documentation will focus on how to format a resume using Markdown and then host that resume on a website.

# Prerequisites
I know you understand Markdown and how to do basic operations on the command line, so all of the following instructions are written with that in mind.

You will have to get the resources listed below. I noticed you use a Mac, so the linked installation guides will be for macOS.
- __Python__: A programming language needed to install various dependencies.
    - [Installing Python on Mac](https://docs.python.org/3/using/mac.html)
- __Pelican__: Used for generating website files using Markdown content.
    - Run ```python -m pip install "pelican[markdown]"``` in the command line to install Pelican.
- __Git__: Distributed version control system. Used to manage changes to the files you will make throughout this process.
    - [Installing Git on Mac](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git.html#_installing_on_macos)
- __GitHub account__: Web platform based on Git. Used to store files online and host websites.
    - [GitHub website](https://github.com)
- __ghp-import__: Used to host your created website on GitHub.
    - Run ```python -m pip install ghp-import``` in the command line to install ghp-import.

# Instructions
I will break the process of creating a Markdown resume and hosting it online into 3 ordered sections:
1. Creating a resume with Markdown.
2. Embedding this resume into a Pelican website.
3. Hosting the Pelican website on GitHub Pages.

## Creating a Resume With Markdown
1. Find the resume that you want to host on the website.
    - You can use your own resume or find one elsewhere.
2. Try reformatting the resume into Markdown until you are satisfied.
    - Here is a [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/) that may help with choosing syntax.
3. Save your work as a ```.md``` file.

> __Relation to Etter's book:__  
> Once you finish converting the resume into Markdown, take a look at the appearance of the raw text version. What should stand out to you is how easy the text is to read, even with all the syntax! You might even agree with me that writing the syntax was not all too hard either. 
>
> This is why Etter lists _Use Lightweight Markup_ as one of his principles. It allows technical writers to write well-formatted documents in an incredibly easy way.

## Creating a GitHub Repository
1. Go to [github.com](https://github.com.com) and login.
2. In the top right corner of the screen, click the __+__.
3. Click __New repository__.
4. Change the __Repository name__ field to whatever you want.
    - You will have to use this name in the next section.
5. Click __Create repository__ at the bottom of the form.
    - The other fields can be left as default.

If you have any troubles, you may also refer to the GitHub documentation for creating a repository [here](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

## Creating a Website With Pelican
1. Create a directory on your computer for the website files.
2. Navigate to this directory in the command line (e.g. by using ```cd```).
3. Run ```pelican-quickstart``` in the command line inside this directory.
    - This will prompt you with a series of questions. For most, you can just press __Enter__ to provide a default answer. 
    - The important question is "Do you want to specify a URL prefix?"
        - Answer this with ```https://<GitHub username>.github.io/<GitHub repository name>```.
4. Put your Markdown resume file into the ```content``` folder that is generated.
    - Turn the ```.md``` file into a Pelican article by following [these steps](https://docs.getpelican.com/en/latest/quickstart.html#create-an-article).
5. Generate the website files by running ```pelican content``` in the command line.
6. Get the website running locally by executing ```pelican --listen``` in the command line.
    - Note: "running locally" means only your machine can access the website.
7. View the website with the address ```localhost:8000``` or ```127.0.0.1:8000``` in a web browser.

> __Relation to Etter's book:__  
> Trying to manually recreate the website that you just generated would be very tough. This is one of the reasons Etter lists _Make Static Websites_ as one of his principles. Static site generators like Pelican make the process of creating and modifying websites much easier, which is great for technical writers who want to focus more on documentation.

## Hosting the Website With GitHub Pages
1. Navigate to the website directory and run ```git init``` in the command line.
2. Run ```git add .```.
3. Run ```git commit -m "Initial commit"```.
4. Run ```git branch -M main```.
5. Run ```git remote add origin https://github.com/<username>/<repository-name>.git```.
6. Run ```git push -u origin main```.
7. Run ```pelican content -s publishconf.py```.
8. Run ```ghp-import output -b gh-pages```.
9. Run ```git push origin gh-pages```.
10. View your website on https://\<username>.github.io/\<repository-name>.

> __Relation to Etter's book:__  
> Now, we are following Etter's _Build a Website_ principle. Look at how easy the process was for uploading your site to GitHub pages! In the book, Etter mentions how having your content on a website gives you the ability to ensure everybody viewing your content is seeing the newest version. With this process, it is very easy to upload those "new versions".

# Resources
- [Markdown Tutorial](https://commonmark.org/help/tutorial/)
- [Pelican documentation](https://docs.getpelican.com/en/latest/)
- [What is Git?](https://www.youtube.com/watch?v=2ReR1YJrNOM)
- [How to use GitHub Pages](https://www.youtube.com/watch?v=5XhxR9Vs6zc)

# FAQs
### Q: Why is Markdown better than writing raw HTML?
- Markdown is better for two reasons:
    - It is quicker to write. Search up "HTML syntax" on the internet. It is incredibly more complicated than Markdown.
    - For the same reasons Markdown is quicker to write, it is also easier to understand. 

### Q: I changed the Markdown version of my resume, so why don't I see the changes when I refresh the website in my browser?
- Locally:
    - You have to regenerate the HTML version of the website with ```pelican content```
- On GitHub Pages:
    - You have to upload the newest version of your code to GitHub Pages. Look at steps 7-9 for section [Hosting the Website With GitHub Pages](#hosting-the-website-with-github-pages)

# Credits
- Written by Andre
- Thank you to William and Elan for reviewing my website and README
- The theme used for my website is the default Pelican theme
