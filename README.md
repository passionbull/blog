### Introduction

`steemblog` is a blog service that syncs your steem blogs into [https://steemblog.github.io](https://steemblog.github.io) pages. It's built based on steem APIs and [hexo](https://hexo.io) blog framework.

![Pixabay](https://cdn.pixabay.com/photo/2015/06/01/09/04/blog-793047_1280.jpg)
<br/>
Image Source: [Pixabay](https://cdn.pixabay.com/photo/2015/06/01/09/04/blog-793047_1280.jpg)


### Features

1. Synchronize posts from steem by account to https://steemblog.github.io/@{account} daily.
1. With the help of hexo themes, the blog is easier to read, search, archive, etc.

You can find my blog from [https://steemblog.github.io/@robertyan](https://steemblog.github.io/@robertyan) as an example.


### How to Sync Your Blogs

To use the blog service, we simply add your steem account name to the STEEM_ACCOUNTS variable of this project's Travis CI job, then the synchronization will be done daily automatically.

You may contact [@robertyan](https://busy.org/@robertyan) if you need help to setup the service in steemblog.


### Commands

The commands / tasks in this project is manged with `invoke` package.

By running `pipenv run invoke -l`, you're able to see the available tasks in the bot.

```
Available tasks:

  blog.build         build the static pages from steem posts
  blog.build-all     download the posts of all the accounts, and generate pages
  blog.clean         clean the downloaded posts
  blog.deploy        deploy the static blog to the GitHub pages
  blog.download      download the posts to local by the account
  blog.test          build and launch the blog server in local environment
  steem.list-posts   list the post by account, tag, keyword, etc.
```

To see the introduction of a command, run `pipenv run invoke -h <command>`.


### Reference

- The blog service is built based on the [steem blog mirroring tool](https://github.com/think-in-universe/blog)
- The interaction with Steem blockchain is built with [beem](https://github.com/holgern/beem) project.
- The blog generation is built with [hexo](https://hexo.io) blog framework.


### License

The project is open sourced under MIT license.

### Step by Step (TEST)

1. fork this project
2. git clone https://github.com/passionbull/blog-1.git
3. cd blog-1
4. git submodule update --init --recursive
5. pipenv install
6. npm install -g hexo-cli
7. npm install
8. pipenv run invoke -l
9. pipenv run invoke blog.download -a jacobyu
10. pipenv run invoke blog.test

### Step by Step (Deploy)

1. check your blog/message.py
    - check type and repository_link, branch in deploy
2. pipenv run invoke blog.download -a jacobyu
3. pipenv run invoke blog.deploy

### Apply SEO

1. npm install --save hexo-auto-canonical
2. npm install hexo-generator-seo-friendly-sitemap --save

### Reference
- https://futurecreator.github.io/2016/06/23/search-engine-optimization-hexo-plugins/

