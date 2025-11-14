---
layout: article
title: "Test Gitalk"
comments: true
---
<p>Questa è una pagina di test per Gitalk.</p>

<div id="gitalk-container"></div>

<!-- Gitalk CSS/JS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk/dist/gitalk.css" />
<script src="https://cdn.jsdelivr.net/npm/gitalk/dist/gitalk.min.js"></script>

<script>
  var gitalk = new Gitalk({
    clientID: 'Ov23li1FyOMzy49M0G3O',          // dalla tua GitHub OAuth App
    clientSecret: '34010bfd027b4c874a23a04296a16ad884f25db9',  // dalla tua GitHub OAuth App
    repo: 'gitalk',                      // il repo pubblico dove creare le issue
    owner: 'ghiboz',                     // proprietario del repo pubblico
    admin: ['ghiboz'],                   // solo admin possono inizializzare issue
    id: location.pathname,               // id unico per pagina
    distractionFreeMode: false
  });

  gitalk.render('gitalk-container');
</script>
