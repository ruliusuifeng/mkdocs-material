---
template: overrides/main.html
---

# Adding a git repository

If your documentation is related to source code, Material for MkDocs provides
the ability to display information to the project's repository as part of the
static site, including statistics like stars and forks. Furthermore, individual
documents can be linked to specific source files.

## Configuration

In order to display a link to the repository of your project as part of your
documentation, set [`repo_url`][1] in `mkdocs.yml` to the public URL of your
repository, e.g.:

``` yaml
repo_url: https://github.com/squidfunk/mkdocs-material
```

The link to the repository will be rendered next to the search bar on big
screens and as part of the main navigation drawer on smaller screen sizes.
Additionally, for GitHub and GitLab, the number of stars and forks is
automatically requested and rendered for _public repositories_.

  [1]: https://www.mkdocs.org/user-guide/configuration/#repo_url

### Repository name

[:octicons-file-code-24: Source][2] · :octicons-milestone-24: Default:
_automatically set to_ `GitHub`, `GitLab` _or_ `Bitbucket`

MkDocs will infer the source provider by examining the URL and try to set the
_repository name_ automatically. If you wish to customize the name, set
[`repo_name`][3] in `mkdocs.yml`:

``` yaml
repo_name: squidfunk/mkdocs-material
```

  [2]: https://github.com/squidfunk/mkdocs-material/blob/master/src/partials/source.html
  [3]: https://www.mkdocs.org/user-guide/configuration/#repo_name

### Repository icon

[:octicons-file-code-24: Source][2] · :octicons-milestone-24: Default:
`fontawesome/brands/git-alt`

While the default _repository icon_ is a generic git icon, it can be set to
[any icon bundled with the theme][4] by referencing a valid icon path in
`mkdocs.yml`:

``` yaml
theme:
  icon:
    repo: fontawesome/brands/git-alt
```

Some popular choices:

- :fontawesome-brands-git: – `fontawesome/brands/git`
- :fontawesome-brands-git-alt: – `fontawesome/brands/git-alt`
- :fontawesome-brands-git-square: – `fontawesome/brands/git-square`
- :fontawesome-brands-github: – `fontawesome/brands/github`
- :fontawesome-brands-github-alt: – `fontawesome/brands/github-alt`
- :fontawesome-brands-github-square: – `fontawesome/brands/github-square`
- :fontawesome-brands-gitlab: – `fontawesome/brands/gitlab`
- :fontawesome-brands-gitkraken: – `fontawesome/brands/gitkraken`
- :fontawesome-brands-bitbucket: – `fontawesome/brands/bitbucket`
- :fontawesome-solid-trash: – `fontawesome/solid/trash`

  [4]: https://github.com/squidfunk/mkdocs-material/tree/master/material/.icons

### Latest release

[:octicons-file-code-24: Source][5] ·
[:octicons-heart-fill-24:{: .tx-heart } Insiders only][5]{: .tx-insiders }

The visual appearance of the repository link has been improved as part of
[Insiders][5], and will now automatically include the latest release tag which
is not marked as a draft or pre-release:

<figure markdown="1">

[![Search suggestions][6]][6]

  <figcaption markdown="1">

A demo is worth a thousand words — check it out at
[squidfunk.github.io/mkdocs-material-insiders][7]

  </figcaption>
</figure>

  [5]: ../insiders.md
  [6]: ../assets/screenshots/repository.png
  [7]: https://squidfunk.github.io/mkdocs-material-insiders/setup/adding-a-git-repository/

### Edit button

[:octicons-file-code-24: Source][8] · :octicons-milestone-24: Default:
_automatically set_

If the repository URL points to a [GitHub][9], [GitLab][10] or [Bitbucket][11]
repository, an _edit button_ is displayed at the top of each document. This
behavior can be changed by setting [`edit_uri`][12] in `mkdocs.yml`:

=== "Customize edit path"

    ``` yaml
    edit_uri: edit/master/docs/
    ```

=== "Hide edit button"

    ``` yaml
    edit_uri: ""
    ```

  [8]: https://github.com/squidfunk/mkdocs-material/blob/master/src/base.html
  [9]: https://github.com/
  [10]: https://about.gitlab.com/
  [11]: https://bitbucket.org/
  [12]: https://www.mkdocs.org/user-guide/configuration/#edit_uri

### Revision date

[:octicons-file-code-24: Source][13] ·
[:octicons-cpu-24: Plugin][14]

The [git-revision-date][13] plugin adds support for displaying the date a
document was _last updated_ at the bottom of each page. It can be installed
with `pip`:

```
pip install mkdocs-git-revision-date-plugin
```

Then, add the following to `mkdocs.yml`:

``` yaml
plugins:
  - git-revision-date
```

The following options are supported:

`enabled_if_env`{: #enabled_if_env }

:   :octicons-milestone-24: Default: _none_ – This option defines whether the
    date is actually extracted from git, which makes it possible to disable
    extraction for cases when the repository is not available:

    ``` yaml
    plugins:
      - git-revision-date:
          enabled_if_env: CI
    ```

_Material for MkDocs doesn't provide official support for the other options of
this plugin, so they may be supported but can also yield weird results. Use
them at your own risk._

  [13]: https://github.com/squidfunk/mkdocs-material/blob/master/src/partials/source-date.html
  [14]: https://github.com/zhaoterryy/mkdocs-git-revision-date-plugin

### Revision date, localized

[:octicons-file-code-24: Source][13] ·
[:octicons-cpu-24: Plugin][15]

Similarly, the [git-revision-date-localized][15] plugin adds support for adding
a localized _last updated_ date at the bottom of each page. It can be installed
with `pip`:

```
pip install mkdocs-git-revision-date-localized-plugin
```

Then, add the following to `mkdocs.yml`:

``` yaml
plugins:
  - git-revision-date-localized
```

The following options are supported:

`type`{: #type }

:   :octicons-milestone-24: Default: `date` – This option allows to change the
    format of the date to be displayed. Valid values are `date`, `datetime`,
    `iso_date`, `iso_datetime` and `timeago`:

    ``` yaml
    plugins:
      - git-revision-date-localized:
          type: date
    ```

`fallback_to_build_date`{: #fallback_to_build_date }

:   :octicons-milestone-24: Default: `false` – This option specifies whether
    the time when `mkdocs build` was executed should be used as a fallback when
    the git repository is not available:

    ``` yaml
    plugins:
      - git-revision-date-localized:
          fallback_to_build_date: true
    ```

_Material for MkDocs doesn't provide official support for the other options of
this plugin, so they may be supported but can also yield weird results. Use
them at your own risk._

  [15]: https://github.com/timvink/mkdocs-git-revision-date-localized-plugin
