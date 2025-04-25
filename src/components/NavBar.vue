<template>
    <nav class="navbar">
        <div class="container">
            <router-link to="/" class="logo">WH</router-link>
            <div class="nav-links">
                <router-link to="/" class="nav-link">Home</router-link>
                <router-link to="/about" class="nav-link">About</router-link>
                <router-link to="/projects" class="nav-link">Projects</router-link>
            </div>
        </div>
    </nav>
</template>

<script setup>
// Component logic here
</script>

<style scoped>
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 1000;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 1rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: #3498db;
    text-decoration: none;
}

.nav-links {
    display: flex;
    gap: 2rem;
}

.nav-link {
    color: #2c3e50;
    text-decoration: none;
    font-weight: 500;
    transition: color 0.3s ease;
}

.nav-link:hover {
    color: #3498db;
}

.router-link-active {
    color: #3498db;
}
</style>