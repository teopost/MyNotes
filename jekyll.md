Risorse jekyll
====

* http://jekyllbootstrap.com/
* https://help.github.com/articles/using-jekyll-with-pages/
* http://webdesign.tutsplus.com/tutorials/getting-to-know-github-pages-static-project-pages-fast--webdesign-11501
* https://help.github.com/articles/about-custom-domains-for-github-pages-sites/
* https://help.github.com/articles/adding-a-cname-file-to-your-repository/

* https://github.com/tomjohnson1492/documentation-theme-jekyll
* https://mmistakes.github.io/so-simple-theme/theme-setup/
* http://thomaslodato.info/thoughts/theme-setup/
* http://kris.shaffermusic.com/   https://github.com/kshaffer/kshaffer.github.io
* https://github.com/slashdotdash/jekyll-lunr-js-search
* http://10consulting.com/
* http://christian.fei.ninja/Simple-Jekyll-Search/about/
* http://frontendcollisionblog.com/  -  https://github.com/joshbeam/joshbeam.github.io 
* https://github.com/octopress/octopress
* http://ironsummitmedia.github.io/startbootstrap-sb-admin-2/pages/index.html#

Appunti sulle pagine di github
---
1. I profili di tipo personale e di tipo organizzazione sono trattati nello stesso modo.
2. Se un repo si chiama utente.github.io (oppure organizzazione.github.io), può essere pushato solo il sorgente jekyll. Github generera' automaticamente il sito e lo pubblichera' su http://utente.github.io (oppure http://organizzazione.github.io). 
3. Se si mette un file nela root del repo chiamato CNAME contenente il dominio (es: ic.apexnet.it) e si mette un record CNAME nel DNS che punta utente.github.io (oppure organizzazione.github.io), posso accedere al sito usando un dominio
4. Se voglio avere piu' siti per un utente (o organizzazione), non posso usare il publish automatico (punto 2), ma posso creare per ogni sito un branch chiamato gh-pages che verrà visto come website). In questo caso e' il file CNAME che ridirige il sito nel repo giusto.
