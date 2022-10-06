<template>
  <div class="container">
    <div class="back-card-container">
      <img class="card-back" src="../assets/bg-card-back.png" alt="Back card">
      <p class="cvv">{{cvc}}</p>
    </div>
    <div class="front-card-container">
      <img class="card-front" src="../assets/bg-card-front.png" alt="Front card">
      <div class="card-details">
        <div class="circle-wrapper">
          <div id="full-circle"></div>
          <div id="empty-circle"></div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: "CardComponent",
  props: {
    "cvc":{
      type:String
    }
  }
}
</script>

<style scoped>
@import "../assets/styles/base.css";

.container {
  background-image: url("../assets/bg-main-mobile.png");
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  flex-direction: column;
  position: relative;
  /*max-width: 100vw;*/
}
.back-card-container{
  position: relative;
  width: 100vw;
  height: fit-content;
}
.cvv{
  position: absolute;
  color: var(--white);
  font-family: var(--font-fam);
  font-size: var(--font-size);
  right: 3rem;
  z-index: 1;
  top: 5.7rem;
}
.card-back{
  scale: .6;
}

/*^back card*/


.front-card-container{
  position: relative;

}
.card-front{
  scale: .6;
  position: absolute;
  left: -4.5rem;
  top: -10.4rem;
}
.card-details{
  position: absolute;
  top: 0;
}
.circle-wrapper{
  position: relative;
  top: -6.5rem;
  left: 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  height: 40px;
}
#full-circle{
  height: 40px;
  width: 40px;
  border-radius: 50%;
  background-color: var(--white);
}
#empty-circle{
  height: 20px;
  width: 20px;
  border-radius: 50%;
  border: 2px solid var(--white);
}

</style>
