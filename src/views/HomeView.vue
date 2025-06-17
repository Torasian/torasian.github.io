<template>
    <div class="home">
        <!-- Hero Section -->
        <section class="hero" :style="{ backgroundImage: `url(${currentProject.hero_image})` }">
            <div class="hero-content">
                <div class="hero-text">

                    <h1 class="text-5xl font-bold text-white mb-4">William Hawken</h1>
                    <p class="text-2xl text-white/90">Multidisciplinary Designer & Front End Developer</p>
                </div>
                <div class="project-info">
                    <h2 class="text-sm font-black text-black mb-2">{{ currentProject.project_title }}</h2>
                    <p class="text-lg text-white/80">{{ currentProject.client_name }}</p>
                </div>
            </div>
        </section>

        <!-- Brand Logos Section -->
        <section class="brand-logos">
            <div class="bg-red-500 text-white p-4">If you see a red box, Tailwind is working!</div>
            <div class="logos-carousel">
                <img src="https://picsum.photos/200/100?random=1" alt="IBM" class="logo">
                <img src="https://picsum.photos/200/100?random=2" alt="Burberry" class="logo">
                <img src="https://picsum.photos/200/100?random=3" alt="Harrods" class="logo">
            </div>
        </section>

        <!-- Featured Projects Section -->
        <section class="featured-projects">
            <h2 class="text-3xl font-bold mb-8">Featured Projects</h2>
            <div class="projects-grid">
                <div v-for="project in featuredProjects" :key="project.slug" class="project-card">
                    <div class="project-image" :style="{ backgroundImage: `url(${project.hero_image})` }"></div>
                    <div class="project-info">
                        <h3 class="text-xl font-bold mb-2">{{ project.project_title }}</h3>
                        <p class="text-gray-600 mb-4">{{ project.description }}</p>
                        <router-link :to="`/projects/${project.slug}`" class="btn">View Project</router-link>
                    </div>
                </div>
            </div>
        </section>

        <!-- Testimonials Section -->
        <section class="testimonials">
            <h2 class="text-3xl font-bold mb-8 text-center">Client Testimonials</h2>
            <div class="testimonials-carousel">
                <div v-for="(testimonial, index) in testimonials" :key="index" class="testimonial-card">
                    <blockquote class="text-gray-600 italic mb-4">{{ testimonial.quote }}</blockquote>
                    <div class="testimonial-author">
                        <strong class="block text-gray-900">{{ testimonial.author }}</strong>
                        <span class="text-gray-500">{{ testimonial.position }}</span>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
import projects from '../data/projects-index.json';

// Featured projects
const featuredProjects = ref(projects.filter(project => project.featured));

// Hero section data
const heroProjects = ref(featuredProjects.value);
const currentHeroIndex = ref(0);

const currentProject = computed(() => heroProjects.value[currentHeroIndex.value]);

// Testimonials data
const testimonials = ref([
    {
        quote: "The app has transformed how our fitting engineers work, making the process more efficient and accurate.",
        author: "Sarah Johnson",
        position: "Head of Quality Control, Burberry"
    },
    {
        quote: "The analytics platform has given us unprecedented insights into our business operations.",
        author: "Michael Brown",
        position: "CTO, Harrods"
    },
    {
        quote: "William's attention to detail and technical expertise made this project a huge success.",
        author: "David Wilson",
        position: "Project Manager, IBM"
    }
]);

// Function to rotate hero background
const rotateHeroBackground = () => {
    currentHeroIndex.value = (currentHeroIndex.value + 1) % heroProjects.value.length;
};

// Start hero rotation
onMounted(() => {
    setInterval(rotateHeroBackground, 5000); // Rotate every 5 seconds
});
</script>

<style scoped>
.home {
    width: 100%;
}

/* Hero Section */
.hero {
    position: relative;
    height: calc(100vh - 4rem);
    width: 100%;
    background-size: cover;
    background-position: center;
    transition: background-image 1s ease-in-out;
}

.hero::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
}

.hero-content {
    position: relative;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 2rem;
    color: white;
    margin: 0 auto;
}

.hero-text {
    text-align: left;
    margin-top: 2rem;
}

.project-info {
    text-align: right;
    margin-bottom: 2rem;
}

/* Brand Logos Section */
.brand-logos {
    padding: 4rem 0;
    background-color: #f8f9fa;
}

.logos-carousel {
    display: flex;
    justify-content: center;
    gap: 4rem;
    padding: 2rem;
}

.logo {
    height: 60px;
    width: auto;
    opacity: 0.7;
    transition: opacity 0.3s ease;
}

.logo:hover {
    opacity: 1;
}

/* Featured Projects Section */
.featured-projects {
    padding: 4rem 2rem;
}

.projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
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
    text-align: left;
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

/* Testimonials Section */
.testimonials {
    padding: 4rem 2rem;
    background-color: #f8f9fa;
}

.testimonials-carousel {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
}

.testimonial-card {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
    .hero-content {
        padding: 1rem;
    }

    .hero-text {
        margin-top: 1rem;
    }

    .project-info {
        margin-bottom: 1rem;
    }

    .logos-carousel {
        flex-wrap: wrap;
        gap: 2rem;
    }
}
</style>