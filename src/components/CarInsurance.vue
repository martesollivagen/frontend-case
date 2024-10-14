<template>
  <div>
    <div :class="['box', { 'selected': isSelected }]">
      <div class="header">
        <v-radio
            :value="title"
            :model-value="isSelected"
            @change="$emit('update:selected', title)">

          <template v-slot:label>
            <p class="custom-radio">{{title}}</p>
          </template>

        </v-radio>

        <div class="price">{{ price }} kr/mnd.</div>
      </div>
      <div v-if="recommended" class="recommended-tag">Anbefalt</div>
      <div class="content">{{ description }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CarInsurance',
  props: {
    price: Number,
    title: String,
    description: String,
    recommended: Boolean,
    isSelected: Boolean
  }
}
</script>

<style scoped>

.box {
  width: 100%;
  max-width: 400px;
  border: 1px solid grey;
  padding: 4px;
  position: relative;
}

.selected {
  border: 2px solid black;
}

.recommended-tag {
  background-color: purple;
  color: white;
  font-weight: bold;
  padding: 4px 8px;
  border-radius: 4px;
  position: absolute;
  top: -20px;
  left: -10px;
}
.custom-radio {
  color: black;
}

.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

</style>
