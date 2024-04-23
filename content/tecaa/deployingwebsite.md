---
title: Deploying Amethyst to the Web
weight: '"4"'
---
## Deploying?

Deploying a website means making it available to the world, by using the Internet. This means that anyone that knows the site address (or URL) can see the notes you published, **and includes their content**. This is what the page will teach you to do.

This is useful if you want to share these contents with your friends. This theme has been designed to be effortless to deploy, primarily on GitHub pages. 

Alternatively, you can deploy your awesome notes to a **custom domain**, if you happen to have one. This means that, instead of having your website's URL be provided by GitHub:

```<YOUR-GITHUB-USERNAME>.github.io```

You will have a custom one, with a different structure and name, that you can easily share.

## Deploying in GitHub pages

If you have followed the steps in the [Setup](tecaa/setup.md) page, you are ready to deploy your website on GitHub pages. 
### Preparing the deployment

There are some steps you need to do to allow your repository to be published as a website. Follow the steps below to finish the setup of your repository.

First, you should go to the repository you used to fork the amethyst theme.
Then, you should click on the "Actions" tab of the repository, so that you can set up repository actions.

![The actions tab, located in your GitHub repository, is located on the top left, being the fourth option from the left.](/images/github-repo.png)
*The actions tab, located in your GitHub repository*

After going into the Actions tab, a page will appear that warns you about enabling workflows on GitHub, and that it was automatically disabled because you forked this repository. Click on the button that says:

```I understand my workflows, go ahead and enable them.```

![Inside the actions tab, there is a green button that you should click so your website deploys when you make changes.](/images/github-actions.png)
*Inside the GitHub actions page, after forking a repository*

This will enable GitHub actions for your repository, which will automatically deploy your website whenever you push changes to this repository, keeping it up to date automatically!
### Enabling GitHub pages

After enabling GitHub actions you can go to the Settings tab of your repository. In the settings tab, there is another tab called "Pages", which you should click on.

![In the pages tab, you can find settings such as setting the source of your files, and using a custom domain.](/images/github-pages.png)
*The GitHub Pages tab*

In this tab, you should change the deploy directory of the project to the "master" branch of your repository, and selecting the root folder.

#### (Optional) Setting up a custom domain

In this screen you can setup a custom domain by typing its URL in the text box and clicking the Save button.

For the website to be hosted on the domain, you have to do an additional step. 

Go to your DNS provider and create a CNAME record that points your domain to `<YOUR-GITHUB-USERNAME.github.io.`
The trailing period is **required**!

>[!info] It may take some time.
>
>The network changes may take 30 minutes to an hour to complete. After this time is up, your domain will be ready to host the website.

With all the preparations done, you're ready to push content that will be displayed on the internet.

### Pushing changes

You need to push changes so that they are seen on the internet. Updating the repository is done in the same way as any other repository:

```shell
# Navigate to Amethyst folder
cd <path-to-amethyst>

# Commit all changes
git add .
git commit -m "message describing changes"

# Push to GitHub to update site
git push origin main

```

Note that these commands push to the main branch. This is intended, as the GitHub actions we prepared earlier take this commit and replicates the same commit on the deploy branch.

### Setting up the site

In this chapter, we get the site finally up and running! 

### Changing the Hugo configuration file

The first thing you need to do is open the *config.yaml file* located in the repository root with your favorite text editor and locate the baseURL property. You have to change this property to the domain which will host your website.

>[!warning] Be careful!
>
>You have to place a **trailing forward slash "/"** for the website to work after deploying, and replace the domains accordingly!


You can find a sample for the file in the theme's [repository](https://github.com/64bitpandas/amethyst/blob/main/config.yaml).
{{< columns >}} 
#### GitHub Pages

If using the domain in GitHub pages, you can use the following example.

```yaml
baseURL: "https://<YOUR-GITHUB-USERNAME>.github.io/amethyst/"
```
<---> 
#### Custom Domain

If you are using a custom domain, you should use the following structure:


```yaml
baseURL: "https://<YOUR-DOMAIN>/"
```

{{< /columns >}}


### Changing the GitHub actions deploy file


The last step revolves around telling GitHub actions how to build and run our site by using the *deploy.yaml file*, located in `/.github/workflows/` in your repository. In this file, you have to change the *"cname" property* to the domain of your page.

>[!warning] Be careful!
>
>Here you don't need the **trailing slash (/)**!

