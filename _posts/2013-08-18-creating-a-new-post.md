---
layout: post

title:          "Creating A New Post in Jekyll on Github.io"
subtitle:       "A quick tutorial about creating a new post on Jekyll within a Github.io environment"
categories:     jekyll github
cover_image:    wollongong-cover.jpg

excerpt:        "This post will instruct you on how to create a new post in your Jekyll blog setup on Github.io."

author:
  name:         Matt Rowles
  twitter: 
  gplus: 
  bio:          Developer
  image:        ks.png
---

This post will instruct you on how to create a new post in your Jekyll blog setup on Github.io.

1. Within a terminal window, navigate to your local repository directory and then updateit with the following command:

        git pull upstream master 

2. In order to contain any changes to the files within your repository in a branch, perform a git checkout for the new post topic. Type the following command into the terminal:

        git checkout -b topic-name

3. Create the file in the **\_posts** directory using the filename convention **yyyy\-mm\-dd\-Post\-Title.md**. After you're finished writing your post, save and close the file.

4. To view a local version of your Jekyll blog and ensure your post is constructed using the correct syntax, you can use the following command:

        jekyll serve --watch

        # Adding "--watch" will actively monitor for any changed files and regenerate the service

5. To ensure your new post will be pushed onto the main repository, it needs to be committed. Type the following command into the terminal to ensure all changed files are added:
    
      # Add all changed files
      git add .

      # Add specific files for this commit only
      git add ./_posts/2013-08-18-test-post.md

6. Check the status of your git commit to ensure you can see that the file/s ready to be added consist of your new post file:
    	
        git status

7. Time to commit your files so that they are ready to push onto your forked repository (and eventually, the main repository). Type the following command into your terminal:

        git commit -am "This is a comment about the changes I made"

8. The following command will push your files into your forked repository, ready for confirmation by either yourself or another moderator within your Github.io space. Please note that the `topic-name` should be the same as in step 2:

        git push origin topic-name
        # Note: you may be asked for your username and password

9. Once you're ready, head on over to your Github space and confirm your pull request. Once done, whoever approves your changes within the main repository will have to review and approve.