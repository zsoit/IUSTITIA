<script>

import html2pdf from "html2pdf.js";
export default {
  name: "Pdf",
  props: {
    msg: String,
  },
  methods: {
    download() {
      const el = document.getElementById("element-to-print");
      const element = el.cloneNode(true);
      element.style.display = "block";

      const opt = {
        margin: 0,
        filename: "spadek_nr_23334324.pdf",
        image: { type: "jpeg", quality: 1.0 },
        html2canvas: { scale: 2,useCORS: true  },
        jsPDF: {
          unit: "in",
          format: "a4",
          orientation: "p",
        },
      };

      html2pdf().set(opt).from(element).save();

    },
  },
};

</script>

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>Twój wniosek został wygenerowany</h3>
    <button @click="download">Pobierz PDF</button>


    <div class="official-document" id="element-to-print" style="display: none">
      <header>
        <h1>Wniosek o stwierdzenie nabycia spadku</h1>
      </header>

      <section>
        <div class="address-section">
          <div class="sender">
            <p>
              Janusz Sram<br>
              Gwiezdana Flota<br>
              Galaktyka Kurvix, planeta C.H.U.J
            </p>
          </div>
          <div class="recipient">
            <p class="text-right">
              <br>
              <br>

            </p>
          </div>
        </div>

        <p>
          Szanowny Pan/Pani Imię Nazwisko Adresata,
        </p>

        <p>
          Treść wniosku znajduje się tutaj. Możesz dostosować zawartość zgodnie z własnymi potrzebami.
          Uczestnicy: (imię i nazwisko oraz dokładny adres miejsca zamieszkania), numer PESEL*
          - Należy wskazać jako uczestników wszystkich spadkobierców ustawowych po osobie zmarłej (art.
          931 § 1 kc i następne), oraz spadkobierców ustanowionych przez spadkodawcę (zmarłego) w
          testamencie (jeżeli testament został sporządzony) wraz z podaniem kim ta osoba była dla
          spadkodawcy (mąż, żona, syn, córka, brat itp.),
          - Jednocześnie jeżeli któryś ze spadkobierców nie żyje w chwili wniesienia sprawy jako uczestników
          postępowania w jego miejsce należy wskazać jego następców prawnych (spadkobierców),
          - W sytuacji gdy wskazany uczestnik jest małoletni (nie ma ukończonych 18 lat) należy oznaczyć ten
          fakt dodatkowo wskazując jego przedstawiciela ustawowego (rodzica, opiekuna prawnego).
          Uczestnicy: (imię i nazwisko oraz dokładny adres miejsca zamieszkania), numer PESEL*
          - Należy wskazać jako uczestników wszystkich spadkobierców ustawowych po osobie zmarłej (art.
          931 § 1 kc i następne), oraz spadkobierców ustanowionych przez spadkodawcę (zmarłego) w
          testamencie (jeżeli testament został sporządzony) wraz z podaniem kim ta osoba była dla
          spadkodawcy (mąż, żona, syn, córka, brat itp.),
          - Jednocześnie jeżeli któryś ze spadkobierców nie żyje w chwili wniesienia sprawy jako uczestników
          postępowania w jego miejsce należy wskazać jego następców prawnych (spadkobierców),
          - W sytuacji gdy wskazany uczestnik jest małoletni (nie ma ukończonych 18 lat) należy oznaczyć ten
          fakt dodatkowo wskazując jego przedstawiciela ustawowego (rodzica, opiekuna prawnego).
        </p>
      </section>

      <br><br><br>
      Janina Piździgrzmot, Prezes Twojego Starego Najebanego

    </div>

  </div>
</template>

<style scoped>
.official-document {
  font-family: 'Arial', sans-serif;
  line-height: 1.6;
  margin: 60px;
  max-width: 21cm; /* A4 width */
}

header {
  text-align: center;
  margin-bottom: 20px;
}

h1 {
  color: #1f487e;
}

section {
  margin-bottom: 20px;
}

p {
  text-align: justify;
}

.address-section {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.sender, .recipient {
  width: 48%;
}

footer {
  margin-top: 20px;
  text-align: center;
  font-size: 0.8em;
  color: #888;
}

</style>