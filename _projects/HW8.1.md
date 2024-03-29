---
name: HW8.1
tools: [Python, HTML, vega-lite]
image: assets/pngs/cars.png
description: HW8.1
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# HW 8.1

Example comes from this [great blog post right here](https://blog.4dcu.be/programming/2021/05/03/Interactive-Visualizations.html) that was also used in [our test import script](https://github.com/UIUC-iSchool-DataViz/is445_bcubcg_fall2022/blob/main/week01/test_imports_week01.ipynb).

We can use a vegachart HTML tag like so:

```
<vegachart schema-url="{{ site.baseurl }}/assets/json/cars.json" style="width: 100%"></vegachart>
```

<vegachart schema-url="{{ site.baseurl }}/assets/json/cars.json" style="width: 100%"></vegachart>

In theory, you can also use [Jekyll hooks](https://jekyllrb.com/docs/plugins/hooks/) to do it, but I haven't figured out a way that looks nice yet.

<!DOCTYPE html>
<html>
<head>
  <style>
    #vis.vega-embed {
      width: 100%;
      display: flex;
    }

    #vis.vega-embed details,
    #vis.vega-embed details summary {
      position: relative;
    }
  </style>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/vega@5"></script>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/vega-lite@5.8.0"></script>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>
</head>
<body>
  <div id="vis"></div>
  <script>
    (function(vegaEmbed) {
      var spec = {"config": {"view": {"continuousWidth": 300, "continuousHeight": 300}}, "hconcat": [{"data": {"url": "https://cdn.jsdelivr.net/npm/vega-datasets@v1.29.0/data/movies.json"}, "mark": {"type": "point"}, "encoding": {"color": {"condition": {"param": "param_3", "value": "steelblue"}, "value": "grey"}, "x": {"field": "IMDB_Rating", "type": "quantitative"}, "y": {"field": "Worldwide_Gross", "scale": {"type": "log"}, "type": "quantitative"}}, "name": "view_10", "transform": [{"filter": "(datum.Worldwide_Gross > 0)"}]}, {"layer": [{"mark": {"type": "bar"}, "encoding": {"color": {"value": "grey"}, "x": {"bin": {}, "field": "IMDB_Rating", "type": "quantitative"}, "y": {"aggregate": "sum", "field": "Worldwide_Gross", "scale": {"type": "log"}, "type": "quantitative"}}}, {"mark": {"type": "bar"}, "encoding": {"x": {"bin": {}, "field": "IMDB_Rating", "type": "quantitative"}, "y": {"aggregate": "sum", "field": "Worldwide_Gross", "scale": {"type": "log"}, "type": "quantitative"}}, "transform": [{"filter": {"param": "param_3"}}]}], "data": {"url": "https://cdn.jsdelivr.net/npm/vega-datasets@v1.29.0/data/movies.json"}}], "params": [{"name": "param_3", "select": {"type": "interval"}, "views": ["view_10"]}], "$schema": "https://vega.github.io/schema/vega-lite/v5.8.0.json"};
      var embedOpt = {"mode": "vega-lite"};

      function showError(el, error){
          el.innerHTML = ('<div style="color:red;">'
                          + '<p>JavaScript Error: ' + error.message + '</p>'
                          + "<p>This usually means there's a typo in your chart specification. "
                          + "See the javascript console for the full traceback.</p>"
                          + '</div>');
          throw error;
      }
      const el = document.getElementById('vis');
      vegaEmbed("#vis", spec, embedOpt)
        .catch(error => showError(el, error));
    })(vegaEmbed);

  </script>
</body>
</html>



## Search The Data & Methods

Below is where we can put some links to both the data and the analysis code as buttons:

```
<div class="left">
{% include elements/button.html link="https://github.com/vega/vega/blob/main/docs/data/cars.json" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://blog.4dcu.be/programming/2021/05/03/Interactive-Visualizations.html" text="The Analysis" %}
</div>
```

<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/licenses_fall2022.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis" %}
</div>

