<script setup>
import Illustration from "@/assets/images/Illustration.vue";
import StarIcon from "@/assets/images/StarIcon.vue";
import { ref, reactive, computed } from "vue";


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

console.log(numbers);

let ratingNumber = ref(NaN);

const selectedNum = (num) => {
  numbers.value.forEach((element) => {
    if (element.num === num) {
      element.selected = true;
      ratingNumber = element?.num;
    } else {
      element.selected = false;
    }
  });
};

const aaa = ref(false);

</script>

<template>
  <div class="card">
    <div class="card__rate" v-show="!aaa">
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
          :class="{ active: number?.selected }"
          @click="selectedNum(number?.num)"
          >{{ number?.num }}</span
        >
      </div>
      
      <button
        class="card__btn"
        @click="
          numbers?.find((el) => (el?.selected == true ? aaa = true : aaa))
        "
      >
        Submit
      </button>
    </div>

    <div class="card__thanks" v-show="aaa">
      <Illustration />
      <span class="card__thanks-rating"
        >You selected {{ ratingNumber }} out of 5</span
      >

      <div class="card__thanks-main">
        <h3 class="card__thanks-title">Thank you!</h3>

        <p class="card__thanks-txt">
          We appreciate you taking the time to give a rating. If you ever need
          more support, don’t hesitate to get in touch!
        </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.card {
  flex-shrink: 0;
  max-width: 412px;
  width: 100%;
  height: 416px;
  padding: 32px;
  background-image: var(--black-gradient);
  border-radius: 30px;

  &__rate {
    display: flex;
    gap: 15px;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;

    &.active {
      display: none;
    }
  }

  &__thanks {
    display: flex;
    gap: 15px;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    height: 100%;

    &.active {
      display: none;
    }

    &-rating {
      padding: 10px 15px;
      background: var(--darkColor);
      border-radius: 35px;
      color: var(--primaryColor);
    }

    &-main {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    &-title {
      color: var(--accentColor);
      text-align: center;

      font-size: 28px;
    }

    &-txt {
      text-align: center;
      color: var(--secondaryColor);
    }
  }

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
      transition: 150ms;

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
    transition: 150ms;

    &:hover {
      background: var(--accentColor);
      color: var(--primaryColor);
    }

    &:active {
      opacity: 0.6;
    }
  }
}
</style>
