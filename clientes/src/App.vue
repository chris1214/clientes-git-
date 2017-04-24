<template>
    <v-app top-toolbar>
        <header>
            <v-toolbar>
                <v-toolbar-side-icon/>
                <v-toolbar-title>Clientes</v-toolbar-title>
            </v-toolbar>
        </header>
        <main>
            <v-content class="grey lighten-3">
                <v-container>

                    <!-- Clientes Cadastrados -->

                     <v-row>
                        <v-col xs12>
                            <p class="grey--text lighten-2 pl-4 ml-2">Clientes cadastrados</p>
                        </v-col>
                    </v-row>

                    <v-card>
                        <v-data-table
                                v-bind:headers="headers"
                                v-model="items"
                                class="elevation-1"
                        >
                            <template slot="items" scope="props">
                                <td>{{ props.item.contratante }}</td>
                                <td>{{ props.item.documento }}</td>
                                <td>{{ props.item.nome }}</td>
                                <td>
                                    <p v-bind:class="[props.item.alert]">
                                        {{ props.item.status }}
                                    </p>
                                </td>
                                <td class="text-xs-right">
                                    <v-btn icon="icon" class="grey--text">
                                        <v-icon>create</v-icon>
                                    </v-btn>
                                    <v-btn icon="icon" class="grey--text">
                                        <v-icon>more_vert</v-icon>
                                    </v-btn>
                                </td>
                            </template>
                        </v-data-table>
                    </v-card>

                    <!-- END Clientes Cadastrados -->

                    <!-- modal -->
                    <v-dialog v-model="detalhesB">
                        <v-card-row>
                            <v-card-title>
                                Detalhes
                            </v-card-title>
                        </v-card-row>
                        <v-card-row>
                            <v-card-text>
                                <v-row>
                                    <v-col xs12>
                                        <p>Nome</p>
                                        <p><b>christopher</b></p>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <p>Validado no Workfinity?</p>
                                        <p class="green--text">Sim</p>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <p>Status</p>
                                        <p class="green--text">Habilitado</p>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <p>Nome do Usuario</p>
                                        <p><b>Christopher</b></p>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <p>Email</p>
                                        <p><b>Christopher@hotmail.com</b></p>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12 class="text-aling-right">
                                        <v-btn primary>FECHAR</v-btn>
                                    </v-col>
                                </v-row>
                            </v-card-text>
                        </v-card-row>
                    </v-dialog>

                    <v-dialog v-model="formularioB">

                        <v-card-row>
                            <v-card-title>Formulario</v-card-title>
                        </v-card-row>

                        <v-card-row>
                            <v-card-text>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Nome" label="Nome"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-select
                                                v-bind:items="valido"
                                                v-model="valor"
                                                label="Validado no Workfinity?"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Usuario" label="Nome do Usuario"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-select
                                                v-bind:items="status"
                                                v-model="stato"
                                                label="Status"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Senha" label="Senha" type="password"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12 class="text-aling-right ">
                                        <v-btn primary>ENVIAR</v-btn>
                                        <v-btn primary>CANCELAR</v-btn>
                                    </v-col>
                                </v-row>
                            </v-card-text>
                        </v-card-row>
                    </v-dialog>

                    <v-dialog v-model="formularioCssM">
                        <v-card-row>
                            <v-card-title>Formulario</v-card-title>
                        </v-card-row>
                        <v-card-row>
                            <v-card-text>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Nome" label="Nome"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-select
                                                v-bind:items="valido"
                                                v-model="valor"
                                                label="Validado no Workfinity?"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Usuario" label="Nome do Usuario"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-select
                                                v-bind:items="status"
                                                v-model="stato"
                                                label="Status"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Senha" label="Senha" type="password"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12 class="text-aling-right ">
                                        <v-btn primary>ENVIAR</v-btn>
                                        <v-btn primary>CANCELAR</v-btn>
                                    </v-col>
                                </v-row>
                            </v-card-text>
                        </v-card-row>
                    </v-dialog>

                    <v-dialog v-model="detalhes">

                        <v-toolbar class="primary">
                            <v-icon class="white--text">info</v-icon>
                            <v-toolbar-title>Detalhes</v-toolbar-title>
                            <v-spacer></v-spacer>
                            <v-btn icon="icon" v-on:click.native="detalhes = false">
                                <v-icon>close</v-icon>
                            </v-btn>
                        </v-toolbar>

                        <v-list two-line>
                            <v-list-item>
                                <v-list-tile>

                                    <v-list-tile-action>
                                        <v-icon>star</v-icon>
                                    </v-list-tile-action>

                                    <v-list-tile-content>
                                        <v-list-tile-sub-title>
                                            Nome
                                        </v-list-tile-sub-title>
                                        <v-list-tile-title>
                                            christopher
                                        </v-list-tile-title>
                                    </v-list-tile-content>
                                </v-list-tile>
                                <v-divider inset></v-divider>
                            </v-list-item>

                            <v-list-item>
                                <v-list-tile>
                                    <v-list-tile-action>
                                    </v-list-tile-action>
                                    <v-list-tile-content>
                                        <v-list-tile-sub-title>
                                            Validado no Workfinity?
                                        </v-list-tile-sub-title>
                                        <v-list-tile-title>
                                            Sim
                                        </v-list-tile-title>
                                    </v-list-tile-content>
                                </v-list-tile>
                                <v-divider inset></v-divider>
                            </v-list-item>

                            <v-list-item>
                                <v-list-tile>
                                    <v-list-tile-content>
                                        <v-list-tile-sub-title>
                                            Status
                                        </v-list-tile-sub-title>
                                        <v-list-tile-title>
                                            Habilitado
                                        </v-list-tile-title>
                                    </v-list-tile-content>
                                </v-list-tile>
                                <v-divider inset></v-divider>
                            </v-list-item>

                            <v-list-item>
                                <v-list-tile>
                                    <v-list-tile-content>
                                        <v-list-tile-sub-title>
                                            Nome do Usuario
                                        </v-list-tile-sub-title>
                                        <v-list-tile-title>
                                            Christopher
                                        </v-list-tile-title>
                                    </v-list-tile-content>
                                </v-list-tile>
                                <v-divider inset></v-divider>
                            </v-list-item>

                            <v-list-item>
                                <v-list-tile>
                                    <v-list-tile-content>
                                        <v-list-tile-sub-title>
                                            Email
                                        </v-list-tile-sub-title>
                                        <v-list-tile-title>
                                            Christopher@hotmail.com
                                        </v-list-tile-title>
                                    </v-list-tile-content>
                                </v-list-tile>
                            </v-list-item>

                        </v-list>
                    </v-dialog>

                    <v-dialog v-model="formulario">
                        <v-card-row>

                            <v-toolbar class="primary">
                                <v-icon class="white--text">edit</v-icon>
                                <v-toolbar-title>Formulario</v-toolbar-title>
                                <v-spacer></v-spacer>
                                <v-btn icon="icon" v-on:click.native="formulario = false">
                                    <v-icon>close</v-icon>
                                </v-btn>
                            </v-toolbar>
                        </v-card-row>
                        <v-card-row>

                            <v-card-text>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Nome" label="Nome" prepend-icon="edit"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-select
                                                v-bind:items="valido"
                                                v-model="valor"
                                                label="Validado no Workfinity?"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Usuario" label="Nome do Usuario"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-select
                                                v-bind:items="status"
                                                v-model="stato"
                                                label="Status"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs12>
                                        <v-text-field name="Senha" label="Senha" type="password"/>
                                    </v-col>
                                </v-row>
                            </v-card-text>
                            <v-divider/>
                            <v-card-text>
                                <v-row>
                                    <v-col xs12 class="text-aling-right ">
                                        <v-btn primary>ENVIAR</v-btn>
                                    </v-col>
                                </v-row>
                            </v-card-text>
                        </v-card-row>
                    </v-dialog>

                    <v-dialog class="modal-medium" v-model="formulario2Col">
                        <v-card-row>

                            <v-toolbar class="primary">
                                <v-icon class="white--text">edit</v-icon>
                                <v-toolbar-title>Formulario</v-toolbar-title>
                                <v-spacer></v-spacer>
                                <v-btn icon="icon" v-on:click.native="formulario = false">
                                    <v-icon>close</v-icon>
                                </v-btn>
                            </v-toolbar>

                        </v-card-row>
                        <v-card-row>

                            <v-card-text>
                                <v-row>
                                    <v-col xs6>
                                        <v-text-field name="Nome" label="Nome" prepend-icon="edit"/>
                                    </v-col>
                                    <v-col xs6>
                                        <v-select
                                                v-bind:items="valido"
                                                v-model="valor"
                                                label="Validado no Workfinity?"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>

                                <v-row>
                                    <v-col xs6>
                                        <v-text-field name="Usuario" label="Nome do Usuario"/>
                                    </v-col>
                                    <v-col xs6>
                                        <v-select
                                                v-bind:items="status"
                                                v-model="stato"
                                                label="Status"
                                                item-value="text"/>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col xs6>
                                        <v-text-field name="Senha" label="Senha" type="password"/>
                                    </v-col>
                                    <v-col xs6>
                                        <v-text-field name="Email" label="Email" type="e-mail"/>
                                    </v-col>
                                </v-row>

                                <v-row class="text-aling-right">
                                    <v-col xs12>
                                        <v-btn primary>ENVIAR</v-btn>
                                    </v-col>
                                </v-row>

                            </v-card-text>
                        </v-card-row>
                    </v-dialog>

                    <v-dialog class="modal-medium" v-model="detalhes2Col">

                        <v-toolbar class="primary">
                            <v-icon class="white--text">info</v-icon>
                            <v-toolbar-title>Detalhes</v-toolbar-title>
                            <v-spacer></v-spacer>
                            <v-btn icon="icon" v-on:click.native="detalhes = false">
                                <v-icon>close</v-icon>
                            </v-btn>
                        </v-toolbar>

                        <v-list two-line>
                            <v-row>
                                <v-col xs6>
                                    <v-list-item>
                                        <v-list-tile>
                                            <v-list-tile-action>
                                                <v-icon>star</v-icon>
                                            </v-list-tile-action>

                                            <v-list-tile-content>
                                                <v-list-tile-sub-title>
                                                    Nome
                                                </v-list-tile-sub-title>
                                                <v-list-tile-title>
                                                    christopher
                                                </v-list-tile-title>
                                            </v-list-tile-content>
                                        </v-list-tile>
                                        <v-divider inset></v-divider>
                                    </v-list-item>
                                </v-col>
                                <v-col xs6>
                                    <v-list-item>
                                        <v-list-tile>
                                            <v-list-tile-action>
                                            </v-list-tile-action>
                                            <v-list-tile-content>
                                                <v-list-tile-sub-title>
                                                    Validado no Workfinity?
                                                </v-list-tile-sub-title>
                                                <v-list-tile-title>
                                                    Sim
                                                </v-list-tile-title>
                                            </v-list-tile-content>
                                        </v-list-tile>
                                        <v-divider></v-divider>
                                    </v-list-item>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col xs6>
                                    <v-list-item>
                                        <v-list-tile>
                                            <v-list-tile-content>
                                                <v-list-tile-sub-title>
                                                    Status
                                                </v-list-tile-sub-title>
                                                <v-list-tile-title>
                                                    Habilitado
                                                </v-list-tile-title>
                                            </v-list-tile-content>
                                        </v-list-tile>
                                        <v-divider></v-divider>
                                    </v-list-item>
                                </v-col>
                                <v-col xs6>
                                    <v-list-item>
                                        <v-list-tile>
                                            <v-list-tile-content>
                                                <v-list-tile-sub-title>
                                                    Nome do Usuario
                                                </v-list-tile-sub-title>
                                                <v-list-tile-title>
                                                    Christopher
                                                </v-list-tile-title>
                                            </v-list-tile-content>
                                        </v-list-tile>
                                        <v-divider></v-divider>
                                    </v-list-item>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col xs6>
                                    <v-list-item>
                                        <v-list-tile>
                                            <v-list-tile-content>
                                                <v-list-tile-sub-title>
                                                    Email
                                                </v-list-tile-sub-title>
                                                <v-list-tile-title>
                                                    Christopher@hotmail.com
                                                </v-list-tile-title>
                                            </v-list-tile-content>
                                        </v-list-tile>
                                    </v-list-item>
                                </v-col>
                                <v-col xs6>
                                    <v-list-item>
                                        <v-list-tile>
                                            <v-list-tile-content>
                                                <v-list-tile-sub-title>
                                                    Email
                                                </v-list-tile-sub-title>
                                                <v-list-tile-title>
                                                    Christopher@hotmail.com
                                                </v-list-tile-title>
                                            </v-list-tile-content>
                                        </v-list-tile>
                                    </v-list-item>
                                </v-col>
                            </v-row>
                        </v-list>
                    </v-dialog>

                    <v-dialog v-model="dialogForm" class="dialog-medium">

                        <v-card-row>
                            <v-toolbar class="primary">
                                <v-icon class="white--text">edit</v-icon>
                                <v-toolbar-title>Formulario</v-toolbar-title>
                                <v-spacer></v-spacer>
                                <v-btn icon="icon" v-on:click.native="dialogForm = false">
                                    <v-icon>close</v-icon>
                                </v-btn>
                            </v-toolbar>
                        </v-card-row>

                        <v-card-row>
                            <v-card-text>
                                <v-container fluid>
                                    <v-text-field label="Email" required/>
                                    <v-text-field label="Password" type="password" required/>
                                    <v-text-field label="Legal first name" required/>
                                    <v-text-field label="Legal middle name"/>
                                    <v-text-field label="Legal last name" required/>
                                    <small>*indicates required field</small>
                                </v-container>
                            </v-card-text>
                        </v-card-row>
                        <v-card-row actions>
                            <!--<v-btn class="green&#45;&#45;text darken-1" flat="flat" @click.native="d2 = false">Disagree</v-btn>-->
                            <v-btn class="primary--text darken-1" flat="flat" @click.native="d2 = false">Agree</v-btn>
                        </v-card-row>
                    </v-dialog>

                    <!-- END modal -->

                    <!-- Novo Cliente -->

                    <!--<v-row>
                        <v-col xs12>
                            <p class="grey&#45;&#45;text lighten-2 pl-3">Novo Cliente</p>
                        </v-col>
                    </v-row>

                    <v-card>
                        <v-card-text>
                            <v-row>
                                <v-col xs4>
                                    <v-text-field name="Nome" label="Nome"/>
                                </v-col>
                                <v-col xs4>
                                    <v-select
                                            v-bind:items="valido"
                                            v-model="valor"
                                            label="Validado no Workfinity?"
                                            item-value="text"/>
                                </v-col>
                                <v-col xs4>
                                    <v-select
                                            v-bind:items="status"
                                            v-model="stato"
                                            label="Status"
                                            item-value="text"/>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col xs4>
                                    <v-text-field name="Usuario" label="Nome do Usuario"/>
                                </v-col>
                                <v-col xs4>
                                    <v-text-field name="Senha" label="Senha" type="password"/>
                                </v-col>
                                <v-col xs4>
                                    <v-text-field name="Email" label="Email" type="e-mail"/>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col xs3>
                                    <v-select
                                            v-bind:items="documento"
                                            v-model="tipo"
                                            label="Tipo de Documento"
                                            item-value="text"
                                    />
                                </v-col>
                                <v-col xs3>
                                    <v-text-field name="documento" label="Número do Documento"/>
                                </v-col>
                                <v-col xs3>
                                    <v-select
                                            v-bind:items="contratante"
                                            v-model="TipoContratante"
                                            label="Tipo do Contratante"
                                            item-value="text"
                                    />
                                </v-col>
                                <v-col xs3>
                                    <v-text-field name="cep" label="CEP"/>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col xs12 sm6>
                                    <v-menu
                                            :close-on-content-click="false"
                                    >
                                        <v-text-field
                                                slot="activator"
                                                label="Data"
                                                v-model="e3"
                                        ></v-text-field>
                                        <v-date-picker v-model="e3" no-title scrollable actions>
                                            <template scope="{ save, cancel }">
                                                <v-card-row actions>
                                                    <v-btn flat primary @click.native="cancel()">Cancel</v-btn>
                                                    <v-btn flat primary @click.native="save()">Save</v-btn>
                                                </v-card-row>
                                            </template>
                                        </v-date-picker>
                                    </v-menu>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col class="text-aling-right" xs12>
                                    <v-btn primary>ENVIAR</v-btn>
                                    <v-btn primary>VOLTAR</v-btn>
                                </v-col>
                            </v-row>
                        </v-card-text>
                    </v-card>-->

                    <!-- END Novo Cliente -->

                    <!-- Detalhes -->

                    <!--<v-row>
                        <p class="grey&#45;&#45;text lighten-2 pl-4">Detalhes</p>
                    </v-row>

                    <v-card>
                        <v-card-text>
                            <v-row>
                                <v-col xs4>
                                    <p>Nome</p>
                                    <p><b>Gustavo</b></p>
                                </v-col>
                                <v-col xs4>
                                    <p>Validado no Workfinity?</p>
                                    <p class="green&#45;&#45;text">Sim</p>
                                </v-col>
                                <v-col xs4>
                                    <p>Status</p>
                                    <p class="green&#45;&#45;text">Habilitado</p>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col xs4>
                                    <p>Nome do Usuario</p>
                                    <p><b>Gustavo</b></p>
                                </v-col>
                                <v-col xs4>
                                    <p>Email</p>
                                    <p><b>Gustavo@hotmail.com</b></p>
                                </v-col>
                                <v-col xs4>
                                    <p>Contratante</p>
                                    <p><b>BANRISUL</b></p>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col xs4>
                                    <p>Tipo de documento</p>
                                    <p><b>CPF</b></p>
                                </v-col>
                                <v-col xs4>
                                    <p>Número do Documento</p>
                                    <p><b>99638266015</b></p>
                                </v-col>
                                <v-col xs4>
                                    <p>CEP</p>
                                    <p><b>22666999</b></p>
                                </v-col>
                            </v-row>
                            <v-row>
                                <v-col class="text-aling-right" xs12>
                                    <v-btn primary>Voltar</v-btn>
                                </v-col>
                            </v-row>
                        </v-card-text>
                    </v-card>-->

                    <!-- END Detalhes -->

                    <!-- detalhes com paginadores -->

                    <!--<v-row>
                        <p class="grey&#45;&#45;text lighten-2 pl-4">Detalhes</p>
                    </v-row>

                    <v-card>
                        <v-tabs
                          grow
                        >
                          <v-tab-item
                            v-bind:href="'#01'"
                            ripple
                            slot="activators"
                          >
                            Item 01
                          </v-tab-item>

                          <v-tab-content
                          v-bind:id=" '01' "
                            slot="content"
                          >
                            <v-card>
                              <v-card-text>
                                  <v-row>
                                      <v-col xs4>
                                          <p>Nome</p>
                                          <p><b>Gustavo</b></p>
                                      </v-col>
                                      <v-col xs4>
                                          <p>Validado no Workfinity?</p>
                                          <p class="green&#45;&#45;text">Sim</p>
                                      </v-col>
                                      <v-col xs4>
                                          <p>Status</p>
                                          <p class="green&#45;&#45;text">Habilitado</p>
                                      </v-col>
                                  </v-row>
                                  <v-row>
                                      <v-col xs4>
                                          <p>Nome do Usuario</p>
                                          <p><b>Gustavo</b></p>
                                      </v-col>
                                      <v-col xs4>
                                          <p>Email</p>
                                          <p><b>Gustavo@hotmail.com</b></p>
                                      </v-col>
                                      <v-col xs4>
                                          <p>Contratante</p>
                                          <p><b>BANRISUL</b></p>
                                      </v-col>
                                  </v-row>
                                  <v-row>
                                      <v-col xs4>
                                          <p>Tipo de documento</p>
                                          <p><b>CPF</b></p>
                                      </v-col>
                                      <v-col xs4>
                                          <p>Número do Documento</p>
                                          <p><b>99638266015</b></p>
                                      </v-col>
                                      <v-col xs4>
                                          <p>CEP</p>
                                          <p><b>22666999</b></p>
                                      </v-col>
                                  </v-row>
                                  <v-row>
                                      <v-col class="text-aling-right" xs12>
                                          <v-btn primary>Voltar</v-btn>
                                      </v-col>
                                  </v-row>
                              </v-card-text>
                            </v-card>
                          </v-tab-content>

                          <v-tab-item
                            v-bind:href="'#02'"
                            ripple
                            slot="activators"
                          >
                            Item 02
                          </v-tab-item>
                          <v-tab-content
                            v-bind:id=" '02' "
                            slot="content"
                          >
                            <v-card>
                              <v-card-text>
                                  conteudo 02
                              </v-card-text>
                            </v-card>
                          </v-tab-content>

                          <v-tab-item
                            v-bind:href="'#03'"
                            ripple
                            slot="activators"
                          >
                            Item 03
                          </v-tab-item>
                          <v-tab-content
                            v-bind:id=" '03' "
                            slot="content"
                          >
                            <v-card>
                              <v-card-text>
                                  conteudo 03
                              </v-card-text>
                            </v-card>
                          </v-tab-content>
                        </v-tabs>
                    </v-card>-->

                    <!-- END detalhes com aginadores -->


                    <!-- buttons -->
                    <!--<v-row>
                        <v-col xs12 class="text-aling-right">
                            <v-btn primary>Modal detalhes</v-btn>
                            <v-btn primary>Modal Form</v-btn>
                        </v-col>
                    </v-row>-->
                    <!-- END buttons -->

                </v-container>
            </v-content>
        </main>
    </v-app>
