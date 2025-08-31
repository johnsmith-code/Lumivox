# Lumivox
Lumivox Web Devloper 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lumivox - Premium Graphics Design Studio</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f0c29 0%, #302b63 50%, #24243e 100%);
            color: #ffffff;
            overflow-x: hidden;
            position: relative;
        }

        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
        }

        .glass-effect {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .nav-item {
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-item::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4);
            bottom: -5px;
            left: 0;
            transition: width 0.3s ease;
        }

        .nav-item:hover::after {
            width: 100%;
        }

        .project-card {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            transform-style: preserve-3d;
        }

        .project-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
        }

        .gradient-text {
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-size: 300% 300%;
            animation: gradient 3s ease infinite;
        }

        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .floating {
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
            100% { transform: translateY(0px); }
        }

        .typewriter {
            overflow: hidden;
            border-right: 3px solid #4ecdc4;
            white-space: nowrap;
            animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: #4ecdc4; }
        }

        .counter {
            font-size: 3rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .testimonial-card {
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .testimonial-card:hover {
            transform: translateY(-5px) rotate(2deg);
        }

        .team-member {
            transition: all 0.3s ease;
        }

        .team-member:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
        }

        .social-icon {
            transition: all 0.3s ease;
        }

        .social-icon:hover {
            transform: translateY(-3px) scale(1.1);
        }

        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            width: 0%;
            height: 4px;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4);
            z-index: 1000;
            transition: width 0.3s ease;
        }

        .theme-toggle {
            position: fixed;
            right: 30px;
            bottom: 30px;
            z-index: 1000;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
        }

        .theme-toggle:hover {
            transform: scale(1.1) rotate(180deg);
        }

        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #0f0c29 0%, #302b63 50%, #24243e 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }

        .loader {
            width: 50px;
            height: 50px;
            border: 3px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            border-top: 3px solid #4ecdc4;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .parallax {
            background-attachment: fixed;
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
        }
    </style>
