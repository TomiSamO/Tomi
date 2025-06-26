<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Business Analyst Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-color: #2563eb;
            --secondary-color: #1e40af;
            --accent-color: #06b6d4;
            --text-dark: #1f2937;
            --text-light: #6b7280;
            --bg-light: #f8fafc;
            --white: #ffffff;
            --gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --shadow: 0 10px 25px rgba(0,0,0,0.1);
            --shadow-hover: 0 20px 40px rgba(0,0,0,0.15);
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text-dark);
            overflow-x: hidden;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            transition: all 0.3s ease;
        }

        nav.scrolled {
            background: rgba(255, 255, 255, 0.98);
            box-shadow: var(--shadow);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-dark);
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-links a:hover {
            color: var(--primary-color);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background: var(--gradient);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            background: var(--gradient);
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 1000"><polygon fill="rgba(255,255,255,0.1)" points="0,1000 1000,0 1000,1000"/></svg>');
            background-size: cover;
        }

        .hero-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            color: white;
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            opacity: 0;
            transform: translateY(30px);
            animation: slideUp 1s ease forwards;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0;
            transform: translateY(30px);
            animation: slideUp 1s ease 0.2s forwards;
        }

        .cta-button {
            display: inline-block;
            padding: 1rem 2rem;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.3);
            opacity: 0;
            transform: translateY(30px);
            animation: slideUp 1s ease 0.4s forwards;
        }

        .cta-button:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-3px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }

        /* Skills Section */
        .skills {
            padding: 5rem 0;
            background: var(--bg-light);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .skill-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: var(--gradient);
        }

        .skill-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .skill-icon {
            width: 60px;
            height: 60px;
            background: var(--gradient);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
            font-size: 1.5rem;
            color: white;
        }

        .skill-card h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--text-dark);
        }

        .skill-card p {
            color: var(--text-light);
            line-height: 1.6;
        }

        /* Portfolio Section */
        .portfolio {
            padding: 5rem 0;
            background: white;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .project-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            position: relative;
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .project-image {
            height: 200px;
            background: var(--gradient);
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3rem;
            opacity: 0.8;
        }

        .project-content {
            padding: 2rem;
        }

        .project-title {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            color: var(--text-dark);
        }

        .project-category {
            color: var(--primary-color);
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .project-description {
            color: var(--text-light);
            margin-bottom: 1.5rem;
            line-height: 1.6;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .tag {
            background: var(--bg-light);
            color: var(--text-dark);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        /* Contact Section */
        .contact {
            padding: 5rem 0;
            background: var(--gradient);
            color: white;
            text-align: center;
        }

        .contact-form {
            max-width: 600px;
            margin: 2rem auto 0;
            display: grid;
            gap: 1rem;
        }

        .form-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
        }

        .contact-form input,
        .contact-form textarea {
            padding: 1rem;
            border: none;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .contact-form input::placeholder,
        .contact-form textarea::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        .contact-form textarea {
            grid-column: 1 / -1;
            min-height: 120px;
            resize: vertical;
        }

        .submit-btn {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .submit-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        /* Footer */
        footer {
            background: var(--text-dark);
            color: white;
            text-align: center;
            padding: 2rem 0;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .social-links a {
            width: 40px;
            height: 40px;
            background: var(--gradient);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-decoration: none;
            transition: transform 0.3s ease;
        }

        .social-links a:hover {
            transform: translateY(-3px);
        }

        /* Animations */
        @keyframes slideUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Mobile Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1.1rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .skills-grid,
            .portfolio-grid {
                grid-template-columns: 1fr;
            }

            .form-group {
                grid-template-columns: 1fr;
            }

            .container {
                padding: 0 1rem;
            }
        }

        /* Scroll animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav id="navbar">
        <div class="nav-container">
            <div class="logo"> Hi there,
                My name is ****Tomi Sam-Oladipo****.
                Welome to My Portfolio</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#portfolio">Portfolio</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Senior Business Analyst</h1>
            <p>Experienced in eliciting requirements, analyzing business processes, and supporting organizational change initiatives. Skilled in collaborating with stakeholders to identify needs and deliver value-driven solutions with strong communication and structured problem-solving approach.</p>
            <a href="#portfolio" class="cta-button">View My Work</a>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="skills">
        <div class="container">
            <h2 class="section-title fade-in">Core Competencies</h2>
            <div class="skills-grid">
                <div class="skill-card fade-in">
                    <div class="skill-icon">📋</div>
                    <h3>Requirements Elicitation & Documentation</h3>
                    <p>Expert in gathering business needs from cross-functional stakeholders, documenting business requirements, use cases, user stories, and functional specifications using structured approaches.</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">🔄</div>
                    <h3>Process Modeling & Analysis (BPMN)</h3>
                    <p>Proficient in analyzing current state and mapping future state processes using BPMN, creating process models and wireframes to identify gaps and recommend solutions.</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">🤝</div>
                    <h3>Stakeholder Engagement & Facilitation</h3>
                    <p>Skilled in stakeholder analysis, consensus-building, negotiation, and presentation abilities to align teams and stakeholders effectively through strong communication and influencing skills.</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">🧪</div>
                    <h3>Test Planning & UAT Coordination</h3>
                    <p>Experienced in developing test plans, coordinating user acceptance testing, and supporting QA teams to validate functionality and ensure quality through thorough testing support.</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">💼</div>
                    <h3>Business Case Development & Change Management</h3>
                    <p>Expert in business case development, cost-benefit analysis, options analysis, and supporting organizational change through training documentation and user coordination.</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">🔧</div>
                    <h3>Tools & Methodologies</h3>
                    <p>Proficient in Microsoft Office, Google Suite, Visio, Jira, Confluence, Miro, SQL (basic), and experienced in Agile, Waterfall, and Scrum methodologies with DevOps and CI/CD understanding.</p>
                </div>
            </div>
            
            <!-- Certifications Section -->
            <div style="margin-top: 4rem;">
                <h3 class="section-title fade-in" style="font-size: 2rem; margin-bottom: 2rem;">Professional Certifications</h3>
                <div class="certifications-grid" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem;">
                    <div class="cert-card fade-in" style="background: white; padding: 1.5rem; border-radius: 10px; box-shadow: var(--shadow); text-align: center; transition: transform 0.3s ease;">
                        <div style="font-size: 2rem; margin-bottom: 0.5rem;">🏆</div>
                        <h4 style="color: var(--primary-color); margin-bottom: 0.5rem;">CBAP</h4>
                        <p style="color: var(--text-light); font-size: 0.9rem;">Certified Business Analysis Professional | IIBA</p>
                    </div>
                    <div class="cert-card fade-in" style="background: white; padding: 1.5rem; border-radius: 10px; box-shadow: var(--shadow); text-align: center; transition: transform 0.3s ease;">
                        <div style="font-size: 2rem; margin-bottom: 0.5rem;">☁️</div>
                        <h4 style="color: var(--primary-color); margin-bottom: 0.5rem;">Salesforce Certified</h4>
                        <p style="color: var(--text-light); font-size: 0.9rem;">Business Analyst | Administrator | Service & Sales Cloud | Data Cloud</p>
                    </div>
                    <div class="cert-card fade-in" style="background: white; padding: 1.5rem; border-radius: 10px; box-shadow: var(--shadow); text-align: center; transition: transform 0.3s ease;">
                        <div style="font-size: 2rem; margin-bottom: 0.5rem;">💻</div>
                        <h4 style="color: var(--primary-color); margin-bottom: 0.5rem;">Google IT Support</h4>
                        <p style="color: var(--text-light); font-size: 0.9rem;">Professional Certificate | Coursera</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Portfolio Section -->
    <section id="portfolio" class="portfolio">
        <div class="container">
            <h2 class="section-title fade-in">Portfolio Projects</h2>
            <div class="portfolio-grid">
                <div class="project-card fade-in">
                    <div class="project-image">⚡</div>
                    <div class="project-content">
                        <div class="project-category">Process Automation</div>
                        <h3 class="project-title">Automated Manual Leave Management Process</h3>
                        <p class="project-description">Transformed manual leave management into a streamlined digital workflow, reducing processing time by 87% and saving $65,000 annually. Improved employee experience with approval times under 24 hours and created leadership dashboards for data-driven staffing decisions.</p>
                        <div class="project-tags">
                            <span class="tag">Process Automation</span>
                            <span class="tag">Cost Reduction</span>
                            <span class="tag">Dashboard Development</span>
                            <span class="tag">87% Time Reduction</span>
                        </div>
                    </div>
                </div>
                <div class="project-card fade-in">
                    <div class="project-image">🔗</div>
                    <div class="project-content">
                        <div class="project-category">Systems Integration</div>
                        <h3 class="project-title">CRM and ERP Systems Integration</h3>
                        <p class="project-description">Established Salesforce CRM as single source of truth through strategic ERP integration, eliminating data reconciliation and boosting productivity by 35%. Implemented real-time visibility and unified reporting, resulting in 28% fewer customer inquiries.</p>
                        <div class="project-tags">
                            <span class="tag">Salesforce CRM</span>
                            <span class="tag">ERP Integration</span>
                            <span class="tag">35% Productivity Boost</span>
                            <span class="tag">Data Unification</span>
                        </div>
                    </div>
                </div>
                <div class="project-card fade-in">
                    <div class="project-image">📊</div>
                    <div class="project-content">
                        <div class="project-category">Requirements Analysis</div>
                        <h3 class="project-title">Cross-Functional Requirements Elicitation</h3>
                        <p class="project-description">Led comprehensive requirements gathering sessions with internal and external stakeholders, creating detailed functional specifications and process flows that ensured delivered solutions aligned with business objectives and stakeholder expectations.</p>
                        <div class="project-tags">
                            <span class="tag">Requirements Gathering</span>
                            <span class="tag">Stakeholder Management</span>
                            <span class="tag">Process Documentation</span>
                            <span class="tag">Solution Alignment</span>
                        </div>
                    </div>
                </div>
                <div class="project-card fade-in">
                    <div class="project-image">🎯</div>
                    <div class="project-content">
                        <div class="project-category">Quality Assurance</div>
                        <h3 class="project-title">UAT Coordination & Test Planning</h3>
                        <p class="project-description">Developed comprehensive test plans and coordinated user acceptance testing across multiple projects, ensuring business needs were met through systematic validation and quality assurance processes with cross-functional teams.</p>
                        <div class="project-tags">
                            <span class="tag">Test Planning</span>
                            <span class="tag">UAT Coordination</span>
                            <span class="tag">Quality Assurance</span>
                            <span class="tag">Business Validation</span>
                        </div>
                    </div>
                </div>
                <div class="project-card fade-in">
                    <div class="project-image">🔧</div>
                    <div class="project-content">
                        <div class="project-category">Future Project</div>
                        <h3 class="project-title">Your Next Project Here</h3>
                        <p class="project-description">This section is ready for your upcoming portfolio projects. Add your project details, outcomes, and key achievements to showcase your growing expertise in business analysis and process improvement.</p>
                        <div class="project-tags">
                            <span class="tag">Coming Soon</span>
                            <span class="tag">New Project</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
        <div class="container">
            <h2 class="section-title">Let's Collaborate</h2>
            <p>Ready to discuss your next business analysis project? Let's connect and explore how we can drive results together.</p>
            <form class="contact-form">
                <div class="form-group">
                    <input type="text" placeholder="Tomi Sam-Oladipo" required>
                    <input type="email" placeholder="Your Email" required>
                </div>
                <input type="text" placeholder="Subject" required>
                <textarea placeholder="Your Message" required></textarea>
                <button type="submit" class="submit-btn">Send Message</button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="social-links">
                <a href="#" title="LinkedIn">💼</a>
                <a href="#" title="Email">📧</a>
                <a href="#" title="GitHub">💻</a>
            </div>
            <p>&copy; 2025 Senior Business Analyst Portfolio. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // Smooth scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Navbar scroll effect
        window.addEventListener('scroll', () => {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Fade in animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => {
            observer.observe(el);
        });

        // Form submission
        document.querySelector('.contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you for your message! I\'ll get back to you soon.');
            this.reset();
        });

        // Add some interactive hover effects
        document.querySelectorAll('.project-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-10px) scale(1.02)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });
    </script>
</body>
</html>
