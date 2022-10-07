<template>
  <div class="page">
    <CardComponent
        :cvc="123"
        :full_name="full_name"
        :MM="MM" :YY="YY"/>
    <form>
      <div class="card-info">
        <label for="card-holder">CARDHOLDER NAME</label><br>
        <input type="text" id="card-holder" placeholder="e.g Jane Appleseed" required>
      </div>
      <div class="card-info">
        <label for="card-number">CARD NUMBER</label><br>
        <input type="text" id="card-number" placeholder="e.g 1234 5678 9123 0000" required>
      </div>
      <div class="date-cvv">
        <div class="labels">
          <label for="exp-date">EXP. DATE (MM/YY)</label>
          <label for="cvc">CVC</label>
        </div>
        <div class="input-wrapper">
          <input type="text" id="exp-date" placeholder="MM" required maxlength="2">
          <input type="text" placeholder="YY" required maxlength="2">
          <input type="text" id="cvc" placeholder="123" required maxlength="3">
        </div>
      </div>
      <button id="btn">Confirm</button>
    </form>
  </div>
</template>

<script>
import CardComponent from "@/components/CardComponent";
export default {
  name: "FormComponent",
  data(){
    return{
      full_name: "JANE APPLESEED",
      MM:"00",
      YY:"00"
    }
  },
  components:{
    CardComponent
  }
}
</script>

<style scoped>
@import "../assets/styles/base.css";
.page{
  display: flex;
  flex-direction: column;
  padding: 0;
  margin: 0;
  /*overflow-x: hidden;*/
}
form{
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 90vw;
  margin-top: 1rem;
}
label{
  color: var(--very-dark-violet);
  font-family: var(--font-fam);
  font-size: 13px;
}
input{
  border-radius: 5px;
  border: 1px solid var(--dark-gray-violet);
  color: var(--dark-gray-violet);
  font-size: var(--font-size);
  font-family: var(--font-fam);
  margin-top: .5rem;
  padding: .8rem 0 .8rem .5rem ;
  width: 100%;
}
input:focus{
  color: var(--very-dark-violet);
}


.input-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 3fr;
  gap: 1.5rem;
}

button{
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

</style>
