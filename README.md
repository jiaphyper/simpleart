
# Simpleart

A (nearly) no-CSS, fast, minimalist [Hugo](https://gohugo.io/) theme ported from [hugo-theme-nostyleplease](https://github.com/hanwenguo/hugo-theme-nostyleplease).

<img src="https://raw.githubusercontent.com/jiaphyper/simpleart/main/screenshot.png" width="60%"/>

## 🌐 Live Demo

Check out the live demo of SimpleArt theme:

👉 [Demo](https://jiaphyper.github.io/simpleart/)


## Features

* Fast (**under 4kb of CSS!**)
* Randomly wondering for articles
* Light, dark and auto modes
* Responsive
* Content first (typography optimized for maximum readability)
* RSS feed (using Hugo's embedded RSS template)
* MathJax support


## Installation

The easiest way is to clone this repo (or add as a submodule) to `themes/simpleart` 

### 1. Clone the Theme
```bash
git clone https://github.com/jiaphyper/simpleart.git themes/simpleart
```

### 2. Replace Configuration
Replace your site's hugo.toml with the theme's configuration file:

```bash
cp -f themes/simpleart/hugo.toml ./hugo.toml
```

### 3. Copy Content Files
Overwrite your site's content directory:

```bash
cp -R themes/simpleart/content/ ./content/
```

### 4. Copy Static Assets
Replace static files (images, JS, CSS, etc.):

```bash
cp -R themes/simpleart/static/ ./static/
```

## 5. Run the Development Server

Start the Hugo development server with this command:

```bash
hugo server -D
```

this will  

+ Start a local web server (-D includes draft content)

+ Automatically reload when files change

+ Print the access URL to your terminal

After running the command:

+ Open your web browser

+ Visit: http://localhost:1313

+ You should see your blog with the theme applied

Note:

> Press Ctrl+C in terminal to stop the server  
> The `-D` flag shows draft posts (remove it for production)


## Usage

You can edit `hugo.toml` file to customize your blog. You can change things such as the name of the blog, the author, the appearance of the theme (light, dark or auto), how dates are formatted, etc. Customizable fields should be straightforward to understand. 

### Random reading

Set `random_reading_enable = true`, the webpage appears a wondering button. by clicking the button, the webpage directs a random page of your articles. You can edit the button text by `random_button_text` 

```toml
[params]
  random_reading_enable = false
  random_button_text = "Wondering"  
```

- When enabled (`random_reading_enable = true`), a button appears in your webpage
- Clicking the button will redirect visitors to a randomly selected article
- The button text can be customized via `random_button_text`

> Note: `content/random.md` file **CAN NOT** be deleted when you want to use random wondering.

### Advertising & Footer Configuration

#### Google AdSense Integration

Configure your AdSense settings in `hugo.toml`:

```toml
[params.adsense]
  enable = true                 # Enable/disable AdSense globally
  client_id = "ca-pub-xxxxxxxxxxxxxxx"  # Your AdSense publisher ID
  auto_ads = true               # Enable Auto Ads (recommended)
  article_top_slot = "123456789"    # Article top ad slot ID
  article_bottom_slot = "123456789" # Article bottom ad slot ID
```

**Implementation Notes:**

- Auto Ads will automatically place ads in optimal locations
- Article slots will display ads at the top/bottom of your content
- Requires valid AdSense account and approved site

#### Footer Configuration

Customize your footer with social links and copyright:

```toml
[params.footer]
  copyright = "© 2017 - {{ now.Format \"2006\" }}"  # Dynamic year range
  
  # Social links with Font Awesome icons
  links = [
    { icon = "fa-brands fa-twitter", text = "Twitter", url = "https://x.com/username" },
    { icon = "fa-brands fa-github", text = "GitHub", url = "https://github.com/username" },
    { icon = "fa-solid fa-envelope", text = "Email", url = "mailto:email@example.com" },
    { icon = "fa-solid fa-rss", text = "RSS", url = "/index.xml" }
  ]
```
> You can found icon in [fontawesome](https://fontawesome.com).
> If you want to revise footer, you can edit in `themes/simpleart/layouts/partials/footer.html`.


### Customize the menu (Homepage)

In order to add/edit/delete entries from the main menu, you have to edit the `/themes/simpleart/data/menu.toml` file. Through that file you can define the structure of the menu. Take a look at the default configuration to get an idea of how it works and read on for a more comprehensive explanation.

The example of `menu.toml` is as follows.

```toml
[[entries]]
title = "info"

  [[entries.entries]]
  title = "a (nearly) no-CSS, fast, minimalist Hugo theme ported from <a href='https://github.com/hanwenguo/hugo-theme-nostyleplease/'>no-style-please</a>."

  [[entries.entries]]
  title = "github repo"
  url = "https://github.com/jiaphyper/simpleart"


[[entries]]
title = "all posts"

  [entries.post_list]
  limit = 5
  show_more = true
  show_more_text = "See archive..."
  show_more_url = "posts"

[[entries]]
title = "posts by category"

  [entries.post_list]
  section = "posts"
  show_more = true
  show_more_text = "See more posts..."
  show_more_url = "posts"

[[entries]]
title = "rss"
url = "index.xml"

[[entries]]
title = "another list"

  [[entries.entries]]
  title = "with subitems"

    [[entries.entries.entries]]
    title = "with subsubitems"

    [[entries.entries.entries]]
    title = "example page"
    url = "about"

[[entries]]
title = "PRO TIP"
entries = [
   { title = "to edit this menu, edit data/menu.toml file" }
  ]
```


### Section pages

A so-called section page is a page that shows a list of posts in a specific section. It should be automatically created by hugo when a new section is created.

### Customize the index page

The `index.md` page should use layout `home`, which is the layout that displays the menu. If you want to have some content after the menu, you can just add that content in the `_index.md` file, and it will automatically show under the menu.

Another thing you can do to customize the index page is show the description of your blog between the title and the menu. To do this, just edit `config.toml` and change `params.theme_config.show_description` to `true`.


### Adding table of contents

You can add a table of contents by supplying the `toc: true` param to your post front matter. If you want a border around it you can also set `tocBorder: true`. The toc style behavior is handled by Goldmark and the defaults can be found in the `hugo.toml` file.

### Posts list group by date in descending order.

just edit `hugo.toml` and change `params.theme_config.isListGroupByDate` to `true`.

### Last but not least

1. you can edit the css in `themes/simpleart/assests/css/main.scss` file.  
2. change logo in `static` folder.  


## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/jiaphyper/simpleart/.

## Acknowledge

Some of the code comes from [hugo-theme-nostyleplease](https://github.com/hanwenguo/hugo-theme-nostyleplease/), a fork of this theme.

## License

The theme is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
