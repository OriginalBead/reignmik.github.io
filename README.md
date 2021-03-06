# Sandbox
> Landing page for all of our projects.

Both the project categories and search suggestions in http://esri.github.io are powered by GitHub [topics](https://github.com/blog/2309-introducing-topics).

[<kbd>web-development</kbd>](https://github.com/Esri?q=topic%3Aweb-development)
[<kbd>data-management</kbd>](https://github.com/Esri?q=topic%3Adata-management)
[<kbd>spatial-analysis</kbd>](https://github.com/Esri?q=topic%3Aspatial-analysis)
[<kbd>publishing-sharing</kbd>](https://github.com/Esri?q=topic%3Apublishing-sharing)
[<kbd>native-development</kbd>](https://github.com/Esri?q=topic%3Anative-development)

You can find a complete list of searchable topics in [`search-topics.yml`](src/data/search-topics.yml). When a [topic](https://github.com/blog/2309-introducing-topics) is added to an Esri repository, it will be reflected in search immediately.

## Development

The website is generated using the open source static site generator [`acetate`](https://github.com/patrickarlt/acetate) and styled with the help of [`calcite-web`](https://esri.github.io/calcite-web/).

1. Fork and clone the project
2. Install the [`package.json`](package.json) dependencies by running `npm install`
3. Run `npm start`. This will generate built pages in memory, launch the site on http://localhost:8000 and watch the raw source for changes.
4. To create a build that will be saved to disk, use `grunt build`

## Architecture

Information for the case studies and featured projects can be found in [`projects.yml`](src/data/projects.yml)

```yaml
- title: R Analysis
    description: Develop and share R statistical analysis with ArcGIS.
    url: //r-arcgis.github.io/
    displayLang: R
    searchLang: r
    stars: 109
```

Templated markup for the featured content is located in [`_macros.html`](src/layouts/_macros.html)

For example, below we define a loop to generate 24 cards using information from `projects.yml`
```html
<div class="block-group block-group-4-up tablet-block-group-2-up phone-block-group-1-up">
    {% for project in projectInfo.projects %}
    {% if loop.index > 1 %}
    <div class="card block leader-1">
        <div class="card-content card-bar-{{ projectInfo.color }}">
        <h4>{{ project.title }}</h4>
        <p class="card-last">{{ project.description }}</p>
        <!-- ... -->
        </div>
    </div>
    {% endif %}
    {% endfor %}
    </div>
```
`<html>` scaffolding can be found in [`src/index.html`](https://github.com/Esri/esri.github.io/blob/master/src/index.html)

## Contributing

Anyone and everyone is welcome to contribute. Please see our [guidelines for contributing](https://github.com/esri/contributing).
