---
title: "En ny vetenskap har skapats - Prompt engineering"
date: 2023-03-09T20:31:53+01:00
image: pic12.jpeg
draft: false
publishDate: 2023-03-12
---

## Prompt engineering

ref: https://amatriain.net/blog/PromptEngineering

### 1. Vad är en uppmaning?

Generativa AI-modeller gränssnitt med användaren genom mestadels textinmatning. Du berättar för modellen vad den ska göra genom ett textgränssnitt, och modellen försöker utföra uppgiften. Vad du säger till modellen att göra i vid bemärkelse är uppmaningen.

När det gäller bildgenererande AI-modeller som DALLE-2 eller Stable Diffusion är uppmaningen främst en beskrivning av bilden du vill generera.

När det gäller stora språkmodeller (LLM) som GPT-3 eller ChatGPT kan prompten innehålla allt från en enkel fråga ("Vem är USA:s president?") till ett komplicerat problem med alla typer av data som infogas i prompt (observera att du till och med kan mata in en CSV-fil med rådata som en del av inmatningen). Det kan också vara ett vagt uttalande som ”Berätta ett skämt. Jag är nere idag."

Ännu mer generellt, i generativa uppgiftsorienterade modeller som Gato, kan uppmaningen vara extremt hög och definiera en uppgift du behöver hjälp med ("Jag behöver organisera en veckas resa till Grekland").

För resten av det här dokumentet, och för nu, kommer vi att fokusera på det specifika användningsfallet för uppmaningar för LLM.

### 2. Delar av en prompt

Generellt sett, och på en hög nivå, kan en prompt ha något av följande:

* Instruktioner
* Fråga
* Indata
* Exempel

### 3. Grundläggande snabbexempel

För att få ett resultat måste antingen 1 eller 2 finnas. Allt annat är valfritt. Låt oss se några exempel (alla använder ChatGPT).

Instruktioner + Fråga
Utöver att ställa en enkel fråga, kanske nästa nivå av sofistikering i en prompt är att inkludera några instruktioner om hur modellen ska svara på frågan. Här ber jag om råd om hur man skriver en högskoleuppsats, men inkluderar även instruktioner om de olika aspekterna jag är intresserad av att höra om i svaret.

"Hur ska jag skriva min antagningsuppsats? Ge mig förslag på de olika avsnitten jag bör ta med, vilken ton jag ska använda och vilka uttryck jag bör undvika.”

#### Instruktioner och indata

Om man fortsätter med det föregående exemplet undgår det ingen att om man kan be en LLM om råd om hur man skriver en uppsats så kan man också direkt be den skriva själva uppsatsen.

Notera:Jag förespråkar inte att detta ska vara en etisk användning av dessa verktyg, men det är viktigt att vara medveten om att denna möjlighet finns och redan används av studenter runt om i världen. Det ligger utanför räckvidden för den här inledande guiden att diskutera alla möjliga etiska, juridiska eller moraliska problem som LLMs eller generativ AI som helhet introducerar, men jag trodde att det skulle vara viktigt att åtminstone nämna i ett inledande exempel. Att man KAN göra något med en generativ modell betyder inte att det är rätt sak att göra! Å andra sidan, om du är på den mottagande sidan, förbereder du dig och din organisation bättre för alla typer av AI-genererat innehåll som kommer din väg. Lyckligtvis, för situationer som den som beskrivs i det här exemplet, pågår redan ansträngningar som GPTZero för att upptäcka AI-genererat innehåll.

Tillbaka till exemplet, låt oss se vad som händer när jag matar in data om mig och ge några instruktioner:

> "Med tanke på följande information om mig, skriv en högskoleuppsats med fyra stycken: Jag kommer ursprungligen från Barcelona, ​​Spanien. Medan min barndom hade olika traumatiska händelser, som att min far dog när jag bara var 6, tror jag fortfarande att jag hade en ganska lycklig barndom. Under min barndom bytte jag skola väldigt ofta, och gick i alla typer av skolor, från offentliga skolor till mycket religiösa privata. En av de mest "exotiska" sakerna jag gjorde under de åren är att tillbringa ett helt läsår med att studera 6:e klass i Twin Falls, Idaho, med min utökade familj. 
> 
> Jag började jobba väldigt tidigt. Mitt första jobb, som engelsklärare, var vid 13 års ålder. Efter det, och under hela mina studier, arbetade jag som lärare, servitör och till och med byggnadsarbetare.”*

#### Fråga + exempel
Du kan också mata in exempel i en språkmodell. I exemplet nedan inkluderar jag några av de program jag gillar och inte gillar att bygga ett "billigt" rekommendationssystem. Observera att även om jag bara lade till några få program, är längden på den här listan endast begränsad av vilken tokengräns vi än kan ha i LLM-gränssnittet.

>"Här är några exempel på tv-program jag verkligen gillar: Breaking Bad, Peaky Blinders, The Bear. Jag gillade inte Ted Lasso. Vilka andra program tror du att jag kan gilla?”

### 4. Så, vad är prompt engineering ändå?

Nu när vi vet vad en prompt är, och vi har sett några exempel på det, låt oss diskutera vad som är prompt engineering.

Snabb ingenjörskonst är en mycket ny men snabbt växande disciplin som har som mål att utforma den optimala prompten givet en generativ modell och ett mål. Snabb ingenjörskonst växer så snabbt att många tror att den kommer att ersätta andra aspekter av maskininlärning som funktionsteknik eller arkitekturteknik för stora neurala nätverk.

Snabb ingenjörskonst kräver viss domänförståelse för att införliva målet i prompten (t.ex. genom att bestämma hur bra och dåliga resultat ska se ut). Det kräver också förståelse för modellen. Olika modeller kommer att reagera olika på samma typ av uppmaningar.

Att generera uppmaningar i någon skala kräver ett programmatiskt tillvägagångssätt. På den mest grundläggande nivån vill du generera promptmallar som kan modifieras programmatiskt enligt någon datauppsättning eller kontext. Som ett grundläggande exempel, om du hade en databas med personer med en kort text om dem som liknar den som användes i högskoleuppsatsen ovan. Uppmaningsmallen skulle bli något i stil med "Med tanke på följande information om [ANVÄNDARE], skriv en högskoleuppsats med fyra stycken: [USER_BLURB]". Och det programmatiska tillvägagångssättet för att generera högskolebrev för alla användare skulle se ut ungefär så här:

```
  for user,blurb in students.items():
      prompt = “Given the following information about {}, write a 4 paragraph college essay: {}”.format(user, blurb)
      callGPT(prompt)
```

Slutligen är prompt engineering, som alla ingenjörsdiscipliner, iterativ och kräver en del utforskning för att hitta rätt lösning. Även om detta inte är något jag har hört talas om, kommer prompt engineering att kräva många av samma tekniska processer som mjukvaruteknik (t.ex. versionskontroll och regressionstestning).

För fler exempel läs följande bloginlägg som är basen för detta inlägg. -> https://amatriain.net/blog/PromptEngineering
