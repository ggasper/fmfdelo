# Splošno o predlogah za zaključna dela na FMF

Na tem repozitoriju boste našli predloge za dela diplomskega seminarja in magistrska dela na OM FMF.
Pred uporabo predloge, **prosim preberite navodila na vaši spletni učilnici in spodnja tehnična
navodila**.

Za pisanje zaključnega dela prenesite arhiv [template.zip](template.zip) in primerno preimenujte datoteko
`PredlogaDela.tex`.
Lahko prenesete tudi [angleško verzijo](template_english.zip).

Predloga ustreza tudi [navodilom za pisanje magisterija](https://www.fmf.uni-lj.si/si/knjiznica-matematicna/navodila-bol-mag/).

## Urejanje dokumenta in uporaba predloge

Za urejanje dokumentov močno priporočamo [Visual Studio Code](https://code.visualstudio.com)
s podaljškom [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
Literatura se prevede avtomatsko brez dodatnih nastavitev.

V LaTeX dokumentu pod napisom #TODO
"naslednje ukaze ustrezno napolnite"
izpolnite ime avtorja, mentorja, morebitnega somentorja, naslov dela in ostalo.
Ti ukazi se uporabijo v generiranju naslovnice, izjave, povzetka in PDF metapodatkov.
Več navodil o tem, kako pisati, je na spletni učilnici.

Magisterij #TODO:
Če želite, lahko odkomentirate kazalo slik.
Dopolnite program dela in povzetek ter ključne besede.
Nato nadaljujte z uvodom. 

### Prevajanje

Dokument bi se moral prevesti brez posebnosti, če imate `.cls` in `.tex` datoteki v isti mapi.
Nekaj pogostih težav in rešitev je opisanih v razdelku Odpravljanje težav pri prevajanju.

### Preverjanje črkovanja

Uporabljajte urejevalnik, ki preverja črkovanje.
Za preverjanje črkovanja neodvisno od uporabljenega urejevalnika lahko uporabite
[aspell](http://aspell.net/).

* Visual Studio Code: #TODO podaljšek LanguageTool.

### Pravilno stavljenje besedila

* **Presledki po pikah za kraticami:** za presledek za piko v kratici uporabite `~` ali `\ `;
  v nasprotnem primeru je presledek predolg. "npr., t. i., tj." ipd.
  Primeri: pravilno je `t.~i.\ ` ali `t.~i.~`, `npr.~` ali `npr.\ ` in ne `t. i.` in `npr. `.
* **Pisanje enačb:** uporabljajte okolja `\[ \]`, `equation`, `align` ali `align*`
  in ne `eqnarray` ipd.

### Reference in citiranje literature

Sledite navodilom in primerom citiranja literature v dokumentu. 
Na voljo imate tudi možnost avtomatskega navajanja literature s sistemom [BibTeX](http://www.bibtex.org/),
ki avtomatsko pravilno uredi in oblikuje vnose literature.

Uporabljajte LaTeXovo sklicevanje, ki ga vedno povežite s prejšnjo besedo z nedeljivim presledkom, 
kot npr. `na sliki~\ref{fig:label} vidimo`.
Pri ukazih `\ref` in `\cite`, bi moral urejevalnik tudi sam ponuditi obstoječe oznake.
Če pri ukazu `\cite` ne ponudi možnih bibliografskih ključev, je morda kriv makro `\literatura`.
Tega lahko na vrstici `\bibliography{\literatura}` pri koncu dokumenta zamenjate z imenom vaše 
`.bib` datoteke (brez končnice), kar včasih pomaga urejevalniku.

#### Uporaba sistema BibTeX #TODO preveri, če je kaj zastarelo

Za uporabo sistema [BibTeX](http://www.bibtex.org/) je treba na koncu datoteke napisati 
```
\bibliographystyle{fmf-sl}
\bibliography{literatura}
```
Bodite pozorni na slog `fmf-sl`. Če ste bili do sedaj navajeni okolja `thebibliography`, 
ga zgornji vrstici v celoti nadomeščata.

Narediti je potrebno še datoteko `literatura.bib`, ki vsebuje vnose kot npr:
```
@Article{kearsley1975linearly,
  author  = {Kearsley, Elliot A and Fong, JT},
  title   = {{Linearly independent sets of isotropic Cartesian tensors of ranks up to eight}},
  journal = {J. Res. Natl Bureau of Standards Part B: Math. Sci. B},
  year    = {1975},
  volume  = {79},
  pages   = {49--58},
  doi     = {10.6028/jres.079b.005}
}
```

LaTeX nato poskrbi, da se vsak vnos iz datoteke `literatura.bib`, ki je tudi citiran v dokumentu s
pomočjo `\cite{label}` se pojavi na končnem seznamu literature, ki je avtomatsko pravilno oblikovan
in urejen. V `fmf-sl.bst` datoteki je definiran stil navajanja literature, ki ustreza [navodilom za
navajanje literature](https://www.fmf.uni-lj.si/storage/24240/LiteraturaM.pdf).

Najpogostejši tipi citatov so `@article` za članke, `@book` za knjige, `@phdthesis`,
`@mastersthesis` in `@bachelorsthesis` za doktorate, magisterije in diplome, `@inproceedings` za
konference in `@misc` za ostalo (ponavadi splene naslove). Seznam literature se obravnava kot
običajno LaTeX kodo, tako da se lahko v njej uporablja tudi matematiko `$...$` in je potrebno
escapati vse posebne znake (npr. `#`, `%`, ...). Vnose za BibTeX datoteko pogosto dobite kar na
strani, kjer ste članek dobili. Če pa ne, ga najverjetneje lahko [poiščete na Google
Scholar-ju](https://scholar.google.si/scholar?hl=en&as_sdt=0%2C5&q=Linearly+independent+sets+of+isotropic+Cartesian+tensors+of+ranks+up+to+eight&btnG=),
kliknete na ikono `''`, izberete BibTeX in skopirate podatke. **Podatke o članku ali knjigi je
potrebno vedno ročno preveriti, saj so lahko narobe.**
Članki so avtomatko abecedno urejeni po priimku in nato imenu prvega avtorja. Člankom brez avtorja
je potrebno dodati polje `key={kljuc}`, ki pove kljuc, glede na katerega se urejajo. Da bi bili ti
članki na koncu besedila in urejeni po npr. spletnih naslovih, je lahko ključ oblike
`žžž-http://...`.

Preveri urejevalnike #TODO Zotero?
Več o urejanju literature je na voljo
[tukaj](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#BibTeX).  Za urejanje `.bib`
datotek priporočam program [JabRef](http://www.jabref.org/), ki zna samodejno okrajšati imena revij,
dobiti DOI člankov in podatke iz ISBN ter lepo oblikuje datoteko. Na voljo je za Windows, Linux in
Mac.

Ta sistem močno priporočam, še vedno pa lahko izbrišete tisti dve vrstici in se vrnete nazaj na
okolje `thebibliography`.

### Pisanje algoritmov in izvorne kode

Za vključevanje izvorne kode inpisanje algoritmov v psevdokodi so v predlogi že zakomentirani
primerni ukazi za vključevanje paketov.

Za vključevanje izvorne kode priporočamo paket [minted](https://github.com/gpoore/minted),
ki zna s pomočjo Python knjižnice [pygments](http://pygments.org/) obarvati več kot 300 jezikov.
Za njegovo uporabo morate imati naloženo omenjeno knjižnico.
To preverite tako, da v konzolo napišete `pygmentize --help` in vidite, ali deluje.
Poleg tega je treba LaTeX-u dovoliti izvajanje zunanjih programov s pomočjo opcije `-shell-escape`.

Za pisanje algoritmov je v paketu že vključen primer algoritma in paket
[algoritmix](http://tug.ctan.org/macros/latex/contrib/algorithmicx/algorithmicx.pdf).
Sintakso paketa najlažje razberete kar iz primera, opisana pa je tudi v dokumentaciji paketa.
Podobno kot pri slikah, mora biti na vsak algoritem podan sklic v besedilu, 
opisani pa morajo biti tudi vsi vhodni in izhodni parametri.


## Odpravljanje težav pri prevajanju

#### `pdfapart undefined`

Če dobite pri prevajanju napako podobno `! Package keyval Error: pdfapart undefined.`, 
priporočamo, da posodobite svojo distribucijo LaTeX-a na najnovejšo verzijo.

#### `./fmfdelo.cls  ! Undefined control sequence.`

Če dobite napako oblike
```
(./fmfdelo.cls
! Undefined control sequence.
\UseTextAccent ...up \@firstofone \let \@curr@enc
                                                  \cf@encoding \@use@text@en...
l.2 ...fmfdelo}[2016/10/13 Zaključna dela na FMF]
```
morate posodobiti `.cls` datoteko na najnovejšo verzijo. V `fmfdelo.cls` v vrstici `2`
dela težave `č`, ki ga je potrebno zamenjati s `c`.

### Čiščenje dodatnih datotek

Če gre kaj na robe in preizkušate rešitve, **ne pozabite vmes počistiti dodatnih datotek** 
(`.log`, `.aux` ipd.), v katerih se lahko stare napake zadržujejo dlje, kot je treba. 

* Visual Studio Code: v paleti ukazov (Command Palette, `Ctrl+Shift+p` oz. `Cmd+Shift+p` na MacOS) 
  natipkate `Clean Auxiliary Files`.
  Tam bo pisalo tudi, s katero bližnjico pridete do te funkcije na vašem računalniku.
* Ukazna vrstica: poženete ukaz `latexmk -c`.
* TexStudio: `Tools > Clean Auxiliary Files`.


## PDF format za dolgoročno shranjevanje: PDF/A-1b

Knjižnica zahteva shranjevanje PDF datotek magisterijev in diplom v 
[PDF/A-1b formatu](https://en.wikipedia.org/wiki/PDF/A), primernem za arhiviranje. 
V tem formatu boste morali tudi oddati svoje zaključno delo.
Ta PDF format je bolj omejen od običajnega in med drugim zahteva PDF metapodatke, 
da so vse uporabljene pisave vdelane v dokument in da slike ne vsebujejo prosojnih elementov.
PDF, generiran s to predlogo, naj bi že ustrezal standardu PDF/A-1b.
Za to poskrbi že vključeni paket `\usepackage[a-1b]{pdfx}`.
Lahko gre kaj narobe, če vključite slike s prosojno barvo.

Vaš PDF pred oddajo (ali pa že kdaj prej) vseeno preverite z uporabo 
[kakšnega validatorja](https://www.pdf-online.com/osa/validate.aspx).

Metapodatki o avtorju, naslovu, itd. se nastavijo avtomatsko med prevajanjem.
Vidite jih lahko v naslovni vrstici pregledovalnika PDF dokumentov.
Med prevajanjem se pripravijo tudi zaznamki za poglajva in podpoglavja v PDF.
Ti so vidni na levi strani pregledovalnika v drevesni strukturi.
Na tem mestu lahko včasih nastopijo težave z matematičnimi/UTF-8 znaki v naslovu ali poglavjih, 
če jih pregledovalnik PDF dokumentov ne prebavi.
V tem primeru se avtomatsko izpustijo, če pa jih želimo zamenjati z golim besedilom (plain text)
ali UTF-8 znaki, pa lahko to storimo z `\texorpdfstring`, kot je prikazano na primeru v predlogi.


### Napake pri preverjanju formata PDF/A

#### Prosojnost

Napaki `The value of the key SMask is an image but must be None.` ali 
`The key S has a value Transparency which is prohibited.` pomenita,
da imate vključeno kakšno prosojno sliko. 
Za rastrske slike je ponavadi dovolj, da s primernim programom prosojno barvo spremenite v belo.
Za slike v vektorskih formatih je potrebno ponavadi nastaviti ozadje, 
za `.pdf` format lahko na primer kar uredite datoteko in zamenjate
`/Transparency` pri polju `/S` z `/GTS_PDFA1`.
V najslabšem primeru lahko PDF pretvorite v PDF/A-1b format tudi s kakim drugim programom,
orodjem na spletu, ali pa v matematični knjižnici.

#### Ključne besede #TODO

V primeru napake
`The required XMP property 'pdf:Keywords' for the document information entry 'Keywords' is missing.`
se zakomentira vrstico `\Keywords{\kljucnebesede}`, pobriše datoteko `.xmpdata` in
ponovno prevede dokument.


## Pogosta vprašanja

Za težave in vprašanja glede predloge, odprite nov issue, pred tem pa preglejte [že
obstoječe](https://github.com/ul-fmf/fmfdelo/issues?q=is%3Aissue), če morda rešijo
vašo težavo.


## Zahvale

Hvala Anji Petković za angleško verzijo magisterija,
Maji Klavžar za natančna navodila glede navajanja literature, 
Sašu Strletu in Matjažu Konvalinki kot skrbnikoma programov za vse potrebne informacije in 
Aniti Buckley za pomoč pri poenotenju in uvedbi PDF/A formata.

Matija Pretnar & Jure Slak (jure.slak@fmf.uni-lj.si)
