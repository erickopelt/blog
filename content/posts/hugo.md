+++
title = "Hugo - From zero to deploy"
date = "2020-02-29"
author = "Erick Euller Opelt"
description = "Step by step tutorial for creating a new site using [hugo](https://gohugo.io) and deploying using [Netlify](https://www.netlify.com/)"
+++

This is a step by step guide for creating a blog from zero using [hugo](https://gohugo.io) and deploy on [Netlify](https://www.netlify.com/) with continuous delivery.

### Installation

First install the latest version of Hugo. In the official [installation guide](https://gohugo.io/getting-started/installing/) you can find the best way to install the package on your distro. If you are running any debian derivative I'd recommend downloading the .deb package and installing via dpkg.

### Creating a new site

After download you can create a new empty hugo site.

``` sh 
hugo new site blog
```

After running the command above, a new directory called blog will appear in the current directory. Before starting the server to see your site you have to choose a theme.


### Choosing a theme

There are thousands of awesome themes in the hugo [gallery](https://themes.gohugo.io/) to choose from. For this guide we will use the [hello-friend](https://themes.gohugo.io/hugo-theme-hello-friend/) theme, the same one that this blog runs on. To add the theme to your site you just need to copy the contents of the theme to the `/themes` folder. The best way to do this is by adding using as a new git submodule, this way you can keep the theme up to date with new features.

```sh 
git submodule add https://github.com/panr/hugo-theme-hello-friend.git themes/hello-friend
```

By now you already have a full functional site, just navigate into the site folder and run 

```sh
hugo server
```

The command output will point out the server port, it usually is 1313 so just head to [localhost:1313](http://localhost:1313)

### Adding content

All content for the site must be stored in the /content folder as markdown files. If you are creating a blog, the posts should be at the /content/posts folder and have header with the page's metadata information, like the example below:

```
+++
title = "Hugo - From zero to deploy"
date = "2020-02-29"
author = "Erick Euller Opelt"
description = "Test"
+++
```

The template for this header is at the /archetypes folder and can customized at will. Hugo's cli has a helper for creating new content with the header, just type:

```sh
hugo new posts/hello.md
```
 
### Tips for customization

If you want to customize the site style without drastically change the theme you can do so by add ing a css file in the /static folder. For template customization, hugo lets you override the theme partial by creating a new partial with the same name file into layouts/partials.

### Deploy

For deployment we will be using [Netlify](https://www.netlify.com/) with Github integration. So first thing create a new repository and push your code to Github. After that jump into Netlify dashboard.

In the Netlify dashboard click in the New site button then select Github as the repo provider. You need to authorize Netlify usage of your Github account and select wich repository will be available for deploy. Now just select the right repository and setup the build configuration. Netlify recognizes hugo and the default build configuration show it's already enough.


### Conclusion

Hugo makes creation easy with simple tools and a variety of themes and turns adding new content into the simple task of just creating a new markdown file. Combine with Netlify effortless configuration and integration and you have the fastest setup I have ever experienced.