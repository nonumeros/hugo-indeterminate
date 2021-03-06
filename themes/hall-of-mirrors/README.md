# Hall of Mirrors

> PhotoSwipe Image Gallery for [After Dark]. Hall of Mirrors adds a responsive JavaScript image gallery using [PhotoSwipe](http://photoswipe.com).

[![Latest NPM version](https://img.shields.io/npm/v/hall-of-mirrors.svg?style=flat-square)](https://www.npmjs.com/package/hall-of-mirrors)
[![NPM downloads per month](https://img.shields.io/npm/dm/hall-of-mirrors.svg?style=flat-square)](https://www.npmjs.com/package/hall-of-mirrors)
[![Minimum After Dark version](https://img.shields.io/badge/after%20dark->%3D%205.4.0-000000.svg?style=flat-square)](https://git.habd.as/comfusion/after-dark/)
[![WTFPL licensed](https://img.shields.io/npm/l/hall-of-mirrors.svg?style=flat-square&longCache=true)](https://git.habd.as/comfusion/hall-of-mirrors/src/branch/master/COPYING)

## Demo

<video controls>
  <source src="https://jhabdas.keybase.pub/after-dark-hall-of-mirrors-demo.mp4" type="video/mp4">
  <p>Your browser doesn't support HTML5 video. Here is a <a href="https://jhabdas.keybase.pub/after-dark-hall-of-mirrors-demo.mp4">link to the video</a> instead.</p>
</video>

## Setup

None requried unless you're hosting your site from a subdirectory (e.g. `example.com/blog/`). If so you'll need to update the url types in `default-skin.css` to point to your base url. A script called `urlize` has been provided to facilitate this change.

## Installation

1. Copy the contents of this repository into a directory called `themes/hall-of-mirrors` under the root of your After Dark site.
2. Add `hall-of-mirrors` as a [theme component](https://gohugo.io/themes/theme-components/) to your After Dark site `config.toml`, e.g.

    ```toml
    theme = [
      "hall-of-mirrors",
      "after-dark"
    ]
    ```

3. Add and specify settings for the module in your After Dark site config, e.g.

    ```toml
    [params.modules.hall_of_mirrors]
      enabled = true # Required in version 0.1.0
    ```

4. Create a [Leaf Bundle] to group image resources you wish to display in a PhotoSwipe gallery together with your content.
5. [Configure the gallery](#configuration) to your liking.
6. Build and deploy your After Dark site.

## Configuration

To display a gallery add the [Page Resources] you wish to display to your [Leaf Bundle] and configure your front matter.

### Minimal

The following is all you need to display a basic gallery. Seriously.

```toml
[[resources]]
  src = "**.jpg" # Display any jpeg image in the leaf bundle
  name = "gallery" # Name must include the word 'gallery'
```

```toml
[[resources]]
  src = "images/gallery/**.jpg" # Restrict images to a folder
  name = "Image gallery" # Provide a more friendly gallery name
```

### Extended

If you want to add captions and enhance SEO you can configure individual resources.

```toml
[[resources]]
  src = "**/ray-hennessy-763310-unsplash.jpg"
  [resources.params]
    thumb_size = "750x" # Adjust size of thumbnail image
  [resources.params.meta]
    creator = "Ray Hennessy"
    description = "This is a long description. It is shown instead of the title and is intended to provide more information."

[[resources]]
  src = "**sprat**" # Glob for image with 'sprat' in the filename
  title = "Diverse succulents around a rock"
  [resources.params]
    hide_credits = true # Display title but not creator
  [resources.params.meta]
    creator = "Annie Spratt" # Maps to schema structured data

[[resources]]
  src = "**/blake-richard-verdoorn-20063-unsplash.jpg"
  title = "Bridge over a green waterfall"
  [resources.params]
    hide_credits = true
    thumb_size = "350x"
  [resources.params.meta]
    creator = "Blake Richard Verdoorn"
    keywords = ["nature", "waterfall", "bridge"]

[[resources]]
  src = "images/gallery/**.jpg"
  name = "Nature gallery"
  [resources.params.meta]
    genere = "digital" # Set a genere for all image resources
```

This should get you started. Expect some breaking changes as the development is completed.

## License

Copyright (C) 2018 Josh Habdas <jhabdas@protonmail.com>

This work is free. You can redistribute it and/or modify it under the
terms of the Do What The Fuck You Want To Public License, Version 2,
as published by Sam Hocevar. See the COPYING file for more details.

[After Dark]: https://git.habd.as/comfusion/after-dark/
[Leaf Bundle]: https://gohugo.io/content-management/page-bundles/#leaf-bundles
[Page Resources]: https://gohugo.io/content-management/page-resources/
