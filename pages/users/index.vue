<template>
  <div>
    <v-row>
      <v-col class="mx-auto" cols="12" sm="8" md="8">
        <v-simple-table
          fixed-header
          height="400px"
        >
          <thead>
            <tr>
              <th class="text-left">Nome</th>
              <th class="text-left">Username</th>
              <th class="text-center">Detalhes</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="user in users" :key="user.name">
              <td>{{ user.name }}</td>
              <td>{{ user.username }}</td>
              <td class="text-center">
                <v-icon small @click="details(user)">
                  mdi-account-details
                </v-icon>
              </td>
            </tr>
          </tbody>
        </v-simple-table>
      </v-col>
    </v-row>

    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="600px">
        <v-card>
          <v-card-title>
            <span class="text-h5">Detalhes do usuário</span>
          </v-card-title>

          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12" sm="6" md="6">
                  <h3>Nome:</h3>
                  <span> {{ userDetails.name }} </span>
                </v-col>
                <v-col cols="12" sm="6" md="6">
                  <h3>Username:</h3>
                  <span> {{ userDetails.username }} </span>
                </v-col>
                <v-col cols="12">
                  <h3>Email:</h3>
                  <a :href="`mailto:${userDetails.email}`">
                    {{ userDetails.email }}
                  </a>
                </v-col>
                <v-col cols="12" sm="6" md="6">
                  <h3>Telefone:</h3>
                  <span> {{ userDetails.phone }} </span>
                </v-col>
                <v-col cols="12" sm="6" md="6">
                  <h3>Site:</h3>
                  <a
                    :href="`http://${userDetails.website}`"
                    target="_blank"
                    rel="noopener noreferrer"
                    >{{ userDetails.website }}</a
                  >
                </v-col>

                <v-col cols="12" v-if="userDetails.address">
                  <v-expansion-panels>
                    <v-expansion-panel>
                      <v-expansion-panel-header
                        style="
                          color: rgba(0, 0, 0, 0.6);
                          font-size: 18px;
                          font-weight: 700;
                        "
                      >
                        Endereço
                      </v-expansion-panel-header>
                      <v-expansion-panel-content>
                        <v-row style="color: rgba(0, 0, 0, 0.6)">
                          <v-col cols="12" sm="6" md="6">
                            <h3>Rua:</h3>
                            <span>
                              {{ userDetails.address.street }}
                            </span>
                          </v-col>
                          <v-col cols="12" sm="6" md="6">
                            <h3>Apartamento:</h3>
                            <span> {{ userDetails.address.suite }} </span>
                          </v-col>
                          <v-col cols="12" sm="6" md="6">
                            <h3>Cidade:</h3>
                            <span> {{ userDetails.address.city }} </span>
                          </v-col>
                          <v-col cols="12" sm="6" md="6">
                            <h3>CEP:</h3>
                            <span>
                              {{ userDetails.address.zipcode }}
                            </span>
                          </v-col>
                        </v-row>
                      </v-expansion-panel-content>
                    </v-expansion-panel>
                  </v-expansion-panels>
                </v-col>

                <v-col cols="12" v-if="userDetails.company">
                  <v-expansion-panels>
                    <v-expansion-panel>
                      <v-expansion-panel-header
                        style="
                          color: rgba(0, 0, 0, 0.6);
                          font-size: 18px;
                          font-weight: 700;
                        "
                      >
                        Empresa
                      </v-expansion-panel-header>
                      <v-expansion-panel-content>
                        <v-row style="color: rgba(0, 0, 0, 0.6)">
                          <v-col cols="12" sm="6" md="6">
                            <h3>Nome:</h3>
                            <span> {{ userDetails.company.name }} </span>
                          </v-col>
                          <v-col cols="12" sm="6" md="6">
                            <h3>Slogan:</h3>
                            <span> {{ userDetails.company.catchPhrase }} </span>
                          </v-col>
                          <v-col cols="12" sm="6" md="6">
                            <h3>Estratégia de negócio:</h3>
                            <span> {{ userDetails.company.bs }} </span>
                          </v-col>
                        </v-row>
                      </v-expansion-panel-content>
                    </v-expansion-panel>
                  </v-expansion-panels>
                </v-col>
              </v-row>
            </v-container>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="#0D47A1" text @click="dialog = false"
              ><v-icon>mdi-close</v-icon> Fechar
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
export default {
  data: () => ({
    users: [],
    userDetails: {},
    dialog: false,
  }),

  async mounted() {
    await this.getAll();
  },

  methods: {
    async getAll() {
      try {
        const response = await this.$axios.$get("/users");

        this.users = response;
      } catch (error) {
        throw new Error(error);
      }
    },
    details(user) {
      this.userDetails = user;
      this.dialog = true;
    },
  },
};
</script>
<style>
  .v-data-table__wrapper {
    overflow-x: hidden !important;
  }
</style>
