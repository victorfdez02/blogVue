<template>
    <div class="col-lg-4 col-md-6 mb-4">
        <div class="card h-100">
            <img class="card-img-top"
                src="https://d585tldpucybw.cloudfront.net/sfimages/default-source/blogs/templates/vuet3-light-1200x303.png?sfvrsn=508f5918_3"
                alt="Foto">
            <div class="card-body">
                <div class="d-flex justify-content-between align-items-center mb-3">
                    <h5 class="card-title">{{ post.title }}</h5>
                    <div>
                        <button class="btn btn-sm mb-1" @click="editarContenido">Editar</button><br>
                        <button class="btn btn-sm " @click="toggleContent">{{ isOpen ? 'Menos' : 'Más'
                        }}</button>
                    </div>
                </div>
                <p v-show="isOpen" class="card-text">{{ contenido }}</p>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    post: Object
});

const isOpen = ref(false);
const contenido = ref(props.post.body);

const toggleContent = () => {
    isOpen.value = !isOpen.value;
};

const editarContenido = () => {
    const nuevoContenido = prompt('Ingrese el nuevo contenido:', contenido.value);
    if (nuevoContenido !== null) {
        contenido.value = nuevoContenido;
    }
};
</script>
