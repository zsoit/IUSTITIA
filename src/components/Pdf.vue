<script>
import html2pdf from "html2pdf.js";

export default {
  name: "Pdf",
  props: {
    document_info:{
     type: Object,
     required: true,
    },
    applicant: {
      type: Object,
      required: true,
    },
    participant: {
      type: Object,
      required: true,
    },
    died: {
      type: Object,
      required: true,
    },
    court: {
      type: Object,
      required: true,
    },
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
        html2canvas: { scale: 2, useCORS: true },
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
    <h3>Twój wniosek został wygenerowany</h3>
    <button @click="download">Pobierz PDF</button>

    <div class="official-document" id="element-to-print" style="display: none">
      <header>
        <p>{{document_info.city}}, dnia {{document_info.date}}</p>
        <h2 class="text-right">
          {{ court.name }}
        </h2>
        <h1>WNIOSEK O STWIERDZENIE NABYCIA SPADKU</h1>
      </header>

      <section>
        <p>
          <b>Wnioskodawca:</b>
          {{ applicant.name }} {{ applicant.surname }} {{ applicant.pesel }}
          {{ applicant.post_address }}
        </p>

        <p>
          <b>Uczestnicy:</b>
          {{ participant.name }} {{ participant.surname }}
          {{ participant.pesel }}
          {{ participant.post_address }}
        </p>

        <p>
          - Należy wskazać jako uczestników wszystkich spadkobierców ustawowych
          po osobie zmarłej (art. 931 § 1 kc i następne), oraz spadkobierców
          ustanowionych przez spadkodawcę (zmarłego) w testamencie (jeżeli
          testament został sporządzony) wraz z podaniem kim ta osoba była dla
          spadkodawcy (mąż, żona, syn, córka, brat itp.),
          <br />
          - Jednocześnie jeżeli któryś ze spadkobierców nie żyje w chwili
          wniesienia sprawy jako uczestników postępowania w jego miejsce należy
          wskazać jego następców prawnych (spadkobierców),
          <br />
          - W sytuacji gdy wskazany uczestnik jest małoletni (nie ma ukończonych
          18 lat) należy oznaczyć ten fakt dodatkowo wskazując jego
          przedstawiciela ustawowego (rodzica, opiekuna prawnego).
        </p>
      </section>

      <section>
        <h3>Treść rządania wniosku</h3>
        <p>
          Wnoszę o stwierdzenie nabycia spadku po {{ died.name }}
          {{ died.surname }} zmarłym w dniu {{ died.date }} w
          {{ died.post_address }} na podstawie: (ustawy lub testamentu).
        </p>
      </section>

      <section>
        <h3>UZASADNIENIE</h3>
        <p>
          Spadkodawca {{ died.name }} {{ died.surname }} ostatnio stale
          zamieszkały w {{ died.post_address }} zmarł w dniu {{ died.date }}.
        </p>
        <p>Zmarły pozostawił testament / nie pozostawił testamentu</p>
        <p>W dniu śmierci był(a) {{ died.marital_status }}.</p>
        <p>Związek małżeński zawierał {{ died.martial_count }}.</p>
        <p>
          Spadkobiercami są: <i><b> {{ participant.name }} {{ participant.surname }} </b></i>
        </p>

        <p>
          W skład spadku wchodzi gospodarstwo rolne o powierzchni  <i>{{died.farm_count}} położone w {{ died.post_address }} </i>
        </p>
      </section>

      <br /><br /><br />
      <p>..........................................................</p>
      <p>własnoręczny podpis wnioskodawcy</p>

      <br /><br /><br />

      <section style="margin-top: 200px">
        <h3>Uwagi do wniosku</h3>

        <p>Do wniosku należy dołączyć:</p>

        <ul>
          <li>opłatę sądową w wysokości 100 zł</li>
          <li>
            dodatkowo każdy ze spadkobierców jeżeli stwierdzenie nabycia spadku
            ma nastąpić w okresie 6 miesięcy od daty śmierci spadkodawcy
            obowiązany jest uiścić 100 zł tytułem opłaty sądowej od oświadczenia
            o przyjęciu lub odrzuceniu spadku opłatę tą uiszcza się w chwili
            składania oświadczenia na rozprawie, przed Sądem
          </li>
          <li>
            odpisy wniosku w liczbie odpowiadającej ilości wskazanych
            uczestników postępowania
          </li>
          <li>testament (jeżeli był sporządzony) w oryginale</li>
          <li>
            odpis skrócony aktu zgonu (oraz akt małżeństwa zmarłego- w
            przypadku, gdy żyje małżonek zmarłego) w oryginale
          </li>
          <li>
            odpisy skrócone aktów urodzenia, lub małżeństwa synów zmarłego- w
            oryginale
          </li>
          <li>
            odpisy skrócone aktów małżeństwa córek zmarłego- w oryginale (jeżeli
            są pannami akty urodzenia),
          </li>
          <li>
            Jeżeli zmarły nie miał dzieci- odpisy skrócone aktów urodzenia braci
            zmarłego i aktów małżeństwa sióstr zmarłego (jeżeli są pannami- akty
            urodzenia), akt małżeństwa rodziców zmarłego (jeżeli żyją)
          </li>
          <li>
            w oryginale - opłatę za wpis w Rejestrze Spadkowym w wysokości 5 zł
            - wyłącznie na konto NBP 60 1010 1528 0016 9013 9800 0000 (należy
            obowiązkowo podać sygn. akt sprawy i można wpłacać w kasie tut.
            Sądu) * Podanie numeru PESEL jest obowiązkowe dla wnioskodawcy, dla
            uczestników – o ile jest to możliwe.
          </li>
        </ul>
      </section>
    </div>
  </div>
</template>

<style>
#element-to-print{
  color: black !important;
}
h1,
h3 {
  font-size: 15px;
  font-weight: bold;
}
h2 {
  font-size: 15px;
  text-align: right;
  font-weight: bold;

}

p,
li {
  font-size: 14px;
}

.official-document {
  font-family: "Arial", sans-serif;
  line-height: 1.6;
  margin: 60px;
  max-width: 21cm; /* A4 width */
}

header {
  text-align: center;
  margin-bottom: 20px;
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

.sender,
.recipient {
  width: 48%;
}

.text-rigth {
  text-align: right;
}

footer {
  margin-top: 20px;
  text-align: center;
  font-size: 0.8em;
  color: #888;
}
</style>
