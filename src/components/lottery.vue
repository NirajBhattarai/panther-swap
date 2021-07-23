<template>
  <div class="lottery_wrapper">
    <div class="col1">
      <h4 class="heading">The PANTHER Lottery</h4>
      <p class="title" style="margin-top: 1rem">Buy tickets with PANTHER</p>
      <p class="title">Win if 2, 3 or 4 of your ticket numbers match!</p>
    </div>
    <div class="col2">
      <div class="progress_col2_wrapper">
      <div class="progress_wrapper">
        <div class="inner_wrapper"></div>
      </div>
      <h2 class="time_details">
        <span>0h, 23m</span>
        Until ticket sale
      </h2>
      <p class="subTitle">0h, 21m Until lottery draw</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Lottery"
};
</script>

<style scoped lang="scss">
@import "../theme/scss/variables.scss";
.lottery_wrapper {
  background: linear-gradient(
    139.73deg,
    #182233 0%,
    #243E6D 100%
  );
  padding: 3.5rem 4rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  margin: 2rem;
  border-radius: 1.375rem;
}
.progress_col2_wrapper{
  max-width: 35.75rem;
  margin-left: auto;
}
.col1 {
  width: calc(50% - 7.687rem/2);
  box-shadow: 5px 5px 20px #FF0000;
  background: linear-gradient(to bottom right, #182233,  #243E6D);
  border-radius: 1.375rem;
  padding: 2.125rem;
}
.col2 {
   width: calc(50% - 7.687rem/2);
}
.heading {
  color: $darkPink;
  font-size: 1.5rem;
}
.title {
  font-size: 1rem;
  font-weight: 600;
  color: $white;
}
.progress_wrapper {
  background-color: $darkGray;
  border-radius: 1rem;
  height: 1rem;
}
.inner_wrapper {
  background-color: $darkPink;
  width: 70%;
  border-radius: 1rem;
  height: 1rem;
}
.time_details {
  margin-top: 1rem;
  color: $white;
  text-align: center;
  & span {
    color: $darkPink;
  }
}
.subTitle {
  font-size: 1rem;
  color: $white;
  text-align: center;
}
</style>