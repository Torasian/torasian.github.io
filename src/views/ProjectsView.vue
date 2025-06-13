<template>
    <div class="projects">
        <div class="container">
            <h1>My Projects</h1>
            <div class="projects-grid">
                <div v-for="project in projects" :key="project.slug" class="project-card">
                    <router-link :to="`/projects/${project.slug}`" class="project-link">
                        <div class="project-image" :style="{ backgroundImage: `url(${project.hero_image})` }"></div>
                        <div class="project-info">
                            <h3>{{ project.project_title }}</h3>
                            <p>{{ project.description }}</p>
                        </div>
                    </router-link>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import projects from '../data/projects-index.json'
</script>

<style scoped>
.projects {
    min-height: 100vh;
    padding: 4rem 2rem;
    background-color: #f8f9fa;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
}

h1 {
    font-size: 2.5rem;
    color: #2c3e50;
    margin-bottom: 2rem;
    text-align: center;
}

.projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}

.project-link {
    text-decoration: none;
    color: inherit;
    display: block;
}

.project-card {
    background: white;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
}

.project-card:hover {
    transform: translateY(-5px);
}

.project-image {
    height: 200px;
    background-size: cover;
    background-position: center;
}

.project-info {
    padding: 1.5rem;
}

.project-info h3 {
    font-size: 1.3rem;
    color: #2c3e50;
    margin-bottom: 0.5rem;
}

.project-info p {
    color: #7f8c8d;
    margin-bottom: 1rem;
    line-height: 1.5;
}

.project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
}

.tag {
    background: #e1f0fa;
    color: #3498db;
    padding: 0.3rem 0.6rem;
    border-radius: 4px;
    font-size: 0.8rem;
}
</style>