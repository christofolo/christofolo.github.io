---
layout: page
title: Store
subtitle: PDFs and Guitar Pro files
---

Checkout Session ID: <span id="session"></span>

<a href="{{ site.url }}/downloads/zombie_strumming.zip">Download Zombie PDFs and GP here.</a>

<script>
var urlParams = new URLSearchParams(window.location.search);

if (urlParams.has("session_id")) {
document.getElementById("session").textContent = urlParams.get(
"session_id"
);
}
</script>