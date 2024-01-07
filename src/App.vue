<script setup>

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

</script>

<template>
  <h1>Progressive Watch </h1>
  <div class="watch">

  </div>

</template>

<style>


</style>