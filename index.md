---
title: Home
layout: home
type: parent
order: 1
---
<style>
    .main .container {
        max-width: 2800px; /* Adjust as needed */
    }
    #photo-gallery {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
    }
    #photo-gallery .thumb {
        flex: 1 1 calc(25% - 10px); /* 3 columns with gap */
        margin: 0;
    }
    #photo-gallery .thumb img {
        width: 100%;
        height: auto;
        cursor: pointer;
    }
</style>

<div class="section header">
	<div class="container">
		<!-- <img src="{{ "/assets/img/logo.svg" | relative_url }}"> -->
		<h1 class="logo_title">inherentlygia photography</h1>
		<!-- <h3 class="section-heading">photography</h3> -->
		<p class="section-description">
			In the world, off the map.
		</p>
		<div id="navbar-wrapper">
			<div id="navbar">
				<!-- <img id="brand" class="hide" src="{{ "/assets/img/logo.svg" | relative_url }}"> -->
				{% assign mypages = site.pages | where: "type", "parent" | sort: "order" %}
				{% for page in mypages %}
				<a class="button" href="{{ page.url | relative_url }}">{{ page.title }}</a>
				{% endfor %}
			</div>
		</div>
	</div>
</div>

<div class="section main">
    <div class="container">
        <!-- {{ page.body | markdownify }} -->
        <div id="photo-gallery">
			{% assign coll = site.collections | where: "label", "home" | first %}
			{% assign list = coll.files | sort: "basename" %}
			{% assign l = coll.files.size | divided_by: 2 | ceil %}
            {% for image in coll.files %}
            <a class="thumb" href="{{ coll.label | append: '/' | append: image.name | relative_url }}">
                <img class="lozad" data-src="{{ coll.label | append: '/' | append: image.name | relative_url }}" alt="{{ image.basename }}" />
            </a>
            {% endfor %}
        </div>
    </div>
</div>