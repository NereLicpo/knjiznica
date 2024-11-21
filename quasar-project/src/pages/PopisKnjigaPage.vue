<template>
  <q-page>
    <div class="q-pa-md">
      <q-card flat bordered>
        <q-card-section>
          <div class="text-h4 text-primary text-center q-mb-md">Popis svih knjiga</div>
          <p class="text-body1 text-center">
            Ovdje možete vidjeti popis svih dostupnih knjiga u našoj knjižnici.
          </p>
        </q-card-section>
        <q-card-section>
          <q-table :rows="books" :columns="columns" row-key="id" bordered flat />
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
export default {
  setup() {
    const books = [
      { id: 1, naslov: "Pride and Prejudice", autor: "Jane Austen", opis: "Klasik engleske književnosti o ljubavi i društvenim normama.", stanje: "9/10" },
      { id: 2, naslov: "1984", autor: "George Orwell", opis: "Distopijski roman o totalitarizmu i kontroli društva.", stanje: "10/10" },
      { id: 3, naslov: "To Kill a Mockingbird", autor: "Harper Lee", opis: "Roman o rasnoj nepravdi u američkom društvu.", stanje: "8/10" },
      { id: 4, naslov: "The Great Gatsby", autor: "F. Scott Fitzgerald", opis: "Priča o ljubavi, ambiciji i dekadenciji u doba jazza.", stanje: "9/10" },
      { id: 5, naslov: "Moby Dick", autor: "Herman Melville", opis: "Epska priča o pomorskoj avanturi i opsesiji kapetana Ahab-a.", stanje: "7/10" },
      { id: 6, naslov: "Božanstvena komedija", autor: "Dante Alligheri", opis: "Danteov put kroz krugove pakla", stanje: "8/10" },
      { id: 7, naslov: "Pjesme", autor: "Dobriša Cesarić", opis: "Razne pjesme Dobriše Cesarića", stanje: "5/10" }
    ]


    const columns = [
      { name: "id", label: "ID", align: "left", field: "id" },
      { name: "naslov", label: "Naslov", align: "left", field: "naslov" },
      { name: "autor", label: "Autor", align: "left", field: "autor" },
      { name: "opis", label: "Opis", align: "left", field: "opis" },
      { name: "stanje", label: "Stanje", align: "left", field: "stanje" },
    ];

    return { books, columns };
  },
};
</script>
