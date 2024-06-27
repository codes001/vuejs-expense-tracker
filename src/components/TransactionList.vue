<template>
  <h3>History</h3>
  <ul id="list" class="list">
    //CLASSES TO BE MADE DYNAMIC
    <!-- <li class="minus">
      Cash <span> -$400</span>
      <button class="delete-btn">X</button>
    </li>

    <li class="plus">
      Paycheck <span> $230</span>
      <button class="delete-btn">X</button>
</li> -->
  </ul>
</template>

<script>
export default {
  data() {
    return {
      //Transactions array should be empty by default
      transactions: [],
    };
  },
};
</script>
