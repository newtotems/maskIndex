---
data: products
pagination: 
   size: 24
   data: products
layout: layouts/home.njk
title: Sheet Mask Index - Browse all sheet masks
---

<div class="row">
   <div class="col-md-3">

<h4 class="neutron">By Brand</h4>
<div class="row leftcol">
{% for brand in brands %}
{% if brand.featured === "yes" %}
<div class="col-6 product__set m-0 p-0 text-center">
<a href="/sheet-masks/{{brand.name|slug|replace("'","")}}/" class="btn btn"> 
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
<div class="col-6 product__set m-0 p-0 text-center">
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
<div class="col-6 product__set m-0 p-0 text-center">
<a href="/sheet-masks/colours/{{c|slug}}/" class="btn btn">
{{c}}
</a>
</div>
{% endfor %}


<h4 class="neutron">By Country</h4>

</div>

   </div>

   <div class="col-md-9 order-first order-md-last">
   {# -------------------------------------- latest products #}

{% set productcount = "" %}
{% set brandcount = "" %}

{% for p in products %}
{% set productcount = loop.length %}
{% endfor%}

{% for p in brands %}
{% set brandcount = loop.length %}
{% endfor%}


<div class="row index-header">

<div class="col-12 order-1 order-md-2 align-items-center">
  <h4 class="text-center">Listing <span>{{productcount}}</span> sheet masks from <span>{{brandcount}}</span> brands</h4>
  <p class="text-center aff-disclaimer">When you click a Buy link, we may earn an affiliate commission. <a href="">Learn more</a></p>
  </div>

</div>

<div class="row pagination justify-content-between">

<div class="col-2 pagination__item pagination__prev">
  <p class="text-center"> {% if pagination.href.previous %}<a href="{{ pagination.href.previous }}" class="text-center">Previous</a>{% else %}<span class="text-center">Previous</span>{% endif %}</p>
</div>

<div class="col-2 text-center pagination__item pagination__next">
  <p class="text-center"> {% if pagination.href.next %}<a href="{{ pagination.href.next }}" class="text-center">Next</a>{% else %}<span class="text-center">Next</span>{% endif %}</p>
</div>

</div>

   {% set masks = pagination.items %}
{% include "listmasks.njk" %}

<div class="row pagination justify-content-between">

<div class="col-2 pagination__item pagination__prev">
  <p class="text-center"> {% if pagination.href.previous %}<a href="{{ pagination.href.previous }}" class="text-center">Previous</a>{% else %}<span class="text-center">Previous</span>{% endif %}</p>
</div>

<div class="col-2 text-center pagination__item pagination__next">
  <p class="text-center"> {% if pagination.href.next %}<a href="{{ pagination.href.next }}" class="text-center">Next</a>{% else %}<span class="text-center">Next</span>{% endif %}</p>
</div>

</div>

   </div>
</div>