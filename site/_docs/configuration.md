---
layout: docs
title: Configuration
prev_section: structure
next_section: frontmatter
permalink: /docs/configuration/
---

Jekyll allows you to concoct your sites in any way you can dream up, and it’s
thanks to the powerful and flexible configuration options that this is possible.
These options can either be specified in a `_config.yml` file placed in your
site’s root directory, or can be specified as flags for the `jekyll` executable
in the terminal.

## Configuration Settings

### Global Configuration

The table below lists the available settings for Jekyll, and the various <code
class="option">options</code> (specified in the configuration file) and <code
class="flag">flags</code> (specified on the command-line) that control them.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>Setting</th>
      <th>
        <span class="option">Options</span> and <span class="flag">Flags</span>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr class="setting">
      <td>
        <p class="name"><strong>Site Source</strong></p>
        <p class="description">Change the directory where Jekyll will read files</p>
      </td>
      <td class="align-center">
        <p><code class="option">source: DIR</code></p>
        <p><code class="flag">-s, --source DIR</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Site Destination</strong></p>
        <p class="description">Change the directory where Jekyll will write files</p>
      </td>
      <td class="align-center">
        <p><code class="option">destination: DIR</code></p>
        <p><code class="flag">-d, --destination DIR</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Safe</strong></p>
        <p class="description">Disable <a href="../plugins/">custom plugins, and ignore symbolic links</a>.</p>
      </td>
      <td class="align-center">
        <p><code class="option">safe: BOOL</code></p>
        <p><code class="flag">--safe</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Exclude</strong></p>
        <p class="description">
          Exclude directories and/or files from the
          conversion. These exclusions are relative to the site's
          source directory and cannot be outside the source directory.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">exclude: [DIR, FILE, ...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Include</strong></p>
        <p class="description">
          Force inclusion of directories and/or files in the conversion.
          <code>.htaccess</code> is a good example since dotfiles are excluded
          by default.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">include: [DIR, FILE, ...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Time Zone</strong></p>
        <p class="description">
            Set the time zone for site generation. This sets the <code>TZ</code>
            environment variable, which Ruby uses to handle time and date
            creation and manipulation. Any entry from the
            <a href="http://en.wikipedia.org/wiki/Tz_database">IANA Time Zone
            Database</a> is valid, e.g. <code>America/New_York</code>. A list of all
            available values can be found <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">
            here</a>. The default is the local time zone, as set by your operating system.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">timezone: TIMEZONE</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Encoding</strong></p>
        <p class="description">
            Set the encoding of files by name. Only available for Ruby
            1.9 or later).
            The default value is <code>utf-8</code> starting in 2.0.0,
            and <code>nil</code> before 2.0.0, which will yield the Ruby
            default of <code>ASCII-8BIT</code>.
            Available encodings can be shown by the
            command <code>ruby -e 'puts Encoding::list.join("\n")'</code>.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">encoding: ENCODING</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>Defaults</strong></p>
        <p class='description'>
            Set defaults for <a href="../frontmatter/" title="YAML Front Matter">YAML Front Matter</a>
            variables.
        </p>
      </td>
      <td class='align-center'>
        <p>see <a href="#front-matter-defaults" title="details">below</a></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

