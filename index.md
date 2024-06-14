---
layout: default
title: Home
nav_order: 1
permalink: /
---

Demo for Health Data Science Team.
This would be our homepage for our documentation.

GitHub pages uses **markdown** - which will make it easy for everyone to `contribute`!

# Title 1


## Title 1a

{: .note }
We can add notes


{: .warning }
> We can add warnings

 
# Code

</div>
{% highlight markdown %}
```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```
{% endhighlight %}

</div>
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




```yaml
date_of_birth_multisource()

Description
```







----


