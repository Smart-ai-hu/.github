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

- **Konzultációs és szolgáltatói oldalak űrlappal és admin felülettel** — például egy pécsi
  kiscsoportos Pilates- és fitneszstúdió, valamint catering szolgáltatást biztosító budapesti 
  vállalkozások bemutatkozó oldalai időpontkérő űrlappal.
- **Foglalási rendszer** — egy vendéglátóhely asztalfoglaló oldala elérhetőség-kezeléssel
  és adminfelülettel.
- **Egyedi tervezésű statikus oldalak** — bemutatkozó oldalak, ahol nincs szükség
  adatbázisra, de ugyanazt az üzemeltetési hátteret kapják.
- **Egyedi vállalati webalkalmazások** — Mint például WorkDoc (Dokumentáció kezelő).
- **smart-ai.hu** — a saját oldalunk, ugyanazon a láncon üzemeltetve, mint az ügyfeleké.

Az ügyfélprojektek privát repókban élnek. Referenciákat és elérhető demókat a
[smart-ai.hu](https://smart-ai.hu/) oldalon mutatunk.

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
