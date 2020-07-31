# avinashsc.github.io

To pull the most recent updates:
1. go to the place you have the git repository saved with a terminal
2. `git pull origin master` (or some other branch if you're trying to pull that)
3. `git checkout master`
4. `python -m http.server 8000`
5. use your browser to navigate to `localhost:8000` to see the edits

when you're done, go back to the master branch (if you weren't already there) by using your terminal with the command git checkout master

### Changing a Tableau viz
To change out a Tableau viz in our sheet, you'll need to do the following:
1. Copy the embedding HTML to a blank text editor of your choice
2. Open the `index.html` file of this repository in a separate text editor window.
3. Find the visualization you are trying to replace in `index.html`.

You will see a few different HTML elements regarding the viz in `index.html`.

* The header div section

sample:

```
<div class='w3-container w3-light-grey' style='padding:128px 16px' id='viz1595528313546' style='position: relative'>
```

* The `noscript` of the tableau viz

sample:

```
<noscript>
  <a href='#'><img alt=' ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;An&#47;AnnArborBenchmarking&#47;Map2&#47;1_rss.png' style='border: none' /></a>
</noscript>
```

* The supporting text

sample:

```
<h3>A city, its county, and its competition</h3><br>
<p>Ann Arbor, MI is in Washtenaw county. All metrics are compared at the county level.<br><br>
Many of the selected regions were chosen due to their inclusion in anecdotal comparisons to the Ann Arbor region. Austin, TX is a perfect example.
There are many similarities to Ann Arbor, but when comparing available services and city policy, it is helpful to remember that Austin (Travis county) is eight times larger than Ann Arbor. Where possible, the data have been normalized for population.</p>
<br>

```

* The body of the viz

sample:

```
<object class='tableauViz'  style='display:none;'>
  <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
  <param name='embed_code_version' value='3' />
  <param name='site_root' value='' />
  <param name='name' value='AnnArborBenchmarking&#47;Map2' />
  <param name='tabs' value='no' />
  <param name='toolbar' value='yes' />
  <param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;An&#47;AnnArborBenchmarking&#47;Map2&#47;1.png' />
  <param name='animate_transition' value='yes' />
  <param name='display_static_image' value='yes' />
  <param name='display_spinner' value='yes' />
  <param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en' /></object>
<span class="w3-medium">
```

* The next button

sample:

```
<p><a href="./#viz1595528617697" class="w3-button w3-black">NEXT CHART &gt; Population Movement Summary</a></p>
```

* The JS script

sample:

```
<script type='text/javascript'>
  var divElement = document.getElementById('viz1595528313546');
  var vizElement = divElement.getElementsByTagName('object')[0];
  function getWidth() {
    return Math.max(
      document.documentElement.clientWidth
    );
  }

  function getHeight() {
    return Math.max(
      document.documentElement.clientHeight
    );
  }
  vizElement.style.width=Math.round(0.8*getWidth())+'px';
  vizElement.style.height=Math.round(0.8*getHeight())+'px';
  var scriptElement = document.createElement('script');
  scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
  vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
```

4. Copy the `noscript` section of the new visualization and replace in `index.html`

5. Copy the body portion of the new visualization and replace in `index.html`

6. Copy the new viz ID from the header div section (something like `<div class='tableauPlaceholder' id='viz1595819305032'`) and put in the new id tag in the following places:
* the first line of the JS script portion of the viz
* the id of the header div
* the next button for the previous visualization in `index.html` (this makes sure that the button brings you down to the new visualization from above)

7. Make sure you test any changes locally before pushing to master!!! This could mess up our visualization, so double check :)

8. **Only after debugging locally** add your changes to be staged for a commit using `git add .`

9. commit your changes to `git commit -m "my awesome changes go in this message"`

10. push your changes using `git push origin master` (assumes you were working on master branch)

This will push all the changes automatically to out website at https://avinashsc.github.io/
