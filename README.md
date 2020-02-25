SCP-079 website is generated by [Hakyll], hosted on GitLab Pages.

---

## Site

This project's static Pages are built by [GitLab CI][ci], following 
the steps defined in [`.gitlab-ci.yml`](.gitlab-ci.yml).

## Theme

We call this Hakyll theme `Screen`. 

This is a theme intended to use to [SCP-079](https://scp-079.org) website. 
The theme is converted from a Jekyll theme [darcli](https://github.com/gildasio/darcli). 
We made some changes to make it responsive and more suitable for our site.

There is a post [demo](https://scp-079.org/posts/2019-03-29-post-test/).

## How to use

To use this project as your user or group website, you will need 
additional steps to modify some source code files.

- `templates/archives.html`
- `templates/head.html`
- `templates/open_graph.html`
- `templates/header.html`
- `site.hs`

Also, you should delete some `.md` files in `pages/` and `posts/`.

## Building locally

To work locally with this project, you'll have to follow the steps below:

1. Fork, clone or download this project
2. Modify some files
3. Use cabal or stack:
    - cabal:
        1. Build: `cabal new-update && cabal new-build`
        2. Generate the website: `cabal new-exec site build`
        3. Preview your project: `cabal new-exec site watch`
    - stack:
        1. Build: `stack install`
        2. Generate the website: `stack exec site build`
        3. Preview your project: `stack exec site watch`
4. View the site locally

Read more at Hakyll's [documentation][hakyll].

## Be Better

Welcome to contribute to this 
[project](https://gitlab.com/scp-079/scp-079.gitlab.io/).

## Getting help

* [Tutorials](https://jaspervdj.be/hakyll/tutorials.html)
* [Google discussion group](https://groups.google.com/forum/#!forum/hakyll)
* [Hakyll on StackOverflow](https://stackoverflow.com/questions/tagged/hakyll)

## License

This theme is under [GPLv3](LICENSE_GNU_GPLv3).
The theme is based on [darcli](https://github.com/gildasio/darcli).


All documents of this project is under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

All the sound effects in `static/audio/` are under 
[CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/), 
and come from 
[SCP - Containment Breach](http://www.scpcbgame.com/) 
game.



[ci]: https://about.gitlab.com/gitlab-ci/
[hakyll]: https://jaspervdj.be/hakyll/
[install]: https://jaspervdj.be/hakyll/tutorials/01-installation.html
