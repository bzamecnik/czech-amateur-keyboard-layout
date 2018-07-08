====== Český amatér pro X ======

Máte rádi programátorské rozložení klávesnice? Tedy spojení původní anglické klávesnice (a jejích speciálních znaků) s českou (s nabodeníčky), kde ale nemusím přepínat. Já ho mám fakt rád! Dnes se mi jej konečně podařilo implementovat.


Jestli si někdo vzpomínáte, na starých woknech jej někdo vytvořil pod názvem Český amatér. Více jsem o něm a jemu podobných psal v [[http://www.abclinuxu.cz/blog/bohous/2005/11/30/111471|v blogu]] na AbcLinuxu. 

V čem spočívá Český amatér? Hlavní rys je zmíněné spojení české a anglické klávesnice bez nutnosti mezi nimi přepínat. Nad základní qwerty částí máme písmenka s diakritikou, se shiftem číslice a s AltGr znaky !@#$%... a s AltGr+Shift mrtvá diakritická znamínka. Vpravo od písmen jsou původní znaky z anglické klávesnice (různé závorky, uvozovky, atd.). Zajímavé jsou klávesy vedle backspace: mrtvý háček a čárka. Praktické je, že 'čárka+u' dělá 'ú', 'háček+u' dělá 'ů' a 'čárka+čárka' dělá '='. Na druhé straně pod ESC je backtick (`), se shiftem tilda (~), s AltGr dead kroužek.

Kromě toho fungují (stejně jako v původní české/anglické xkb klávesnici) některé speciální znaky pod AltGr+písmena (např. AltGr+e -> euro). Praktická je i Compose klávesa - zvolil jsem Pause (např. Compose o u -> ů). Existují tuny kombinací snad pro každý Unicode znak.

Klávesové rozložení je maličko uzpůsobeno notebookové klávesnici. Numlock mám pořád "zapnutý", resp. v obou stavech hází čísla ;) Čísla tak mohu zadávat na integrované numerické klávesnici i přes Fn+písmeno, nebo zadávám-li mnoho čísel, zapnout si i Numlock. Klávesa \ vlevo od pravého shiftu je předefinována na hvězdičku - to aby se dobře psaly komentáře /* */. ;)

Nyní mám rozložení, které mně osobně maximálně vyhovuje. Nevím, jak ostatním, ale lze jednoduše upravit. Původně jsem myslel, že bych vycházel z Yetiho klávesnice, ale nakonec jsem přišel na jednodušší způsob. Stačilo pouze upravit následující soubory:

  /etc/X11/xkb/symbols/cz
  /usr/X11/lib/X11/locale/en_US.UTF-8/Compose

Do prvního jsem přidal sekci cz(bohous), ve druhé jsem upravil pár pravidel pro skládání znaků přes Compose a dead keys. Je to na OpenSUSE 10.0, které jede na UTF-8, jinde bude postup obdobný.

Klávesové rozložení lze ozkoušet příkazem:


  # pro normalni PC klavesnici:
    $ setxkbmap -model pc105 -layout cz -variant bohous
  # pro Acer TravelMate 2300:
    $ setxkbmap -model acer_tm_800 -layout cz -variant bohous


To platí až do restartu X serveru. Pro trvalé uložení, to nastavte do ''xfree86.conf''/''xorg.conf''.

Tak a slibované rozložení najdete ve formě diffů na adrese: [[http://pub.zamecnik.org/linux/xkb/cz-amater/]].