</template>

<script>
  export default {
    data () {
      return {
        item: {
          text: 'Get Started'
        },
        e3:"",
        dialogForm: true,
        detalhes2Col: false,
        formulario2Col: false,
        formulario: false,
        formularioB: false,
        formularioCssM: false,
        detalhes: false,
        detalhesB: false,
        valor:{},
        valido:[
            {text:'Sim'},
            {text:'Não'}
        ],
        stato:{},
        status:[
            {text:'Habilitado'},
            {text:'Desabilitado'}
        ],
        documento:[
            {text:'tipo 1'},
            {text:'tipo 2'},
            {text:'tipo 3'}
        ],
        tipo:{},
        contratante:[
            {text:'tipo 1'},
            {text:'tipo 2'},
            {text:'tipo 3'}
        ],
        TipoContratante:{},
        pagina: 1,
        headers: [
          {
           text: 'Contratante',
           left: true,
           value: 'name'
         },
         { text: 'Numero do documento',
           left: true,
           sortable: false,
           value: 'name'
         },
         { text: 'Nome',
           left: true,
           sortable: false,
           value: 'name'
         },
         { text: 'Status',
           left: true,
           sortable: false,
           value: 'name'
         },
         {  text:'',
            left: true,
            sortable: false,
            value: 'name'
         }
        ],
        items: [
          {
           contratante: 'BANRISUL',
           documento: '987',
           nome: 'gustavo',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '654',
           nome: 'Christopher',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '123',
           nome: 'Bianca',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '456',
           nome: 'Adriano',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '987',
           nome: 'gustavo',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '654',
           nome: 'Christopher',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '123',
           nome: 'Bianca',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '456',
           nome: 'Adriano',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '987',
           nome: 'gustavo',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '654',
           nome: 'Christopher',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '123',
           nome: 'Bianca',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '456',
           nome: 'Adriano',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '987',
           nome: 'gustavo',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '654',
           nome: 'Christopher',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '123',
           nome: 'Bianca',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '456',
           nome: 'Adriano',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '987',
           nome: 'gustavo',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '654',
           nome: 'Christopher',
           status: 'Desabilitado',
           alert: 'red--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '123',
           nome: 'Bianca',
           status: 'Habilitado',
           alert: 'green--text'
         },
         {
           contratante: 'BANRISUL',
           documento: '456',
           nome: 'Adriano',
           status: 'Desabilitado',
           alert: 'red--text'
         }
        ]
      }
    }
  }




</script>

<style lang="stylus">
    @import '../node_modules/vuetify/src/stylus/main'
    @import './css/main.css'
</style>
<style media="screen">
    .text-aling-right {
        text-align: right;
    }

    .pull-right {
        float: right;
    }

    .dialog__container .input-group {
        margin: 5px 0;
    }

    .dialog__container .card__title.primary {
        box-shadow: 0 2px 4px -1px rgba(0, 0, 0, 0.2), 0 4px 5px rgba(0, 0, 0, 0.14), 0 1px 10px rgba(0, 0, 0, 0.12);
    }
    .dialog__container.dialog-medium div.dialog--active {
        width: 800px;
    }
    .dialog__container.dialog-large  div.dialog--active {
        width: 1000px;
    }



</style>
