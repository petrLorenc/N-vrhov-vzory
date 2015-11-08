# Navrhove vzory
Budu se zde snažit, svými slovy, popsat co znamenají návrhové vzory, co znamená **OOP** a "obecně dobré" programovací přístupy. Nekdy budu psat bez hacku a carek, protoze to je pro me pohodlnejsi a stejnak mam v planu cely tento clanek prepsat do anglictiny.

Cast 1
Budu se snazit udrzovat jednotnou strukturu a vsechny zdroje uvadet na konci (a vsechny pohromade). Jako hlavni vychozi bod jsem zvolil knizku **Navrhove vzory od Rudolfa Pecinovskeho** a jako rychly prehled jsem zvolil stranky www.tutorialspoint.com/design_pattern/index.htm Dale mi prijdou stojici za precteni stranky http://www.algoritmy.net/ , ktere vychazeji z jiz vyse zminene knizky. Vsechny kody (u jasnych myslenek nebudu uvadet) se budu snazit testovat v **Jave** (jako momentalni Androidar se pokusim priblizit nejake i k Androidu).

# Zaklad
Mezi zakladni zasady objektove orientovaneho programovani bych zvolil tyto:
* **Programovani proti rozhrani** a uprednostnovat rozhrani pred tridami v dedeni
  * Jedna z vyhod uprednostnovani rozhrani (interface) pri dedeni je ze muzete dedit od vice rozhrani
  * Vazba mezi tridami (pri pouziti treba abstract class) pri dedeni je velmi silna (vetsinou nechceme)
  * Abstraktni tridy se vyplati pokud vime ze se bude API menit - neni nutnost velkych zmen (pridani metody k rozhrani nas ale nuti implementovat ji vsude kde se pouziva toto rozhrani)
* Soudrznost (**Cohesion**) tridy
  * Kazda trida by mela soustredovat na jednu konkretni vec -> snadny testing
* Nizka vzajemna provazanost (**Coupling**)
  * Pokud by jsem odstranili jednu tridu tak by nemelo byt nemozne ziskat zpatky funkcni kod
* Neopakovat stejny kod - **DRY** (Dont repeat yourself)
  * Zakladni princip, nedodrzeni vede k mnozstvi chyb z nepozornosti
* Neukazovat ostatnim co nepotrebuji - **zapouzdreni**
  * Nemelo by se stavat ze ostatni objekty dostanou informace ktere nutne nepotrebuji
  * Muze vest k ne/zadoucim zmenam vnitrnich stavu promnenych a tudiz k chybam

# Simple factory method - Jednoducha tovarni funkce
Jedna se o **statickou metodu** kterou budeme volat na tride k navraceni instance teto tridy. Mezi hlavni vyhody bych zaradil ze se nam nutne **nemusi vratit novy objekt** (na rozdil od konstruktoru, ktery ho vzdy vytvori) a neni nutnost volat metody predka hned jako prvni vec. **Muze dokonce vratit instanci nektereho potomka**. V Android prostredi se casto vola metoda **newInstance**(...) ktera svym zpusobem je SFM (z volby jmena by melo byt jasne co funkce vraci - novy objek, singleton ...).
