# Negative Materialism Website

A Hugo-based website using the Hextra theme for the Negative Materialism framework - a dialectical anti-synthesis approach to critiquing late-capitalist class struggle through practical dissection of immediate material conditions.

## Contributing

### How to Contribute

We encourage participation from anyone interested in the Negative Materialism framework. There are several ways to contribute:

#### 1. Submit Content to the Documents Repository
- Visit [https://github.com/Negative-Materialism/Documents](https://github.com/Negative-Materialism/Documents)
- Submit pull requests with new analysis, documentation, or corrections
- Follow the existing content structure and formatting

#### 2. Edit This Website Directly
- Click the "Edit this page on GitHub" button (appears on every page)
- Make your changes directly in the browser
- Submit a pull request for review

#### 3. Content Guidelines

When contributing content:

- Use clear, accessible language
- Include proper front matter with title, date, description, and tags
- Add relevant tags for discoverability
- Keep analysis grounded in material conditions
- Follow the existing writing style and tone

#### 4. Technical Contributions

- Report bugs or suggest improvements
- Contribute to the Hugo configuration
- Improve accessibility or performance
- Add new shortcodes or features

### Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally
3. **Install Hugo** (extended version recommended)
4. **Run the development server**: `hugo server -D`
5. **Make your changes** and test locally
6. **Submit a pull request**

### Content Creation Workflow

1. Create a new `.md` file in the appropriate directory
2. Add proper front matter with metadata
3. Write your content using Markdown
4. Use shortcodes for special features
5. Test locally with `hugo server -D`
6. Submit via pull request

## About This Site

This website is built with [Hugo](https://gohugo.io/) and the [Hextra theme](https://github.com/imfing/hextra), providing a modern, fast, and accessible platform for publishing analysis and documentation.

## Hugo Hextra System

### Data Headers (Front Matter)

Every content file in Hugo uses YAML front matter (data headers) to define metadata. Here's how they work:

#### Basic Structure
```yaml
---
title: "Your Article Title"
date: 2025-01-15
draft: false
description: "A brief description of your content"
tags: ["tag1", "tag2", "tag3"]
categories: ["analysis"]
- **`author`**: Name of the content's author. You can add this field to attribute posts or pages. Example:
  ```yaml
  author: "Jane Doe"
  ```
  For multiple authors, use a list:
  ```yaml
  author:
    - "Jane Doe"
    - "John Smith"
  ```

---
```

#### Key Front Matter Fields

**Essential Fields:**
- **`title`**: The page title (string)
- **`date`**: The date associated with the page, typically creation date (string)
- **`draft`**: Whether to disable rendering unless `--buildDrafts` flag is used (boolean)
- **`description`**: Brief summary for search results and meta tags (string)
- **`type`**: Content type, overriding the value derived from the section (string)

**Content Organization:**
- **`tags`**: Array of topic tags for categorization (string array)
- **`categories`**: Content categories (string array)
- **`weight`**: Page weight for ordering within collections (integer)
- **`slug`**: Override the last segment of the URL path (string)
- **`url`**: Override the entire URL path (string)

**Publishing Control:**
- **`publishDate`**: Publication date - page won't render before this date (string)
- **`expiryDate`**: Expiration date - page won't render after this date (string)
- **`lastmod`**: Last modified date (string)

**Content Enhancement:**
- **`summary`**: Content summary or teaser (string)
- **`keywords`**: Array of keywords for meta tags (string array)
- **`layout`**: Template name to override default template lookup (string)
- **`linkTitle`**: Shorter version of the title (string)

**Menu Integration:**
- **`menus`**: Add page to given menu(s) (string, string array, or map)

**Custom Parameters:**
- **`params`**: Map of custom page parameters (map)
  ```yaml
  params:
    featured: true
    custom_field: "value"
  ```

**Authors (Taxonomy-based):**
- **`authors`**: Array of author names for taxonomy-based author system (string array)
  ```yaml
  authors: ["Jane Doe", "John Smith"]
  ```
  
  This requires setting up the author taxonomy in your `hugo.yaml`:
  ```yaml
  taxonomies:
    author: authors
    tag: tags
    category: categories
  ```
  
  Then create author data files in `/content/authors/author-name/_index.md`:
  ```yaml
  ---
  name: "Jane Doe"
  bio: "Jane is a political theorist specializing in dialectical materialism."
  twitter: "jane_doe"
  ---
  ```

**Advanced Features:**
- **`aliases`**: Array of relative URLs that redirect to current page (string array)
- **`cascade`**: Map of front matter keys passed to descendants (map)
- **`outputs`**: Output formats to render (string array)
- **`resources`**: Metadata for page resources (map array)
- **`sitemap`**: Sitemap options (map)

#### Date Formats

Hugo supports multiple date formats. Use one of these parsable formats:

| Format                    | Time Zone            |
| ------------------------- | -------------------- |
| 2023-10-15T13:18:50-07:00 | America/Los_Angeles  |
| 2023-10-15T13:18:50-0700  | America/Los_Angeles  |
| 2023-10-15T13:18:50Z      | Etc/UTC              |
| 2023-10-15T13:18:50       | Default is Etc/UTC   |
| 2023-10-15                | Default is Etc/UTC   |
| 15 Oct 2023               | Default is Etc/UTC   |

#### Taxonomies

Taxonomies are used to classify content. The most common are `tags` and `categories`, but you can define custom taxonomies in your site configuration:

```yaml
# In hugo.yaml
taxonomies:
  tag: tags
  category: categories
  genre: genres
```

Then use them in front matter:
```yaml
---
tags: ["capitalism", "dialectics", "labor"]
categories: ["analysis"]
genres: ["political-theory", "critique"]
---
```

#### Special Hextra Features

- **`cascade`**: Inherit settings to child pages
  ```yaml
  cascade:
    type: blog  # Makes all child pages blog posts
    params:
      color: red
  ```

- **Menu integration**: Pages automatically appear in navigation based on weight and structure

#### Cascade Targeting

You can target specific pages with cascade using the `target` keyword:

```yaml
cascade:
  params:
    color: red
  target:
    path: '{/articles,/articles/**}'  # Only articles section
    kind: page                        # Only regular pages
    environment: '{staging,production}'  # Only specific environments
```

For multiple targets, use an array:
```yaml
cascade:
- params:
    color: red
  target:
    path: '{/books/**}'
- params:
    color: blue
  target:
    path: '{/films/**}'
```

### Shortcodes

Shortcodes are Hugo's way of creating reusable content components. This site includes several custom shortcodes:

#### Recent Posts Shortcode
```markdown
{{< recent-posts >}}
```
Displays the 20 most recent posts in a card layout with titles, dates, descriptions, and tags.

#### YouTube Shortcode
```markdown
{{< youtube "VIDEO_ID" "Optional Title" >}}
```
Embeds YouTube videos with proper accessibility attributes.

Example:
```markdown
{{< youtube "dQw4w9WgXcQ" "Never Gonna Give You Up" >}}
```

### Content Organization

#### Directory Structure
```
content/
├── _index.md          # Homepage
├── about.md           # About page
├── analysis/          # Analysis section
│   ├── _index.md      # Analysis landing page
│   └── *.md           # Individual analysis posts
└── README.md          # This file
```

#### Content Types

1. **Blog Posts**: Go in the `analysis/` directory
2. **Static Pages**: Use `type: page` in front matter
3. **Section Pages**: Use `_index.md` for section landing pages

### Theme Configuration

The site uses Hextra with custom configurations in `hugo.yaml`:

- **Dark theme** by default with toggle
- **Search functionality** enabled
- **Edit links** pointing to GitHub
- **Custom menu** with social links
- **Logo support** with light/dark variants

### Author System Implementation

This site uses a taxonomy-based author system that allows for rich author information and automatic author pages.

#### Setting Up Authors

1. **Configure taxonomy** in `hugo.yaml`:
   ```yaml
   taxonomies:
     author: authors
     tag: tags
     category: categories
   ```

2. **Create author data files** in `/content/authors/author-name/_index.md`:
   ```yaml
   ---
   name: "Author Name"
   bio: "Author biography and credentials"
   twitter: "twitter_handle"
   ---
   ```

3. **Add authors to posts** in front matter:
   ```yaml
   ---
   title: "Post Title"
   authors: ["Author Name"]
   ---
   ```

#### Author Templates

**Author byline in posts** (add to your single post template):
```html
{{ range .Param "authors" }}
  {{ $name := . }}
  {{ $path := printf "/%s/%s" "authors" ($name | urlize) }}
  {{ with $.Site.GetPage $path }}
    <div class="author-byline">
      <h3>{{ .Params.name }}</h3>
      <p>{{ .Params.bio }}</p>
      {{ if .Params.twitter }}
        <p><a href="https://twitter.com/{{ .Params.twitter }}">@{{ .Params.twitter }}</a></p>
      {{ end }}
    </div>
  {{ end }}
{{ end }}
```

**Author listing page** (create `/layouts/_default/author.terms.html`):
```html
<h1>Authors</h1>
{{ range .Data.Pages }}
  <div class="author-card">
    <h2>{{ .Params.name }}</h2>
    <p>{{ .Params.bio }}</p>
    {{ if .Params.twitter }}
      <p><a href="https://twitter.com/{{ .Params.twitter }}">@{{ .Params.twitter }}</a></p>
    {{ end }}
  </div>
{{ end }}
```

**Individual author pages** (create `/layouts/_default/author.html`):
```html
<h1>{{ .Params.name }}</h1>
<p>{{ .Params.bio }}</p>

<h2>Articles by {{ .Params.name }}</h2>
{{ range .Pages }}
  <article>
    <h3><a href="{{ .RelPermalink }}">{{ .Title }}</a></h3>
    <p>{{ .Summary }}</p>
    <time>{{ .Date.Format "January 2, 2006" }}</time>
  </article>
{{ end }}
```

#### Author Images

Store author images in `/static/img/authors/` following the naming convention:
- File: `/static/img/authors/author-name.jpg`
- Use in templates: `/img/authors/{{ $name | urlize }}.jpg`

## Technical Details

### Requirements
- Hugo Extended (latest version)
- Node.js (for asset processing)

### Development
```bash
# Start development server
hugo server -D

# Build for production
hugo

# Build with drafts
hugo -D
```

### Deployment
The site is configured for Netlify deployment with automatic builds from the main branch.

## License

This project is open source. See the LICENSE file for details.

---

**Join the conversation**: Whether you're contributing analysis, fixing typos, or suggesting improvements, your participation helps build a more robust framework for understanding and resisting late-capitalist exploitation.
