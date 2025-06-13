<template>
    <div class="project-detail">
        <div v-if="project" class="project-content">
            <!-- Hero Section -->
            <div class="hero-section" :style="{ backgroundImage: `url(${project.hero_image})` }">
                <div class="hero-overlay">
                    <div class="container">
                        <div class="hero-content">
                            <div class="client-info">
                                <img :src="project.company_logo" :alt="project.client_name" class="company-logo">
                                <span class="institution">{{ project.institution }}</span>
                            </div>
                            <h1>{{ project.project_title }}</h1>
                            <div class="project-meta">
                                <span class="year">{{ project.year }}</span>
                                <span class="industry">{{ project.industry }}</span>
                                <span v-if="project.award" class="award">{{ project.award }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="container">
                <!-- Project Overview -->
                <section class="project-overview">
                    <div class="overview-content">
                        <div class="description">
                            <h2>Overview</h2>
                            <p>{{ project.description }}</p>
                        </div>
                        <div class="key-details">
                            <div class="detail-item">
                                <h3>My Role</h3>
                                <p>{{ project.my_role }}</p>
                            </div>
                            <div class="detail-item">
                                <h3>Client</h3>
                                <p>{{ project.client_name }}</p>
                            </div>
                            <div class="detail-item">
                                <h3>Date</h3>
                                <p>{{ project.date }}</p>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- Main Content -->
                <section class="main-content">
                    <h2>Project Details</h2>
                    <div class="content-text" v-html="formatContent(project.main_content)"></div>
                </section>

                <!-- Process Section -->
                <section class="process-section">
                    <h2>Process</h2>
                    <div class="process-timeline">
                        <div v-for="(step, phase) in project.process" :key="phase" class="process-step">
                            <h3>{{ phase }}</h3>
                            <p>{{ step }}</p>
                        </div>
                    </div>
                </section>

                <!-- Skills & Tools -->
                <section class="skills-tools">
                    <div class="skills">
                        <h2>Skills</h2>
                        <div class="skill-tags">
                            <span v-for="skill in project.skills" :key="skill" class="tag">{{ skill }}</span>
                        </div>
                    </div>
                    <div class="tools">
                        <h2>Tools & Technologies</h2>
                        <div class="tool-tags">
                            <span v-for="tool in project.tools" :key="tool" class="tag">{{ tool }}</span>
                        </div>
                    </div>
                </section>

                <!-- Project Gallery -->
                <section class="project-gallery">
                    <h2>Project Gallery</h2>
                    <div class="gallery-grid">
                        <div v-for="image in project.images" :key="image.url" class="gallery-item">
                            <img :src="image.url" :alt="image.caption">
                            <p class="caption">{{ image.caption }}</p>
                        </div>
                    </div>
                </section>

                <!-- Metrics -->
                <section v-if="project.metrics" class="metrics-section">
                    <h2>Results</h2>
                    <div class="metrics-grid">
                        <div v-for="(value, metric) in project.metrics" :key="metric" class="metric-card">
                            <h3>{{ formatMetricName(metric) }}</h3>
                            <p class="metric-value">{{ value }}</p>
                        </div>
                    </div>
                </section>

                <!-- Testimonial -->
                <section v-if="project.testimonial" class="testimonial-section">
                    <blockquote class="testimonial">
                        <p>{{ project.testimonial.quote }}</p>
                        <footer>
                            <cite>
                                <strong>{{ project.testimonial.author }}</strong>
                                <span>{{ project.testimonial.position }}</span>
                            </cite>
                        </footer>
                    </blockquote>
                </section>

                <!-- Project Video -->
                <section v-if="project.project_video" class="video-section">
                    <h2>Project Video</h2>
                    <div class="video-container">
                        <video controls>
                            <source :src="project.project_video" type="video/mp4">
                            Your browser does not support the video tag.
                        </video>
                    </div>
                </section>
            </div>
        </div>
        <div v-else class="not-found">
            <h2>Project not found</h2>
            <router-link to="/projects" class="btn">Back to Projects</router-link>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const project = ref(null)
const loading = ref(true)

onMounted(async () => {
    const projectSlug = route.params.slug
    try {
        const module = await import(`../data/projects/${projectSlug}.json`)
        project.value = module.default
    } catch (e) {
        project.value = null
    }
    loading.value = false
})

const formatContent = (content) => {
    return content.replace(/\n\n/g, '<br><br>')
}

const formatMetricName = (metric) => {
    return metric.split('_').map(word =>
        word.charAt(0).toUpperCase() + word.slice(1)
    ).join(' ')
}
</script>

<style scoped>
.project-detail {
    min-height: 100vh;
    background-color: #f8f9fa;
}

.hero-section {
    height: 70vh;
    background-size: cover;
    background-position: center;
    position: relative;
}

.hero-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.6);
    display: flex;
    align-items: center;
}

