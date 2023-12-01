<template>
    <div>
    <!-- Thanks section -->
    <section id="thanks-section">
        <div class="row">
            <div class="col-12 text-center pt-5 pb-4">
                <img src="/assets/images/icon-thank-you.svg" alt="">
            </div>
            <div class="col-12 text-center">
                <h2 class="fw-bold">Dziękujemy! </h2>
                <p class="text-cool-gray px-2 pt-1">
                    Poniżej znajduję się link do wniosku w formacie pdf


                </p>
              <button type="button" class="btn btn-success">Pobierz wniosek</button>

            </div>
        </div>
    </section>
    </div>
</template>

<script setup>

const props = defineProps({
  step: Number
})

</script>