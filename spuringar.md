## 1. 
#### Útskýrðu vel GameLoop í leikjagerð og í Unity.

Game loopan er eitthvað sem er alltaf í gangi á meðan það er verið að spila leikinn. Loopan keyrir mishratt, algengast er að hún keyrir 60 sinnum á sekúndu eða 60 frames per second (FPS). Það sem það þýðir að í hvert skipti sem Loopan keyrir þá tekur leikurinn við input frá notandanum – uppfærir stöðu leiksins – teiknar leikinn á skjáinn 60 sinnum á sekúndu (ef FPS er 60).

 
Unity GameLoop byggir á þessum reglum en gerir það á sinn eigin hátt. Til dæmis er Unity með 3 parta sem gerast í update partinum. Fixed-Update: Gerist mörgum sinnum á milli ramma ef FPS er í lægri kantinum, geti ekki þurft að nota það ef leikurinn uppfærist á háu FPS-i.  Update: venjulega update sem að keyrir einu sinni á ramma. Late-Update: Keyrir eftir að allt sem var inni í Update er búið að keyra. Gagnleg notkun á Late-Update væri t.d. hreyfing á myndavélinni. Eftir að Update er búið að keyra þá keyrir Late-Update og færir myndavélina.
Áður en leikurinn byrjar þá keyrist eitthvað sem heitir Awake fyrir hvern hlut sem er í senunni sem þú ert í. Awake kveikir á hlutnum og eftir það keyrir svo OnEnable sem keyrir bara ef það er búið að kveikja á hlutnum. 
Start er eitthvað sem keyrir fyrir alla hluti í senunni áður en fyrsti ramminn fer í gang og kallar líka á öll script. 
Þegar senan byrjar þá er það fyrsta sem að gerist er það að vélin teiknar allt sem að myndavélin sér svo fer eitthvað í gang sem heitir OnPreCulling sem að gerist áður en að Culling fer í gang sem ákveður hvaða hlutir eru sýnilegir í myndavélinni. Síðan renderar vélinn allt inn og eftir það keyrist OnPostRender sem þýðir að myndavélin er búinn að teikna alla senuna.

## 2. 
#### Hvað er leikjavél? Berðu saman tvær leikjavélar, t.d. Unity og Unreal

Leikjavél er hugbúnaður sem að er gerður fyrir fólk svo það geti búið til leiki á einfaldari og hraðari máta.
	
Munurinn á Unity og Unreal Engine 4 sem eru báðar framúrskarandi leikjavélar á sínu sviði er einhver og það fer mikið eftir því hvað þú vilt gera, svo það gæti verið góð hugmin að skoða þessa valkosti áður en þú byrjar að forrita.

- T.d. er Unity betra ef þú vilt hanna leiki fyrir alls konar tæki eins og síma á meðan Unreal er beins meira í átt að tölvum og leikjatölvum eins og PS4 og XBOX.
- Margir segja að Unreal er mikið betri þegar að kemur að framleiða leiki sem að líta vel út og leikir frá Unreal eru léttari að keyra á hærri FPS. 
- Unity notar scripting tungumál eins og UnityScript og C# en Unreal notar tungumál eins og C++ og Lua. 
- Unreal er alveg frítt að nota nema það að ef leikurinn þinn græðir meira en $3000 þá vill Epic Games taka 5% af því. Unity hins vegar er frítt en ef þú vilt gera meira þá þarftu að borga fyrir betri gerð af hugbúnaðinum.

## 3. 
#### Útskýrðu hvernig árekstur (e. collision detection) gæti verið útfærður í leik með sýnidæmi (kóði, skýringamynd, stærðfræði osfrv.).
Árekstur gerist þegar að tveir hlutir rekast saman og þá annaðhvort festast saman eða fara frá hvor öðrum. Það er hægt að skipta þessari framkvæmd í tvo parta. Annaðhvort eru hlutirnir að skerast saman eða ekki. Svo við þurfum að vita hvenær hlutirnir eru að skerast og hvenær ekki. 
- (AABB) eða Axis Aligned Bounding Box er box sem að er sett meðfram annaðhvort þeim tveim eða þrem ásum á hlutnum ef hann er 2D eða 3D. 
- Það getu ekki snúist (þarf að nota aðra aðferð fyrir snúandi árekstra)
- þarf að hafa: Miðju hlutarins og hálfa breidd og hæð hlutarins (hnit)
- Það ber saman fjarlægðina á tveim hlutum og tékkar hvort að hún sé minni en summa stærða báða hlutanna.

Formúla: |a.center.x – b.center.x| < (a.size.x * b.size.x)
(ef þetta er true þá er árekstur á þeim ás sem stærðin er minni.)
-útskýringarmynd, eitt vitlaust! Þar sem stendur (2, 0) að ofan á að vera (0, 2)
 

