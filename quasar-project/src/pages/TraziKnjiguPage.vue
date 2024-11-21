<template>
  <q-page>
    <div class="q-pa-md">
      <q-card flat bordered>
        <q-card-section>
          <div class="text-h4 text-primary text-center q-mb-md">Pretraživanje</div>
          <p class="text-body1 text-center">
            Pretražite bazu knjiga po naslovu ili autoru.
          </p>
        </q-card-section>

        <q-card-section>
          <!-- Pretraga inputa -->
          <q-input v-model="searchQuery" label="Unesite pojam za pretraživanje" :debounce="300" />
          <q-checkbox v-model="searchByAuthor" label="Pretraži po autoru" />
          <q-checkbox v-model="searchByTitle" label="Pretraži po naslovu" />
          <q-btn color="primary" label="Traži" @click="searchBooks" />
        </q-card-section>

        <q-card-section>
          <q-table :rows="foundBooks" :columns="columns" row-key="id" bordered flat />
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const searchQuery = ref("");
    const searchByAuthor = ref(false);
    const searchByTitle = ref(false);
    const foundBooks = ref([]);

    const books = [
      { id: 1, naslov: "Pride and Prejudice", autor: "Jane Austen", opis: "Klasik engleske književnosti o ljubavi i društvenim normama.", stanje: "9/10" },
      { id: 2, naslov: "1984", autor: "George Orwell", opis: "Distopijski roman o totalitarizmu i kontroli društva.", stanje: "10/10" },
      { id: 3, naslov: "To Kill a Mockingbird", autor: "Harper Lee", opis: "Roman o rasnoj nepravdi u američkom društvu.", stanje: "8/10" },
      { id: 4, naslov: "The Great Gatsby", autor: "F. Scott Fitzgerald", opis: "Priča o ljubavi, ambiciji i dekadenciji u doba jazza.", stanje: "9/10" },
      { id: 5, naslov: "Moby Dick", autor: "Herman Melville", opis: "Epska priča o pomorskoj avanturi i opsesiji kapetana Ahab-a.", stanje: "7/10" }
    ]


    const columns = [
      { name: "id", label: "ID", align: "left", field: "id" },
      { name: "naslov", label: "Naslov", align: "left", field: "naslov" },
      { name: "autor", label: "Autor", align: "left", field: "autor" },
      { name: "opis", label: "Opis", align: "left", field: "opis" },
      { name: "stanje", label: "Stanje", align: "left", field: "stanje" },
    ];

    function searchBooks() {
      foundBooks.value = books.filter((book) =>
        (searchByAuthor.value && book.autor.toLowerCase().includes(searchQuery.value.toLowerCase())) ||
        (searchByTitle.value && book.naslov.toLowerCase().includes(searchQuery.value.toLowerCase()))
      );
    }

    foundBooks.value = books;

    return { searchQuery, searchByAuthor, searchByTitle, foundBooks, columns, searchBooks };
  },
};
</script>

<style scoped>
.q-card {
  margin-top: 20px;
  background-color: #fff;
}

.q-page {
  background-color: #f4f4f4;
  color: #333;
}
</style>
