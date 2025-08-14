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
        
        .profile-avatar {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 3px solid #00FF99;
            margin: 0 auto 30px;
            display: block;
            box-shadow: 0 0 30px rgba(0, 255, 153, 0.3);
            transition: transform 0.3s ease;
        }
        
        .profile-avatar:hover {
            transform: scale(1.1);
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
        
        .github-stats {
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
            cursor: pointer;
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
        
        .repositories-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }
        
        .repo-card {
            background: rgba(0, 255, 153, 0.05);
            border: 1px solid rgba(0, 255, 153, 0.3);
            border-radius: 15px;
            padding: 25px;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
        }
        
        .repo-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 255, 153, 0.2);
        }
        
        .repo-title {
            color: #00FF99;
            font-size: 1.3rem;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .repo-description {
            color: #ccc;
            margin-bottom: 15px;
            min-height: 40px;
        }
        
        .repo-stats {
            display: flex;
            gap: 15px;
            align-items: center;
            font-size: 0.9rem;
        }
        
        .repo-stat {
            display: flex;
            align-items: center;
            gap: 5px;
            color: #999;
        }
        
        .language-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
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
        
        .loading {
            text-align: center;
            padding: 40px;
            color: #00FF99;
        }
        
        .spinner {
            border: 4px solid rgba(0, 255, 153, 0.1);
            border-left: 4px solid #00FF99;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto 20px;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
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
        
        .skills-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .skill-item {
            background: rgba(0, 255, 153, 0.1);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .skill-item:hover {
            background: rgba(0, 255, 153, 0.2);
            transform: translateY(-2px);
        }
        
        .error-message {
            background: rgba(255, 0, 0, 0.1);
            border: 1px solid rgba(255, 0, 0, 0.3);
            color: #ff6b6b;
            padding: 15px;
            border-radius: 10px;
            margin: 20px 0;
            text-align: center;
        }
        
        @media (max-width: 768px) {
            .typing-animation {
                font-size: 1.8rem;
            }
            
            .badge-container {
                gap: 10px;
            }
            
            .github-stats {
                grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            }
        }
        
        .contribution-graph {
            background: rgba(0, 255, 153, 0.05);
            border: 1px solid rgba(0, 255, 153, 0.2);
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            text-align: center;
        }
        
        .language-stats {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
        }
        
        .language-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
        }
        
        .recent-activity {
            max-height: 400px;
            overflow-y: auto;
            background: rgba(0, 255, 153, 0.05);
            border-radius: 10px;
            padding: 20px;
            margin-top: 20px;
        }
        
        .activity-item {
            padding: 10px;
            border-left: 2px solid #00FF99;
            margin-bottom: 15px;
            padding-left: 15px;
        }
        
        .activity-time {
            color: #666;
            font-size: 0.8rem;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Section -->
        <header class="header">
            <img id="profileAvatar" class="profile-avatar" src="" alt="Sasanka Nirmal" style="display: none;">
            <div class="typing-animation" id="typingText">Hello World! I'm Sasanka Nirmal!</div>
            <div class="badge-container">
                <span class="badge" onclick="scrollToSection('about')">👨‍💻 About Me</span>
                <span class="badge" onclick="scrollToSection('stats')">📊 GitHub Stats</span>
                <span class="badge" onclick="scrollToSection('repositories')">🚀 Repositories</span>
                <span class="badge" onclick="scrollToSection('skills')">🛠️ Skills</span>
                <span class="badge" onclick="scrollToSection('contact')">🤝 Contact</span>
            </div>
        </header>

        <!-- About Section -->
        <section class="section" id="about">
            <h2 class="section-title">👨‍💻 About Me</h2>
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 30px; align-items: start;">
                <div style="color: #ccc;">
                    <p style="margin-bottom: 15px;">I'm <strong>Sasanka Nirmal</strong>, a passionate software developer and Linux enthusiast from Wellawaya, Sri Lanka. I thrive on exploring the command line, automating workflows, and contributing to open-source projects.</p>
                    
                    <div style="margin: 20px 0;">
                        <p><strong>📍 Location:</strong> Wellawaya, Sri Lanka</p>
                        <p><strong>📧 Email:</strong> sasanpathirage@gmail.com</p>
                        <p><strong>🎯 Goal:</strong> Automate the world, one script at a time!</p>
                        <p><strong>⚡ Fun Fact:</strong> I once wrote a Bash script to remind me to take breaks during late-night coding sessions!</p>
                    </div>
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
                        <div><span class="command">$ git status</span></div>
                        <div class="output">On branch main - Ready to collaborate!</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- GitHub Stats Section -->
        <section class="section" id="stats">
            <h2 class="section-title">📊 GitHub Statistics</h2>
            <div class="loading" id="statsLoading">
                <div class="spinner"></div>
                <p>Loading GitHub statistics...</p>
            </div>
            <div class="github-stats" id="githubStats" style="display: none;">
                <!-- Stats will be populated by JavaScript -->
            </div>
            <div class="contribution-graph">
                <h3 style="color: #00FF99; margin-bottom: 15px;">📈 Contribution Activity</h3>
                <p style="color: #ccc;">Consistent contributions across repositories and open source projects</p>
            </div>
        </section>

        <!-- Repositories Section -->
        <section class="section" id="repositories">
            <h2 class="section-title">🚀 My Repositories</h2>
            <div class="loading" id="reposLoading">
                <div class="spinner"></div>
                <p>Loading repositories...</p>
            </div>
            <div class="repositories-grid" id="repositoriesGrid" style="display: none;">
                <!-- Repositories will be populated by JavaScript -->
            </div>
        </section>

        <!-- Skills Section -->
        <section class="section" id="skills">
            <h2 class="section-title">🛠️ Skills & Technologies</h2>
            <div class="skills-container">
                <div class="skill-item">
                    <h3>Languages</h3>
                    <div style="margin-top: 10px; display: flex; flex-wrap: wrap; gap: 5px; justify-content: center;">
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Python</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Bash</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">JavaScript</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Java</span>
                    </div>
                </div>
                <div class="skill-item">
                    <h3>Frameworks</h3>
                    <div style="margin-top: 10px; display: flex; flex-wrap: wrap; gap: 5px; justify-content: center;">
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Django</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Node.js</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">React</span>
                    </div>
                </div>
                <div class="skill-item">
                    <h3>DevOps & Tools</h3>
                    <div style="margin-top: 10px; display: flex; flex-wrap: wrap; gap: 5px; justify-content: center;">
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Linux</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Docker</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Git</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Kubernetes</span>
                    </div>
                </div>
                <div class="skill-item">
                    <h3>Databases</h3>
                    <div style="margin-top: 10px; display: flex; flex-wrap: wrap; gap: 5px; justify-content: center;">
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">MongoDB</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">MySQL</span>
                        <span style="background: rgba(0,255,153,0.2); padding: 3px 8px; border-radius: 10px; font-size: 0.8rem;">Supabase</span>
                    </div>
                </div>
            </div>

            <!-- Language Statistics -->
            <div id="languageStats" style="display: none;">
                <h3 style="color: #00FF99; margin: 30px 0 15px 0; text-align: center;">📊 Most Used Languages</h3>
                <div class="language-stats" id="languageStatsContent">
                    <!-- Will be populated by JavaScript -->
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section class="section" id="contact">
            <h2 class="section-title">🤝 Let's Connect!</h2>
            <div class="contact-links">
                <a href="mailto:sasanpathirage@gmail.com" class="contact-link">
                    <span>📧</span> Email
                </a>
                <a href="https://www.linkedin.com/in/sasanirmal" class="contact-link" target="_blank">
                    <span>💼</span> LinkedIn
                </a>
                <a href="https://x.com/SasankaXbob" class="contact-link" target="_blank">
                    <span>🐦</span> X (Twitter)
                </a>
                <a href="https://github.com/SasaNirmal" class="contact-link" target="_blank">
                    <span>🐱</span> GitHub
                </a>
            </div>
            <p style="text-align: center; margin-top: 30px; color: #ccc;">
                🌟 Let's build something awesome together! Fork my repos, submit a PR, or drop me a message!<br>
                <small style="color: #666;">Thanks for visiting! Let's conquer the terminal together! 🐧🚀</small>
            </p>
        </section>
    </div>

    <script>
        // GitHub API configuration
        const GITHUB_USERNAME = 'SasaNirmal';
        const GITHUB_API_BASE = 'https://api.github.com';

        // Typing animation
        const texts = [
            "Hello World! I'm Sasanka Nirmal!",
            "Passionate Developer & Linux Enthusiast 🐧",
            "Bash Scripting Ninja 💻",
            "Open Source Contributor 🚀",
            "Automation Enthusiast ⚡"
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

        // Fetch GitHub user data
        async function fetchGitHubUser() {
            try {
                const response = await fetch(`${GITHUB_API_BASE}/users/${GITHUB_USERNAME}`);
                if (!response.ok) throw new Error('Failed to fetch user data');
                const user = await response.json();
                
                // Update profile avatar
                const avatarImg = document.getElementById('profileAvatar');
                avatarImg.src = user.avatar_url;
                avatarImg.style.display = 'block';
                
                return user;
            } catch (error) {
                console.error('Error fetching GitHub user:', error);
                showError('stats', 'Failed to load GitHub profile data');
                return null;
            }
        }

        // Fetch GitHub repositories
        async function fetchGitHubRepos() {
            try {
                const response = await fetch(`${GITHUB_API_BASE}/users/${GITHUB_USERNAME}/repos?sort=updated&per_page=12`);
                if (!response.ok) throw new Error('Failed to fetch repositories');
                const repos = await response.json();
                return repos;
            } catch (error) {
                console.error('Error fetching repositories:', error);
                showError('repositories', 'Failed to load repositories');
                return [];
            }
        }

        // Language colors for GitHub
        const languageColors = {
            'JavaScript': '#f1e05a',
            'Python': '#3572A5',
            'Java': '#b07219',
            'TypeScript': '#2b7489',
            'HTML': '#e34c26',
            'CSS': '#563d7c',
            'Shell': '#89e051',
            'C++': '#f34b7d',
            'C': '#555555',
            'Go': '#00ADD8',
            'Rust': '#dea584',
            'PHP': '#4F5D95',
            'Ruby': '#701516',
            'Swift': '#ffac45',
            'Kotlin': '#F18E33',
            'Dart': '#00B4AB'
        };

        // Display GitHub statistics
        async function displayGitHubStats(user) {
            const statsContainer = document.getElementById('githubStats');
            const statsLoading = document.getElementById('statsLoading');
            
            if (!user) {
                showError('stats', 'Unable to load GitHub statistics');
                return;
            }

            statsContainer.innerHTML = `
                <div class="stat-card" onclick="animateStatCard(this)">
                    <div class="stat-number">${user.following}</div>
                    <div>Following</div>
                </div>
                <div class="stat-card" onclick="animateStatCard(this)">
                    <div class="stat-number">${new Date(user.created_at).getFullYear()}</div>
                    <div>Joined GitHub</div>
                </div>
            `;
            
            statsLoading.style.display = 'none';
            statsContainer.style.display = 'grid';
        }

        // Display repositories
        async function displayRepositories(repos) {
            const reposContainer = document.getElementById('repositoriesGrid');
            const reposLoading = document.getElementById('reposLoading');
            
            if (!repos || repos.length === 0) {
                showError('repositories', 'No repositories found');
                return;
            }

            const repoCards = repos.map(repo => {
                const languageColor = languageColors[repo.language] || '#666';
                return `
                    <div class="repo-card" onclick="openRepository('${repo.html_url}')">
                        <div class="repo-title">
                            <span>📁</span>
                            ${repo.name}
                        </div>
                        <div class="repo-description">
                            ${repo.description || 'No description available'}
                        </div>
                        <div class="repo-stats">
                            ${repo.language ? `
                                <div class="repo-stat">
                                    <span class="language-dot" style="background-color: ${languageColor}"></span>
                                    ${repo.language}
                                </div>
                            ` : ''}
                            <div class="repo-stat">
                                <span>⭐</span>
                                ${repo.stargazers_count}
                            </div>
                            <div class="repo-stat">
                                <span>🍴</span>
                                ${repo.forks_count}
                            </div>
                            <div class="repo-stat">
                                <span>📅</span>
                                ${new Date(repo.updated_at).toLocaleDateString()}
                            </div>
                        </div>
                    </div>
                `;
            }).join('');

            reposContainer.innerHTML = repoCards;
            reposLoading.style.display = 'none';
            reposContainer.style.display = 'grid';
            
            // Show language statistics
            displayLanguageStats(repos);
        }

        // Display language statistics
        function displayLanguageStats(repos) {
            const languageStats = {};
            repos.forEach(repo => {
                if (repo.language) {
                    languageStats[repo.language] = (languageStats[repo.language] || 0) + 1;
                }
            });

            const sortedLanguages = Object.entries(languageStats)
                .sort(([,a], [,b]) => b - a)
                .slice(0, 6);

            if (sortedLanguages.length > 0) {
                const languageStatsContainer = document.getElementById('languageStatsContent');
                const languageElements = sortedLanguages.map(([language, count]) => {
                    const color = languageColors[language] || '#666';
                    return `
                        <div class="language-item">
                            <div style="display: flex; align-items: center; gap: 5px;">
                                <span class="language-dot" style="background-color: ${color}"></span>
                                <span>${language}</span>
                            </div>
                            <span style="color: #999; font-size: 0.9rem;">${count} repos</span>
                        </div>
                    `;
                }).join('');

                languageStatsContainer.innerHTML = languageElements;
                document.getElementById('languageStats').style.display = 'block';
            }
        }

        // Utility functions
        function showError(sectionId, message) {
            const loadingElement = document.getElementById(`${sectionId}Loading`);
            if (loadingElement) {
                loadingElement.innerHTML = `
                    <div class="error-message">
                        <p>⚠️ ${message}</p>
                        <button onclick="location.reload()" style="margin-top: 10px; padding: 8px 16px; background: #00FF99; color: #000; border: none; border-radius: 5px; cursor: pointer;">
                            Retry
                        </button>
                    </div>
                `;
            }
        }

        function animateStatCard(card) {
            card.style.transform = 'scale(1.1) rotateY(10deg)';
            setTimeout(() => {
                card.style.transform = 'scale(1.05)';
            }, 200);
        }

        function openRepository(url) {
            window.open(url, '_blank');
        }

        function scrollToSection(sectionId) {
            document.getElementById(sectionId).scrollIntoView({ 
                behavior: 'smooth',
                block: 'start'
            });
        }

        // Initialize the profile
        async function initializeProfile() {
            // Start typing animation
            typeWriter();

            // Load GitHub data
            const user = await fetchGitHubUser();
            const repos = await fetchGitHubRepos();

            // Display the data
            await displayGitHubStats(user);
            await displayRepositories(repos);

            // Add scroll animations
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            };

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, observerOptions);

            // Observe all sections
            document.querySelectorAll('.section').forEach(section => {
                section.style.opacity = '0';
                section.style.transform = 'translateY(30px)';
                section.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
                observer.observe(section);
            });
        }

        // Add interactive effects
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize profile
            initializeProfile();

            // Add skill item interactions
            document.querySelectorAll('.skill-item').forEach(item => {
                item.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-5px) scale(1.02)';
                });
                
                item.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0) scale(1)';
                });
            });

            // Add terminal command interactions
            const terminalContent = document.querySelector('.terminal-content');
            if (terminalContent) {
                terminalContent.addEventListener('click', function() {
                    // Add a blinking cursor effect
                    const cursor = document.createElement('span');
                    cursor.textContent = '|';
                    cursor.style.animation = 'blink 1s infinite';
                    cursor.style.color = '#00FF99';
                    
                    const style = document.createElement('style');
                    style.textContent = `
                        @keyframes blink {
                            0%, 50% { opacity: 1; }
                            51%, 100% { opacity: 0; }
                        }
                    `;
                    document.head.appendChild(style);
                    
                    this.appendChild(cursor);
                    setTimeout(() => cursor.remove(), 3000);
                });
            }

            // Add badge hover effects
            document.querySelectorAll('.badge').forEach(badge => {
                badge.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-3px) scale(1.05)';
                });
                
                badge.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0) scale(1)';
                });
            });
        });

        // Add keyboard navigation
        document.addEventListener('keydown', function(e) {
            const sections = ['about', 'stats', 'repositories', 'skills', 'contact'];
            let currentSection = 0;
            
            // Find current section in view
            for (let i = 0; i < sections.length; i++) {
                const section = document.getElementById(sections[i]);
                const rect = section.getBoundingClientRect();
                if (rect.top <= 100 && rect.bottom >= 100) {
                    currentSection = i;
                    break;
                }
            }
            
            // Navigate with arrow keys
            if (e.key === 'ArrowDown' && currentSection < sections.length - 1) {
                scrollToSection(sections[currentSection + 1]);
                e.preventDefault();
            } else if (e.key === 'ArrowUp' && currentSection > 0) {
                scrollToSection(sections[currentSection - 1]);
                e.preventDefault();
            }
        });

        // Add a Easter egg for konami code
        let konamiCode = [];
        const konami = ['ArrowUp', 'ArrowUp', 'ArrowDown', 'ArrowDown', 'ArrowLeft', 'ArrowRight', 'ArrowLeft', 'ArrowRight', 'KeyB', 'KeyA'];
        
        document.addEventListener('keydown', function(e) {
            konamiCode.push(e.code);
            if (konamiCode.length > 10) konamiCode.shift();
            
            if (konamiCode.join(',') === konami.join(',')) {
                // Easter egg: Matrix effect
                document.body.style.background = 'linear-gradient(135deg, #000, #003300, #000)';
                const matrix = document.createElement('div');
                matrix.innerHTML = '🐧 LINUX MASTER MODE ACTIVATED 🐧';
                matrix.style.cssText = `
                    position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%);
                    color: #00FF99; font-size: 2rem; z-index: 9999;
                    text-shadow: 0 0 20px #00FF99; animation: pulse 2s infinite;
                `;
                document.body.appendChild(matrix);
                setTimeout(() => matrix.remove(), 3000);
                konamiCode = [];
            }
        });d(this)">
                    <div class="stat-number">${user.public_repos}</div>
                    <div>Public Repositories</div>
                </div>
                <div class="stat-card" onclick="animateStatCard(this)">
                    <div class="stat-number">${user.followers}</div>
                    <div>Followers</div>
                </div>
                <div class="stat-card" onclick="animateStatCar
