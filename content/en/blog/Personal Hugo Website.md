+++
author = "Jordi Jaspers"
date = 2021-08-01T15:22:26+02:00
draft = false

title = "Portfolio In Hugo & Github Pages"
subtitle = "How do you build a personal website with Github Pages and Hugo?"
tags = ['Web-Development', 'blogging']

# For description meta tag
description = "How do you build a personal website with Github Pages and Hugo?"

# Comment next line and the default banner wil be used.
banner = 'img/hugo_github.png'

+++

## Introduction:
A personal webpage is a perfect place to let the world know about you and showcase your past accomplishments. Put your resume, your projects, your blogs in with a personalized theme which makes people know you have a great taste: all-in-one! It’s your portfolio displayed online, a small yet cool project you can do with not much effort, why not?  
  
With Github Pages, we can host a personal webpage without bothering about finding a domain name, and with Hugo, we have a variety of themes to choose from. This tutorial uses a Mac OS and will run several command-line in terminal: don’t worry, it’s absolutely a tutorial for starters! Now, let’s start this step-by-step tutorial to set up your personal webpage!  
  
* [Building The Site Locally](blog/personal-hugo-website/#Building-The-Site-Locally)
* [Deploy To Github Pages](blog/personal-hugo-website/#Deploy-To-Github-Pages)
  
## HUGO
Hugo is one of the most popular open-source static site generators and is written in GO. It’s simple, efficient, easy to scale and fast to deploy. Simply install with brew, clone themes you like from Github or the official website [HUGO](https://gohugo.io/), make some changes in the configuration file and deploy, then your page will be online.
  
## Github Pages
[Github Pages](https://pages.github.com/) is a static web hosting service provided by Github, which provides 1GB of free space and provides convenient deployment directly through the Github repository.

## Installation
Open your terminal, run the following command:
```bash
brew install hugo
```

Hugo also recommends installing Git, to check if you have it on your computer, run:
```bash
git --version
```

If you’ve installed it, it shows your version of git, if not, it will prompt you to install it automatically.


# Building The Site Locally
Now let’s build a site locally on your computer first. The first step is to go to the directory where you want to save your website, I want to create my site on my desktop, so run the following command in terminal:
```bash
cd <Your project folder>
hugo new site mysite
```

Whenever you _"ls -a"_ in your folder, the generated files look like the following structure:
```bash
07/13/2021  10:44 PM    <DIR>          .
07/13/2021  10:44 PM    <DIR>          ..
07/13/2021  10:44 PM    <DIR>          archetypes
07/13/2021  10:44 PM                83 config.toml
07/13/2021  10:44 PM    <DIR>          content
07/13/2021  10:44 PM    <DIR>          data
07/13/2021  10:44 PM    <DIR>          layouts
07/13/2021  10:44 PM    <DIR>          static
               1 File(s)             83 bytes
               7 Dir(s)   6,273,331,200 bytes free
```

The ones we will work with:

* config.toml : the configuration file, we will need to edit it later.
* content : stores all the content of the website, including all of your blog posts, resumes and so on, can include folders, but usually all .md files.
* static : Stores static files such images, logos, css, js, etc. The files in this directory will be directly copied to the /public folder.
* themes : now it’s empty, but will save the theme of your choice later.
* archetypes : stored .mdtemplate files, it has higher priority than /archetypesfolders under the theme.
* data : stores data files for template calls
* layouts : store .htmltemplates, this folder has higher priority than /layoutsfolders under the theme
* public : After executing the **_"hugo -D"_** command, generates the static files to host your website.

**Choose a theme:**  

Pick a theme you like from the official website Hugo themes or from Github. With the following commands you can install the theme to your Hugo project.  
```bash
cd <YOUR PROJECT>
cd themes
git clone <THE GITHUB REPO OF THE THEME>
```

Another simple solution is to download the entire repository and replace the “themes” folder in your project folder. Next, You will have to change the configuration file with the name of your base URL in _"config.toml"_. 
  
**baseURL = "https://[your github username].github.io/"**  
  
An example configuration is shown below. Note that the picture directories and configuration might vary from theme to theme, make sure to read the instruction of the theme you choose.

```toml
# Use an empty string if you have multiple domain linking to your website
# This string is used to generate the absolute URL for your assets.
baseURL = 'https://jordi-jaspers.github.io/'
defaultContentLanguage = 'en'

# Emoji in markdown files
enableEmoji = true
languageCode = 'en-us'

# Number of blog post per page
paginate = 10
theme = 'pico'

# Title of the website is used for the meta tag title
# and the square icon (not the favicon)
title = 'Jordi Jaspers'

# Path relative to assets folder
[params]
customCSS = [
	"style/style.css",
	"style/theme.sass",
] 

# Path relative to assets folder
customJS = ["js/console.js"]

# Homepage description
# For blog page description you can overwrite it 
# in the front matter
description = "Software Engineer"
email = "JordiJaspers@gmail.com"
favicon = '/favicon.png'
pdf = "/documents/Curriculum_Vitae_JORDI_JASPERS.pdf"

[[params.header]]
night = "/icons/night.svg"
sun = "/icons/sun.svg"

# Dark mode support
# Supported value are :
# - off
# - always
# If commented the theme will use the browser theme.
# darkMode = 'always'

# Social parameters for contact_icons widget
[[params.social]]
alt = "email icon"
icon = "/icons/email.svg"
name = "email"
url = "mailto:jordijaspers@gmail.com"

[[params.social]]
alt = "linkedin icon"
blank = true
icon = "/icons/linkedin.svg"
name = "LinkedIn"
url = "https://www.linkedin.com/in/jordi-jaspers/"

[[params.social]]
alt = "github icon"
blank = true
icon = "/icons/github.svg"
name = "github"
url = "https://github.com/Jordi-Jaspers"

[[params.social]]
alt = "stack-overflow icon"
blank = true
icon = "/icons/stack-overflow.svg"
name = "stack-overflow"
url = "https://stackoverflow.com/users/15013016/jjaspers"

[[params.social]]
alt = "instagram icon"
blank = true
icon = "/icons/instagram.svg"
name = "instagram"
url = "https://www.instagram.com/jordi_jaspers/"

# Navigation bar
[menu]

[[menu.main]]
identifier = "home" # identifier is use for translations
pre = "" # pre is inserted before the translation (icons, image, etc)
url = "/" 
weight = 10 

[[menu.main]]
identifier = "blog" # identifier is use for translations
pre = "" # pre is inserted before the translation (icons, image, etc)
url = "/blog/" 
weight = 20 

[[menu.main]]
identifier = "contact" # identifier is use for translations
pre = "" # pre is inserted before the translation (icons, image, etc)
url = "/#contact" 
weight = 30 

# Syntax highlightning
[markup.highlight]
guessSyntax = false 
lineNumbersInTable = false 
noClasses = false # Set to false to use the Pico default theme.
tabWidth = 2 

[taxonomies]
category = "categories"
tag = "tags"

# Translation
# English, French and Italian are supported but you can contribute
# by adding translation to i18n/ folder.
[languages.en]
contentDir = 'content/en'
languageCode = 'en'
languageName = 'English'
weight = 0
```

## Create your first blog  

You can create your first markdown file in the content folder by running:
```bash
cd mysite
hugo new about.md
```

Or, you can edit the markdown file in your text editor and save it to the content folder. You need to delete the line “draft=true” to make it shown on your site.Content of about.mdwill be available at **http://localhost:1313/about**.

## Test the site locally
Running the following command will give you:
```bash
cd mysite
hugo server
```

The terminal will show instruction like this:

```bash
Start building sites … 
hugo v0.85.0+extended darwin/amd64 BuildDate=unknown

                   | EN  
-------------------+-----
  Pages            | 21  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     | 55  
  Processed images |  0  
  Aliases          |  1  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 4981 ms
```

Go to http://localhost:1313/ in your web browser and the page is shown.

![Fig 1.2: Website Preview](img/blog/personal_hugo_website/website_preview.png)


# Deploy To Github Pages

**Create your Github Repository**
In order to publish your site with the link _"<USERNAME>.github.io"_, you will need to create a repository named <USERNAME>.github.io. Go to your Github webpage and click on the “New” to create a new repository, contain the fully rendered version of your Hugo website.

**Publish to Github**
Get the website rendered in the public folder by running the following commands in your terminal. First step is to remove all the cached and committed files of the public folder.

```bash
cd <YOUR PROJECT FOLDER>
git rm -r --cached public 
```

When that process finishes you can add the github pages repo to your current repo as a submodule. This means whenever you create a clean build of the project the public folder is automatically pushed to your github page. Then you’ll see a public folder appears in the project folder.
  
```bash
git submodule add -b <BRANCH> <REPO OF GITHUB PAGE> public
hugo -D
cd public
git add -A
git commit -m "Commit message"
git push
```

Now the site is successfully published! You can also customize your background image and post new blogs later! If you want to learn more about Hugo or Github, you can refer to the official websites: 

* [HUGO](https://gohugo.io/)
* [Github Pages](https://pages.github.com/)




