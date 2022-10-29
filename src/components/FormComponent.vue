<template>
  <div class="page">
    <CardComponent
        :cvc="card_details.CVC"
        :full_name="card_details.full_name"
        :MM="card_details.MM" :YY="card_details.YY"/>
    <div class="form-wrapper">
      <form v-if="validInput">
        <div class="card-info">
          <label for="card-holder">CARDHOLDER NAME</label><br>
          <input type="text" id="card-holder" placeholder="e.g Jane Appleseed" required v-model="card_details.full_name"
                 maxlength="50">
        </div>
        <div class="card-info">
          <label for="card-number">CARD NUMBER</label><br>
          <input type="number" id="card-number" placeholder="e.g 1234 5678 9123 0000" required maxlength="16" :class="{error:errors.cardNumberError}">
        </div>
        <div class="date-cvv">
          <div class="labels">
            <label for="exp-date">EXP. DATE (MM/YY)</label>
            <label for="cvc">CVC</label>
          </div>
          <div class="input-wrapper">
            <input type="number" id="exp-date" placeholder="MM" required maxlength="2" v-model="card_details.MM"
                   :class="{error: errors.dateError}">

            <input type="number" placeholder="YY" required maxlength="2" v-model="card_details.YY"
                   :class="{error: errors.dateError}">
            <input type="number" id="cvc" placeholder="123" maxlength="3" v-model="card_details.CVC" required
                   :class="{error:errors.CVCError}">
          </div>
        </div>
        <button type="button" id="btn" @click="validation">Confirm</button>
      </form>
      <div class="complete-state" v-else>
        <img src="../assets/icon-complete.svg" alt="Complete">
        <h1>THANK YOU</h1>
        <p>We've added your card details</p>
        <button type="button">Continue</button>
      </div>
    </div>
  </div>
</template>

<script>
import CardComponent from "@/components/CardComponent";
import dayjs from "dayjs";
import localizeFormat from "dayjs/plugin/localizedFormat"

export default {
  name: "FormComponent",
  data() {
    return {
      card_details: {
        full_name: "",
        MM: "",
        YY: "",
        CVC: "",
      },
      errors: {
        nameError: false,
        cardNumberError: false,
        dateError: false,
        CVCError: false
      },
      validInput: true
    }
  },
  components: {
    CardComponent
  },
  computed: {},
  methods: {
    validation(){
      dayjs.extend(localizeFormat)
      //const currentMonth = dayjs.format("MM");
      const currentYear =parseInt(dayjs.format('YY'));
      //let getMonth =(int) this.card_details.MM;
      let getYear = this.card_details.YY;
      if(getYear<currentYear)
      {
        this.errors.dateError=true;
      }

    },
  }
}
</script>

<style scoped>
@import "../assets/styles/base.css";

.page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  /*align-items: center;*/
  padding: 0;
  margin: 0;
  /*overflow-x: hidden;*/
}

form {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 90vw;
  margin-top: 1rem;
}

label {
  color: var(--very-dark-violet);
  font-family: var(--font-fam);
  font-size: 13px;
}

.labels {
  display: grid;
  grid-template-columns: 2fr 3fr;
  gap: 3rem;
}

input {
  border-radius: 5px;
  border: 1px solid var(--light-graysh-violet);
  color: var(--dark-gray-violet);
  font-size: var(--font-size);
  font-family: var(--font-fam);
  margin-top: .5rem;
  padding: .8rem 0 .8rem .5rem;
  width: 100%;
}
input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

input:focus {
  color: var(--very-dark-violet);
  border: 1px solid var(--very-dark-violet);
  outline: none;
}

.input-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 3fr;
  gap: 1.5rem;
}

button {
  border: none;
  border-radius: 7px;
  background-color: var(--very-dark-violet);
  color: var(--white);
  font-size: var(--font-size);
  font-family: var(--font-fam);
  margin-top: 1.5rem;
  width: 100%;
  padding: 1rem;
}

.error {
  border-color: var(--red);
}

.complete-state{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
  max-height: fit-content;
  padding: 1rem;
  font-family: var(--font-fam);
}

.complete-state > h1 {
  color: var(--very-dark-violet);
  font-weight: 500;
}
.complete-state > p {
  color:var(--light-graysh-violet);
}

@media screen and (min-width: 900px) {
  .page {
    display: grid;
    grid-template-columns: 1fr 3fr;
    height: 100vh;
  }

  form {
    max-width: 10cm;
  }

  .form-wrapper {
    width: 100%;
    height: 100%;
    display: grid;
    place-items: center;
  }
}

</style>
