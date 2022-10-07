<template>
  <div class="container">
    <div class="back-card-container">
      <img class="card-back" src="../assets/bg-card-back.png" alt="Back card">
      <p class="cvc">{{ isDefaultValue(cvc) ? '000' : cvc }}</p>
    </div>
    <div class="front-card-container">
      <img class="card-front" src="../assets/bg-card-front.png" alt="Front card">
      <div class="card-details">
        <div class="circle-wrapper">
          <div id="full-circle"></div>
          <div id="empty-circle"></div>
          <div id="card-number-wrapper">
            <span>0000</span>
            <span>0000</span>
            <span>0000</span>
            <span>0000</span>
          </div>
          <div id="name-exp-date">
            <div class="name-date">{{ isDefaultValue(full_name) ? 'JANE APPLESEED' :full_name }}</div>
            <div class="name-date">{{ isDefaultValue(MM) ? '00' : MM }}/{{ isDefaultValue(YY) ? '00' : YY }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: "CardComponent",
  props: {
    "cvc": {
      type: String
    },
    "full_name": {
      type: String
    },
    "MM": {
      type: String
    },
    "YY": {
      type: String
    }
  },
  methods: {
    isDefaultValue(s) {
      return s.length === 0;
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
}

.back-card-container {
  position: relative;
  width: fit-content;
  height: fit-content;
}

.cvc {
  position: absolute;
  color: var(--white);
  font-family: var(--font-fam);
  font-size: var(--font-size);
  right: 120px;
  z-index: 1;
  top: 5.7rem;
}

.card-back {
  scale: .6;
}

/*^back card*/


.front-card-container {
  position: relative;

}

.card-front {
  scale: .6;
  position: absolute;
  left: -4.5rem;
  top: -10.4rem;
}

.card-details {
  position: absolute;
  top: 0;
}

.circle-wrapper {
  position: relative;
  top: -6.5rem;
  left: 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  height: 40px;
}

#full-circle {
  height: 35px;
  width: 35px;
  border-radius: 50%;
  background-color: var(--white);
}

#empty-circle {
  height: 15px;
  width: 15px;
  border-radius: 50%;
  border: 2px solid var(--white);
}

#card-number-wrapper {
  bottom: -50px;
  display: inline-flex;
  justify-content: center;
  color: var(--white);
  font-family: var(--font-fam);
  font-size: 13px;
  gap: .5em;
  position: absolute;
}

#card-number-wrapper > span {
  font-size: var(--font-size);
}

#name-exp-date {
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  width: 250px;
  color: var(--white);
  font-family: var(--font-fam);
  font-size: 13px;
  position: absolute;
  bottom: -80px;
}

</style>
