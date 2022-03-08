---
data: products
pagination: 
   size: 24
   data: products
layout: layouts/home.njk
---

<div class="row">
   <div class="col-md-3">

<h4 class="neutron">By Brand</h4>
<div class="row">
{% for brand in brands %}
{% if brand.featured === "yes" %}
<div class="col-sm-6 product__set">
<a href="/sheet-masks/{{brand.name|slug|replace("'","%27")}}/" class="btn btn">
{{brand.name}}
</a>
</div>
{% endif   %}
{% endfor %}
<h4 class="neutron">By Ingredient</h4>
<h4 class="neutron">By Colour</h4>
<h4 class="neutron">By Country</h4>
</div>

   </div>

   <div class="col-md-9">
   {% set masks = pagination.items %}
{% include "listmasks.njk" %}

 <ol>
    <li>{% if pagination.href.previous %}<a href="{{ pagination.href.previous }}">Previous</a>{% else %}Previous{% endif %}</li>
    <li>{% if pagination.href.next %}<a href="{{ pagination.href.next }}">Next</a>{% else %}Next{% endif %}</li>
  </ol>


   </div>
</div>