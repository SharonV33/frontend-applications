<template>
  <div class="about">
    <h1>Over het project</h1>
    <p>
      Er zijn in Nederland zo'n 1,4 miljoen mensen met een lichamelijke beperking*.
      Dit is ongeveer 8% van de Nederlandse bevolking. Veel van deze mensen kunnen
      zichzelf nog vervoeren, andere laten zich vervoeren door familie of een
      begeleider. Ikzelf val in de eerste categorie, helaas heb ik regelmatig moeite
      met het vinden van een parkeergarage waar ik geen trap voor hoef te gebruiken.
      In samenwerking met de Volkskrant ben ik aan de slag gegaan met het maken van
      een data visualisatie die in kaart brengt hoeveel parkeergarages beschikbaar zijn
      voor mindervalide. Voor dit onderzoek heb ik gebruik gemaakt van een parkeer
      dataset beschikbaar gesteld door de npro**.
    </p>
    <p>
      Wat ik heb ontdekt tijdens het maken van dit project is dat Groningen het erg
      goed doet qua mindervalide toegankelijke parkeergarages. Ongeveer 7% van de
      parkeergarages in de dataset die zich bevinden in Groningen zijn toegankelijk
      voor mindervaliden mensen. Dit is ongeveer hetzelfde percentage als mindervalide
      mensen in Nederland. In deze situatie moet echter wel rekening gehouden worden met
      het feit dat Groningen een minder dichte populatie heeft dan bijvoorbeeld
      Flevoland of noord Holland. Als we kijken naar de data van Flevoland zien we dat
      maar ongeveer 3.5% van de parkeergarages toegankelijk is voor mindervalide mensen.
    </p>
    <sub>
      bronnen:
      * https://www.vgn.nl/feiten-en-cijfers-de-gehandicaptenzorg
      ** https://npropendata.rdw.nl/
    </sub>
  </div>
</template>
<style scoped>
  .about {
    display: flex;
    flex-direction: column;
  }
  p {
    width: 70%;
    align-self: center;
  }
</style>
