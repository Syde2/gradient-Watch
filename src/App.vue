<script setup>
import {computed, ref} from 'vue';

const heure = getCurrentHour()
const angle = computed(()=>
  convertirHeureEnAngle(heure)
)

function convertirHeureEnAngle(heure) {
    // Définir les points de données
    const pointsHeures = [0, 3, 6, 9, 12];
    const pointsAngles = [0, 90, 180, 270, 360];

    // Interpoler l'angle en fonction de l'heure
    const angleInterpole = interpolationLineaire(heure, pointsHeures[0], pointsAngles[0], pointsHeures[pointsHeures.length - 1], pointsAngles[pointsAngles.length - 1]);

    return angleInterpole;
}
// Fonction d'interpolation linéaire
function interpolationLineaire(x, x1, y1, x2, y2) {
    return y1 + (x - x1) * (y2 - y1) / (x2 - x1);
}

function getCurrentHour(){
  const time = new Date();
  const hours = time.getHours() % 12 || 12;
  return(hours)
}


</script>

<template>
<h1>Progressive Watch </h1>
<pre> gradient as an hour hand.  </pre>
<div class="container">
  <div class="watch"></div>
</div>
</template>

<style>

:root{
	--lighthouse: #F3F4F4;
	--porcelainJasper : #DFE2E4;
	--pavedGold:#E8D284;
	--canadianMaple:#CAB266;
	--shadowNight : #2A4F61;
	--petrolSlumber : #243640;
}
.watch{
	height: 330px;
	width: 300px;
	border-radius: 30%;
  border: 10px solid var(--petrolSlumber);
	background-image: conic-gradient(
		from  v-bind(angle+'deg'),
		var(--pavedGold), 
		var(--shadowNight)
		);

  }
  

</style>