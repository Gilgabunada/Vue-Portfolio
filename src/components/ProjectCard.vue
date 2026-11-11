<template>
    <div class="col-md-4">
    <!-- Renders as a clickable <a> when the project has a link, otherwise a plain div -->
    <component
        :is="project.link ? 'a' : 'div'"
        :href="project.link || undefined"
        :target="project.link ? '_blank' : undefined"
        :rel="project.link ? 'noopener noreferrer' : undefined"
        class="card project-card h-100 project-card-link"
    >
        <!-- use ":" directive to bind the project.image to the src attribute -->
        <img :src="project.image" class="card-img-top project-img" alt="...">
        <div class="card-body">
            <!-- use interpolation to bind the project.title to the card title -->
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text project-text">
                {{ project.description }}
            </p>

        </div>
    </component>
</div>
</template>


<script setup>
    defineProps({
        project: Object
    })
</script>
