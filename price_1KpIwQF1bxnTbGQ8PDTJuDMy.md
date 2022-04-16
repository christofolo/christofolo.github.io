---
layout: page
title: Store
subtitle: PDFs and Guitar Pro files
---

<a href="{{ site.url }}/downloads/zombie_strumming.zip">Download Zombie PDFs and GP here.</a>


Checkout Payment ID: <span id="session"></span>

<script>
var urlParams = new URLSearchParams(window.location.search);

if (urlParams.has("session_id")) {
document.getElementById("session").textContent = urlParams.get(
"session_id"
);
}
</script>