<script setup>
import Pdf from './../Pdf.vue'

const props = defineProps({
  step: Number,
  formValues: Object,
  nextStep: Function,
  validateForm: Function
})

</script>

<template>
  <Pdf></Pdf>
  <section id="zero-step">
    <div class="row mt-4 px-2">
      <div class="col-12">
        <h1 class="h2 fw-bold">Pytania wstępne</h1>
        <p class="pt-1">
          Proszę, wypełnij poniższe informację.
        </p>

        <form :id="`form${step}`" class="needs-validation" novalidate>

          <div class="mb-3 position-relative">
            <label for="nameInput" class="form-label  mb-1">Podaj imię oraz nazwisko spadkodawcy</label>
            <input required type="text" class="form-control" id="nameInput" aria-describedby="nameHelp" placeholder="np. Jan Kowalski" v-model="props.formValues.name">

            <div class="invalid-feedback">Imię oraz nazwisko</div>
            <div class="valid-feedback">
              Ok!
            </div>
          </div>

          <div class="mb-3 position-relative">
            <label for="cityInput" class="form-label mb-1">W jakiej miejscowości mieszkał spadkodawca przed śmiercią?</label>
            <input required type="email" pattern="[^@ \t\r\n]+@[^@ \t\r\n]+\.[^@ \t\r\n]+" class="form-control"
              id="cityInput" aria-describedby="cityHelp" placeholder="np. Koszalin" v-model="props.formValues.city">
            <div class="invalid-feedback">Popraw prawidłową miejscowość</div>
            <div class="valid-feedback">
              Ok!
            </div>
          </div>

          <div class="mb-3 position-relative">
            <label for="relationInput" class="form-label mb-1">Kim jesteś dla spadkodawcy?</label>
            <select required class="form-select" id="relationInput" v-model="props.formValues.relation">
                <option value="" disabled selected>Wybierz opcję</option>
                <option value="Żona/mąż">Żona/mąż</option>
                <option value="Córka/Syn">Córka/Syn</option>
                <option value="Matka/Ojciec">Matka/Ojciec</option>
                <option value="Wnuk/Wnuczka">Wnuk/Wnuczka</option>
                <option value="Brat/Siostra">Brat/Siostra</option>
            </select>
            <div class="invalid-feedback">Wybierz odpowiedź</div>
            <div class="valid-feedback">Ok</div>
          </div>
    
        </form>
      </div>
    </div>
  </section>
</template>

