<template>
  <base-layout>
    <div class="d-flex flex-column">
      <v-row>
        <v-col cols="12" md="12" sm="12">
          <h1 class="title">Клиенты этой группы</h1>
          <v-data-table
            class="col-lg-12 col-md-12 col-sm-12 font-weight-bold"
            :headers="headers"
            :items="conditionItem2"
            hide-default-footer
          >
            <template v-slot:item.action="{item}">
              <v-icon small @click="deleteItem(item)">mdi-close</v-icon>
            </template>
          </v-data-table>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="12" sm="12">
          <div
            class="add-client d-flex flex-column flex-lg-row flex-md-row flex-sm-row justify-space-around justify-md-start align-center col-lg-10 flex-wrap flex-md-nowrap"
          >
            <div class="select-block col-lg-7 col-md-5 col-sm-5">
              <v-select
                v-model="selectedItem"
                :items="conditionItem"
                item-text="name"
                label="Выбрать из списка"
                outlined
              ></v-select>
            </div>
            <v-btn
              class="mt-n8 add flex-wrap align-center col-lg-2 col-md-2 col-sm-2 mr-md-12"
              height="57px"
              outlined
              color="primary"
              @click="addClient()"
            >Добавить</v-btn>
            <p
              class="ma-0 mt-lg-n8 body-2 font-weight-bold mt-md-n9 mt-sm-n8 mt-10 mr-md-12 pr-md-12"
            >или</p>
            <v-btn
              text
              small
              class="new-client-create ma-0 mt-lg-n8 font-weight-bold body-2 mt-md-n9 ml-md-n12 mt-sm-n8 mt-4"
            >Создать нового клиента</v-btn>
          </div>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="12" sm="12">
          <p
            class="ma-0 font-weight-bold body-2 text-md-center text-lg-left text-sm-center text-center"
          >
            Для того, чтобы отредактировать или удалить клиентов из списка, перейдите в раздел
            <v-btn text class="white-lists pa-0 font-weight-bold">Белые списки</v-btn>
          </p>
          <v-btn
            height="50px"
            class="save-changes font-weight-bold body-2 mt-8 col-lg-3 col-md-3"
            raised
            color="primary"
          >Сохранить изменения</v-btn>
        </v-col>
      </v-row>
    </div>
  </base-layout>
</template>

<script>
import BaseLayout from "./BaseLayout";
export default {
  components: {
    BaseLayout
  },
  data: () => ({
    //Выбранный option по умолчанию.
    selectedItem: "Клиент-1",
    //Заголовки столбцов таблицы.
    headers: [
      { text: "ФИО", align: "left", value: "name", sortable: false },
      { text: "НОМЕР ТЕЛЕФОНА", value: "phone", sortable: false },
      { text: "ГРУППА", value: "group", sortable: false },
      { text: "", value: "action", sortable: false }
    ],
    //Массив клиентов передаваемый в select
    clientArray: [
      {
        name: "Клиент-1",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-2",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-3",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-4",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-5",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-6",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-7",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-8",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-9",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      },
      {
        name: "Клиент-10",
        phone: "+7 (912) 632-32-32",
        group: "ГАЗПРОМ",
        enable: false
      }
    ]
  }),
  computed: {
    //Метод возвращающий в select элементы у которых enable = false.
    conditionItem() {
      return this.clientArray.filter(item => !item.enable);
    },
    //Метод возвращающий в таблицу элементы у которых enable = true.
    conditionItem2() {
      return this.clientArray.filter(item => item.enable);
    }
  },
  methods: {
    //Метод удаления элемента из таблицы.
    deleteItem(item) {
      const index = this.clientArray.indexOf(item);
      if (confirm("Действительно хотите удалить?")) {
        this.clientArray[index].enable = false;
      }
    },
    //Метод добавления элемента в таблицу.
    addClient() {
      this.clientArray = this.clientArray.map(item => {
        if (item.name === this.selectedItem) {
          item.enable = true;
        }
        return item;
      });
    }
  }
};
</script>