</head>
<body class="min-h-screen">
    <!-- Loading Screen -->
    <div id="loading" class="loading-screen">
        <div class="loader"></div>
    </div>

    <!-- Scroll Progress Bar -->
    <div class="scroll-progress" id="scroll-progress"></div>

    <!-- Theme Toggle -->
    <div class="theme-toggle" id="theme-toggle">
        <i class="fas fa-moon text-white"></i>
    </div>

    <!-- Particle Background -->
    <div id="particles-js"></div>

    <!-- Lateral Navigation -->
    <nav class="fixed left-0 top-0 h-full w-20 md:w-24 z-50 flex flex-col items-center py-8 glass-effect">
        <div class="mb-12">
            <div class="w-12 h-12 bg-gradient-to-r from-purple-500 to-pink-500 rounded-full flex items-center justify-center text-white font-bold text-xl">
                LV
            </div>
        </div>
        
        <div class="flex flex-col space-y-10 items-center">
            <a href="#home" class="nav-item text-white hover:text-purple-300 p-3 rounded-full hover:bg-white/10">
                <i class="fas fa-home text-xl"></i>
            </a>
            <a href="#services" class="nav-item text-white hover:text-purple-300 p-3 rounded-full hover:bg-white/10">
                <i class="fas fa-palette text-xl"></i>
            </a>
            <a href="#portfolio" class="nav-item text-white hover:text-purple-300 p-3 rounded-full hover:bg-white/10">
                <i class="fas fa-images text-xl"></i>
            </a>
            <a href="#stats" class="nav-item text-white hover:text-purple-300 p-3 rounded-full hover:bg-white/10">
                <i class="fas fa-chart-line text-xl"></i>
            </a>
            
            <a href="#contact" class="nav-item text-white hover:text-purple-300 p-3 rounded-full hover:bg-white/10">
                <i class="fas fa-envelope text-xl"></i>
            </a>
        </div>

        <div class="mt-auto">
            <button class="bg-gradient-to-r from-purple-500 to-pink-500 text-white px-6 py-3 rounded-full font-semibold hover:from-purple-600 hover:to-pink-600 transition-all duration-300 transform hover:scale-105">
                Start Project
            </button>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="ml-20 md:ml-24 p-8">
        <!-- Hero Section -->
        <section id="home" class="min-h-screen flex items-center justify-center">
            <div class="text-center max-w-4xl">
                <h1 class="text-5xl md:text-7xl font-bold mb-6 gradient-text">
                    Transform Your <span class="typewriter">Vision into Reality</span>
                </h1>
                <p class="text-xl text-gray-300 mb-8">
                    Lumivox crafts stunning visual experiences that captivate audiences and elevate brands to new heights
                </p>
                <div class="space-x-6">
                    <button class="bg-gradient-to-r from-purple-500 to-pink-500 text-white px-8 py-4 rounded-full font-semibold text-lg hover:from-purple-600 hover:to-pink-600 transition-all duration-300 transform hover:scale-105">
                        Explore Our Work
                    </button>
                    <button class="border-2 border-purple-500 text-purple-300 px-8 py-4 rounded-full font-semibold text-lg hover:bg-purple-500 hover:text-white transition-all duration-300">
                        Contact Us
                    </button>
                </div>
                <div class="mt-12 floating">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/1cfbfa57-c0e8-4dde-9ce1-7f66241e9d6a.png" alt="Modern graphic design workspace showing multiple screens with design software interfaces and creative tools organized on a sleek desk" class="rounded-2xl mx-auto shadow-2xl" onerror="this.style.display='none'">
                </div>
            </div>
        </section>

        <!-- Statistics Section -->
        <section id="stats" class="py-20">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-8 text-center">
                <div class="glass-effect p-8 rounded-2xl">
                    <div class="counter" data-target="250">0</div>
                    <p class="text-gray-300 mt-2">Projects Completed</p>
                </div>
                <div class="glass-effect p-8 rounded-2xl">
                    <div class="counter" data-target="98">0</div>
                    <p class="text-gray-300 mt-2">Happy Clients</p>
                </div>
                <div class="glass-effect p-8 rounded-2xl">
                    <div class="counter" data-target="15">0</div>
                    <p class="text-gray-300 mt-2">Awards Won</p>
                </div>
                <div class="glass-effect p-8 rounded-2xl">
                    <div class="counter" data-target="500">0</div>
                    <p class="text-gray-300 mt-2">Cups of Coffee</p>
                </div>
            </div>
        </section>

        <!-- Services Section -->
        <section id="services" class="py-20">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-bold gradient-text mb-4">Our Creative Arsenal</h2>
                <p class="text-xl text-gray-300">Comprehensive design solutions tailored to your unique needs</p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8">
                <div class="glass-effect p-8 rounded-2xl project-card">
                    <div class="w-16 h-16 bg-purple-500 rounded-xl flex items-center justify-center mb-6">
                        <i class="fas fa-paint-brush text-2xl text-white"></i>
                    </div>
                    <h3 class="text-2xl font-semibold mb-4">Brand Identity</h3>
                    <p class="text-gray-300 mb-4">Craft memorable logos and brand systems that tell your unique story</p>
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/8784211b-8a58-4d7f-8afa-562cf2197e5e.png" alt="Colorful brand identity showcase with logo variations, typography, and brand guidelines on a modern presentation board" class="rounded-xl mb-4" onerror="this.style.display='none'">
                    <a href="#" class="text-purple-400 hover:text-purple-300 font-semibold">Learn More →</a>
                </div>

                <div class="glass-effect p-8 rounded-2xl project-card">
                    <div class="w-16 h-16 bg-blue-500 rounded-xl flex items-center justify-center mb-6">
                        <i class="fas fa-desktop text-2xl text-white"></i>
                    </div>
                    <h3 class="text-2xl font-semibold mb-4">UI/UX Design</h3>
                    <p class="text-gray-300 mb-4">Intuitive and beautiful digital experiences that users love to interact with</p>
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/b813f90a-b276-4823-be55-acfb2f2f5f36.png" alt="Modern user interface design mockup showing app screens with clean layouts and intuitive navigation on multiple devices" class="rounded-xl mb-4" onerror="this.style.display='none'">
                    <a href="#" class="text-blue-400 hover:text-blue-300 font-semibold">Learn More →</a>
                </div>

                <div class="glass-effect p-8 rounded-2xl project-card">
                    <div class="w-16 h-16 bg-green-500 rounded-xl flex items-center justify-center mb-6">
                        <i class="fas fa-film text-2xl text-white"></i>
                    </div>
                    <h3 class="text-2xl font-semibold mb-4">Motion Graphics</h3>
                    <p class="text-gray-300 mb-4">Bring your brand to life with captivating animations and visual storytelling</p>
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/b176f982-d6b2-46bc-aa81-e5b308290a3c.png" alt="Dynamic motion graphics workspace showing animation timelines, video editing software, and visual effects in progress" class="rounded-xl mb-4" onerror="this.style.display='none'">
                    <a href="#" class="text-green-400 hover:text-green-300 font-semibold">Learn More →</a>
                </div>
            </div>
        </section>

        <!-- Portfolio Showcase -->
        <section id="portfolio" class="py-20">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-bold gradient-text mb-4">Featured Work</h2>
                <p class="text-xl text-gray-300">A glimpse into our creative universe</p>
            </div>

            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div class="glass-effect rounded-2xl overflow-hidden project-card">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/88e556de-5abd-4cd8-bebf-89340a23833b.png" alt="Futuristic tech company rebrand with geometric patterns and vibrant color gradients across digital and print media" class="w-full h-48 object-cover" onerror="this.style.display='none'">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2">NexTech Rebrand</h3>
                        <p class="text-gray-300">Complete brand transformation for tech startup</p>
                    </div>
                </div>

                <div class="glass-effect rounded-2xl overflow-hidden project-card">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/763dfe6b-6f38-46c7-a420-16d59037d479.png" alt="Luxury fashion e-commerce platform with elegant typography, product photography, and seamless user experience design" class="w-full h-48 object-cover" onerror="this.style.display='none'">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2">Aurea Fashion</h3>
                        <p class="text-gray-300">Premium e-commerce experience design</p>
                    </div>
                </div>

                <div class="glass-effect rounded-2xl overflow-hidden project-card">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/839f5fcc-f97a-4ae7-a1e9-7e8857bcd219.png" alt="Corporate website redesign with interactive data visualizations, modern interface elements, and responsive design components" class="w-full h-48 object-cover" onerror="this.style.display='none'">
                    <div class="p-6">
                        <h3 class="text-xl font-semibold mb-2">GlobalCorp Website</h3>
                        <p class="text-gray-300">Enterprise website redesign</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Testimonials Section -->
        <section class="py-20">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-bold gradient-text mb-4">Client Love</h2>
                <p class="text-xl text-gray-300">What our amazing clients say about us</p>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <div class="glass-effect p-8 rounded-2xl testimonial-card">
                    <div class="flex items-center mb-6">
                        <div class="w-12 h-12 bg-gradient-to-r from-purple-500 to-pink-500 rounded-full flex items-center justify-center text-white font-bold">
                            JD
                        </div>
                        <div class="ml-4">
                            <h4 class="font-semibold">John Doe</h4>
                            <p class="text-purple-400">CEO, TechStart</p>
                        </div>
                    </div>
                    <p class="text-gray-300 italic">"Lumivox transformed our brand identity completely. Their attention to detail and creativity exceeded our expectations!"</p>
                    <div class="mt-4 text-yellow-400">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                    </div>
                </div>

                <div class="glass-effect p-8 rounded-2xl testimonial-card">
                    <div class="flex items-center mb-6">
                        <div class="w-12 h-12 bg-gradient-to-r from-blue-500 to-cyan-500 rounded-full flex items-center justify-center text-white font-bold">
                            SM
                        </div>
                        <div class="ml-4">
                            <h4 class="font-semibold">Sarah Miller</h4>
                            <p class="text-blue-400">Marketing Director</p>
                        </div>
                    </div>
                    <p class="text-gray-300 italic">"The UI/UX design work was phenomenal. Our conversion rates increased by 40% after the redesign. Absolutely worth it!"</p>
                    <div class="mt-4 text-yellow-400">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                    </div>
                </div>

                <div class="glass-effect p-8 rounded-2xl testimonial-card">
                    <div class="flex items-center mb-6">
                        <div class="w-12 h-12 bg-gradient-to-r from-green-500 to-teal-500 rounded-full flex items-center justify-center text-white font-bold">
                            MJ
                        </div>
                        <div class="ml-4">
                            <h4 class="font-semibold">Mike Johnson</h4>
                            <p class="text-green-400">Creative Director</p>
                        </div>
                    </div>
                    <p class="text-gray-300 italic">"The motion graphics they created for our campaign went viral! Lumivox understands modern visual storytelling perfectly."</p>
                    <div class="mt-4 text-yellow-400">
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                        <i class="fas fa-star"></i>
                    </div>
                </div>
            </div>
        </section>

        

        <!-- Newsletter Section -->
        <section class="py-20">
            <div class="glass-effect p-12 rounded-3xl text-center">
                <h2 class="text-3xl font-bold gradient-text mb-4">Stay in the Creative Loop</h2>
                <p class="text-xl text-gray-300 mb-8">Get exclusive design insights and project updates</p>
                
                <div class="max-w-md mx-auto flex">
                    <input type="email" placeholder="Enter your email" class="flex-1 bg-white/5 border border-white/10 rounded-l-xl px-4 py-3 text-white focus:outline-none focus:ring-2 focus:ring-purple-500">
                    <button class="bg-gradient-to-r from-purple-500 to-pink-500 text-white px-6 py-3 rounded-r-xl font-semibold hover:from-purple-600 hover:to-pink-600 transition-all duration-300">
                        Subscribe
                    </button>
                </div>
            </div>
        </section>

        <!-- Contact Form -->
        <section id="contact" class="py-20">
            <div class="max-w-4xl mx-auto glass-effect p-12 rounded-3xl">
                <div class="text-center mb-12">
                    <h2 class="text-4xl font-bold gradient-text mb-4">Ready to Create Magic?</h2>
                    <p class="text-xl text-gray-300">Tell us about your project and let's make something extraordinary together</p>
                </div>

                <form class="space-y-6">
                    <div class="grid md:grid-cols-2 gap-6">
                        <div>
                            <label class="block text-gray-300 mb-2">Your Name</label>
                            <input type="text" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3 text-white focus:outline-none focus:ring-2 focus:ring-purple-500">
                        </div>
                        <div>
                            <label class="block text-gray-300 mb-2">Email Address</label>
                            <input type="email" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3 text-white focus:outline-none focus:ring-2 focus:ring-purple-500">
                        </div>
                    </div>

                    <div>
                        <label class="block text-gray-300 mb-2">Project Type</label>
                        <select class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3 text-white focus:outline-none focus:ring-2 focus:ring-purple-500">
                            <option>Brand Identity</option>
                            <option>UI/UX Design</option>
                            <option>Motion Graphics</option>
                            <option>Web Design</option>
                            <option>Other</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-gray-300 mb-2">Project Details</label>
                        <textarea rows="5" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3 text-white focus:outline-none focus:ring-2 focus:ring-purple-500"></textarea>
                    </div>

                    <div>
                        <label class="block text-gray-300 mb-2">Upload Files (Optional)</label>
                        <div class="border-2 border-dashed border-white/20 rounded-xl p-8 text-center">
                            <i class="fas fa-cloud-upload-alt text-3xl text-gray-400 mb-2"></i>
                            <p class="text-gray-400">Drag & drop files here or click to browse</p>
                        </div>
                    </div>

                    <button type="submit" class="w-full bg-gradient-to-r from-purple-500 to-pink-500 text-white py-4 rounded-xl font-semibold text-lg hover:from-purple-600 hover:to-pink-600 transition-all duration-300">
                        Send Project Brief
                    </button>
                </form>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="ml-20 md:ml-24 p-8 glass-effect rounded-3xl mt-20">
        <div class="grid md:grid-cols-4 gap-8">
            <div>
                <div class="w-16 h-16 bg-gradient-to-r from-purple-500 to-pink-500 rounded-full flex items-center justify-center text-white font-bold text-2xl mb-4">
                    LV
                </div>
                <p class="text-gray-300">Transforming visions into extraordinary visual experiences.</p>
            </div>

            <div>
                <h3 class="text-xl font-semibold mb-4">Quick Links</h3>
                <ul class="space-y-2">
                    <li><a href="#home" class="text-gray-300 hover:text-purple-300">Home</a></li>
                    <li><a href="#services" class="text-gray-300 hover:text-purple-300">Services</a></li>
                    <li><a href="#portfolio" class="text-gray-300 hover:text-purple-300">Portfolio</a></li>
                    <li><a href="#contact" class="text-gray-300 hover:text-purple-300">Contact</a></li>
                </ul>
            </div>

            <div>
                <h3 class="text-xl font-semibold mb-4">Services</h3>
                <ul class="space-y-2">
                    <li><a href="#" class="text-gray-300 hover:text-purple-300">Brand Identity</a></li>
                    <li><a href="#" class="text-gray-300 hover:text-purple-300">UI/UX Design</a></li>
                    <li><a href="#" class="text-gray-300 hover:text-purple-300">Motion Graphics</a></li>
                    <li><a href="#" class="text-gray-300 hover:text-purple-300">Web Design</a></li>
                </ul>
            </div>

            <div>
                <h3 class="text-xl font-semibold mb-4">Connect</h3>
                <div class="flex space-x-4 mb-4">
                    <a href="#" class="social-icon text-gray-300 hover:text-purple-300">
                        <i class="fab fa-dribbble text-xl"></i>
                    </a>
                    <a href="#" class="social-icon text-gray-300 hover:text-purple-300">
                        <i class="fab fa-behance text-xl"></i>
                    </a>
                    <a href="#" class="social-icon text-gray-300 hover:text-purple-300">
                        <i class="fab fa-instagram text-xl"></i>
                    </a>
                    <a href="#" class="social-icon text-gray-300 hover:text-purple-300">
                        <i class="fab fa-linkedin text-xl"></i>
                    </a>
                </div>
                <p class="text-gray-300">namandixit2116@gmail.com</p>
                <p class="text-gray-300">+1 (555) 123-4567</p>
            </div>
        </div>

        <div class="border-t border-white/10 mt-8 pt-8 text-center">
            <p class="text-gray-400">© 2024 Lumivox. All rights reserved.</p>
        </div>
    </footer>

    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script>
        // Loading screen
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.getElementById('loading').style.opacity = '0';
                setTimeout(() => {
                    document.getElementById('loading').style.display = 'none';
                }, 500);
            }, 1500);
        });

        // Particles.js configuration
        particlesJS('particles-js', {
            particles: {
                number: { value: 80, density: { enable: true, value_area: 800 } },
                color: { value: "#ffffff" },
                shape: { type: "circle" },
                opacity: { value: 0.3, random: true },
                size: { value: 3, random: true },
                line_linked: {
                    enable: true,
                    distance: 150,
                    color: "#ffffff",
                    opacity: 0.1,
                    width: 1
                },
                move: {
                    enable: true,
                    speed: 2,
                    direction: "none",
                    random: true,
                    straight: false,
                    out_mode: "out",
                    bounce: false
                }
            },
            interactivity: {
                detect_on: "canvas",
                events: {
                    onhover: { enable: true, mode: "repulse" },
                    onclick: { enable: true, mode: "push" },
                    resize: true
                }
            }
        });

        // Scroll progress bar
        window.addEventListener('scroll', () => {
            const scrollProgress = document.getElementById('scroll-progress');
            const scrollTop = document.documentElement.scrollTop;
            const scrollHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrollPercent = (scrollTop / scrollHeight) * 100;
            scrollProgress.style.width = scrollPercent + '%';
        });

        // Counter animation
        const counters = document.querySelectorAll('.counter');
        const speed = 200;

        counters.forEach(counter => {
            const updateCount = () => {
                const target = +counter.getAttribute('data-target');
                const count = +counter.innerText;
                const inc = target / speed;

                if (count < target) {
                    counter.innerText = Math.ceil(count + inc);
                    setTimeout(updateCount, 1);
                } else {
                    counter.innerText = target;
                }
            };

            updateCount();
        });

        // Smooth scrolling for navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Add hover effects to project cards
        const projectCards = document.querySelectorAll('.project-card');
        projectCards.forEach(card => {
            card.addEventListener('mouseenter', () => {
                card.style.transform = 'translateY(-10px) scale(1.02)';
            });
            card.addEventListener('mouseleave', () => {
                card.style.transform = 'translateY(0) scale(1)';
            });
        });

        // Theme toggle
        const themeToggle = document.getElementById('theme-toggle');
        themeToggle.addEventListener('click', () => {
            document.body.classList.toggle('light-mode');
            const icon = themeToggle.querySelector('i');
            if (document.body.classList.contains('light-mode')) {
                icon.className = 'fas fa-sun text-white';
                document.body.style.background = 'linear-gradient(135deg, #ffffff 0%, #f0f0f0 50%, #e0e0e0 100%)';
                document.body.style.color = '#333333';
            } else {
                icon.className = 'fas fa-moon text-white';
                document.body.style.background = 'linear-gradient(135deg, #0f0c29 0%, #302b63 50%, #24243e 100%)';
                document.body.style.color = '#ffffff';
            }
        });

        // Form validation
        const contactForm = document.querySelector('form');
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Thank you for your submission! We\'ll get back to you within 24 hours.');
            contactForm.reset();
        });

        // Newsletter subscription
        const newsletterForm = document.querySelector('.newsletter-form');
        if (newsletterForm) {
            newsletterForm.addEventListener('submit', (e) => {
                e.preventDefault();
                alert('Thank you for subscribing to our newsletter!');
                newsletterForm.reset();
            });
        }
    </script>
</body>
</html>
