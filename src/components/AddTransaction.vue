<template>
  <h3>Add new transaction</h3>
  <form>
    <div class="form-control">
      <label for="text">Text</label>
      <input type="text" id="text" placeholder="Add here..." v-model="text" />
    </div>
    <div class="form-control">
      <label for="amount">Amount <br /> </label>
      <input
        type="text"
        id="amount"
        placeholder="Enter amount..."
        v-model="amount"
      />
    </div>
    <button class="btn">Add</button>
  </form>
</template>
