---
data: products
pagination: 
   size: 10
   data: products
layout: layouts/home.njk
---

<div class="row">
   <div class="col-sm-2">

   <h3 class="text-center">Filter By Brand</h3>
<div class="row">
{% for brand in brands %}
{% if brand.featured === "yes" %}
<div class="col">
<a href="/masks/{{brand.name|slug|replace("'","%27")}}/" class="btn btn btn-outline-secondary">
<img src="/img/logos/{{brand.name|slug}}.png">
<!-- {{brand.name}} -->
</a>
</div>
{% endif   %}
{% endfor %}
</div>

   </div>

   <div class="col-sm-10">
   {% set masks = products %}
{% include "listmasks.njk" %}
   </div>
</div>




