---
id: 2024-06-05-setting-up-jekyll-blog
aliases: 
tags: 
categories: jekyll update
date: 2024-06-05
layout: post
title: Setting up jekyll blog
---
Guide to create a blog using GitHub Pages and Jekyll:

### Step-by-Step Guide to Create a Blog Using GitHub Pages and Jekyll

#### 1. **Set Up a GitHub Repository**

1. Go to [GitHub](https://github.com) and log in to your account.
2. Click on the `+` icon in the top-right corner and select `New repository`.
3. Name your repository, for example, `username.github.io`, where `username` is your GitHub username.
4. Set the repository to public and check the box to initialize it with a `README.md` file.
5. Click on `Create repository`.

#### 2. **Install Jekyll**

1. **Install Ruby:**
   - Follow the instructions on [ruby-lang.org](https://www.ruby-lang.org/en/documentation/installation/) to install Ruby on your system.

2. **Install Jekyll and Bundler:**
   Open your terminal and run the following commands:

   ```sh
   gem install jekyll bundler
   ```

#### 3. **Create a New Jekyll Site**

1. **Navigate to your workspace:**
   Open your terminal and navigate to the directory where you want to create your blog.

   ```sh
   cd path/to/your/workspace
   ```

2. **Create a new Jekyll site:**
   Run the following command to create a new Jekyll site in a directory named `myblog`:

   ```sh
   jekyll new myblog
   ```

3. **Navigate to your new Jekyll site directory:**

   ```sh
   cd myblog
   ```

#### 4. **Run Your Jekyll Site Locally**

1. **Install dependencies:**

   ```sh
   bundle install
   ```

2. **Serve your site locally:**

   ```sh
   bundle exec jekyll serve
   ```

3. **Open your browser:**
   Open your browser and go to `http://localhost:4000` to see your site.

#### 5. **Configure Your Jekyll Site**

1. **Open `_config.yml`:**
   Edit the `_config.yml` file to customize your site's settings.

   ```yaml
   title: My Blog
   description: A blog about something awesome
   baseurl: "" # the subpath of your site, e.g. /blog
   url: "https://username.github.io" # the base hostname & protocol for your site
   ```

2. **Update `_config.yml` with your repository details:**
   Make sure the URL and baseurl are correctly set to point to your GitHub Pages site.

#### 6. **Add Content to Your Blog**

1. **Create a new post:**
   Add a new Markdown file to the `_posts` directory. Name the file using the format `YYYY-MM-DD-title.md`.

   ```markdown
   ---
   layout: post
   title: "Welcome to My Blog"
   date: 2024-06-08 12:00:00 -0000
   categories: jekyll update
   ---
   This is my first blog post!
   ```

2. **Commit your changes:**
   Save the file and commit your changes to your local Git repository.

#### 7. **Push Your Site to GitHub**

1. **Add your GitHub repository as a remote:**

   ```sh
   git remote add origin https://github.com/username/username.github.io.git
   ```

2. **Push your site to GitHub:**

   ```sh
   git add .
   git commit -m "Initial commit"
   git push -u origin master
   ```

#### 8. **Configure GitHub Pages**

1. **Go to your GitHub repository:**
   Navigate to the `username.github.io` repository on GitHub.

2. **Set up GitHub Pages:**
   - Go to the repository settings.
   - Scroll down to the "GitHub Pages" section.
   - Select the source as `master branch` or `main branch` (depending on your default branch).
   - Save your changes.

3. **Access your site:**
   Your blog should now be live at `https://username.github.io`.

### Additional Tips

- **Themes:** You can change the theme of your Jekyll site by modifying the `_config.yml` file. You can find available themes at [Jekyll Themes](https://jekyllthemes.io/).
- **Plugins:** Jekyll supports various plugins to extend its functionality. You can add plugins by updating your `Gemfile` and `_config.yml` file.

By following these steps, you should have a basic Jekyll blog hosted on GitHub Pages. You can continue to customize your blog by editing the HTML, CSS, and adding more posts

y following these steps, you should have a basic Jekyll blog hosted on GitHub Pages. You can continue to customize your blog by editing the HTML, CSS, and adding more posts

