<template>
  <div class="wrapper ">
    <br /><br />
    <div class="main main-raised margem">
      <div class="section section-contacts  ">
        <!-- <img src="../assets/img/cabecalhoFINAL2.png"> -->
        <div class="container">
          <div class="md-layout">
            <div
              class="md-layout-item md-size-100 md-xsmall-size-100 mx-auto margem1"
            >
              <h1 class=" text-center title text-responsive" id="cadastro">
                PRÉ-CADASTRO/RECADASTRO
              </h1>
              <p class="text-center description" style="font-size: 19px">
                <!-- fonte é de 18 e mudou para 19 -->
                Preencher ou marcar principalmente todos os itens obrigatórios.
                A efetivação do pré-cadastro/recadastro estará finalizada em até
                24 horas a contar da data de solicitação. A renovação de
                cadastro para alunos de graduação é semestral e para alunos de
                pós-graduação, técnicos administrativos e docentes da UFPA é
                anual. Observações sobre os anexos: Discentes: Atestado de
                matrícula atual (SIGAA) Servidores: Declaração de vínculo
                funcional (SAGITTA) ou carteira funcional (SIGEPE). O nome e a
                foto associados à sua Conta do Google formulário.
                <span class="roxo">
                  O tamanho dos arquivos não deve ultrapassar 2Mb. São aceitos
                  como arquivos PDF , PNG e JPEG. Todos os campos com * são
                  obrigatórios.
                </span>
              </p>
            </div>
          </div>
          <!-- inicio do formulário -->
          <form
            class="contact-form"
            enctype="multipart/form-data"
            onsubmit="setTimeout(function(){window.location.reload();},10);"
            name="formulario"
          >
            <!-- Área mobile -->
            <!-- Nome mobile -->
            <div class=" md-layout">
              <div class="md-layout-item md-size-100 mobile ">
                <md-field :class="isActive ? '' : 'md-error'">
                  <label
                    :class="isActive ? 'label' : ''"
                    aria-label="insira seu nome completo"
                    >Nome completo</label
                  >
                  <md-input
                    style="text-transform: capitalize"
                    v-model="$v.form.idName.$model"
                    id="name"
                    required
                    name="idName"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.idName.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.idName.required && errors">
                  Nome obrigatório
                </div>
              </div>
            </div>
            <!-- Nome social mobile -->
            <div class=" md-layout">
              <div class="md-layout-item md-size-100 mobile">
                <md-field>
                  <label class="label" aria-label="Insira seu nome social"
                    >Seu nome social</label
                  >
                  <md-input
                    style="text-transform: capitalize"
                    v-model="form.socialName"
                    name="socialName"
                    type="text"
                    class="ca-input"
                  ></md-input>
                </md-field>
              </div>
            </div>
            <!-- email mobile -->
            <div class="md-layout">
              <div class="md-layout-item md-size-100 mobile">
                <md-field maxlength="5" :class="{ show: !isActive }">
                  <label
                    :class="isActive ? 'label' : 'label2'"
                    aria-label="Insira seu email"
                    >Seu email</label
                  >
                  <md-input
                    v-model="$v.form.email.$model"
                    required
                    name="email"
                    type="email"
                  ></md-input>
                </md-field>
                <md-field
                  class="md-error"
                  v-if="!$v.form.email.email.required && errors"
                >
                  <label
                    :class="isActive ? 'label' : 'label2'"
                    aria-label="Insira seu email corretamente"
                    aria-invalid="true"
                    >Seu email corretamente</label
                  >
                  <md-input
                    v-model="$v.form.email.$model"
                    required
                    name="email"
                    type="email"
                  ></md-input>
                  <md-icon v-if="!$v.form.email.email.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.email.required && errors">
                  Email obrigatório
                </div>
                <div class="error" v-if="!$v.form.email.email && errors">
                  Preecha o email corretamente
                </div>
              </div>
            </div>
            <!-- sexo mobile -->
            <div class=" md-layout">
              <div class="md-layout-item md-size-100 mobile ">
                <md-field :class="isActive ? '' : 'md-error'">
                  <label
                    :class="isActive ? 'label' : ''"
                    aria-label="informe seu sexo"
                    >Informe seu sexo</label
                  >
                  <md-input
                    style="text-transform: capitalize"
                    v-model="$v.form.sex.$model"
                    id="name"
                    required
                    name="sex"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.sex.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.sex.required && errors">
                  Sexo obrigatório
                </div>
              </div>
            </div>
            <!-- Área desktop -->
            <!-- campos de nome e nome social -->
            <div class=" md-layout">
              <div class="md-layout-item md-size-50 desktop ">
                <md-field :class="isActive ? '' : 'md-error'">
                  <label
                    :class="isActive ? 'label' : ''"
                    aria-label="insira seu nome completo"
                    >Nome completo</label
                  >
                  <md-input
                    style="text-transform: capitalize"
                    v-model="$v.form.idName.$model"
                    id="name"
                    required
                    name="idName"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.idName.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.idName.required && errors">
                  Nome obrigatório
                </div>
              </div>
              <div class="md-layout-item md-size-50 desktop">
                <md-field>
                  <label class="label" aria-label="Insira seu nome social"
                    >Seu nome social</label
                  >
                  <md-input
                    style="text-transform: capitalize"
                    v-model="form.socialName"
                    name="socialName"
                    type="text"
                    class="ca-input"
                  ></md-input>
                </md-field>
              </div>
            </div>
            <!-- campo de email, sexo e nacionalidade -->
            <div class="md-layout">
              <div class="md-layout-item md-size-50 desktop">
                <md-field maxlength="5" :class="{ show: !isActive }">
                  <label
                    :class="isActive ? 'label' : 'label2'"
                    aria-label="Insira seu email"
                    >Seu email</label
                  >
                  <md-input
                    v-model="$v.form.email.$model"
                    required
                    name="email"
                    type="email"
                  ></md-input>
                </md-field>
                <md-field
                  class="md-error"
                  v-if="!$v.form.email.email.required && errors"
                >
                  <label
                    :class="isActive ? 'label' : 'label2'"
                    aria-label="Insira seu email corretamente"
                    aria-invalid="true"
                    >Seu email corretamente</label
                  >
                  <md-input
                    v-model="$v.form.email.$model"
                    required
                    name="email"
                    type="email"
                  ></md-input>
                  <md-icon v-if="!$v.form.email.email.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.email.required && errors">
                  Email obrigatório
                </div>
                <div class="error" v-if="!$v.form.email.email && errors">
                  Preecha o email corretamente
                </div>
              </div>
              <!-- sexo para desktop -->
              <div class="md-layout-item md-size-25 desktop">
                <md-field :class="isActive ? verde : 'md-error'">
                  <label
                    :class="isActive ? 'label' : 'label2'"
                    aria-label="informe seu sexo"
                    >Informe seu sexo</label
                  >
                  <md-input
                    v-model="$v.form.sex.$model"
                    required
                    name="sex"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.sex.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.sex.required && errors">
                  Sexo obrigatório
                </div>
              </div>
              <!-- nacionalidade para desktop -->
              <div class="md-layout-item md-size-25 desktop">
                <md-field :class="isActive ? verde : 'md-error'">
                  <label
                    :class="isActive ? 'label' : 'label2'"
                    aria-label="insira sua nacionalidade"
                    >Nacionalidade</label
                  >
                  <md-input
                    v-model="$v.form.nationality.$model"
                    required=""
                    class="ca-input"
                    name="nationality"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.nationality.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div
                  class="error"
                  v-if="!$v.form.nationality.required && errors"
                >
                  Nacionalidade obrigatório
                </div>
              </div>
            </div>

            <!-- Campos de endereço e Numero -->
            <div class="md-layout">
              <div class="md-layout-item md-size-50 desktop">
                <md-field :class="isActive ? verde : 'md-error'">
                  <label
                    :class="isActive ? 'label' : 'label2'"
                    aria-label="endereço completo (cep, rua, numero)"
                    >Endereço completo</label
                  >
                  <md-input
                    v-model="$v.form.address.$model"
                    required
                    class="ca-input"
                    name="address"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.address.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.address.required && errors">
                  Endereço obrigatório
                </div>
              </div>
              <!-- nacionalidade mobile -->
              <div class="md-layout-item md-size-50 mobile">
                <md-field :class="isActive ? '' : 'md-error'">
                  <label
                    :class="isActive ? 'label' : ''"
                    aria-label="insira sua nacionalidade"
                    >Nacionalidade</label
                  >
                  <md-input
                    v-model="$v.form.nationality.$model"
                    required
                    class="ca-input"
                    name="nationality"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.idName.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div
                  class="error"
                  v-if="!$v.form.nationality.required && errors"
                >
                  Campo obrigatório
                </div>
              </div>
              <!-- campo numero de contato mobile e desktop -->
              <div class="md-layout-item md-size-50 ">
                <md-field maxlength="5" :class="isActive ? verde : 'md-error'">
                  <label
                    :class="isActive ? 'label' : ''"
                    class="desktop"
                    aria-label="insira numero para contatos com ddd; apenas números"
                    >Número para contato</label
                  >
                  <label
                    class="mobile"
                    :class="isActive ? 'label' : ''"
                    aria-label="insira numero para contatos com ddd; apenas números"
                    >N° de contato</label
                  >
                  <md-input
                    v-model="$v.form.contact.$model"
                    name="contact"
                    class="ca-input"
                    inputmode="numeric"
                    required
                    type="text"
                    v-mask="'(##)#####-####'"
                  ></md-input>
                  <md-icon v-if="!$v.form.contact.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.contact.required && errors">
                  Contato obrigatório
                </div>
              </div>
            </div>

            <!-- campos de data de nascimento e CPF -->
            <div class="md-layout">
              <div class="md-layout-item md-size-50">
                <md-field :class="isActive ? verde : 'md-error'">
                  <label :class="isActive ? 'label' : 'label2'"
                    >Data de nascimento</label
                  >
                  <md-input
                    v-model="$v.form.birthdate.$model"
                    alt="só números"
                    name="birthdate"
                    inputmode="numeric"
                    aria-label="data de nascimento; apenas números"
                    class="ca-input"
                    required=""
                    type="text"
                    v-mask="'##/##/####'"
                  ></md-input>
                  <md-icon v-if="!$v.form.birthdate.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.birthdate.required && errors">
                  Data de nascimento obrigatório
                </div>
              </div>
              <div class="md-layout-item md-size-50">
                <md-field maxlength="5" :class="isActive ? verde : 'md-error'">
                  <label :class="isActive ? 'label' : 'label2'">CPF</label>
                  <md-input
                    v-model="$v.form.cpf.$model"
                    name="cpf"
                    aria-label="insira seu CPF; apenas números"
                    required
                    inputmode="numeric"
                    class="ca-input"
                    type="text"
                    v-mask="'###.###.###-##'"
                  ></md-input>
                  <md-icon v-if="!$v.form.cpf.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.cpf.required && errors">
                  CPF obrigatório
                </div>
              </div>
            </div>

            <!-- campo de endereço e modal de upload de arquivos mobile -->
            <div class="md-layout">
              <div class="md-layout-item md-size-100 mobile">
                <md-field :class="isActive ? '' : 'md-error'">
                  <label :class="isActive ? 'label' : ''"
                    >Endereço completo
                  </label>
                  <md-input
                    v-model="$v.form.address.$model"
                    required=""
                    name="address"
                    type="text"
                  ></md-input>
                  <md-icon v-if="!$v.form.idName.required && errors"
                    >clear</md-icon
                  >
                </md-field>
                <div class="error" v-if="!$v.form.address.required && errors">
                  Campo obrigatório
                </div>
              </div>
              <div class="md-layout-item md-size-100 mobile">
                <md-button
                  class="md-primary md-round md-block"
                  @click="classicModal = true"
                  ><md-icon>library_books</md-icon> Envio de
                  documentos</md-button
                >
                <modal v-if="classicModal" @close="classicModalHide">
                  <template slot="header">
                    <h4 class="modal-title"></h4>
                    <md-button
                      class="
                        md-simple md-just-icon md-round
                        modal-default-button
                      "
                      @click="classicModalHide"
                    >
                      <md-icon>clear</md-icon>
                    </md-button>
                  </template>

                  <template slot="body">
                    <label class="label"
                      >Documentos de Identificação necessários.
                    </label>
                    <p>
                      <strong>1.</strong> Identidade ou CNH(frente e verso)
                      <strong>2.</strong> Comprovante de Matricula<br />
                      <strong>3.</strong> Foto de perfil (3x4)
                      <strong>4.</strong> Comprovante de residência
                    </p>
                    <div class="md-layout-item md-size-100">
                      <b-field class="campo">
                        <b-upload
                          v-model="$v.form.dropFiles.$model"
                          multiple
                          expanded
                          drag-drop
                          rounded
                        >
                          <section class="section" style="padding: 30px 50px">
                            <div class="content has-text-centered">
                              <p>
                                <b-icon
                                  icon="upload"
                                  type="is-primary"
                                ></b-icon>
                              </p>
                              <p>Deixe aqui seus documentos</p>
                              <p class="vermelho" style="margin-top: -20px">
                                PDF, PNG ou JPEG
                              </p>
                            </div>
                          </section>
                        </b-upload>
                      </b-field>
                      <div class="tags">
                        <span
                          v-for="(file, index) in form.dropFiles"
                          :key="index"
                          class="tag is-primary"
                        >
                          {{ file.name }}
                          <button
                            class="delete is-small"
                            type="button"
                            @click="deleteDropFile(index)"
                          ></button>
                        </span>
                      </div>
                    </div>
                  </template>
                  <template slot="footer">
                    <md-button
                      class="md-danger md-simple"
                      @click="classicModalHide"
                      >Fechar</md-button
                    >
                  </template>
                </modal>
                <div class="error" v-if="!$v.form.dropFiles.required && errors">
                  Campo obrigatório
                </div>
              </div>
            </div>

            <!-- campos de deficiência e upload de arquivos desktop -->
            <div class="md-layout">
              <div class="md-layout-item md-size-50 md-small-size-100 desktop">
                <div class="desktop  label">
                  <label class="" aria-label="você sabe que eu sei"
                    >Você possui alguma deficiência? Se sim, qual?</label
                  >
                  <br />
                </div>
                <div id="example-3">
                  <input
                    type="checkbox"
                    value="Deficiência mental"
                    v-model="form.deficiency"
                    name="deficiency"
                    title="Deficiência mental"
                  />
                  <label
                    style="color: #000; font-weight: bold; margin-left: 4px"
                    for="jack"
                    >Deficiência mental</label
                  >

                  <input
                    type="checkbox"
                    value="Deficiência auditiva"
                    v-model="form.deficiency"
                    style="margin-left: 33px"
                    name="deficiency"
                    title="Deficiência auditiva"
                  />
                  <label
                    style="color: #000; font-weight: bold; margin-left: 4px"
                    for="john"
                    >Deficiência auditiva</label
                  >

                  <input
                    type="checkbox"
                    style="margin-left: 43px"
                    value="Deficiência física"
                    v-model="form.deficiency"
                    name="deficiency"
                    title="Deficiência fisica"
                  />
                  <label
                    style="color: #000; font-weight: bold; margin-left: 4px"
                    for="mike"
                    >Deficiência física</label
                  >
                  <br />
                  <input
                    type="checkbox"
                    value="Deficiencia visual"
                    v-model="form.deficiency"
                    name="deficiency"
                    data-message="Esse é do primeiro botão"
                    title="Deficiencia visual"
                  />
                  <label
                    style="color: #000; font-weight: bold; margin-left: 4px"
                    for="mike"
                    >Deficiência visual</label
                  >

                  <input
                    type="checkbox"
                    value="Deficiência multipla"
                    v-model="form.deficiency"
                    style="margin-left: 40px"
                    name="deficiency"
                    title="Deficiência multipla"
                  />
                  <label
                    style="color: #000; font-weight: bold; margin-left: 4px"
                    for="mike"
                    >Deficiência múltipla</label
                  >

                  <input
                    type="checkbox"
                    id="dislexia"
                    style="margin-left: 40px"
                    value="Dislexia"
                    v-model="form.deficiency"
                    name="deficiency"
                  />
                  <label
                    style="color: #000; font-weight: bold; margin-left: 4px"
                    for="mike"
                    >Dislexia</label
                  >
                  <br />
                </div>
              </div>

              <!-- Modal para upload de arquivos -->
              <div
                class="md-layout-item md-size-33 desktop"
                style="margin-left: 150px; margin-top: 40px"
              >
                <md-button
                  class="md-success md-round md-block"
                  @click="classicModal = true"
                >
                  envie seus documentos
                  <md-icon>library_books</md-icon></md-button
                >
                <modal v-if="classicModal" @close="classicModalHide">
                  <template slot="header">
                    <md-button
                      class="
                        md-simple md-just-icon md-round
                        modal-default-button
                      "
                      @click="classicModalHide"
                      aria-modal="true"
                      role="dialog"
                    >
                      <md-icon>clear</md-icon>
                    </md-button>
                  </template>

                  <template slot="body">
                    <label class="label"
                      >Documentos de Identificação necessários.
                    </label>
                    <p>
                      <strong>1.</strong> Identidade ou CNH(frente e verso)
                      <strong>2.</strong> Comprovante de Matricula<br />
                      <strong>3.</strong> Foto de perfil (3x4)
                      <strong>4.</strong> Comprovante de residência
                    </p>
                    <div class="md-layout-item md-size-100">
                      <b-field class="campo">
                        <b-upload
                          v-model="form.dropFiles"
                          multiple
                          expanded
                          drag-drop
                          rounded
                          :disabled="isUploadAreaDisabled"
                          @input="validateNumberOfFiles"
                        >
                          <section class="section" style="padding: 30px 50px">
                            <div class="content has-text-centered">
                              <p>
                                <b-icon
                                  icon="upload"
                                  type="is-primary"
                                ></b-icon>
                              </p>
                              <p>
                                Faça o upload dos seus documentos<br />
                                <span class="vermelho" style="margin-top: -20px"
                                  >PDF, PNG, JPEG</span
                                >
                              </p>
                              <!-- <p class="vermelho" style="margin-top: -20px">
                                PDF, PNG ou JPEG
                              </p> -->
                            </div>
                          </section>
                        </b-upload>
                      </b-field>
                      <div class="tags">
                        <span
                          v-for="(file, index) in form.dropFiles"
                          :key="index"
                          class="tag is-primary"
                        >
                          {{ file.name }}
                          <button
                            class="delete is-small"
                            type="button"
                            @click="deleteDropFile(index)"
                          ></button>
                        </span>
                      </div>
                    </div>
                  </template>

                  <template slot="footer">
                    <md-button
                      class="md-danger md-simple"
                      @click="classicModalHide"
                      >fechar</md-button
                    >
                  </template>
                </modal>
                <div class="error" v-if="errors">
                  <p v-if="!$v.form.dropFiles.required">
                    Arquivos obrigatórios
                  </p>
                  <p v-if="!$v.form.dropFiles.minLength">
                    Por favor, anexe a quantidade de arquivos requisitada
                  </p>
                  <p v-if="uploadErrors">
                    Um ou mais arquivos excedem o tamanho limite ou possuem um
                    formato inválido
                  </p>
                </div>
                <!-- <div class="error" v-if="!$v.form.dropFiles.required && errors">
                  Campo obrigatório
                </div> -->
              </div>
            </div>
            <br />

            <!-- Checkbox mobile -->
            <h4 class="mobile label">Deficiência</h4>
            <div class="md-layout-item md-size-100 deficiency mobile">
              <br />
              <li id="example-3" style="list-style: none">
                <input
                  type="checkbox"
                  id="mental"
                  value="Deficiência mental"
                  v-model="form.deficiency"
                  name="deficiency"
                />
                <label
                  style="font-weight: bold; color: #000 !important"
                  for="mental"
                  >Mental</label
                >
              </li>
              <li class="li-defi">
                <input
                  type="checkbox"
                  id="auditiva"
                  value="Deficiência auditiva"
                  v-model="form.deficiency"
                  name="deficiency"
                />
                <label
                  style="font-weight: bold; color: #000 !important"
                  for="auditiva"
                  >Auditiva</label
                >
              </li>
              <li class="li-defi">
                <input
                  type="checkbox"
                  id="fisica"
                  value="Deficiência física"
                  v-model="form.deficiency"
                  name="deficiency"
                />
                <label
                  style="font-weight: bold; color: #000 !important"
                  for="fisica"
                  >Física</label
                >
              </li>
            </div>
            <div class="md-layout-item md-size-100 deficiency mobile">
              <li style="list-style: none">
                <input
                  type="checkbox"
                  id="visual"
                  value="Deficiência visual"
                  v-model="form.deficiency"
                  name="deficiency"
                />
                <label
                  style="font-weight: bold; color: #000 !important"
                  for="visual"
                  >Visual</label
                >
              </li>
              <li class="li-defi">
                <input
                  type="checkbox"
                  id="multipla"
                  value="Deficiência multipla"
                  v-model="form.deficiency"
                  name="deficiency"
                />
                <label
                  style="font-weight: bold; color: #000 !important"
                  for="multipla"
                  >Múltipla</label
                >
              </li>
              <li class="li-defi">
                <input
                  type="checkbox"
                  id="dislexia"
                  value="Dislexia"
                  v-model="form.deficiency"
                  name="deficiency"
                  aria-checked="false"
                />
                <label
                  style="font-weight: bold; color: #000 !important"
                  for="dislexia"
                  >Dislexia</label
                >
              </li>
            </div>

            <br />
            <!-- botão de enviar -->
            <div class="md-layout">
              <div class="md-layout-item md-size-50 mx-auto text-center">
                <!-- <md-input type="submit" value="enviar"></md-input> -->

                <vue-recaptcha :sitekey="recaptchaSitekey">
                  <md-button
                    :class="isActive ? 'md-success' : 'md-warning'"
                    class=" md-round testee "
                    type="submit"
                    @click.prevent="submit"
                    value="Enviar Cadastro"
                    >{{ isActive ? textoBotaoOn : textobotaoOff }}</md-button
                  >
                </vue-recaptcha>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const axios = require('axios')
