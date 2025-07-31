<template>
  <section class="movie-grid">
    <h2>Featured Movies</h2>
    <div class="search-bar">
      <input v-model="search" @input="onSearch" placeholder="Search movies..." />
    </div>
    <div class="movies">
      <div v-for="movie in movies" :key="movie.id" class="movie-item">
        <img :src="movie.image" :alt="movie.title" />
        <h3>{{ movie.title }}</h3>
        <p>{{ movie.description }}</p>
        <button class="close-btn" @click="removeMovie(movie.id)">×</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'MovieGrid',
  data() {
    return {
      search: '',
      movies: [
        { id: 1, title: 'Movie One', description: 'A great movie.', image: require('@/assets/movie1.jpg') },
        { id: 2, title: 'Movie Two', description: 'Another great movie.', image: require('@/assets/movie2.jpg') },
        { id: 3, title: 'Movie Three', description: 'Yet another great movie.', image: require('@/assets/movie3.jpg') }
      ]
    }
  },
  methods: {
    removeMovie(id) {
      this.movies = this.movies.filter(m => m.id !== id);
    },
    onSearch() {
      // API search logic to be implemented
    }
  }
}
</script>

<style scoped>
.movie-grid { padding: 2rem 1rem; }
.movie-grid h2 { text-align: center; margin-bottom: 1.5rem; }
.search-bar { text-align: center; margin-bottom: 1.5rem; }
.search-bar input { padding: 0.5rem 1rem; border: 1px solid #ccc; border-radius: 4px; width: 250px; max-width: 90%; }
.movies { display: flex; gap: 2rem; justify-content: center; flex-wrap: wrap; }
.movie-item { background: #f9f9f9; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.07); padding: 1rem; width: 220px; position: relative; }
.movie-item img { width: 100%; border-radius: 6px; margin-bottom: 0.5rem; }
.movie-item h3 { margin: 0.5rem 0 0.3rem; font-size: 1.1rem; }
.movie-item p { font-size: 0.97rem; color: #555; }
.close-btn { position: absolute; top: 8px; right: 8px; background: #e74c3c; color: #fff; border: none; border-radius: 50%; width: 24px; height: 24px; font-size: 1.1rem; cursor: pointer; line-height: 1; }
.close-btn:hover { background: #c0392b; }
@media (max-width: 900px) {
  .movies { flex-direction: column; align-items: center; }
}
</style>