.hero-content {
    color: white;
    text-align: center;
}

.client-info {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 1rem;
}

.company-logo {
    height: 40px;
    width: auto;
}

.institution {
    font-size: 1.2rem;
    opacity: 0.9;
}

.hero-content h1 {
    font-size: 3.5rem;
    margin-bottom: 1rem;
}

.project-meta {
    display: flex;
    gap: 2rem;
    justify-content: center;
    font-size: 1.1rem;
}

.award {
    color: #ffd700;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
}

section {
    padding: 4rem 0;
}

.project-overview {
    margin-top: -4rem;
    position: relative;
    z-index: 1;
}

.overview-content {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 2rem;
}

.key-details {
    display: grid;
    gap: 1.5rem;
}

.detail-item h3 {
    color: #3498db;
    margin-bottom: 0.5rem;
}

h2 {
    font-size: 2rem;
    color: #2c3e50;
    margin-bottom: 1.5rem;
}

.content-text {
    line-height: 1.8;
    color: #2c3e50;
}

.process-timeline {
    display: grid;
    gap: 2rem;
    margin-top: 2rem;
}

.process-step {
    background: white;
    padding: 1.5rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.process-step h3 {
    color: #3498db;
    margin-bottom: 0.5rem;
    text-transform: capitalize;
}

.skills-tools {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
}

.skill-tags,
.tool-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
}

.tag {
    background: #e1f0fa;
    color: #3498db;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    font-size: 0.9rem;
}

.gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}

.gallery-item {
    position: relative;
}

.gallery-item img {
    width: 100%;
    height: 300px;
    object-fit: cover;
    border-radius: 8px;
}

.caption {
    margin-top: 0.5rem;
    color: #7f8c8d;
    font-size: 0.9rem;
}

.metrics-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
}

.metric-card {
    background: white;
    padding: 1.5rem;
    border-radius: 8px;
    text-align: center;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.metric-value {
    font-size: 2rem;
    color: #3498db;
    font-weight: bold;
    margin-top: 0.5rem;
}

.testimonial {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    font-style: italic;
    position: relative;
}

.testimonial::before {
    content: '"';
    font-size: 4rem;
    color: #3498db;
    opacity: 0.2;
    position: absolute;
    top: 0;
    left: 1rem;
}

.testimonial footer {
    margin-top: 1rem;
    text-align: right;
}

.testimonial cite {
    font-style: normal;
    display: block;
}

.video-container {
    position: relative;
    padding-bottom: 56.25%;
    height: 0;
    overflow: hidden;
}

.video-container video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border-radius: 8px;
}

.not-found {
    text-align: center;
    padding: 4rem 0;
}

.btn {
    display: inline-block;
    padding: 0.8rem 1.5rem;
    background: #3498db;
    color: white;
    text-decoration: none;
    border-radius: 4px;
    transition: background 0.3s ease;
}

.btn:hover {
    background: #2980b9;
}

@media (max-width: 768px) {
    .hero-content h1 {
        font-size: 2.5rem;
    }

    .overview-content {
        grid-template-columns: 1fr;
    }

    .skills-tools {
        grid-template-columns: 1fr;
    }

    .project-meta {
        flex-direction: column;
        gap: 0.5rem;
    }
}
</style>