import _ from 'lodash'
import { required, minLength, email } from 'vuelidate/lib/validators'
import VueRecaptcha from 'vue-recaptcha'
import { Modal } from '@/components'
export default {
  bodyClass: 'landing-page',
  components: { VueRecaptcha, Modal },
  props: {
    header: {
      type: String,
      default: require('@/assets/img/cabecalhoFINAL2.png'),
    },
  },
  data() {
    return {
      form: {
        testes: [],
        idName: '', // nome na identidade
        socialName: '',
        address: '',
        email: '',
        contact: '',
        cpf: '',
        birthdate: '', //data de nascimento
        nationality: '',
        sex: '',
        deficiency: [],
        dropFiles: [],
      },
      textoBotaoOn: 'Enviar formulário',
      textobotaoOff: 'Verifique os dados',
      isActive: true,
      errors: false,
      uploadErrors: false,
      isSubmitButtonDisabled: true,
      recaptchaSitekey: process.env.VUE_APP_RECAPTCHA_SITEKEY,
      isUploadAreaDisabled: false,
      classicModal: false,
      isImageModalActive: false,
      isCardModalActive: false,
    }
  },
  validations: {
    form: {
      idName: {
        required,
      },
      address: {
        required,
      },
      email: {
        required,
        email,
      },
      contact: {
        required,
      },
      cpf: {
        required,
      },
      birthdate: {
        required,
      },
      nationality: {
        required,
      },
      sex: {
        required,
      },
      dropFiles: {
        required,
        minLength: minLength(4),
      },
    },
  },
  watch: {
    'form.dropFiles'() {
      this.uploadErrors = false
      _.forEach(this.form.dropFiles, file => {
        if (this.validate(file) !== '') {
          this.uploadErrors = true
        }
      })
    },
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.header})`,
      }
    },
  },

  methods: {
    submit() {
      if (this.$v.$invalid) {
        this.errors = true
        alert('Formulário inválido, verifique suas informações')
        this.isActive = false
      } else {
        this.errors = false
        this.sendForm()
        this.isActive = true
      }
    },
    validateNumberOfFiles() {
      if (this.form.dropFiles.length > 3) {
        this.isUploadAreaDisabled = true
      }
    },
    classicModalHide() {
      this.classicModal = false
    },
    deleteDropFile(index) {
      this.form.dropFiles.splice(index, 1)
      if (this.form.dropFiles.length < 4) {
        this.isUploadAreaDisabled = false
      }
    },
    validate(file) {
      const MAX_SIZE = 2000000
      const allowedTypes = ['image/png', 'image/jpeg', 'application/pdf']

      if (file.size > MAX_SIZE) {
        return `Tamanho maximo: ${MAX_SIZE / 1000000}Mb`
      }

      if (!allowedTypes.includes(file.type)) {
        return 'Tipo de arquivo não permitido'
      }

      return ''
    },
    async sendForm() {
      if (this.uploadErrors) {
        this.errors = true
      } else {
        try {
          const formData = new FormData()
          _.forEach(this.form.dropFiles, file => {
            if (this.validate(file) === '') {
              formData.append('files', file)
            }
          })
          formData.append('idName', this.form.idName)
          formData.append('socialName', this.form.socialName)
          formData.append('address', this.form.address)
          formData.append('email', this.form.email)
          formData.append('contact', this.form.contact)
          formData.append('cpf', this.form.cpf)
          formData.append('birthdate', this.form.birthdate)
          formData.append('nationality', this.form.nationality)
          formData.append('sex', this.form.sex)
          formData.append('deficiency', this.form.deficiency)

          // console.log(formData);
          await axios
            .post(
              `http://${process.env.VUE_APP_API_HOST}:${process.env.VUE_APP_API_PORT}/upload`,
              formData
            )
            .then(function(response) {
              alert(
                'Seu formulário foi enviado. Sua senha será disponibilizada na primeira vez que fizer um empréstimo. O prazo é de 24 horas para a conclusão do seu pré cadastro.'
              )
              document.Location.reload(true)
            })
            .catch(function(error) {
              // handle error
              console.log(error)
            })
        } catch (error) {
          console.log(error)
        }
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.text-responsive {
  font-size: 3rem;
}
.md-card-actions.text-center {
  display: flex;
  justify-content: center !important;
}
.contact-form {
  margin-top: 30px;
}

