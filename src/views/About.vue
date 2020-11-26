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
