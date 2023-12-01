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
  <Pdf
      :applicant="{
      name: 'Mateusz',
      surname: 'Lufka',
      pesel: '0999',
      post_address: 'Pilulice, 77-000 Chuj',
    }"
      :participant="{
      name: 'Jan',
      surname: 'Pawel II',
      pesel: '0999',
      post_address: 'Pizdogrzmoty Dolne, 88-200 Bychawa',
    }"
      :died="{
      name: 'Janusz',
      surname: 'Sram',
      date: '24 maj',
      post_address: 'chuj',
      marital_status: 'zameżny',
      martial_count: '2',
    }"
      :court="{
      name: 'Sąd Rejonowy w Rzeszowie I lub XI Wydział Cywilny - Jebanie Starego',
    }"
  ></Pdf>
  <section id="first-step">
    <div class="row mt-4 px-2">
      <div class="col-12">
        <h1 class="h2 fw-bold">Twoje informacje</h1>
        <p class="pt-1">
          Proszę, wypełnij poniższe informację.
        </p>

        <form :id="`form${step}`" class="needs-validation" novalidate>

          <div class="mb-3 position-relative">
            <label for="nameInput" class="form-label  mb-1">Imię oraz nazwisko</label>
            <input required type="text" class="form-control" id="nameInput" aria-describedby="nameHelp" placeholder="np. Jan Kowalski" v-model="props.formValues.name">

            <div class="invalid-feedback">Imię oraz nazwisko</div>
            <div class="valid-feedback">
              Ok!
            </div>
          </div>

          <div class="mb-3 position-relative">
            <label for="inputEmail" class="form-label mb-1">Uzupełnij</label>
            <input required type="email" pattern="[^@ \t\r\n]+@[^@ \t\r\n]+\.[^@ \t\r\n]+" class="form-control"
              id="inputEmail" aria-describedby="emailHelp" placeholder="np. jan.kowalski@poczta.pl" v-model="props.formValues.email">
            <div class="invalid-feedback">Popraw</div>
            <div class="valid-feedback">
              Ok!
            </div>
          </div>

          <div class="mb-3 position-relative">
            <label for="inputPhone" class="form-label mb-1">Numer telefonu</label>
            <input required type="tel" pattern="^[\+]?[(]?[0-9]{3}[)]?[-\s\.]?[0-9]{3}[-\s\.]?[0-9]{4,6}$"
              class="form-control" id="inputPhone" placeholder="np. +48 000 000 000" v-model="props.formValues.tel">
            <div class="invalid-feedback">Popraw</div>
            <div class="valid-feedback">Ok</div>
          </div>

        </form>
      </div>
    </div>
  </section>
</template>

