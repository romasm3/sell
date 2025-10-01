<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MovieStream - Каталог фильмов</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script defer src="https://unpkg.com/alpinejs@3.x.x/dist/cdn.min.js"></script>
    <style>
        body {
            background-color: #141414;
        }
        .movie-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .movie-card:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.6);
        }
        .category-btn {
            transition: all 0.3s ease;
        }
        .category-btn.active {
            background-color: #e50914;
            color: white;
        }
    </style>
</head>
<body class="bg-[#141414] text-white" x-data="movieApp()">
    
    <!-- Header -->
    <header class="bg-black bg-opacity-90 fixed w-full top-0 z-50 backdrop-blur-sm">
        <div class="container mx-auto px-4 py-4">
            <div class="flex items-center justify-between">
                <div class="flex items-center space-x-8">
                    <h1 class="text-3xl font-bold text-[#e50914]">MovieStream</h1>
                    <nav class="hidden md:flex space-x-6">
                        <a href="#" class="hover:text-gray-300 transition">Главная</a>
                        <a href="#" class="hover:text-gray-300 transition">Фильмы</a>
                        <a href="#" class="hover:text-gray-300 transition">Сериалы</a>
                        <a href="#" class="hover:text-gray-300 transition">Новинки</a>
                        <a href="#" class="hover:text-gray-300 transition">Мой список</a>
                    </nav>
                </div>
                <div class="flex items-center space-x-4">
                    <input type="text" placeholder="Поиск..." 
                           class="bg-black bg-opacity-50 border border-gray-700 rounded px-4 py-2 focus:outline-none focus:border-[#e50914] transition"
                           x-model="searchQuery"
                           @input="filterMovies()">
                    <button class="bg-[#e50914] hover:bg-[#c40812] px-4 py-2 rounded transition">
                        Профиль
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-4 pt-24 pb-12">
        
        <!-- Hero Section -->
        <section class="mb-12">
            <div class="relative h-96 rounded-lg overflow-hidden">
                <img src="https://images.unsplash.com/photo-1536440136628-849c177e76a1?w=1200" 
                     alt="Featured" 
                     class="w-full h-full object-cover">
                <div class="absolute inset-0 bg-gradient-to-r from-black via-black/50 to-transparent">
                    <div class="absolute bottom-12 left-12 max-w-xl">
                        <h2 class="text-5xl font-bold mb-4">Рекомендуемое</h2>
                        <p class="text-lg mb-6 text-gray-300">Откройте для себя лучшие фильмы и сериалы. Смотрите без ограничений в любое время.</p>
                        <div class="flex space-x-4">
                            <button class="bg-white text-black px-8 py-3 rounded font-semibold hover:bg-gray-200 transition flex items-center">
                                <svg class="w-6 h-6 mr-2" fill="currentColor" viewBox="0 0 20 20">
                                    <path d="M6.3 2.841A1.5 1.5 0 004 4.11V15.89a1.5 1.5 0 002.3 1.269l9.344-5.89a1.5 1.5 0 000-2.538L6.3 2.84z"/>
                                </svg>
                                Смотреть
                            </button>
                            <button class="bg-gray-700 bg-opacity-70 px-8 py-3 rounded font-semibold hover:bg-gray-600 transition">
                                Подробнее
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Categories Filter -->
        <section class="mb-8">
            <div class="flex flex-wrap gap-3">
                <button @click="selectedCategory = 'all'; filterMovies()" 
                        class="category-btn px-6 py-2 rounded-full border border-gray-700 hover:border-white transition"
                        :class="{'active': selectedCategory === 'all'}">
                    Все
                </button>
                <template x-for="category in categories" :key="category">
                    <button @click="selectedCategory = category; filterMovies()" 
                            class="category-btn px-6 py-2 rounded-full border border-gray-700 hover:border-white transition"
                            :class="{'active': selectedCategory === category}"
                            x-text="category">
                    </button>
                </template>
            </div>
        </section>

        <!-- Movies Grid -->
        <section>
            <h2 class="text-2xl font-bold mb-6" x-text="selectedCategory === 'all' ? 'Все фильмы' : selectedCategory"></h2>
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-4">
                <template x-for="movie in filteredMovies" :key="movie.id">
                    <div class="movie-card cursor-pointer">
                        <div class="relative rounded-lg overflow-hidden bg-gray-900">
                            <img :src="movie.poster" 
                                 :alt="movie.title" 
                                 class="w-full h-72 object-cover">
                            <div class="absolute inset-0 bg-black bg-opacity-0 hover:bg-opacity-70 transition flex items-center justify-center opacity-0 hover:opacity-100">
                                <button class="bg-[#e50914] p-4 rounded-full hover:scale-110 transition">
                                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 20 20">
                                        <path d="M6.3 2.841A1.5 1.5 0 004 4.11V15.89a1.5 1.5 0 002.3 1.269l9.344-5.89a1.5 1.5 0 000-2.538L6.3 2.84z"/>
                                    </svg>
                                </button>
                            </div>
                            <div class="absolute top-2 right-2 bg-black bg-opacity-75 px-2 py-1 rounded text-sm">
                                <span x-text="movie.rating"></span> ⭐
                            </div>
                        </div>
                        <div class="mt-2">
                            <h3 class="font-semibold truncate" x-text="movie.title"></h3>
                            <p class="text-sm text-gray-400" x-text="movie.year"></p>
                        </div>
                    </div>
                </template>
            </div>

            <!-- No Results -->
            <div x-show="filteredMovies.length === 0" class="text-center py-12">
                <p class="text-gray-400 text-xl">Фильмы не найдены</p>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-black bg-opacity-50 mt-16 py-12 border-t border-gray-800">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                <div>
                    <h3 class="text-xl font-bold text-[#e50914] mb-4">MovieStream</h3>
                    <p class="text-gray-400">Смотрите фильмы и сериалы в любое время, в любом месте.</p>
                </div>
                <div>
                    <h4 class="font-semibold mb-4">Навигация</h4>
                    <ul class="space-y-2 text-gray-400">
                        <li><a href="#" class="hover:text-white transition">Главная</a></li>
                        <li><a href="#" class="hover:text-white transition">Фильмы</a></li>
                        <li><a href="#" class="hover:text-white transition">Сериалы</a></li>
                        <li><a href="#" class="hover:text-white transition">Новинки</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-semibold mb-4">Поддержка</h4>
                    <ul class="space-y-2 text-gray-400">
                        <li><a href="#" class="hover:text-white transition">Помощь</a></li>
                        <li><a href="#" class="hover:text-white transition">FAQ</a></li>
                        <li><a href="#" class="hover:text-white transition">Контакты</a></li>
                        <li><a href="#" class="hover:text-white transition">Подписка</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-semibold mb-4">Юридическая информация</h4>
                    <ul class="space-y-2 text-gray-400">
                        <li><a href="#" class="hover:text-white transition">Условия использования</a></li>
                        <li><a href="#" class="hover:text-white transition">Конфиденциальность</a></li>
                        <li><a href="#" class="hover:text-white transition">Cookie</a></li>
                    </ul>
                </div>
            </div>
            <div class="mt-8 pt-8 border-t border-gray-800 text-center text-gray-400">
                <p>&copy; 2025 MovieStream. Все права защищены.</p>
            </div>
        </div>
    </footer>

    <script>
        function movieApp() {
            return {
                selectedCategory: 'all',
                searchQuery: '',
                categories: ['Боевик', 'Комедия', 'Драма', 'Фантастика', 'Триллер', 'Ужасы'],
                movies: [
                    { id: 1, title: 'Начало', category: 'Фантастика', year: 2010, rating: 8.8, poster: 'https://images.unsplash.com/photo-1440404653325-ab127d49abc1?w=400' },
                    { id: 2, title: 'Темный рыцарь', category: 'Боевик', year: 2008, rating: 9.0, poster: 'https://images.unsplash.com/photo-1509347528160-9a9e33742cdb?w=400' },
                    { id: 3, title: 'Форрест Гамп', category: 'Драма', year: 1994, rating: 8.8, poster: 'https://images.unsplash.com/photo-1485846234645-a62644f84728?w=400' },
                    { id: 4, title: 'Матрица', category: 'Фантастика', year: 1999, rating: 8.7, poster: 'https://images.unsplash.com/photo-1478720568477-152d9b164e26?w=400' },
                    { id: 5, title: 'Джокер', category: 'Триллер', year: 2019, rating: 8.4, poster: 'https://images.unsplash.com/photo-1534447677768-be436bb09401?w=400' },
                    { id: 6, title: 'Крик', category: 'Ужасы', year: 1996, rating: 7.3, poster: 'https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?w=400' },
                    { id: 7, title: 'Дэдпул', category: 'Комедия', year: 2016, rating: 8.0, poster: 'https://images.unsplash.com/photo-1594908900066-3f47337549d8?w=400' },
                    { id: 8, title: 'Мстители', category: 'Боевик', year: 2012, rating: 8.0, poster: 'https://images.unsplash.com/photo-1608889825205-eebdb9fc5806?w=400' },
                    { id: 9, title: 'Интерстеллар', category: 'Фантастика', year: 2014, rating: 8.6, poster: 'https://images.unsplash.com/photo-1419242902214-272b3f66ee7a?w=400' },
                    { id: 10, title: 'Молчание ягнят', category: 'Триллер', year: 1991, rating: 8.6, poster: 'https://images.unsplash.com/photo-1518676590629-3dcbd9c5a5c9?w=400' },
                ],
                filteredMovies: [],
                
                init() {
                    this.filteredMovies = this.movies;
                },
                
                filterMovies() {
                    let filtered = this.movies;
                    
                    if (this.selectedCategory !== 'all') {
                        filtered = filtered.filter(movie => movie.category === this.selectedCategory);
                    }
                    
                    if (this.searchQuery.trim() !== '') {
                        const query = this.searchQuery.toLowerCase();
                        filtered = filtered.filter(movie => 
                            movie.title.toLowerCase().includes(query) ||
                            movie.category.toLowerCase().includes(query)
                        );
                    }
                    
                    this.filteredMovies = filtered;
                }
            }
        }
    </script>
</body>
</html>
