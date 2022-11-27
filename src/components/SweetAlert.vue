<template>
  <div>
    <button class="btn btn-success" @click="showAlert()">Hola</button
    ><br /><br />
    <button class="btn btn-info" @click="imagenAlert()">Imagen</button
    ><br /><br />
    <button class="btn btn-warning" @click="customAlert()">Custom</button
    ><br /><br />
    <button class="btn btn-danger" @click="htmlAlert()">Html</button><br /><br />
    <button class="btn btn-secondary" @click="saveAlert()">Guardar</button>
  </div>
</template>

<script>
export default {
  name: "SweetAlert",
  methods: {
    showAlert() {
      this.$swal.fire({
        title: "Bienvenido",
        icon: "warning"
      });
    },
    imagenAlert() {
      this.$swal.fire({
        imageUrl: "https://i.ebayimg.com/images/g/VuwAAOSw--NexIbC/s-l500.jpg",
        imageHeight: 600,
        imageWidth: 400,
        imageAlt: "DeadPool",
        title: "¡Chimichanga!",
      });
    },
    customAlert() {
      this.$swal.fire({
        title: "Modal custom",
        width: 500,
        heightAuto: false,
        padding: "3em",
        color: "yellow",
        background:
          "#272928 url(https://media4.giphy.com/media/l36kU80xPf0ojG0Erg/giphy.gif)",
      });
    },
    htmlAlert() {
      this.$swal.fire({
        title:
          "<ul> <li>lista</li> <li> HTML </li> <li>en el </li> <li>modal</li> </ul>",
        icon: "info",
        html:
          "Puedes usar <b>negrita</b>, " +
          '<a href="https://github.com/NazarRom/sweetalert2_post.git" target="_blank">enlace</a> ' +
          "y otras etiquetas HTML",
        showCloseButton: true,
        showCancelButton: true,
        focusConfirm: false,
        confirmButtonText: "Genial",
        cancelButtonText: "Cancel",
      });
    },
    saveAlert() {
      this.$swal
        .fire({
          title: "¿Guardar los cambios?",
          showDenyButton: true,
          showCancelButton: true,
          confirmButtonText: "Guardar",
          denyButtonText: "No guardar",
        })
        .then((result) => {
          if (result.isConfirmed) {
            this.$swal.fire("Guardado!", "", "success");
            this.savedExm();
          } else if (result.isDenied) {
            this.$swal.fire("Los cambios no se han guardado", "", "info");
            this.dontSavedExm();
          }
        });
    },
    savedExm() {
      console.log("Saved");
    },
    dontSavedExm() {
      console.log("Dont saved");
    },
  },
};
</script>

<style></style>
