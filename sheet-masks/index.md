---
data: products
pagination: 
   size: 10
   data: products
layout: layouts/home.njk
---

<div class="row">
   <div class="col-sm-3">

   <h3 class="text-center">Filter By Brand</h3>
<div class="row">
{% for brand in brands %}
{% if brand.featured === "yes" %}
<div class="col-sm-6">
<a href="/sheet-masks/{{brand.name|slug|replace("'","%27")}}/" class="btn btn">
<img src="/img/logos/{{brand.name|slug}}.png" class="img-fluid" alt="{{brand.name}}" title="{{brand.name}}">
</a>
</div>
{% endif   %}
{% endfor %}
</div>

   </div>

   <div class="col-sm-9">
   {% set masks = products %}
{% include "listmasks.njk" %}
   </div>
</div>




