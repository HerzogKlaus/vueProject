<template>
  <div class="d-flex flex-column">
    <v-row>
      <v-col cols="12" md="12" sm="12">
        <v-list class="mt-n5">
          <v-list-item-group v-model="item">
            <v-list-item v-for="(item, i) in menuItems" :key="i" :to="item.href">
              <v-list-item-content>
                <v-list-item-title v-text="item.head" class="headline"></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-col>
    </v-row>
  </div>
</template>
<script>
export default {
  data: () => ({
    item: 1,
    menuItems: [{ head: "Клиенты", href: '/'}, { head: "Группы", href: '/GroupsView'}]
  })
};
</script>