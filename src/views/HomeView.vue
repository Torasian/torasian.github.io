<template>
    <div class="home">
        <section class="hero">
            <h1>William Hawken</h1>
            <h2>Multidisciplinary Designer & Front End Developer</h2>
            <p class="subtitle">Creating beautiful, functional digital experiences</p>
            <div class="cta-buttons">
                <router-link to="/projects" class="btn primary">View My Work</router-link>
                <router-link to="/about" class="btn secondary">Learn More</router-link>
            </div>
        </section>
    </div>
</template>

<script setup>
// Component logic here
</script>

<style scoped>
.home {
    min-height: calc(100vh - 4rem);
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
}

.hero {
    text-align: center;
    padding: 2rem;
    max-width: 800px;
    width: 100%;
}

h1 {
    font-size: 3.5rem;
    margin-bottom: 1rem;
    color: #2c3e50;
}

h2 {
    font-size: 2rem;
    color: #34495e;
    margin-bottom: 1rem;
}

.subtitle {
    font-size: 1.2rem;
    color: #7f8c8d;
    margin-bottom: 2rem;
}

.cta-buttons {
    display: flex;
    gap: 1rem;
    justify-content: center;
}

.btn {
    padding: 0.8rem 1.5rem;
    border-radius: 5px;
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s ease;
}

.primary {
    background-color: #3498db;
    color: white;
}

.primary:hover {
    background-color: #2980b9;
}

.secondary {
    background-color: transparent;
    border: 2px solid #3498db;
    color: #3498db;
}

.secondary:hover {
    background-color: #3498db;
    color: white;
}

@media (max-width: 768px) {
    h1 {
        font-size: 2.5rem;
    }

    h2 {
        font-size: 1.5rem;
    }

    .cta-buttons {
        flex-direction: column;
        align-items: center;
    }

    .btn {
        width: 200px;
    }
}
</style>