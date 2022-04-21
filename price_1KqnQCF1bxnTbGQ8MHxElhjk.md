---
layout: page
title: Store
subtitle: Hotel California Bass
---

<a href="{{ site.url }}/downloads/hc_bass.zip">Download Hotel California Bass PDFs and GP here.</a>


Checkout Payment ID: <span id="session"></span>

<script>
var urlParams = new URLSearchParams(window.location.search);

if (urlParams.has("session_id")) {
document.getElementById("session").textContent = urlParams.get(
"session_id"
);
}
</script>