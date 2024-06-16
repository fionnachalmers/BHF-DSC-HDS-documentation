---
layout: default
title: Home
nav_order: 1
permalink: /
---

# Welcome 👋

Demo for Health Data Science Team.
This would be our homepage for our documentation.

# Meet the Team

<div style="display: flex; gap: 7px;">
  <a href="mailto:thomas.bolton@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/tom_bolton.png" alt="Tom Bolton" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:john.nolan@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/john_nolan.png" alt="John Nolan" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:mehrdad.mizani@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/mehrdad_mizani.png" alt="Mehrdad Mizani" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:zach.welshman@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/zach_welshman.png" alt="Zach Welshman" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:james.farrell@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/jamie_farrell.png" alt="Jamie Farrell" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:lars.murdock@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/lars_murdock.png" alt="Lars Murdock" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:anna.stevenson@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/anna_stevenson.png" alt="Anna Stevenson" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:fionna.chalmers@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/fionna_chalmers.png" alt="Fionna Chalmers" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
  <a href="mailto:jadene.lewis@hdruk.ac.uk" style="flex: none;">
    <img src="https://fionnachalmers.github.io/BHF-DSC-HDS-documentation/assets/images/jadene_lewis.png" alt="Jadene Lewis" style="width: 90px; height: 90px; object-fit: cover;">
  </a>
</div>


I've built it using [just-the-docs](https://just-the-docs.com/docs/ui-components/labels/) template.

GitHub pages uses **markdown** - which will make it easy for everyone to `contribute`!
I've popped some of the available customisation below.

HTML will render in markdown, so you can do things not possible with plain markdown syntax E.g. this
<a href="http://example.com" target="_blank">link</a> opening up on a new tab.

I've made some link buttons throught the doc that open in new pages so you can just copy and paste the code from here.

I've added some custom css to bring the template in line with the brand colours.


This has all been built using <a href="https://github.com/fionnachalmers/BHF-DSC-HDS-documentation" target="_blank">this repo</a>.


Once we have some more documentation we can move our site over to **https://github.com/BHFDSC/documentation**.

Adding links to sections of the GitHub page:  E.g. Jump to [Methodology]({% link docs/curated_assets/kpcs_methodology.md %}#Something) for more details.

[Have buttons for links](https://github.com/fionnachalmers/BHF-DSC-HDS-documentation){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

The above button opens the link in the same page because it is written in markdown.

<a href="https://github.com/fionnachalmers/BHF-DSC-HDS-documentation" class="btn btn-primary fs-5 mb-4 mb-md-0 mr-2" target="_blank">This button uses HTML to open the link in a new tab</a>

<span class="fs-3">
  <a href="https://github.com/BHFDSC/cvd-covid-tre-dashboard" class="btn" target="_blank">Another button example</a>
</span>


[Go to KPC Individual Tables]({% link docs/curated_assets/kpcs_methodology.md %}#individual-tables){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

It is set up that as soon as a page is edited (via a commit) the site will automatically deploy the new version.

When you add a new file - make sure to make it a .md file!

# Title 1


## Title 1a

{: .note }
We can add notes


{: .warning }
We can add warnings

{: .new}
New information

{: .new-title}
> My note title has changed
>
> A paragraph with a custom title callout

{: .highlight }
Highlights

{: .highlight-title }
> Look at this
>
> Another paragraph
>
> Another
> >
> An indent
>
> The last paragraph
> >
> An indent

## Title 1b

Labels!
{: .label .label-green }

More Labels
{: .label .label-red }

Coming soon
{: .label .label-yellow }

<span class="label label-red">Labels using HTML</span>

 
# Code


{% highlight markdown %}
```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```
{% endhighlight %}


{% highlight markdown %}
```r
# Phenotype Definitions
phenotype_ids = phenotypes_search %>% pull(phenotype_id)

phenotype_definitions = data.frame()

for(i in 1:length(phenotype_ids)){
  phenotype_definitions = phenotype_definitions %>%
    rbind(
      client$phenotypes$get_detail(phenotype_ids[i]) %>%
        select(phenotype_id,definition,concept_information) %>%
        remove_rownames()
      )
}
```
{% endhighlight %}


{% highlight markdown %}
```python
from pyspark.sql import SparkSession

# Initialize a Spark session
spark = SparkSession.builder.appName("exampleApp").getOrCreate()

# Create a DataFrame
data = [("James", "Sales", 3000), ("Michael", "Sales", 4600), ("Robert", "Sales", 4100)]
columns = ["Employee_Name", "Department", "Salary"]
df = spark.createDataFrame(data, columns)
```
{% endhighlight %}




```yaml
date_of_birth_multisource()

 Description
```

----


