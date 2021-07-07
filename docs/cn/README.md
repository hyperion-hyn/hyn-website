Forked from https://github.com/y7kim/agency-jekyll-theme

#### 自定义插件:
1. [https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin](https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin)


#### 在github.com pages使用自定义插件的方法
[How do I configure GitHub to use non-supported Jekyll site plugins?
](https://stackoverflow.com/questions/28249255/how-do-i-configure-github-to-use-non-supported-jekyll-site-plugins)
1. 使用[Travis CI](https://docs.travis-ci.com/user/tutorial/), 需要在[travis-ci.com](travis-ci.com)上用github.com账号登录授权
2. 本地使用bundle exec jekyll build，然后将_site目录当成gh-pages分支推送上去
   1. from your working folder git init
   2. git remote add origin git@github.com:userName/userName.github.io.git (UO) or git remote add origin git@github.com:userName/repositoryName.git (P)
   3. jekyll new . creates your code base
   4. in _config.yml, set the baseurl parameter to baseurl: '' (UO) or baseurl: '/repositoryName' (P)
   5. in .gitignore add _site, it will be versioned in the other branch
   6. jekyll build will create the destination folder and build site.
   7. git checkout -b sources (UO) or git checkout master (P)
   8. git add -A
   9. git commit -m "jekyll base sources" commit your source code
   10. git push origin sources (UO) or git push origin master (P) push your sources in the appropriate branch
   11. cd _site
   12. touch .nojekyll, this file tells gh-pages that there is no need to build
   13. git init init the repository
   14. git remote add origin git@github.com:userName/userName.github.io.git (UO) or git remote add origin git@github.com:userName/repositoryName.git (P)
   15. git checkout master (UO) or git checkout -b gh-pages (P) put this repository on the appropriate branch
   16. git add -A
   17. git commit -m "jekyll first build" commit your site code
   18. git push origin master (UO) or git push origin gh-pages (P)

现在采用的方式是第二种，所以开发的时候需要在master或者是其他不是gh-pages的分支上开发。开发完成，测试没问题后，使用`bundle exec jekyll build`生成静态文件。切换到_site目录，将生成的文件提交

**需要注意的是，每次`bundle exec jekyll build`，都会删除掉_site目录下的`.nojekyll`这个文件，所以在提交前，需要将这个文件重置一下再提交。**

**警告：请不要将`gh-page`这个分支合并到master或者是其他开发分支上**

