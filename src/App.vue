<script setup>
import {computed, ref} from 'vue';

const heureEnMinutes = ref(getTimeInMinutes())
const angle = computed(()=>
  convertirTempsEnAngle(heureEnMinutes.value)
)

function convertirTempsEnAngle(heure) {
    // Définir les points de données
    const pointsMinutes = [0, 180, 360, 540, 720];
    const pointsAngles = [0, 90, 180, 270, 360];

    // Interpoler l'angle en fonction de l'heure
    const angleInterpole = interpolationLineaire(heure, pointsMinutes[0], pointsAngles[0], pointsMinutes[pointsMinutes.length - 1], pointsAngles[pointsAngles.length - 1]);
    return angleInterpole;
}
function interpolationLineaire(x, x1, y1, x2, y2) {
    return y1 + (x - x1) * (y2 - y1) / (x2 - x1);
}
function getTimeInMinutes(){
  const time = new Date();
  const hours = time.getHours() % 12 || 12;
  const minutes = time.getMinutes();
  const totalMinutes = hours *60 + minutes
  return( totalMinutes)
}



</script>

<template>
<h1>Progressive Watch </h1>
<pre> gradient as an hour hand.  </pre>
<div class="container">
  <div class="watch">
    <div class="mask"></div>
  </div>
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
	height: 236px;
	width: 199px; 
  position: absolute;
  top: 46%;
	border-radius: 18%;

  z-index: 3;
	background-image: conic-gradient(
		from  v-bind(angle+'deg'),
		var(--pavedGold), 
		var(--shadowNight)
		);

  }


</style>