### Build Command Options

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>Setting</th>
      <th><span class="option">Options</span> and <span class="flag">Flags</span></th>
    </tr>
  </thead>
  <tbody>
    <tr class="setting">
      <td>
        <p class="name"><strong>Regeneration</strong></p>
        <p class="description">Enable auto-regeneration of the site when files are modified.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">-w, --watch</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Configuration</strong></p>
        <p class="description">Specify config files instead of using <code>_config.yml</code> automatically. Settings in later files override settings in earlier files.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--config FILE1[,FILE2,...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Drafts</strong></p>
        <p class="description">Process and render draft posts.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--drafts</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Future</strong></p>
        <p class="description">Publish posts with a future date.</p>
      </td>
      <td class="align-center">
        <p><code class="option">future: BOOL</code></p>
        <p><code class="flag">--future</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>LSI</strong></p>
        <p class="description">Produce an index for related posts.</p>
      </td>
      <td class="align-center">
        <p><code class="option">lsi: BOOL</code></p>
        <p><code class="flag">--lsi</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Limit Posts</strong></p>
        <p class="description">Limit the number of posts to parse and publish.</p>
      </td>
      <td class="align-center">
        <p><code class="option">limit_posts: NUM</code></p>
        <p><code class="flag">--limit_posts NUM</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Force polling</strong></p>
        <p class="description">Force watch to use polling.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--force_polling</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

### Serve Command Options

In addition to the options below, the `serve` sub-command can accept any of the options
for the `build` sub-command, which are then applied to the site build which occurs right
before your site is served.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>Setting</th>
      <th><span class="option">Options</span> and <span class="flag">Flags</span></th>
    </tr>
  </thead>
  <tbody>
    <tr class="setting">
      <td>
        <p class="name"><strong>Local Server Port</strong></p>
        <p class="description">Listen on the given port.</p>
      </td>
      <td class="align-center">
        <p><code class="option">port: PORT</code></p>
        <p><code class="flag">--port PORT</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Local Server Hostname</strong></p>
        <p class="description">Listen at the given hostname.</p>
      </td>
      <td class="align-center">
        <p><code class="option">host: HOSTNAME</code></p>
        <p><code class="flag">--host HOSTNAME</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Base URL</strong></p>
        <p class="description">Serve the website from the given base URL</p>
      </td>
      <td class="align-center">
        <p><code class="option">baseurl: URL</code></p>
        <p><code class="flag">--baseurl URL</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Detach</strong></p>
        <p class="description">Detach the server from the terminal</p>
      </td>
      <td class="align-center">
        <p><code class="option">detach: BOOL</code></p>
        <p><code class="flag">-B, --detach</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note warning">
  <h5>Do not use tabs in configuration files</h5>
  <p>
    This will either lead to parsing errors, or Jekyll will revert to the
    default settings. Use spaces instead.
  </p>
</div>

## Front Matter defaults

Using [YAML Front Matter](../frontmatter/) is one way that you can specify configuration in the pages and posts for your site. Setting things like a default layout, or customizing the title, or specifying a more precise date/time for the post can all be added to your page or post front matter.

Often times, you will find that you are repeating a lot of configuration options. Setting the same layout in each file, adding the same category - or categories - to a post, etc. You can even add custom variables like author names, which might be the same for the majority of posts on your blog.

Instead of repeating this configuration each time you create a new post or page, Jekyll provides a way to set these defaults in the site configuration. To do this, you can specify  site-wide defaults using the `defaults` key in the `_config.yml` file in your projects root directory.

The `defaults` key holds an array of scope/values pairs that define what defaults should be set for a particular file path, and optionally, a file type in that path.

Let's say that you want to add a default layout to all pages and posts in your site. You would add this to your `_config.yml` file:

{% highlight yaml %}
defaults:
  -
    scope:
      path: "" # an empty string here means all files in the project
    values:
      layout: "default"
{% endhighlight %}

Here, we are scoping the `values` to any file that exists in the scopes path. Since the path is set as an empty string, it will apply to **all files** in your project. You probably don't want to set a layout on every file in your project - like css files, for example - so you can also specify a `type` value under the `scope` key.

{% highlight yaml %}
defaults:
  -
    scope:
      path: "" # an empty string here means all files in the project
      type: "posts" # previously `post` in Jekyll 2.2.
    values:
      layout: "default"
{% endhighlight %}

Now, this will only set the layout for files where the type is `posts`.
The different types that are available to you are `pages`, `posts`, `drafts` or any collection in your site. While `type` is optional, you must specify a value for `path` when creating a `scope/values` pair.

As mentioned earlier, you can set multiple scope/values pairs for `defaults`.

{% highlight yaml %}
defaults:
  -
    scope:
      path: ""
      type: "posts"
    values:
      layout: "my-site"
  -
    scope:
      path: "projects"
      type: "pages"
    values:
      layout: "project" # overrides previous default layout
      author: "Mr. Hyde"
{% endhighlight %}

With these defaults, all posts would use the `my-site` layout. Any html files that exist in the `projects/` folder will use the `project` layout, if it exists. Those files will also have the `page.author` [liquid variable](../variables/) set to `Mr. Hyde` as well as have the category for the page set to `project`.

{% highlight yaml %}
collections:
  - my_collection:
    output: true

defaults:
  -
    scope:
      path: ""
      type: "my_collection" # a collection in your site, in plural form
    values:
      layout: "default"
{% endhighlight %}

In this example the `layout` is set to `default` inside the [collection](../collections) with the name `my_collection`.

### Precedence

Jekyll will apply all of the configuration settings you specify in the `defaults` section of your `_config.yml` file. However, you can choose to override settings from other scope/values pair by specifying a more specific path for the scope.

You can see that in the last example above. First, we set the default layout to `my-site`. Then, using a more specific path, we set the default layout for files in the `projects/` path to `project`. This can be done with any value that you would set in the page or post front matter.

Finally, if you set defaults in the site configuration by adding a `defaults` section to your `_config.yml` file, you can override those settings in a post or page file. All you need to do is specify the settings in the post or page front matter. For example:

{% highlight yaml %}
# In _config.yml
...
defaults:
  -
    scope:
      path: "projects"
      type: "pages"
    values:
      layout: "project"
      author: "Mr. Hyde"
      category: "project"
...
{% endhighlight %}

{% highlight yaml %}
# In projects/foo_project.md
---
author: "John Smith"
layout: "foobar"
---
The post text goes here...
{% endhighlight %}

The `projects/foo_project.md` would have the `layout` set to `foobar` instead of `project` and the `author` set to `John Smith` instead of `Mr. Hyde` when the site is built.

## Default Configuration

Jekyll runs with the following configuration options by default. Unless
alternative settings for these options are explicitly specified in the
configuration file or on the command-line, Jekyll will run using these options.

<div class="note warning">
  <h5>There are two unsupported kramdown options</h5>
  <p>
    Please note that both <code>remove_block_html_tags</code> and
    <code>remove_span_html_tags</code> are currently unsupported in Jekyll due to the
    fact that they are not included within the kramdown HTML converter.
  </p>
</div>

{% highlight yaml %}
# Where things are
source:      .
destination: ./_site
plugins:     ./_plugins
layouts:     ./_layouts
data_source: ./_data
collections: null

# Handling Reading
safe:         false
include:      [".htaccess"]
exclude:      []
keep_files:   [".git", ".svn"]
encoding:     "utf-8"
markdown_ext: "markdown,mkdown,mkdn,mkd,md"
textile_ext:  "textile"

# Filtering Content
show_drafts: null
limit_posts: 0
future:      true
unpublished: false

# Plugins
whitelist: []
gems:      []

# Conversion
markdown:    kramdown
highlighter: pygments
lsi:         false
excerpt_separator: "\n\n"

# Serving
detach:  false
port:    4000
host:    0.0.0.0
baseurl: "" # does not include hostname

# Backwards-compatibility
relative_permalinks: false

# Outputting
permalink:     date
paginate_path: /page:num
timezone:      null

quiet:    false
defaults: []

# Markdown Processors
maruku:
  use_tex:    false
  use_divs:   false
  png_engine: blahtex
  png_dir:    images/latex
  png_url:    /images/latex
  fenced_code_blocks: true

rdiscount:
  extensions: []

redcarpet:
  extensions: []

kramdown:
  auto_ids:      true
  footnote_nr:   1
  entity_output: as_char
  toc_levels:    1..6
  smart_quotes:  lsquo,rsquo,ldquo,rdquo
  use_coderay:   false

  coderay:
    coderay_wrap:              div
    coderay_line_numbers:      inline
    coderay_line_number_start: 1
    coderay_tab_width:         4
    coderay_bold_every:        10
    coderay_css:               style

redcloth:
  hard_breaks: true
{% endhighlight %}

## Markdown Options

The various Markdown renderers supported by Jekyll sometimes have extra options available.

### Redcarpet

Redcarpet can be configured by providing an `extensions` sub-setting, whose value should be an array of strings. Each string should be the name of one of the `Redcarpet::Markdown` class's extensions; if present in the array, it will set the corresponding extension to `true`.

Jekyll handles two special Redcarpet extensions:

- `no_fenced_code_blocks` --- By default, Jekyll sets the `fenced_code_blocks` extension (for delimiting code blocks with triple tildes or triple backticks) to `true`, probably because GitHub's eager adoption of them is starting to make them inescapable. Redcarpet's normal `fenced_code_blocks` extension is inert when used with Jekyll; instead, you can use this inverted version of the extension for disabling fenced code.

Note that you can also specify a language for highlighting after the first delimiter:

        ```ruby
        # ...ruby code
        ```

With both fenced code blocks and highlighter enabled, this will statically highlight the code; without any syntax highlighter, it will add a `class="LANGUAGE"` attribute to the `<code>` element, which can be used as a hint by various JavaScript code highlighting libraries.

- `smart` --- This pseudo-extension turns on SmartyPants, which converts straight quotes to curly quotes and runs of hyphens to em (`---`) and en (`--`) dashes.

All other extensions retain their usual names from Redcarpet, and no renderer options aside from `smart` can be specified in Jekyll. [A list of available extensions can be found in the Redcarpet README file.][redcarpet_extensions] Make sure you're looking at the README for the right version of Redcarpet: Jekyll currently uses v2.2.x, and extensions like `footnotes` and `highlight` weren't added until after version 3.0.0. The most commonly used extensions are:

- `tables`
- `no_intra_emphasis`
- `autolink`

[redcarpet_extensions]: https://github.com/vmg/redcarpet/blob/v2.2.2/README.markdown#and-its-like-really-simple-to-use

### Kramdown

In addition to the defaults mentioned above, you can also turn on recognition of Github Flavored Markdown by passing an `input` option with a value of "GFM".

For example, in your `_config.yml`:

    kramdown:
      input: GFM

### Custom Markdown Processors

If you're interested in creating a custom markdown processor, you're in luck! Create a new class in the `Jekyll::Converters::Markdown` namespace:

{% highlight ruby %}
class Jekyll::Converters::Markdown::MyCustomProcessor
  def initialize(config)
    require 'funky_markdown'
    @config = config
  rescue LoadError
    STDERR.puts 'You are missing a library required for Markdown. Please run:'
    STDERR.puts '  $ [sudo] gem install funky_markdown'
    raise FatalException.new("Missing dependency: funky_markdown")
  end

  def convert(content)
    ::FunkyMarkdown.new(content).convert
  end
end
{% endhighlight %}

Once you've created your class and have it properly setup either as a plugin in the `_plugins` folder or as a gem, specify it in your `_config.yml`:

{% highlight yaml %}
markdown: MyCustomProcessor
{% endhighlight %}
