<template>
  <div class="home">
    <header-app>
      <div class="row">
        <button
          class="btn btn-dark offset-3 col-sm-4 mb-3 mx-auto"
          data-bs-toggle="modal"
          data-bs-target="#calluser">
          Entramos em contato com você!
        </button>
      </div>
    </header-app>

    <div class="row" id="menu1">
      <div class="col-sm-12 col-md-7 my-4">
        <h2 class="border-bottom cor1" id="menu1">O que fazemos?</h2>
        <div class="row text-center">
          <div class="col-sm-12 col-md m-2 d-flex align-items-center justify-content-center">
            <div class="card">
              <img src="../assets/rato.jpg" class="card-img-top" alt="...">
              <div class="card-body">
                <p class="card-text">Imunização contra roedores.</p>
              </div>
            </div>
          </div>
          <div class="col-sm-12 col-md m-2 d-flex align-items-center justify-content-center">
            <div class="card">
              <img src="../assets/barata.jpg" class="card-img-top" alt="...">
              <div class="card-body">
                <p class="card-text">Imunização contra baratas.</p>
              </div>
            </div>
          </div>
          <div class="col-sm-12 col-md m-2 d-flex align-items-center justify-content-center">
            <div class="card">
              <img src="../assets/cupim.jpg" class="card-img-top" alt="...">
              <div class="card-body">
                <p class="card-text">Imunização contra cupins.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-sm-12 col-md my-4 mx-2">
        <h2 class="border-bottom cor1" id="menu2">Contatos</h2>
        <address>
          <p title="celular" class="cor2">Whatsapp: (21) 98116-0079</p>
          <p title="fixo" class="cor2">Fixo: (21) 2758-3416</p>
          <p title="Email">Email: <a href="mailto:#">antonioallan.peres@gmail.com</a></p>
        </address>
      </div>
    </div>

    <a
      href="https://api.whatsapp.com/send?phone=5521981160079&text=Olá! Gostaria de fazer um orçamento!"
      class="float"
      target="_blank"
    >
      <i class="fa fa-whatsapp my-float"></i>
    </a>

    <div class="modal fade" id="calluser" tabindex="-1" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="calluser">Quais seus dados?</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <p>Para atendermos melhor a você, poderia nos fornecer alguns dados?</p>
            <form @submit.prevent="sendMail">
              <input class="form-control mt-2" type="text" placeholder="Seu nome" v-model="nome" required>
              <input class="form-control mt-2" type="email" placeholder="Seu email" v-model="email" required>
              <input class="form-control mt-2" type="text" placeholder="Seu celular" v-model="celular" required>
              <div class="mt-2">
                <p selected>Escolha qual o tipo de dedetização que deseja?</p>
                <div>
                  <input id="opc1" class="form-check-input" type="checkbox" value="Dedetização" v-model="tipos">
                  <label class="form-check-label mx-2" for="opc1">Dedetização</label>
                </div>
                <div>
                  <input id="opc2" class="form-check-input" type="checkbox" value="Descupiização" v-model="tipos">
                  <label class="form-check-label mx-2" for="opc2">Descupização</label>
                </div>
                <div>
                  <input id="opc3" class="form-check-input" type="checkbox" value="Desratização" v-model="tipos">
                  <label class="form-check-label mx-2" for="opc3">Desratização</label>
                </div>
                <div>
                  <input id="opc4" class="form-check-input" type="checkbox" value="Outros" v-model="tipos">
                  <label class="form-check-label mx-2" for="opc4">Outros</label>
                </div>
                <div class="tags mt-2">
                  <div class="badge rounded-pill bg-primary mx-2" v-for="tipo in tipos" :key="tipo">{{ tipo }}</div>
                </div>
              </div>
              <div class="row">
                <button type="submit" class="btn btn-dark offset-3 col-sm-4 mb-3 mt-3 mx-auto" data-bs-dismiss="modal">Confirmar</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import emailjs from 'emailjs-com';
import HeaderApp from "@/components/HeaderApp.vue";

export default {
  components: { HeaderApp },
  data() {
    return {
      nome: "",
      email: "",
      celular: "",
      tipos: []
    };
  },
  methods: {
    sendMail(e){
      const emailProps = {
        nome: this.nome,
        email: this.email,
        celular: this.celular,
        tipos: this.tipos
      }

      console.log(emailProps)

      try {
        emailjs.send('service_3ybncim', 'template_vdoy4je', emailProps, 'user_be9rncovwoZ3RybSePcvx')
        .then((result) => {
            console.log('SUCCESS!', result.status, result.text);
        }, (error) => {
            console.log('FAILED...', error);
        });
      } catch(error) {
          console.log({error})
      }

      this.name = ''
      this.email = ''
      this.celular = ''
      tipos =  []
    }
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100;300&display=swap");

body {
  font-family: "Roboto", sans-serif;
  margin: 0;
  padding: 0;
}

.body_page {
  margin: 0 auto;
}

.cor1 {
  color: #3c6e71;
}

.cor2 {
  color: #353535;
}

@media (min-width: 320px){
  .card {
    max-width: 18.5rem;
  }
}

@media (min-width: 420px){
  .card {
    max-width: 25.5rem;
  }
  
}
 
.float {
  position: fixed;
  width: 60px;
  height: 60px;
  bottom: 40px;
  right: 40px;
  background-color: #25d366;
  color: #fff;
  border-radius: 50px;
  text-align: center;
  font-size: 30px;
  box-shadow: 2px 2px 3px #999;
  z-index: 1;
}

.my-float {
  margin-top: 16px;
}

.row {
  --bs-gutter-x: 0;
}
</style> 