<script setup>
import StarIcon from "@/assets/images/StarIcon.vue";
import { ref } from "vue";

const numbers = ref([
  {
    num: 1,
    id: 1,
    selected: false,
  },
  {
    num: 2,
    id: 2,
    selected: false,
  },
  {
    num: 3,
    id: 3,
    selected: false,
  },
  {
    num: 4,
    id: 4,
    selected: false,
  },
  {
    num: 5,
    id: 5,
    selected: false,
  },
]);


const selectedNum = (num) => {
  numbers.value.forEach((element) => {
    if (element.num === num) {
      element.selected = true;
    } else {
      element.selected = false;
    }
  });
};
</script>

<template>
  <div class="card">
    <div class="card__star">
      <StarIcon class="card__star-icon" />
    </div>

    <h3 class="card__title">How did we do?</h3>

    <p class="card__txt">
      Please let us know how we did with your support request. All feedback is
      appreciated to help us improve our offering!
    </p>

    <div class="card__rating">
      <span
        class="card__rating-num" 
        v-for="(number, index) in numbers"
        :key="index"
        :class="{'active': number?.selected}"
        @click="selectedNum(number?.num)"
        >{{ number?.num }}</span
      >
    </div>

    <button class="card__btn" >Submit</button>
  </div>
</template>

<style lang="scss">
.card {
  max-width: 412px;
  width: 100%;
  flex-shrink: 0;
  display: flex;
  gap: 15px;
  flex-direction: column;
  justify-content: space-between;
  max-width: 412px;
  width: 100%;
  min-height: 416px;
  padding: 32px;
  background-image: var(--black-gradient);
  border-radius: 30px;

  &__star {
    height: 48px;
    width: 48px;
    background: var(--darkColor);
    border-radius: 50%;
    display: grid;
    place-items: center;
  }

  &__title {
    color: var(--accentColor);
    font-size: 28px;
  }

  &__txt {
    color: var(--secondaryColor);
  }

  &__rating {
    display: flex;
    justify-content: space-between;

    &-num {
        height: 50px;
        width: 50px;
        border-radius: 50%;
        color: var(--secondaryColor);
        background: var(--darkColor);
        display: grid;
        place-items: center;
        cursor: pointer;
        font-weight: 700;

        &:hover {
            color: var(--accentColor);
            background: var(--mediumColor);
        }

        &.active {
            background: var(--primaryColor);
            color: var(--accentColor);
        }
    }
  }

  &__btn {
    border: 0;
    outline: 0;
    background: var(--primaryColor);
    padding: 15px;
    text-align: center;
    border-radius: 30px;
    cursor: pointer;
    color: var(--accentColor);
    text-transform: uppercase;
    font-size: 16px;
    font-weight: 700;
    letter-spacing: 3px;

    &:hover {
        background: var(--accentColor);
        color: var(--primaryColor);
    }
  }
}
</style>

<!-- 1 2 3 4 5 Submit You selected out of 5 Thank you! We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch! -->
