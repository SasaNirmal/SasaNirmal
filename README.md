<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sasanka Nirmal - Interactive Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'JetBrains Mono', 'Courier New', monospace;
            background: linear-gradient(135deg, #0f0f23, #1a1a2e, #16213e);
            color: #00FF99;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .header {
            text-align: center;
            padding: 60px 0;
            position: relative;
        }
        
        .typing-animation {
            font-size: 2.5rem;
            font-weight: bold;
            margin-bottom: 30px;
            color: #00FF99;
            text-shadow: 0 0 20px rgba(0, 255, 153, 0.5);
        }
        
        .badge-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            margin: 30px 0;
        }
        
        .badge {
            padding: 8px 16px;
            border-radius: 20px;
            background: rgba(0, 255, 153, 0.1);
            border: 1px solid #00FF99;
            color: #00FF99;
            text-decoration: none;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .badge:hover {
            background: #00FF99;
            color: #0f0f23;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 255, 153, 0.3);
        }
        
        .section {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 30px;
            margin: 30px 0;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0, 255, 153, 0.2);
            transition: transform 0.3s ease;
        }
        
        .section:hover {
            transform: translateY(-5px);
        }
        
        .section-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: #00FF99;
            text-align: center;
            position: relative;
        }
        
        .section-title::after {
            content: '';
            width: 50px;
            height: 2px;
            background: #00FF99;
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-top: 20px;
        }
        
        .about-info {
            color: #ccc;
        }
        
        .about-info p {
            margin-bottom: 15px;
        }
        
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .skill-category {
            background: rgba(0, 255, 153, 0.1);
            padding: 20px;
            border-radius: 10px;
            border: 1px solid rgba(0, 255, 153, 0.3);
        }
        
        .skill-category h3 {
            color: #00FF99;
            margin-bottom: 15px;
        }
        
        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }
        
        .skill-tag {
            background: rgba(0, 255, 153, 0.2);
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 0.9rem;
            color: #fff;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .skill-tag:hover {
            background: #00FF99;
            color: #0f0f23;
        }
        
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }
        
        .project-card {
            background: rgba(0, 255, 153, 0.05);
            border: 1px solid rgba(0, 255, 153, 0.3);
            border-radius: 15px;
            padding: 25px;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 255, 153, 0.2);
        }
        
        .project-title {
            color: #00FF99;
            font-size: 1.3rem;
            margin-bottom: 10px;
        }
        
        .project-description {
            color: #ccc;
            margin-bottom: 15px;
        }
        
        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 15px;
        }
        
        .tech-badge {
            background: rgba(0, 255, 153, 0.2);
            padding: 3px 8px;
            border-radius: 10px;
            font-size: 0.8rem;
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .stat-card {
            background: rgba(0, 255, 153, 0.1);
            border: 1px solid rgba(0, 255, 153, 0.3);
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            transition: all 0.3s ease;
        }
        
        .stat-card:hover {
            transform: scale(1.05);
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: #00FF99;
            margin-bottom: 5px;
        }
        
        .terminal {
            background: #000;
            color: #00FF99;
            padding: 20px;
            border-radius: 10px;
            font-family: 'JetBrains Mono', monospace;
            margin: 20px 0;
            position: relative;
            overflow: hidden;
        }
        
        .terminal-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .terminal-buttons {
            display: flex;
            gap: 8px;
        }
        
        .terminal-button {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }
        
        .red { background: #ff5555; }
        .yellow { background: #ffb86c; }
        .green { background: #50fa7b; }
        
        .terminal-content {
            font-size: 0.9rem;
        }
        
        .command {
            color: #8be9fd;
        }
        
        .output {
            color: #f8f8f2;
            margin-bottom: 10px;
        }
        
        .contact-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 30px;
        }
        
        .contact-link {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 12px 24px;
            background: rgba(0, 255, 153, 0.1);
            border: 1px solid #00FF99;
            border-radius: 25px;
            color: #00FF99;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .contact-link:hover {
            background: #00FF99;
            color: #0f0f23;
            transform: translateY(-3px);
        }
        
        .interactive-element {
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .interactive-element:hover {
            color: #fff;
        }
        
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
        }
        
        .modal-content {
            background: linear-gradient(135deg, #1a1a2e, #16213e);
            margin: 15% auto;
            padding: 30px;
            border-radius: 15px;
            width: 80%;
            max-width: 600px;
            border: 1px solid #00FF99;
        }
        
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }
        
        .close:hover {
            color: #00FF99;
        }
        
        @media (max-width: 768px) {
            .about-grid {
                grid-template-columns: 1fr;
            }
            
            .typing-animation {
                font-size: 1.8rem;
            }
            
            .badge-container {
                gap: 10px;
            }
        }
        
        .progress-bar {
            width: 100%;
            height: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            overflow: hidden;
            margin: 10px 0;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #00FF99, #00cc7a);
            border-radius: 10px;
            transition: width 2s ease;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Section -->
        <header class="header">
            <div class="typing-animation" id="typingText">Hello World! I'm Sasanka Nirmal!</div>
            <div class="badge-container">
                <span class="badge interactive-element" onclick="showTerminal()">🐧 Linux Expert</span>
                <span class="badge interactive-element" onclick="showSkills()">💻 Developer</span>
                <span class="badge interactive-element" onclick="showStats()">📊 GitHub Stats</span>
                <span class="badge interactive-element" onclick="showProjects()">🚀 Projects</span>
            </div>
        </header>

        <!-- About Section -->
        <section class="section">
            <h2 class="section-title">👨‍💻 About Me</h2>
            <div class="about-grid">
                <div class="about-info">
                    <p>I'm <strong>Sasanka Nirmal</strong>, a passionate software developer and Linux enthusiast from Wellawaya, Sri Lanka. I thrive on exploring the command line, automating workflows, and contributing to open-source projects.</p>
                    <p><strong>📍 Location:</strong> Wellawaya, Sri Lanka</p>
                    <p><strong>📧 Email:</strong> sasanpathirage@gmail.com</p>
                    <p><strong>🎯 Goal:</strong> Automate the world, one script at a time!</p>
                </div>
                <div class="terminal">
                    <div class="terminal-header">
                        <div class="terminal-buttons">
                            <div class="terminal-button red"></div>
                            <div class="terminal-button yellow"></div>
                            <div class="terminal-button green"></div>
                        </div>
                        <span style="margin-left: 10px;">sasanka@linux:~$</span>
                    </div>
                    <div class="terminal-content">
                        <div><span class="command">$ whoami</span></div>
                        <div class="output">sasanka_nirmal - passionate_developer</div>
                        <div><span class="command">$ cat mission.txt</span></div>
                        <div class="output">Building tools that make life easier!</div>
                        <div><span class="command">$ echo $PASSION</span></div>
                        <div class="output">Linux + Bash + Open Source = ❤️</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Skills Section -->
        <section class="section" id="skillsSection">
            <h2 class="section-title">🛠️ Skills & Tech Stack</h2>
            <div class="skills-grid">
                <div class="skill-category">
                    <h3>Languages</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Python</span>
                        <span class="skill-tag">Bash</span>
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">Java</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h3>Frameworks/Tools</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Node.js</span>
                        <span class="skill-tag">Django</span>
                        <span class="skill-tag">Docker</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h3>DevOps</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Linux</span>
                        <span class="skill-tag">Git</span>
                        <span class="skill-tag">Kubernetes</span>
                    </div>
                </div>
                <div class="skill-category">
                    <h3>Databases</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">MongoDB</span>
                        <span class="skill-tag">MySQL</span>
                        <span class="skill-tag">Supabase</span>
                    </div>
                </div>
            </div>
            
            <!-- Progress Bars -->
            <div style="margin-top: 30px;">
                <h3 style="color: #00FF99; margin-bottom: 20px;">Current Learning Progress</h3>
                <div>
                    <label>Bash Scripting</label>
                    <div class="progress-bar">
                        <div class="progress-fill" id="bashProgress" style="width: 0%"></div>
                    </div>
                </div>
                <div>
                    <label>Linux SysAdmin</label>
                    <div class="progress-bar">
                        <div class="progress-fill" id="linuxProgress" style="width: 0%"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section class="section" id="projectsSection">
            <h2 class="section-title">🌟 Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card interactive-element" onclick="openProject('library')">
                    <h3 class="project-title">📚 LibrarySystem</h3>
                    <p class="project-description">A robust library management system for books, users, and transactions with advanced features.</p>
                    <div class="project-tech">
                        <span class="tech-badge">Python</span>
                        <span class="tech-badge">Django</span>
                        <span class="tech-badge">MySQL</span>
                    </div>
                    <p style="color: #00FF99;">⭐ Click to explore features</p>
                </div>
                
                <div class="project-card interactive-element" onclick="openProject('bash')">
                    <h3 class="project-title">⚡ Bash Automation Toolkit</h3>
                    <p class="project-description">A collection of powerful Bash scripts for automating file management and system tasks.</p>
                    <div class="project-tech">
                        <span class="tech-badge">Bash</span>
                        <span class="tech-badge">Linux</span>
                        <span class="tech-badge">Shell</span>
                    </div>
                    <p style="color: #00FF99;">⭐ View automation scripts</p>
                </div>
                
                <div class="project-card interactive-element" onclick="openProject('web')">
                    <h3 class="project-title">🌐 Task Tracker Pro</h3>
                    <p class="project-description">A modern task-tracking web app with real-time updates and collaborative features.</p>
                    <div class="project-tech">
                        <span class="tech-badge">React</span>
                        <span class="tech-badge">Node.js</span>
                        <span class="tech-badge">MongoDB</span>
                    </div>
                    <p style="color: #00FF99;">⭐ Live demo available</p>
                </div>
            </div>
        </section>

        <!-- GitHub Stats Section -->
        <section class="section" id="statsSection">
            <h2 class="section-title">📊 GitHub Stats</h2>
            <div class="stats-container">
                <div class="stat-card interactive-element" onclick="animateStats()">
                    <div class="stat-number" id="repoCount">25+</div>
                    <div>Public Repositories</div>
                </div>
                <div class="stat-card interactive-element" onclick="animateStats()">
                    <div class="stat-number" id="starCount">150+</div>
                    <div>Stars Earned</div>
                </div>
                <div class="stat-card interactive-element" onclick="animateStats()">
                    <div class="stat-number" id="commitCount">500+</div>
                    <div>Commits This Year</div>
                </div>
                <div class="stat-card interactive-element" onclick="animateStats()">
                    <div class="stat-number" id="followerCount">100+</div>
                    <div>Followers</div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section class="section">
            <h2 class="section-title">🤝 Let's Connect!</h2>
            <div class="contact-links">
                <a href="mailto:sasanpathirage@gmail.com" class="contact-link">
                    <span>📧</span> Email
                </a>
                <a href="https://www.linkedin.com/in/sasanirmal" class="contact-link">
                    <span>💼</span> LinkedIn
                </a>
                <a href="https://x.com/SasankaXbob" class="contact-link">
                    <span>🐦</span> X (Twitter)
                </a>
                <a href="https://github.com/SasaNirmal" class="contact-link">
                    <span>🐱</span> GitHub
                </a>
            </div>
            <p style="text-align: center; margin-top: 20px; color: #ccc;">
                🌟 Let's build something awesome together! Fork my repos, submit a PR, or drop me a message!
            </p>
        </section>
    </div>

    <!-- Modals -->
    <div id="projectModal" class="modal">
        <div class="modal-content">
            <span class="close">&times;</span>
            <div id="modalContent"></div>
        </div>
    </div>

    <script>
        // Typing animation
        const texts = [
            "Hello World! I'm Sasanka Nirmal!",
            "Passionate Developer & Linux Enthusiast",
            "Bash Scripting Ninja 🐧",
            "Open Source Contributor 🚀"
        ];
        let textIndex = 0;
        let charIndex = 0;
        let isDeleting = false;

        function typeWriter() {
            const currentText = texts[textIndex];
            const typingElement = document.getElementById('typingText');
            
            if (isDeleting) {
                typingElement.textContent = currentText.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingElement.textContent = currentText.substring(0, charIndex + 1);
                charIndex++;
            }
            
            if (!isDeleting && charIndex === currentText.length) {
                setTimeout(() => isDeleting = true, 2000);
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                textIndex = (textIndex + 1) % texts.length;
            }
            
            setTimeout(typeWriter, isDeleting ? 50 : 100);
        }

        // Initialize typing animation
        typeWriter();

        // Progress bar animations
        function animateProgressBars() {
            document.getElementById('bashProgress').style.width = '75%';
            document.getElementById('linuxProgress').style.width = '60%';
        }

        // Animate stats
        function animateStats() {
            const stats = [
                { id: 'repoCount', target: 25 },
                { id: 'starCount', target: 150 },
                { id: 'commitCount', target: 500 },
                { id: 'followerCount', target: 100 }
            ];
            
            stats.forEach(stat => {
                let current = 0;
                const increment = stat.target / 50;
                const timer = setInterval(() => {
                    current += increment;
                    if (current >= stat.target) {
                        current = stat.target;
                        clearInterval(timer);
                    }
                    document.getElementById(stat.id).textContent = Math.floor(current) + '+';
                }, 30);
            });
        }

        // Project modal functions
        function openProject(project) {
            const modal = document.getElementById('projectModal');
            const content = document.getElementById('modalContent');
            
            const projectData = {
                library: {
                    title: '📚 LibrarySystem',
                    description: 'A comprehensive library management system built with Django and Python.',
                    features: [
                        'Book inventory management',
                        'User registration and authentication',
                        'Transaction tracking',
                        'Advanced search and filtering',
                        'Admin dashboard'
                    ],
                    tech: ['Python', 'Django', 'MySQL', 'Bootstrap'],
                    github: 'https://github.com/SasaNirmal/LibrarySystem'
                },
                bash: {
                    title: '⚡ Bash Automation Toolkit',
                    description: 'Collection of powerful Bash scripts for system automation.',
                    features: [
                        'File backup automation',
                        'Log analysis tools',
                        'System monitoring scripts',
                        'Network diagnostics',
                        'Deployment helpers'
                    ],
                    tech: ['Bash', 'Linux', 'Shell Scripting', 'Cron'],
                    github: '#'
                },
                web: {
                    title: '🌐 Task Tracker Pro',
                    description: 'Modern task management application with real-time collaboration.',
                    features: [
                        'Real-time task updates',
                        'Team collaboration',
                        'Project management',
                        'Time tracking',
                        'Progress analytics'
                    ],
                    tech: ['React', 'Node.js', 'MongoDB', 'Socket.io'],
                    github: '#'
                }
            };
            
            const proj = projectData[project];
            content.innerHTML = `
                <h2 style="color: #00FF99; margin-bottom: 20px;">${proj.title}</h2>
                <p style="color: #ccc; margin-bottom: 20px;">${proj.description}</p>
                
                <h3 style="color: #00FF99; margin-bottom: 10px;">✨ Features:</h3>
                <ul style="color: #ccc; margin-bottom: 20px;">
                    ${proj.features.map(feature => `<li style="margin-bottom: 5px;">• ${feature}</li>`).join('')}
                </ul>
                
                <h3 style="color: #00FF99; margin-bottom: 10px;">🛠️ Technologies:</h3>
                <div style="display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 20px;">
                    ${proj.tech.map(tech => `<span class="tech-badge">${tech}</span>`).join('')}
                </div>
                
                <a href="${proj.github}" target="_blank" class="contact-link" style="display: inline-flex;">
                    <span>🐱</span> View on GitHub
                </a>
            `;
            
            modal.style.display = 'block';
        }

        // Navigation functions
        function showTerminal() {
            document.querySelector('.terminal').scrollIntoView({ behavior: 'smooth' });
        }

        function showSkills() {
            document.getElementById('skillsSection').scrollIntoView({ behavior: 'smooth' });
            setTimeout(animateProgressBars, 500);
        }

        function showStats() {
            document.getElementById('statsSection').scrollIntoView({ behavior: 'smooth' });
            setTimeout(animateStats, 500);
        }

        function showProjects() {
            document.getElementById('projectsSection').scrollIntoView({ behavior: 'smooth' });
        }

        // Modal close functionality
        document.querySelector('.close').onclick = function() {
            document.getElementById('projectModal').style.display = 'none';
        }

        window.onclick = function(event) {
            const modal = document.getElementById('projectModal');
            if (event.target === modal) {
                modal.style.display = 'none';
            }
        }

        // Initialize animations on scroll
        window.addEventListener('scroll', function() {
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => {
                const rect = section.getBoundingClientRect();
                if (rect.top < window.innerHeight && rect.bottom > 0) {
                    section.style.opacity = '1';
                    section.style.transform = 'translateY(0)';
                }
            });
        });

        // Add some interactive effects
        document.querySelectorAll('.skill-tag').forEach(tag => {
            tag.addEventListener('click', function() {
                this.style.transform = 'scale(1.2)';
                setTimeout(() => {
                    this.style.transform = 'scale(1)';
                }, 200);
            });
        });

        // Initialize progress bars after page load
        window.addEventListener('load', function() {
            setTimeout(animateProgressBars, 1000);
        });
    </script>
</body>
</html>
