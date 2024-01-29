<template>
  <div>
    <h1>Profil Utilisateur</h1>
    <p v-if="error">Erreur lors du chargement du profil.</p>
    <div v-else>
      <p>Nom: {{ userProfile.name }}</p>
      <p>Email: {{ userProfile.email }}</p>
    </div>
  </div>
</template>

<script setup>
import { useAsyncData } from 'nuxt/app'

const { data: userProfile, error } = useAsyncData('userProfile', () =>
    // Simuler une requête API
    new Promise((resolve) => {
      setTimeout(() => {
        resolve({
          name: 'John Doe',
          email: 'john.doe@example.com',
          // Autres données du profil
        })
      }, 1000) // Simule un délai réseau
    })
)
</script>
