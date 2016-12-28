Appunti sulle pagine di github
===
1. I profili di tipo personale e di tipo organizzazione sono trattati nello stesso modo.
2. Se un repo si chiama utente.github.io (oppure organizzazione.github.io), può essere pushato solo il sorgente jekyll. Github generera' automaticamente il sito e lo pubblichera' su http://utente.github.io (oppure http://organizzazione.github.io). 
3. Se si mette un file nela root del repo chiamato CNAME contenente il dominio (es: ic.apexnet.it) e si mette un record CNAME nel DNS che punta utente.github.io (oppure organizzazione.github.io), posso accedere al sito usando un dominio
4. Se voglio avere piu' siti per un utente (o organizzazione), non posso usare il publish automatico (punto 2), ma posso creare per ogni sito un branch chiamato gh-pages che verrà visto come website). In questo caso e' il file CNAME che ridirige il sito nel repo giusto.
5. Anche senza file CNAME poso referenziale le pagine html create nel branch gh-pages usando l'url utente.github.io/repository

* https://help.github.com/articles/using-jekyll-with-pages/
* https://help.github.com/articles/about-custom-domains-for-github-pages-sites/
* http://webdesign.tutsplus.com/tutorials/getting-to-know-github-pages-static-project-pages-fast--webdesign-11501


Risorse jekyll
====
* http://rickfoosusa.blogspot.it/2011/10/howto-use-doxygen-with-github.html
* http://dirk.net/2010/04/26/gh-pages-gh-pages-non-fast-forward-when-creating-github-project-page/
* http://jekyllbootstrap.com/
* https://help.github.com/articles/adding-a-cname-file-to-your-repository/
* https://github.com/slashdotdash/jekyll-lunr-js-search
* http://10consulting.com/

Liste di temi jekyll
===
* https://drjekyllthemes.github.io/
* http://jekyllthemes.org/
* https://jekyllthemes.io/
* http://themes.jekyllrc.org/
* https://blog.webjeda.com/jekyll-themes/
* https://github.com/CloudCannon/


Temi interessanti
===
* http://christian.fei.ninja/Simple-Jekyll-Search/about/
* https://github.com/tomjohnson1492/documentation-theme-jekyll
* http://thomaslodato.info/thoughts/theme-setup/
* http://kris.shaffermusic.com/  (https://github.com/kshaffer/kshaffer.github.io)
* https://github.com/okfn/handbook-theme/
* http://hyde.getpoole.com/
* https://community.algolia.com/algoliasearch-jekyll-hyde/
* https://github.com/alexcarpenter/material-jekyll-theme
* https://github.com/nandomoreirame/end2end
* https://github.com/CloudCannon/Strata-Jekyll-Theme
* https://github.com/CloudCannon/Read-Only-Jekyll-Theme
* https://github.com/willianjusten/will-jekyll-template
* https://mmistakes.github.io/so-simple-theme/theme-setup/
* http://frontendcollisionblog.com/ (https://github.com/joshbeam/joshbeam.github.io)

