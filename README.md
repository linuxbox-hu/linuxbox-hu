# linuxbox.hu

Source for [linuxbox.hu](https://linuxbox.hu), a Hungarian-language Linux/sysadmin blog
built with [Hugo](https://gohugo.io/) and the [Chirpy](https://github.com/geekifan/hugo-theme-chirpy)
theme. The site was migrated from an older Drupal installation, and later from Jekyll; the
`article/`, `blog/`, `node/` and `story/` legacy URLs are preserved via `aliases:` front matter
on the posts they used to point to.

## Local development

```shell
hugo mod vendor              # vendor the theme + its dependencies into _vendor/
hugo server                  # serve locally with live reload
hugo --gc --minify           # production build, output in public/
```

## Deployment

The site is deployed by pulling this repo on the production host and running a Hugo build there
(served by Apache) — there is no CI/CD pipeline or GitHub Pages involved.

## License

Site content is © its authors. The Hugo/Chirpy scaffolding is published under the [MIT](LICENSE) License.
