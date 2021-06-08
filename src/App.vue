<template>
  <h3>Parsing data</h3>
  <div class="button">
    <button @click="page++">incress page</button>
    <button @click="page--">decress page</button>
    <button @click="togleBook">Hide book</button>
  </div>
  <div>
    <button @click="togleModal">Show Modal</button>
  </div>
  <div>
    <button @click="togleFilterFav">Filter Fav</button>:
    {{ filter ? "Favorite book" : "All" }}
  </div>
  <span v-bind:title="message" v-if="showBook">
    <a :href="instagram">Cek my profil</a>
    <div>pages: {{ page }}</div>
    <ul class="list-book">
      <li
        v-for="(book, i) in filter ? filteredBooks : books"
        v-bind:key="i"
        v-bind:class="{ fav: book.fav }"
        @click="togleFav(i)"
      >
        <img :src="book.img" :alt="book.title" />
        <div class="content">
          <h3>{{ book.title }}</h3>
          <p>Author: {{ book.author }}</p>
        </div>
      </li>
    </ul>
  </span>
  <div v-if="isModal">
    <Modal
      :modalData="modal"
      :text="modal.text"
      isActive="active"
      @close="togleModal"
    />
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal
  },
  data() {
    return {
      showBook: true,
      filter: true,
      instagram: "https://instagram.com/abam.afriansyah",
      message: "You loaded this page on " + new Date().toLocaleString(),
      books: [
        {
          title: "Bincang Akhlak",
          author: "Ustad Jek",
          img: "/assets/1.jpg",
          fav: true
        },
        {
          title: "Ubur Ubur Lembur",
          author: "Raditya Dika",
          img: "/assets/2.jpg",
          fav: false
        },
        {
          title: "This is Why I Need You",
          author: "Brian Khrisna",
          img: "/assets/3.jpg",
          fav: true
        }
      ],
      page: 321,
      modal: {
        title: "This is a Modal",
        text: "Ini adalah sebagian text dari isi data"
      },
      isModal: false
    };
  },
  methods: {
    togleModal() {
      this.isModal = !this.isModal;
    },
    reverseHandling() {
      this.page++;
    },
    togleBook() {
      this.showBook = !this.showBook;
    },
    togleFav(e) {
      this.books[e].fav = !this.books[e].fav;
    },
    togleFilterFav() {
      this.filter = !this.filter;
    }
  },
  computed: {
    filteredBooks() {
      return this.books.filter(book => book.fav);
    }
  }
};
</script>

<style scoped>
.container {
  margin: 1rem;
  padding: 1rem;
  border: solid 1px;
  border-radius: 10px;
}

#data span {
  display: block;
}

.box {
  text-align: center;
  background: #ddd;
  width: 200px;
  padding: 100px 0;
  margin: 20px;
  display: inline-block;
}

.list-book {
  list-style: none;
  padding: 0;
  width: auto;
}

.list-book li {
  background-color: lightgrey;
  margin: 1rem;
  padding: 1rem;
  /* border: solid 1px black; */
  border-radius: 10px;
  box-shadow: 5px 5px 5px #ddd;
  display: flex;
}

.list-book li.fav {
  color: midnightblue;
  background-color: lightpink;
}

.list-book li img {
  padding: 0px 1rem;
}

h1 {
  text-align: center;
}
</style>
