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
{% set ingredientlist = [] %}
{% for product in products %}
{% for ingredient in product.ingredients %}

         {% if ingredient not in ingredientlist %}
         {% set ingredientlist = (ingredientlist.push(ingredient), ingredientlist) %}
         {% endif %}

{% endfor %}
{% endfor %}

{% for ingredient in ingredientlist %}
<div class="col-sm-6 product__set">
<a href="/sheet-masks/ingredients/{{ingredient|slug}}/" class="btn btn">
{{ingredient}}
</a>
</div>
{% endfor %}

<h4 class="neutron">By Colour</h4>
{% set colourlist = [] %}
{% for product in products %}
{% if product.colour %}
{% if product.colour not in colourlist %}
         {% set colourlist = (colourlist.push(product.colour), colourlist) %}
{% endif %}
{% endif %}

{% endfor %}

{% for c in colourlist %}
<div class="col-sm-6 product__set">
<a href="/sheet-masks/colours/{{c|slug}}/" class="btn btn">
{{c}}
</a>
</div>
{% endfor %}

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