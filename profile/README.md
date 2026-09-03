# Smart-AI

**Weboldalak, üzleti alkalmazások és AI-alapú automatizációk magyar vállalkozásoknak.**

Kis és közepes cégeknek építünk olyan digitális eszközöket, amelyek az első naptól
üzemelnek, és később sem hagyják magára a tulajdonosukat: minden weboldalunk és
alkalmazásunk verziókezelt, automatikusan tesztelt, és folyamatos figyelés alatt áll.

📧 hello@smart-ai.hu · 🌐 [smart-ai.hu](https://smart-ai.hu/)

---

## Mivel foglalkozunk

| Terület | Mit jelent ez a gyakorlatban |
|---|---|
| 🌐 **Weboldalak és üzemeltetés** | Gyors, mobilbarát, konverzióra tervezett bemutatkozó és értékesítési oldalak. Az oldal az átadás után is a mi rendszerünkben fut: frissítés, biztonsági mentés, elérhetőség-figyelés. |
| 📋 **Ügyfélkezelő adminfelület** | Ha az oldalon jelentkezési vagy konzultációs űrlap van, a beérkező kérések egy saját, jelszóval és opcionális kétlépcsős azonosítással védett felületen érkeznek, ahol státuszozhatók, jegyzetelhetők és Excelbe exportálhatók. |
| 🏢 **Üzleti alkalmazások** | Böngészőben futó rendszerek több szervezetnek, felhasználói jogosultságokkal. Saját termékünk a **WorkDoc**, egy dokumentumkezelő kis és közepes vállalkozásoknak. |
| 🖥️ **Asztali eszközök** | Windows-alkalmazások automatikus frissítéssel. Saját termékünk a **Spycam**, egy képernyőrögzítő rajzolható jelölésekkel és hangfelvétellel. |
| 🤖 **AI-automatizációk** | Ismétlődő üzleti folyamatok (értesítések, adatátadás, riportok) automatizálása, hogy ne emberi figyelem tartsa össze őket. |
| 🛒 **Webshopok** és 📱 **mobilalkalmazások** | A következő szolgáltatási körünk, ugyanerre az alapra építve. |

---

## Hogyan készül nálunk egy weboldal

Az ügyfél szemszögéből a folyamat így néz ki:

1. **Már az első napon van cím.** A projekt indulásakor az oldal egy ideiglenes
   `<ügyfél>.smart-ai.hu` címen él, egy márkázott „készül" oldallal. Senki nem lát
   félkész sablont.
2. **A fejlesztés látható és követhető.** Minden változás naplózva van, és bármelyik
   korábbi állapot percek alatt visszaállítható.
3. **Semmi nem kerül élesbe ellenőrzés nélkül.** Minden módosítás automatikus
   tesztelésen megy át. Ha elbukik, az oldal a korábbi, működő állapotban marad.
4. **Az élesítés egyetlen kapcsoló.** Amikor az oldal kész, egy beállítás átváltásával
   a „készül" oldal helyére a végleges oldal lép. Ugyanígy váltunk át az ideiglenes
   címről az ügyfél saját domainjére.
5. **Az élő oldalt figyeljük.** Tízpercenként ellenőrizzük az elérhetőséget. Ha az oldal
   nem válaszol, automatikusan jegy nyílik, és helyreállás után magától záródik.
6. **Az űrlapok adatai az ügyfélé.** A beküldések nem egy külső táblázatba folynak, hanem
   az oldal saját, védett adminjába. Az e-mail-értesítések az ügyfél saját
   levelezőszolgáltatói fiókjából mennek, a saját domainjéről.

Az adatkezelés GDPR-tudatos: az űrlapokon kötelező hozzájárulás van, a beküldött adatokat
a webről elzárt helyen tároljuk, és semmilyen jelszó vagy kulcs nem kerül a kódba.

---

## Eddigi munkáink

A szervezet repói alapján ezek a projekttípusok készültek el eddig:

- **Konzultációs és szolgáltatói oldalak űrlappal és adminnal** — például egy pécsi
  kiscsoportos Pilates- és fitneszstúdió, valamint mentálhigiénés és tanácsadó
  szakemberek bemutatkozó oldalai időpontkérő űrlappal.
- **Foglalási rendszer** — egy vendéglátóhely asztalfoglaló oldala elérhetőség-kezeléssel
  és adminfelülettel.
- **Egyedi tervezésű statikus oldalak** — bemutatkozó oldalak, ahol nincs szükség
  adatbázisra, de ugyanazt az üzemeltetési hátteret kapják.
- **WorkDoc** — több szervezetet kiszolgáló dokumentumkezelő rendszer (React, PostgreSQL,
  szerveroldali jogosultságkezelés).
- **Spycam** — Windows képernyőrögzítő aláírt, automatikusan frissülő kiadásokkal.
- **smart-ai.hu** — a saját oldalunk, ugyanazon a láncon üzemeltetve, mint az ügyfeleké.

Az ügyfélprojektek privát repókban élnek. Referenciákat és elérhető demókat a
[smart-ai.hu](https://smart-ai.hu/) oldalon mutatunk.

---

## A rendszer belülről

Ez a rész azoknak szól, akiket az érdekel, mi tartja össze a fentieket.

### A repók szerepe

| Repó | Szerep |
|---|---|
| `smart-ai-ops` | Központi vezérlő: új projekt indítása egy gombnyomással, sablonfrissítések terítése, éles adatbázis-migráció, elérhetőség-figyelés. A logika TypeScript-szkriptekben él, egységtesztekkel. |
| `template-mindset` | Sorozatgyártott sablon: „készül" oldal + alap weboldal + beépített konzultációs adminmodul. Ez a kanonikus forrás, a közös fájlok innen terjednek. |
| `template-general` | Egyedi oldalak sablonja: ugyanaz a váz, adminmodul nélkül. |
| `integral-admin` | Újrafelhasználható PHP-adminmodul: űrlapfogadó végpont, admin lista, státuszok, jelszó-visszaállítás, TOTP. Keretrendszer és Composer nélkül, mert osztott tárhelyen fut. |
| ügyfélrepók | A sablonból generált, privát projektek. Egy repó egy oldal egy tárhely-könyvtárral. |
| `.github` | Ez a repó: közös issue- és PR-sablonok, org-profil. |

A régi generáció (Next.js-monorepo sablon közös Supabase-tartalommal, illetve a
MySQL-alapú „lite" sablon) archiválva van. Tanulságaik beépültek a mostani sablonokba.

### Az élesítési lánc

```
push a main-re ──▶ CI (szintaxis, konfig, kötelező fájlok)
                        │ csak zöld CI után
                        ▼
                  Deploy prod
                    1. guard: minden szükséges titok jelen van, különben leáll
                    2. siteMode olvasása a project.config.json-ból
                    3. horgony-ellenőrzés a tárhelyen (lásd lent)
                    4. FTPS-feltöltés a saját, zárt tárhely-könyvtárba
                    5. health check, amíg a tárhely alapértelmezett oldala el nem tűnik
                        │
                        ▼
                  smoke job (külön, titkok nélkül)
                    főoldal HTML-e, védett mappák 403/404,
                    adminmodulnál az űrlapvégpont válasza is
```

A visszaállítás ugyanez a lánc egy megadott commit vagy tag állapotával. Nincs
külön „rollback-mechanizmus": a git a forrás, a tárhely csak tükör.

### A biztonsági modell

Két valós incidens formálta, mindkettő az osztott tárhely természetéből fakadt: egy
közös hozzáférés rossz célra irányított törlése, illetve egy rossz gyökérrel létrehozott
feltöltő fiók, amely egy másik oldal könyvtárába deployolt. Az ebből született szabályok:

- **Egy repó, egy zárt feltöltő fiók, egy könyvtár.** A feltöltő fiók kizárólag a saját
  oldal könyvtárát látja. Közös, fiókszintű SSH- vagy FTP-hozzáférést a deploy nem
  használ, és ilyen kulcs a rendszerben nincs.
- **Horgonyfájl.** Minden oldal könyvtárában van egy kézzel elhelyezett fájl, amelynek
  tartalma a projekt egyedi azonosítója. A deploy a feltöltés *előtt* beolvassa, és ha
  hiányzik vagy eltér, megtagadja a feltöltést. Hálózati hiba is elutasításnak számít
  (fail-closed). Az automatizálás szándékosan nem helyezi el ezt a fájlt, mert akkor
  önmagát igazolná.
- **Nincs törlő üzemmód.** A feltöltő action „clean slate" opciója tiltott: a
  horgonyt is törölné, és a tükrözés hatóköre projektenként külön állapotfájllal van
  elválasztva.
- **A célútvonal nem titok, hanem literál.** A feltöltés mindig a zárt fiók gyökerébe
  megy. Ha egy titok hiányzik, a guard leállít, nem pedig üres útvonalra deployol.
- **Titkok a helyükön.** Adatbázis-jelszó, admin-hash, SMTP-kulcs a tárhelyen, a
  publikus könyvtáron kívül él, futásidejű konfigból. Az ügyfél levelezőfiókjának
  kulcsa projektenként, kézzel kerül a repóba, mert egy közös kulcs az ügyfél domainjét
  a mi fiókunkhoz kötné.

### Sablonfrissítés terítése

A projektrepók a workflow-kat *másolatban* kapják, nem központosított hívással. Ez
tudatos döntés: egy hibás közös workflow egyszerre minden élő oldalt érintene. Ehelyett
a `smart-ai-ops` szelektív syncje PR-t nyit a kifejezetten megadott célrepókban, alapból
száraz futással, a védett repókat kódból tiltva. Csak infrastruktúra-fájlok terjednek,
tartalmi fájlok soha. A sablonok maguk is sync-célpontok, így nem csúsznak el egymástól.

### Néhány tanulság, amit nem szeretnénk újra megtanulni

- A GitHub Actions a `run:` blokkokat `bash -e`-vel futtatja. Egy `set -uo pipefail`
  ezt nem kapcsolja ki, ezért a hibázó parancs utáni takarítás holt kód. Aki minden
  ellenőrzést le akar futtatni, `||` mögé tesz mindent; aki takarítani akar, `trap EXIT`-et használ.
- `printf | grep -q` és `pipefail` együtt versenyhelyzet: a `grep -q` az első találatnál
  kilép, a `printf` EPIPE-ot kap, és a pipeline hibásnak számít. Here-string a megoldás.
- A GitHub a repóneveket kis- és nagybetűtől függetlenül oldja fel. Egy bájtpontos
  tiltólistát a `Smart-AI` alak megkerül, ezért minden ilyen védelemnél kisbetűsítünk.
- Sablon-önvédelem (`if: !startsWith(github.repository, 'Smart-ai-hu/template-')`), hogy
  egy sablonrepó soha ne deployolja önmagát, akkor sem, ha a workflow-t átmásolják.
- Osztott tárhely FTPS-tanúsítványa nem az IP-címre szól. A horgony-olvasó `curl` ezért
  nem ellenőrzi a tanúsítványt, a biztonsági határ a zárt fiók, nem a TLS-lánc.

---

## Hogyan dolgozunk együtt

Minden repó ugyanazokat a sablonokat örökli ebből a repóból:

- **Issue-sablonok:** 🐛 *Hibabejelentés* (mi történt, mit vártál, hogyan idézhető elő),
  ✨ *Új feladat* (mit kérünk, miért, elfogadási kritériumok, határidő),
  📝 *Tartalom módosítás* (melyik oldalon, mire változzon, megvannak-e az anyagok).
- **PR-sablon:** mit változtat, melyik issue-hoz tartozik, és egy ellenőrzőlista, amelynek
  legfontosabb pontja: a main-be merge sikeres CI után automatikusan élesít.
- **Commitok és dokumentáció magyarul.** A projektrepók `CLAUDE.md`-je és `docs/` mappája
  a helyi konvenciókat és a tárhelyoldali lépéseket írja le.
- **AI-asszisztált fejlesztés, emberi jóváhagyással.** A kód nagy része AI-eszközökkel
  készül, de minden élesbe menő változás PR-en, teszten és emberi döntésen megy át.

---

## Kapcsolat

📧 hello@smart-ai.hu · 🌐 [smart-ai.hu](https://smart-ai.hu/) · 📍 Magyarország
