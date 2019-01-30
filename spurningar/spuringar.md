## 1. 
#### Útskýrðu vel GameLoop í leikjagerð og í Unity.

Game loopan er eitthvað sem er alltaf í gangi á meðan það er verið að spila leikinn. Loopan keyrir mishratt, algengast er að hún keyrir 60 sinnum á sekúndu eða 60 frames per second (FPS). Það sem það þýðir að í hvert skipti sem Loopan keyrir þá tekur leikurinn við input frá notandanum – uppfærir stöðu leiksins – teiknar leikinn á skjáinn 60 sinnum á sekúndu (ef FPS er 60).
![loop](https://user-images.githubusercontent.com/33831578/51359171-627d5480-1abe-11e9-9334-eccb5626dedc.png)

 
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
 ![math](https://user-images.githubusercontent.com/33831578/51359193-817be680-1abe-11e9-83e2-870d7c8ee982.png)

## 4
#### Hvað er e. asset? Nefndu algengar tegundir
Assets eru hlutirnir sem þú getur notað í leikinn þinn eins og myndir eða hljóð fyrir einhvern hlut, líka til dæmis þrívíddarmódel fyrir kassa. Allir þessir hlutir eru eitthvað sem var ekki búið til í unity og var gert fyrirfram með einhverju öðru.

## 5
#### Hvað er e. game object og hvernig tengist það e. components í e. Inspector? 
Game object er einhver hlutur sem þú setur í leikinn, til dæmis í "Tanks" leikinum þá er skriðdrekinn game object og Í Inspector getur þú breytt því hvernig Game Object-inn hagar sér í leiknum með því að breyta hraðanum á honum eða gefa honum meira líf.

## 6
#### Hvað er líkt og ólíkt með game object og prefab? 
Game object er bara hluturinn sjálfur sem er í leiknum og hann notar prefab sem er eins konar template til að segja sér hvernig hann á að hegða sér. Prefab er bara hluturinn með öllum stillingunum sem var síðast vistað í Inspector á meðan Game Object er bara hluturinn í leiknum.

## 7
#### Hvert er samband þríhyrnings og e. mesh í 3D umhverfi?
Mesh er öll grafíkin í leikjagerð, öll módelin í leikjum eru mesh og öll þessi mesh eru gerð úr einu formi, og þar er þessi þríhyrningur (triangle mesh) sem hluturinn er settur saman úr. 

## 8
#### Hvað er tags og layers? 
#### Tag
Tags eru leið til þess að flokka saman hluti í leiknum þínum sem þjóna líkum tilgangi. Eins og players og collectibles sem virka öll á sama hátt og þar með geturu sett sama reference í scriptu til að hafa áhrif á alla hluti með sama tag þegar eitthvað gerið við þá.

#### Layers
Layers eru mest notaðir fyrir myndavélina þegar þú vilt að hún renderar bara einhvern part af scene-inu eða fyrir lýsinguna ef þú vilt bara setja ljós á einhvern sérstakan part af scene-inu t.d. öll hús eða eitthvað.

## 9
#### Útskýrðu stuttlega hlutverk eftirfarandi glugga/svæði í Unity:
<ol>
<li> Scene view</li>
Í scene view getur þú séð allt scene-ið og fært hluti til á x, y, z ásunum, gert hluti minni og lagað til hluti eins og hitboxes svo það passi.
<li> Game view</li>
Í game view getur þú séð hvenrig leikurinn spilast (hvernig manneskjas sem spilar leikinn upplifar hann). Gott að nota þetta til þess að prófa leikinn af og til svo þú getir verið viss um að þú ert ekki að gera neitt vitlaust.
<li> Project</li>
Í project glugganum sést öll prefabs hjá þér, assets og scripts. Svo getur þú dregið inn hlutina í Hierachy gluggann og ef það er game object á bætist það líka við í scene view eða leikinn.
<li> Hierachy</li>
Í Hierachy getur þú séð lista yfir öll game objects sem þú ert með í leiknum og það getur líka verið prefab með einhverjum game object. Þar getu þú eytt game object úr leiknum og dregið inn game object frá project glugganum.
<li> Inspector</li>
Í inspector getur þú still hlutinn þinn til að haga sér á ákveðinn hátt, þú getur bætt við ljósi þannig að það kemur ljós útfrá hlutnum eða einu component sem heitir Rigidbody sem lætur hlutinn verða undir áhrifum þyngdarafls.
</ol>


## 10
#### Gerðu eftirfarandi í Unity:
<ol>
<li> Búðu til 3D project sem heitir V1_nafn</li>
<li> Náðu í Standard Assets í Unity Store</li>
<li> Búðu til senu (e. scene) og láttu það heita sena1.</li>
<li> Búðu til jörð (Plane eða terrain) og settu lit á það eða e. mesh</li>
<li> Búðu til 3D GameObject (kassa). Láttu hann líta raunverulega út.</li>
<li> Bættu nokkrum tilbúnum umhverfis hlutum í senuna</li>
</ol>
