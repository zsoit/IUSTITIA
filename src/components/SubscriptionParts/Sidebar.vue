<template>

  <!-- Mobile Nav -->
  <nav class="col-7 col-sm-6 d-flex justify-content-around mt-4 pt-3 d-xl-none" id="mobile-nav">
    <span 
    class="step-number d-inline-flex"
    v-bind:class="[ step === 0 ? 'active' : '']"
    >1
    </span>

    <span 
    class="step-number d-inline-flex"
    v-bind:class="[step === 1 ? 'active' : '']"
    >2
    </span>

    <span 
    class="step-number d-inline-flex"
    v-bind:class="[step === 2 ? 'active' : '']"
    >3
    </span>

    <span 
    class="step-number d-inline-flex"
    v-bind:class="[step >= 3 ? 'active' : '']"
    >4
    </span>
  </nav>

  <!-- Aside desktop -->
  <div class="d-none d-xl-block col-xl-3 mt-3 px-5 pt-5 bg-desktop">
    <aside class="d-none d-xl-flex">
      <nav id="desktop-nav" class="flex-column">

        <!-- Nav 0 -->
        <div class="nav-item">
          <span 
          class="step-number"
          v-bind:class="[step === 0 ? 'active' : '']"
          >0</span>
          <div class="nav-infos">
            <p class="text-uppercase">Krok 0 <br>
              <span class="text-white fw-bold h6">Pytania wstępne</span>
            </p>
          </div>
        </div>

        <!-- Nav 1 -->
        <div class="nav-item mt-2">
          <span 
          class="step-number"
          v-bind:class="[step === 1 ? 'active' : '']"
          >1</span>
          <div class="nav-infos">
            <p class="text-uppercase">Krok 1 <br>
              <span class="text-white fw-bold h6">Twoje dane</span>
            </p>
          </div>
        </div>

        <!-- Nav 2 -->
        <div class="nav-item mt-2">
          <span 
          class="step-number"
          v-bind:class="[step === 2 ? 'active' : '']"
          >2</span>
          <div class="nav-infos">
            <p class="text-uppercase">Krok 2 <br>
              <span class="text-white fw-bold h6">Wybierz adres</span>
            </p>
          </div>
        </div>

        <!-- Nav 3 -->
        <div class="nav-item mt-2">
          <span 
          class="step-number"
          v-bind:class="[step >= 3 ? 'active' : '']"
          >3</span>
          <div class="nav-infos">
            <p class="text-uppercase">Krok 3<br>
              <span class="text-white fw-bold h6">Dezycja</span>
            </p>
          </div>
        </div>

        <!-- Nav 4 -->
        <div class="nav-item mt-2">
          <span 
          class="step-number"
          v-bind:class="[step >= 4 ? 'active' : '']"
          >4</span>
          <div class="nav-infos">
            <p class=" text-uppercase">Krok 4 <br>
              <span class="text-white fw-bold h6">Podsumowanie</span>
            </p>
          </div>
        </div>

      </nav>
    </aside>
  </div>

</template>

<script setup>

const stepNb = defineProps({
step: Number
})

</script>

<style>
.bg-desktop, #mobile-nav{
background-color: hsl(213deg, 96%, 18%) !important;
padding: 35px;
}
</style>
