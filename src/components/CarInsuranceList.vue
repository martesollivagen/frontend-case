<template>
  <div>
    <h3>Velg dekning:</h3>
    <v-radio-group v-model="selected">
      <div class="car-insurance-list">
        <CarInsurance
            v-for="option in insurances"
            :key="option.title"
            :title="option.title"
            :price="option.price"
            :description="option.description"
            :recommended="option.recommended"
            :isSelected="selected === option.title"
            @update:selected="selected = $event"
        />
      </div>
    </v-radio-group>
    <h4 class="text-decoration-underline">Sammenlign dekninger</h4>
  </div>
</template>

<script>
import CarInsurance from "./CarInsurance.vue";

export default {
  name: 'CarInsuranceList',
  components: {
    CarInsurance
  },
  data() {
    return {
      selected: '',
      randomComponent: null,
      insurances: [
        {
          title: "Toppkasko",
          price: 1235,
          description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          recommended: false
        },
        {
          title: "Kasko med leiebil",
          price: 1179,
          description: "En forsikring som passer de fleste biler. Dekker det meste av skader, også de du selv er ansvarlig for. Inkluderer: minikasko og ansvar.",
          recommended: false
        },
        {
          title: "Kasko",
          price: 1123,
          description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          recommended: false
        },
        {
          title: "Minikasko",
          price: 491,
          description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          recommended: false
        },
        {
          title: "Ansvar",
          price: 362,
          description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          recommended: false
        },
      ]
    };
  },
  created() {
    this.randomComponent = Math.floor(Math.random() * this.insurances.length);
    this.insurances[this.randomComponent].recommended = true;
  }
}
</script>

<style scoped>

.car-insurance-list {
  display: flex;
  flex-direction: column;
  gap: 24px;
  align-items: center;
}
</style>
