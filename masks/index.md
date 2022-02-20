---
data: products
pagination: 
   size: 10
   data: products
layout: layouts/home.njk
---

{% set masks = products %}
{% include "listmasks.njk" %}

