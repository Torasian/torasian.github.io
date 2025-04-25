<template>
    <div class="projects">
        <div class="container">
            <h1>My Projects</h1>
            <div class="projects-grid">
                <div v-for="project in projects" :key="project.id" class="project-card">
                    <div class="project-image" :style="{ backgroundImage: `url(${project.image})` }">
                        <div class="project-overlay">
                            <div class="project-links">
                                <a :href="project.demo" target="_blank" class="btn">View Demo</a>
                                <a :href="project.github" target="_blank" class="btn">View Code</a>
                            </div>
                        </div>
                    </div>
                    <div class="project-info">
                        <h3>{{ project.title }}</h3>
                        <p>{{ project.description }}</p>
                        <div class="project-tags">
                            <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const projects = [
    {
        id: 1,
        title: 'E-commerce Platform',
        description: 'A modern e-commerce platform built with Vue.js and Node.js, featuring real-time inventory management and secure payment processing.',
        image: 'https://picsum.photos/600/400?random=1',
        demo: '#',
        github: '#',
        tags: ['Vue.js', 'Node.js', 'MongoDB', 'Stripe']
    },
    {
        id: 2,
        title: 'Task Management App',
        description: 'A collaborative task management application with real-time updates, team features, and progress tracking.',
        image: 'https://picsum.photos/600/400?random=2',
        demo: '#',
        github: '#',
        tags: ['React', 'Firebase', 'Material-UI']
    },
    {
        id: 3,
        title: 'Portfolio Website',
        description: 'A responsive portfolio website showcasing my work and skills, built with Vue.js and modern CSS techniques.',
        image: 'https://picsum.photos/600/400?random=3',
        demo: '#',
        github: '#',
        tags: ['Vue.js', 'CSS3', 'Vue Router']
    }
]
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
    position: relative;
}

.project-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
    opacity: 1;
}

.project-links {
    display: flex;
    gap: 1rem;
}

.btn {
    padding: 0.5rem 1rem;
    background: #3498db;
    color: white;
    text-decoration: none;
    border-radius: 4px;
    font-size: 0.9rem;
    transition: background 0.3s ease;
}

.btn:hover {
    background: #2980b9;
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