<template>
  <form class="form" @submit.prevent="handleSubmit">
    <CustomSelect :items="cities"
      v-model="city"
      class="form__select" />
    <CustomInput v-model="price"
      placeholder="Цена, от" />
    <SubmitButton class="form__submit"
      type="submit">Подбор жилья</SubmitButton>
  </form>
</template>

<script>
import CustomInput from "../shared/CustomInput";
import CustomSelect from "../shared/CustomSelect";
import SubmitButton from "../ButtonOne.vue";
export default {
  name: "ApartmentsFilterForm",
  components: {
    CustomInput,
    CustomSelect,
    SubmitButton,
  },
  data() {
    return {
      price: "",
      city: "",
    };
  },
  computed: {
    cities() {
      return [
        { value: "", label: "Город", selected: true },
        "Kyiv",
        "Odesa",
        "Poltava",
        "Kharkiv",
        "Dnipro",
        "Lviv",
        "Kherson",
        "Mariupol",
      ];
    },
  },
  methods: {
    handleSubmit() {
      this.$emit("submit", { city: this.city, price: this.price });
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  display: flex;

  &__select {
    margin-right: 30px;
  }

  &__submit {
    margin-left: auto;
  }
}
</style>