.md-layout {
  .md-field {
    margin-bottom: 0;
  }

  .error {
    font-size: 0.8rem;
    color: #000;
  }
}

.md-has-textarea + .md-layout {
  margin-top: 15px;
}
.show {
  display: none;
}

.label-file {
  width: 100px;
  color: #9c27b0;
  text-align: center;
  border: 2px solid #ccc;
  border-radius: 4px;
  font-size: 13px;
  background-color: white;
  background-position: 10px 10px;
  padding: 12px 10px 12px 10px;
  cursor: pointer;
  font-weight: 800;
}
.label {
  font-weight: bold;
  color: #000 !important;
  font-size: 16px;
}
.label2 {
  color: #000 !important;
  font-size: 16px;
}
.desktop {
  display: inline-block;
}
.mobile {
  display: none;
}
.labelValid {
  font-weight: bold;
  color: #000 !important;
  font-size: 16px;
}

.li-defi {
  list-style: none;
  margin-left: 20px;
}
.roxo {
  color: #7e395d;
  font-weight: bold;
  font-size: 19px;
}
.verde {
  color: #008000;
  font-weight: 600;
}

.campo {
  text-align: center;
  position: relative;
}
.margem {
  margin-top: 0%;
}
.margem1 {
  margin-top: 6%;
}
.ca-input {
  border-bottom: 2px solid black;
}
.testee {
  position: relative;
}

@media screen and (max-width: 500px) {
  .text-responsive {
    font-size: 1.5rem;
  }

  .description {
    font-size: 1rem;
  }
  .section {
    padding: 20px 0;
  }

  .md-size-50 {
    width: 100;
  }
  .desktop {
    display: none;
  }
  .mobile {
    display: flex;
    flex-direction: column;

    &.md-layout-item.deficiency {
      flex-direction: row;
    }
  }
}
</style>
