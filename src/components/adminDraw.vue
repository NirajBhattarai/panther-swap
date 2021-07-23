<template>
  <div class="grid__wrapper">
    <div class="grid_col_1">
      <PantherTable />
    </div>
    <div class="grid_col_2">
      <AdminUnlockWallet />
    </div>
  </div>
</template>

<script>
import PantherTable from "./cards/pantherTable.vue";
import AdminUnlockWallet from "./cards/adminUnlockWallet.vue";

export default {
  name: "AdminDraw",
  components: {
    PantherTable,
    AdminUnlockWallet
  }
};
</script>

<style scoped>
.grid__wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-top: 2rem;
}
.grid_col_1,
.grid_col_2 {
  width: calc(50% - 1rem);
}
</style>