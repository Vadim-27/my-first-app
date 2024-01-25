<template>
  <div id="app">
    <!-- <h2>{{ text }}</h2> -->
    <Container>
      <ApartmentsFilterForm 
      class="apartments-filter"
      @submit="filter"
      />
    </Container>
    <ApartmentsList :items="filteredApartments">
      <template v-slot:apartment="{ apartment }">
        <ApartmentsItem
          
          :key="apartment.id"
          :descr="apartment.descr"
          :rating="apartment.rating"
          :imgSrc="apartment.imgUrl"
          :price="apartment.price"
        />
      </template>
    </ApartmentsList>
  </div>
</template>

<script>
import ApartmentsList from "./components/Apartment/ApartmentsList.vue";
import ApartmentsItem from "./components/Apartment/ApartmentsItem.vue";
import apartments from "./components/Apartment/apartments";
import Container from "./components/shared/Container.vue";
import ApartmentsFilterForm from "./components/Apartment/ApartmentsFilterForm.vue";

export default {
  name: "App",
  components: {
    ApartmentsList,
    ApartmentsItem,
    Container,
    ApartmentsFilterForm,
  },
  data() {
    return {
      // text: '',
      apartments,
      filters: {
        city: '',
        price: ''
      }
    };
  },
  
  computed: {
    filteredApartments() {
      return this.filterByCityName(this.filterByPrice(this.apartments))
    }
  },
  methods: {
    filter({ city, price }) {
        console.log('Filtering with city:', city, 'and priceуууу:', price);
      this.filters.city = city;
      this.filters.price = price;
    },
    filterByCityName(apartments) {
      console.log('Filtering by city:', this.filters.city);
      if (!this.filters.city) return apartments

      return apartments.filter((apartment) => {
        return apartment.location.city === this.filters.city
      })
    },
    filterByPrice(apartments) {
      console.log('Filtering by priceееее:', this.filters.price);
      if (!this.filters.price) return apartments

      return apartments.filter((apartment) => {
        return apartment.price >= this.filters.price
      })
    }

  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.apartments-filter {
  margin-bottom: 40px;
}
</style>