You can find a sample for the file in the theme's [repository](https://github.com/64bitpandas/amethyst/blob/main/.github/workflows/deploy.yaml).

```yaml
- name: Deploy  
  uses: peaceiris/actions-gh-pages@v3  
  with:  
	github_token: ${{ secrets.GITHUB_TOKEN }} # this can stay as is, GitHub fills this in for us!
	publish_dir: ./public  
	publish_branch: deploy
	cname: <YOUR-DOMAIN>

```

## How was this page built?

{{< expand >}}

This page was adapted from the already existing "deploying amethyst on the web" page that is present on the [theme's tutorial](https://amethyst.bencuan.me/setup/hosting/). This page tried to make the content easier to understand by following [google's style guidelines for technical documentation](https://developers.google.com/style/highlights) as close as possible. Special attention was given to the highlights present on the style guide, to make the reading experience seamless and pleasant.

The development process involved the following steps:

1. Creation of a new Markdown file named `deployingwebsite.md` within the `/content/tecaa/` directory.
2. Configuration of front matter settings, including the title of the page and its weight relative to other pages within the same directory.
3. Added the necessary content and organized the page using various Markdown and Amethyst features, ensuring compliance with the defined group decisions.

### Author

This page was created by Rafael Cardoso (Nº 1190982), a Master Student in Informatics Engineering at ISEP, Porto, Portugal.
This website was a project created for the TECAA course unit.

### Amethyst Features

The Amethyst theme features [exclusive](https://amethyst.bencuan.me/features/buttons/) markdown rendering options that even the Obsidian app does not have. The following sections highlight the features used in this page.

{{< tabs "Amethyst Features" >}}
{{< tab "Expand" >}} 

The Expand feature was used to write this very section on how the page was written. 

Expand creates a collapsible area of text, perfect to hide these optional details that are not part of the main page's content.

{{< /tab >}}
{{< tab "Tabs" >}} 

The tabs feature was used in this section to more succinctly summarize the markdown styles used in the page. 

This prevents the need for the user to scroll and read content between headings.

{{< /tab >}}
{{< tab "Columns" >}} 

The comuns feature was used in the section where the user has to choose a custom domain, or the GitHub pages domain as they edit the theme file. 

The feature neatly organizes the content so that the user can easily identify their use case.

{{< /tab >}}
{{< /tabs >}}
### Obsidian Flavored Markdown

The markdown used in the page's construction was adapted to render well on the website. The website uses mostly [Obsidian Flavored Markdown](https://help.obsidian.md/Editing+and+formatting/Obsidian+Flavored+Markdown), because it was made with the Obsidian software in mind, which allows users to build a network of notes and build a knowledge base.

As such, this markdown may not follow the same syntax as other types of markdown, failing to render on other websites.

{{< tabs "Obsidian Flavored Markdown" >}}
{{< tab "Headings" >}} 

Headings were only created to section off information into easy to read blocks so that the user can infer at what step they are in the tutorial the page is trying to present. 

The headings present in the original have been adapted as sections here. 

Some sections have been added, instead of being hidden away in smaller pages with few content, such as the "Setting up a custom domain" section, which was hidden away in a small page. 

As it has to do with deploying, it has been moved here for those that need it.

{{< /tab >}}
{{< tab "Content" >}} 

The content in each section tries to be as informative as possible, while providing context to the reader of what is going on. 

For example, the user might not be familiar with "deploying" a website, so it is explained very clearly what hosting a website means, and that it is what this tutorial will teach them how to do. 

Context is given for everything within reason.

{{< /tab >}}
{{< tab "Links" >}} 

As per the style guide, Links are interwoven into the content in such a way that you could remove the link, and the phrase would still make sense. 

This helps with readability, and it's up to the user to click on the link if they need the information the link is trying to provide.

{{< /tab >}}
{{< tab "Images" >}} 

Images provide a way for the user to see what they should do in the tutorial. Along with these images, they include captions as well as **alt text** that describes the image's content. 

This alt text is used so that the image can be described to a blind user by screen readers.

{{< /tab >}}
{{< tab "Callouts" >}} 

Callouts were used to bring attention to the user in critical moments, and are used to bring attention without cutting the flow of text. 

Their content are warnings and information about things the user should really pay attention to.

{{< /tab >}}
{{< /tabs >}}

{{< /expand >}}