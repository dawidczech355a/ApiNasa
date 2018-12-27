<template>
  <div :class="[{ flexStart: step === 1}, 'wrapper']">
    <transition name="fade">
      <FirstPageImage v-if="step === 0" />
    </transition>  
    <FirstPage v-if="step === 0" />
    <SearchInput 
        :value="searchValue" 
        v-model="searchValue"               
        @input="handleInput" 
        :dark="step === 1" 
      />
      <div class="results" v-if="!loading && step === 1" >
        <ItemsFromApi v-for="item in results" :item="item" @click.native="handleModalOpen(item)" />
      </div>
        <Loader v-if="loading && step === 1" />
        <Modal v-if="modalOpen" :item="modalItem" @closeModal="modalOpen = false"/>
        <CloseModal v-if="modalOpen" @closeModalFromOtherClass="modalOpen = false" />
  </div>
</template>

<script>
  import axios from 'axios';
  //umozliwia pobranie API i zaladowanie jej do strony 
  import debounce from 'lodash.debounce';
  //biblioteka lodash - debounce rozpoczecie wyszukiwania w momencie kiedy odczekamy zalozona ilosc czasu 
  import FirstPage from '@/components/FirstPage.vue';
  import SearchInput from '@/components/SearchInput.vue';
  import FirstPageImage from '@/components/FirstPageImage.vue';
  import ItemsFromApi from '@/components/ItemsFromApi.vue';
  import Modal from '@/components/Modal.vue';
  import CloseModal from '@/components/CloseModal.vue';
  import Loader from '@/components/Loader.vue';

  const API = 'https://images-api.nasa.gov'; 

export default {
  views: 'Home',
  name: 'Search',
  components: {
    FirstPage, 
    SearchInput,
    FirstPageImage,
    ItemsFromApi,
    Modal,
    CloseModal,
    Loader,
    },
  data() {
    return {
      modalOpen: false,
      modalItem: null,
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleModalOpen(item) {
      this.modalOpen = true;
      this.modalItem = item;
    },
    handleInput: debounce(function() {
          this.loading = true;
          console.log(this.searchValue);
          axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
          .then((response) => {
                this.results = response.data.collection.items;
                this.loading = false;
                this.step = 1;
                if(response.data.collection.metadata.total_hits === 0) {
                  this.step = 0;
                  this.loading = false;
                  alert("Incorrect name, please try again ;)");
                } else if (this.searchValue === '') {
                  this.step = 0;
                  this.loading = false;
                }
          })
          .catch((error) => {
            console.log(error);
        });
    }, 1000),

  }
};
</script>
<style lang="scss" scoped>
  .wrapper {
    width: 100%;
    position: relative;
    height: 100vh;
    align-items: center;
    display: flex;
    flex-direction: column;
    text-align: center;
    justify-content: center;
  
    &.flexStart {
      justify-content: flex-start; 
    }

    .results {
      width: 100%;
      display: grid;
      grid-template-columns: 1fr 1fr;

      @media (min-width: 768px) {
        width: 100%;
        grid-template-columns: 1fr 1fr 1fr;
        grid-gap: 10px;
      }
        @media (min-width: 1024px) {
          width: 100%;
          grid-template-columns: 1fr 1fr 1fr 1fr;
      }
          @media (max-width: 500px) {
            width: 100%;
            grid-template-columns: 1fr;
      }
    }
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity 1s ease;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }

</style>