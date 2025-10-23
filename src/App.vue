<script setup>
import { ref, watch, onMounted } from "vue";

// Dark mode
const theme = ref("light");

// Charger le thème sauvegardé au démarrage
onMounted(() => {
  const savedTheme = localStorage.getItem("theme");
  if (savedTheme === "dark") {
    theme.value = "dark";
    document.documentElement.classList.add("dark");
  } else {
    theme.value = "light";
    document.documentElement.classList.remove("dark");
  }
});

// Fonction pour basculer le thème
function toggleTheme() {
  if (theme.value === "light") {
    theme.value = "dark";
    document.documentElement.classList.add("dark");
  } else {
    theme.value = "light";
    document.documentElement.classList.remove("dark");
  }
  // Sauvegarde dans le localStorage
  localStorage.setItem("theme", theme.value);
}
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <header
      class="bg-bg dark:bg-(--dark-bg) text-text-primaire dark:text-(--dark-text-primaire) shadow-md z-0"
    >
      <div
        class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex justify-between items-center h-16"
      >
        <!-- Logo / Titre -->
        <h1 class="text-2xl font-(--font-dancing)">Ma Collection</h1>

        <!-- Boutons du header -->
        <div class="flex items-center space-x-4">
          <!-- Toggle Dark Mode -->
          <button
            @click="toggleTheme"
            class="p-2 rounded hover:bg-border dark:hover:bg-(--dark-border) transition"
          >
            🌓
          </button>
        </div>
      </div>
    </header>

    <main class="grow p-5 bg-bg dark:bg-(--dark-bg)">
      <form action="#" class="bg-bg-card p-10 dark:bg-(--dark-bg-card) rounded">
        <div class="flex justify-between items-center mb-5">
          <h2 class="text-xl">Entrée des informations</h2>
          <button
            class="p-2 rounded text-text-primaire dark:text-(--dark-text-primaire) hover:bg-border dark:hover:bg-(--dark-border) transition"
          >
            X
          </button>
        </div>

        <div class="flex gap-3">
          <label class="mb-5 w-1/4 flex gap-2 items-center" for="name">
            <span
              class="font-semibold text-text-secondaire dark:text-(--dark-text-secondaire)"
              >Nom :
            </span>
            <input
              class="input-label"
              type="text"
              id="name"
              placeholder="Nom de l'album"
            />
          </label>
          <label class="mb-5 w-1/4 flex gap-2 items-center" for="artist">
            <span
              class="font-semibold text-text-secondaire dark:text-(--dark-text-secondaire)"
              >Artiste :
            </span>
            <input
              class="input-label"
              type="text"
              id="artist"
              placeholder="Nom de l'artiste"
            />
          </label>
          <label class="mb-5 w-1/4 flex gap-2 items-center" for="year">
            <span
              class="font-semibold text-text-secondaire dark:text-(--dark-text-secondaire)"
              >Année :
            </span>
            <input class="input-label" type="date" id="year" />
          </label>
          <label class="mb-5 w-1/4 flex gap-2 items-center" for="style">
            <span
              class="font-semibold text-text-secondaire dark:text-(--dark-text-secondaire)"
              >Style :
            </span>
            <select id="genre" class="input-label">
              <option
                value=""
                class="text-text-secondaire dark:text-(--dark-text-secondaire)"
              >
                Choisir le style de l'album
              </option>
              <option value="Rap">Rap</option>
              <option value="Romantique">Romantique</option>
              <option value="Dark">Dark</option>
              <option value="Metal">Metal</option>
              <option value="Hip-hop">Hip-hop</option>
            </select>
          </label>
        </div>
      </form>

      <div class="w-full">
        <ul class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-5 gap-6">
          <li>
            <img src="" alt="" />
          </li>
        </ul>
      </div>
    </main>

    <footer
      class="flex justify-center items-center min-h-10 bg-bg dark:bg-(--dark-bg) text-text-primaire dark:text-(--dark-text-primaire) shadow-[0px_-4px_6px_0px_rgba(0,0,0,0.1)]"
    >
      &copy; 2025
    </footer>
  </div>
</template>

<style scoped>
@reference "tailwindcss";
@custom-variant dark (&:where(.dark, .dark *));
</style>
