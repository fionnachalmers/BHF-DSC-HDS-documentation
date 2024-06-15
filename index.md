---
layout: default
title: Home
nav_order: 1
permalink: /
---

# Welcome 👋

Demo for Health Data Science Team.
This would be our homepage for our documentation.

I've built it using just-the-docs template. See this guide for more info: https://just-the-docs.com/docs/ui-components/labels/

GitHub pages uses **markdown** - which will make it easy for everyone to `contribute`!
I've popped some of the available customisation below.

This has all been build using this repo: https://github.com/fionnachalmers/BHF-DSC-HDS-documentation

Once we have some documentation we can move our site over to https://github.com/BHFDSC/documentation

Adding links to external pages:  See [Test](https://github.com/fionnachalmers/BHF-DSC-HDS-documentation) for more details.

Adding links to sections of the GitHub page:  See [Methodology]({% link docs/curated_assets/kpcs_methodology.md %}#Something) for more details.

[Buttons for links](https://github.com/fionnachalmers/BHF-DSC-HDS-documentation){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }



# Title 1


## Title 1a

{: .note }
We can add notes


{: .warning }
We can add warnings

{: .new}
New information

{: .highlight }
Highlights

## Title 1b

Labels!
{: .label .label-green }

More Labels
{: .label .label-red }

Coming soon
{: .label .label-yellow }

 
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


