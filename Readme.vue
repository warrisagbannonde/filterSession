<template>
  <div>
    <button class="accordion" @click="toggleAccordion">
      Lien 1
    </button>
    <div class="panel" v-show="isOpen">
      Contenu du lien 1
    </div>

    <!-- Ajoutez d'autres boutons et panneaux ici pour les autres liens -->

  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    toggleAccordion() {
      this.isOpen = !this.isOpen;
    }
  }
};
</script>

<style scoped>
.accordion {
  background-color: #eee;
  color: #444;
  cursor: pointer;
  padding: 18px;
  width: 100%;
  text-align: left;
  border: none;
  outline: none;
  transition: 0.4s;
}

.panel {
  padding: 18px;
  background-color: white;
  display: none;
  overflow: hidden;
  transition: max-height 0.2s ease-out;
}

.active, .accordion:hover {
  background-color: #ccc;
}
</style>
