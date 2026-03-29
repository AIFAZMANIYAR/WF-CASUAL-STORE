<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MD AIFAZ | Video Editor Portfolio</title>
    <style>
        /* CSS VARIABLES & RESET */
        :root {
            --bg-color: #0a0a0c;
            --surface-color: #16161a;
            --surface-hover: #222228;
            --primary-color: #00e5ff;
            --text-main: #ffffff;
            --text-muted: #94a1b2;
            --border-color: #2c2c35;
            --danger-color: #ff3366;
            --font-main: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: var(--font-main);
        }

        body, html {
            width: 100%;
            height: 100%;
            background-color: var(--bg-color);
            color: var(--text-main);
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* UTILITIES */
        .hidden { display: none !important; }
        .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
        .section-title { font-size: 2.5rem; text-align: center; margin-bottom: 3rem; color: var(--text-main); text-transform: uppercase; letter-spacing: 2px; }
        .section-title span { color: var(--primary-color); }
        .btn { padding: 12px 24px; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; transition: var(--transition); font-size: 1rem; }
        .btn-primary { background-color: var(--primary-color); color: #000; }
        .btn-primary:hover { background-color: #00b3cc; transform: translateY(-2px); }
        .btn-outline { background-color: transparent; border: 2px solid var(--primary-color); color: var(--primary-color); }
        .btn-outline:hover { background-color: var(--primary-color); color: #000; }
        .btn-danger { background-color: transparent; border: 1px solid var(--danger-color); color: var(--danger-color); padding: 5px 10px; font-size: 0.8rem;}
        .btn-danger:hover { background-color: var(--danger-color); color: #fff; }

        input, textarea, select {
            width: 100%; padding: 12px; margin-bottom: 15px; background: var(--surface-color);
            border: 1px solid var(--border-color); color: var(--text-main); border-radius: 8px;
            font-size: 1rem;
        }
        input:focus, textarea:focus, select:focus { outline: none; border-color: var(--primary-color); }

        /* HEADER */
        header { position: fixed; top: 0; width: 100%; background: rgba(10, 10, 12, 0.9); backdrop-filter: blur(10px); z-index: 1000; border-bottom: 1px solid var(--border-color); }
        .nav-container { display: flex; justify-content: space-between; align-items: center; height: 70px; }
        .logo { font-size: 1.5rem; font-weight: 800; letter-spacing: 1px; color: var(--text-main); text-decoration: none; }
        .logo span { color: var(--primary-color); }
        .nav-links { display: flex; gap: 20px; }
        .nav-links a { color: var(--text-main); text-decoration: none; font-weight: 500; transition: var(--transition); }
        .nav-links a:hover { color: var(--primary-color); }

        /* HERO SECTION */
        #hero { height: 100vh; display: flex; align-items: center; justify-content: center; text-align: center; position: relative; padding-top: 70px; }
        .hero-bg { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: radial-gradient(circle at center, #1a1a24 0%, var(--bg-color) 70%); z-index: -1; }
        .hero-content h1 { font-size: 4vw; margin-bottom: 10px; letter-spacing: -1px; }
        @media (max-width: 768px) { .hero-content h1 { font-size: 2.5rem; } }
        .hero-content h2 { font-size: 1.5rem; color: var(--primary-color); margin-bottom: 20px; font-weight: 400; }
        .hero-content p { font-size: 1.1rem; color: var(--text-muted); max-width: 600px; margin: 0 auto 30px; line-height: 1.6; }
        .hero-stats { display: flex; justify-content: center; gap: 30px; margin-top: 40px; }
        .stat-item { background: var(--surface-color); padding: 15px 25px; border-radius: 12px; border: 1px solid var(--border-color); }
        .stat-item h3 { color: var(--primary-color); font-size: 1.5rem; }
        .stat-item p { font-size: 0.9rem; color: var(--text-muted); }

        /* ABOUT SECTION */
        #about { padding: 100px 0; background-color: var(--surface-color); }
        .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 50px; align-items: center; }
        @media (max-width: 768px) { .about-grid { grid-template-columns: 1fr; } }
        .about-text p { font-size: 1.1rem; line-height: 1.8; color: var(--text-muted); margin-bottom: 20px; }
        .skills-container { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 20px; }
        .skill-tag { background: var(--bg-color); border: 1px solid var(--primary-color); color: var(--primary-color); padding: 8px 15px; border-radius: 20px; font-size: 0.9rem; }

        /* PORTFOLIO SECTION */
        #portfolio { padding: 100px 0; }
        .filter-btns { display: flex; justify-content: center; gap: 10px; margin-bottom: 40px; flex-wrap: wrap; }
        .filter-btn { background: var(--surface-color); border: 1px solid var(--border-color); color: var(--text-main); padding: 8px 16px; border-radius: 20px; cursor: pointer; transition: var(--transition); }
        .filter-btn.active, .filter-btn:hover { background: var(--primary-color); color: #000; border-color: var(--primary-color); }
        .portfolio-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; }
        .video-card { background: var(--surface-color); border-radius: 12px; overflow: hidden; cursor: pointer; transition: var(--transition); border: 1px solid var(--border-color); position: relative; }
        .video-card:hover { transform: translateY(-5px); border-color: var(--primary-color); box-shadow: 0 10px 20px rgba(0, 229, 255, 0.1); }
        .video-thumb { height: 400px; display: flex; align-items: center; justify-content: center; font-size: 5rem; background: linear-gradient(45deg, #1a1a24, #2a2a35); position: relative;}
        .play-icon { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-size: 3rem; background: rgba(0,0,0,0.5); border-radius: 50%; padding: 10px; }
        .video-info { padding: 15px; }
        .video-title { font-size: 1.1rem; margin-bottom: 5px; }
        .video-cat { font-size: 0.8rem; color: var(--primary-color); text-transform: uppercase; letter-spacing: 1px; }

        /* SERVICES SECTION */
        #services { padding: 100px 0; background-color: var(--surface-color); }
        .services-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        .service-card { background: var(--bg-color); border: 1px solid var(--border-color); padding: 30px; border-radius: 16px; text-align: center; transition: var(--transition); }
        .service-card:hover { border-color: var(--primary-color); }
        .service-price { font-size: 2rem; color: var(--primary-color); font-weight: bold; margin: 20px 0; }
        .service-title { font-size: 1.3rem; margin-bottom: 15px; }
        .service-desc { color: var(--text-muted); line-height: 1.6; }

        /* TOOLS SECTION */
        #tools { padding: 80px 0; }
        .tools-grid { display: flex; flex-wrap: wrap; justify-content: center; gap: 20px; }
        .tool-card { background: var(--surface-color); padding: 15px 30px; border-radius: 12px; font-weight: 500; border: 1px solid var(--border-color); font-size: 1.1rem; display: flex; align-items: center; gap: 10px;}

        /* CONTACT SECTION */
        #contact { padding: 100px 0; background-color: var(--surface-color); }
        .contact-wrapper { max-width: 600px; margin: 0 auto; background: var(--bg-color); padding: 40px; border-radius: 16px; border: 1px solid var(--border-color); }
        
        /* FOOTER */
        footer { padding: 30px 0; text-align: center; border-top: 1px solid var(--border-color); background: var(--bg-color); }
        .admin-link { color: var(--text-muted); font-size: 0.8rem; text-decoration: none; opacity: 0.5; transition: opacity 0.3s; }
        .admin-link:hover { opacity: 1; }

        /* MODAL */
        .modal-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 2000; display: flex; align-items: center; justify-content: center; opacity: 0; pointer-events: none; transition: opacity 0.3s; }
        .modal-overlay.active { opacity: 1; pointer-events: all; }
        .modal-content { background: var(--surface-color); width: 90%; max-width: 800px; border-radius: 12px; overflow: hidden; position: relative; border: 1px solid var(--border-color); }
        .close-modal { position: absolute; top: 15px; right: 20px; color: #fff; font-size: 2rem; cursor: pointer; z-index: 10; line-height: 1;}
        .video-player-sim { width: 100%; aspect-ratio: 9/16; max-height: 70vh; background: #000; display: flex; flex-direction: column; align-items: center; justify-content: center; font-size: 6rem; }
        @media (min-aspect-ratio: 1/1) { .video-player-sim { aspect-ratio: 16/9; } }
        .modal-info { padding: 20px; text-align: center; }

        /* LOGIN VIEW */
        #login-view { height: 100vh; display: flex; align-items: center; justify-content: center; background: var(--bg-color); }
        .login-box { background: var(--surface-color); padding: 40px; border-radius: 16px; border: 1px solid var(--border-color); width: 100%; max-width: 400px; text-align: center; }
        .error-msg { color: var(--danger-color); font-size: 0.9rem; margin-bottom: 15px; display: none; }

        /* ADMIN DASHBOARD */
        #admin-view { min-height: 100vh; display: flex; background: var(--bg-color); }
        .admin-sidebar { width: 250px; background: var(--surface-color); border-right: 1px solid var(--border-color); padding: 20px 0; }
        .admin-sidebar h2 { padding: 0 20px; margin-bottom: 30px; font-size: 1.2rem; color: var(--primary-color); }
        .admin-nav { list-style: none; }
        .admin-nav li { padding: 15px 20px; cursor: pointer; transition: var(--transition); border-left: 3px solid transparent; }
        .admin-nav li:hover, .admin-nav li.active { background: rgba(0, 229, 255, 0.1); border-left-color: var(--primary-color); color: var(--primary-color); }
        .admin-content { flex: 1; padding: 40px; overflow-y: auto; }
        .admin-panel { display: none; }
        .admin-panel.active { display: block; }
        .admin-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 30px; }
        
        /* Admin Tables/Lists */
        .admin-list { background: var(--surface-color); border-radius: 12px; border: 1px solid var(--border-color); overflow: hidden; }
        .admin-list-item { display: flex; justify-content: space-between; align-items: center; padding: 15px 20px; border-bottom: 1px solid var(--border-color); }
        .admin-list-item:last-child { border-bottom: none; }
        .item-actions { display: flex; gap: 10px; }

        .form-group { margin-bottom: 20px; background: var(--surface-color); padding: 20px; border-radius: 12px; border: 1px solid var(--border-color); }
        .form-group h3 { margin-bottom: 15px; font-size: 1.1rem; }
    </style>
</head>
<body>

    <!-- ==================== FRONTEND VIEW ==================== -->
    <div id="frontend-view">
        <header>
            <div class="container nav-container">
                <a href="#" class="logo">MD <span>AIFAZ</span></a>
                <div class="nav-links">
                    <a href="#about">About</a>
                    <a href="#portfolio">Work</a>
                    <a href="#services">Services</a>
                    <a href="#contact">Contact</a>
                </div>
            </div>
        </header>

        <section id="hero">
            <div class="hero-bg"></div>
            <div class="container hero-content">
                <h1 id="f-name">MD AIFAZ</h1>
                <h2 id="f-title">Professional Video Editor & UGC Creator</h2>
                <p id="f-tagline">I create high-performing videos that help creators and brands grow fast.</p>
                <div style="display: flex; gap: 15px; justify-content: center;">
                    <a href="#portfolio" class="btn btn-primary">View Portfolio</a>
                    <a href="#contact" class="btn btn-outline">Hire Me</a>
                </div>
                <div class="hero-stats">
                    <div class="stat-item">
                        <h3 id="f-exp">3+ Years</h3>
                        <p>Experience</p>
                    </div>
                    <div class="stat-item">
                        <h3>100+</h3>
                        <p>Projects Delivered</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="about">
            <div class="container">
                <h2 class="section-title">About <span>Me</span></h2>
                <div class="about-grid">
                    <div class="about-text">
                        <p id="f-about">I’m MD AIFAZ, a passionate video editor with 3+ years of experience creating engaging short-form videos, UGC content, and cinematic edits...</p>
                        <p style="color: var(--primary-color); font-weight: bold;" id="f-edu">BCS FY Student</p>
                    </div>
                    <div>
                        <h3>My Core Skills</h3>
                        <div class="skills-container" id="f-skills">
                            <!-- Skills generated by JS -->
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="portfolio">
            <div class="container">
                <h2 class="section-title">My <span>Work</span></h2>
                <div class="filter-btns" id="f-filters">
                    <!-- Filters generated by JS -->
                </div>
                <div class="portfolio-grid" id="f-portfolio-grid">
                    <!-- Videos generated by JS -->
                </div>
            </div>
        </section>

        <section id="services">
            <div class="container">
                <h2 class="section-title">Pricing & <span>Services</span></h2>
                <div class="services-grid" id="f-services-grid">
                    <!-- Services generated by JS -->
                </div>
            </div>
        </section>

        <section id="tools">
            <div class="container">
                <h2 class="section-title">Tools I <span>Use</span></h2>
                <div class="tools-grid" id="f-tools-grid">
                    <!-- Tools generated by JS -->
                </div>
            </div>
        </section>

        <section id="contact">
            <div class="container">
                <h2 class="section-title">Let's <span>Work Together</span></h2>
                <div class="contact-wrapper">
                    <input type="text" id="c-name" placeholder="Your Name" required>
                    <input type="text" id="c-budget" placeholder="Estimated Budget ($)" required>
                    <select id="c-type">
                        <option value="Reels/Shorts Editing">Reels/Shorts Editing</option>
                        <option value="UGC Video Creation">UGC Video Creation</option>
                        <option value="AI Video Editing">AI Video Editing</option>
                        <option value="Documentary Editing">Documentary Editing</option>
                        <option value="Other">Other</option>
                    </select>
                    <textarea id="c-msg" rows="4" placeholder="Tell me about your project..." required></textarea>
                    <button class="btn btn-primary" style="width: 100%;" onclick="submitWhatsAppForm()">Send via WhatsApp 📱</button>
                </div>
            </div>
        </section>

        <footer>
            <div class="container">
                <p>&copy; 2026 MD AIFAZ. All rights reserved.</p>
                <br>
                <a href="#" class="admin-link" onclick="showView('login'); return false;">Admin Login</a>
            </div>
        </footer>

        <!-- Video Modal -->
        <div class="modal-overlay" id="video-modal">
            <div class="close-modal" onclick="closeModal()">×</div>
            <div class="modal-content">
                <div class="video-player-sim" id="m-player">🎥</div>
                <div class="modal-info">
                    <h3 id="m-title" style="margin-bottom: 5px; font-size: 1.5rem;">Video Title</h3>
                    <p id="m-cat" style="color: var(--primary-color);">Category</p>
                    <p style="margin-top: 15px; color: var(--text-muted); font-size: 0.9rem;">*This is a sandbox simulation. Real external videos cannot be loaded in this environment. Imagine a high-quality edit playing here!*</p>
                </div>
            </div>
        </div>
    </div>

    <!-- ==================== LOGIN VIEW ==================== -->
    <div id="login-view" class="hidden">
        <div class="login-box">
            <h2 style="margin-bottom: 20px;">Admin <span style="color: var(--primary-color);">Login</span></h2>
            <p style="color: var(--text-muted); margin-bottom: 20px; font-size: 0.9rem;">Use: admin / aifaz123</p>
            <div id="login-error" class="error-msg">Invalid credentials!</div>
            <input type="text" id="l-user" placeholder="Username">
            <input type="password" id="l-pass" placeholder="Password">
            <button class="btn btn-primary" style="width: 100%; margin-bottom: 15px;" onclick="attemptLogin()">Login to Dashboard</button>
            <a href="#" class="admin-link" onclick="showView('frontend'); return false;">← Back to Site</a>
        </div>
    </div>

    <!-- ==================== ADMIN VIEW ==================== -->
    <div id="admin-view" class="hidden">
        <div class="admin-sidebar">
            <h2>AIFAZ <span>Admin</span></h2>
            <ul class="admin-nav">
                <li class="active" onclick="switchAdminTab('dash-videos', this)">🎥 Videos</li>
                <li onclick="switchAdminTab('dash-services', this)">💼 Services</li>
                <li onclick="switchAdminTab('dash-tools', this)">🛠️ Tools & Skills</li>
                <li onclick="switchAdminTab('dash-info', this)">👤 Personal Info</li>
                <li style="margin-top: 50px; color: var(--danger-color);" onclick="logout()">🚪 Logout</li>
            </ul>
        </div>
        <div class="admin-content">
            
            <!-- VIDEOS TAB -->
            <div id="dash-videos" class="admin-panel active">
                <div class="admin-header">
                    <h2>Manage Videos</h2>
                </div>
                <div class="form-group">
                    <h3>Add New Video</h3>
                    <div style="display: flex; gap: 10px; margin-bottom: 10px;">
                        <input type="text" id="a-vid-title" placeholder="Video Title" style="flex: 2; margin:0;">
                        <select id="a-vid-cat" style="flex: 1; margin:0;">
                            <option value="Reels">Reels</option>
                            <option value="Shorts">Shorts</option>
                            <option value="UGC">UGC</option>
                            <option value="AI">AI</option>
                            <option value="Documentary">Documentary</option>
                        </select>
                        <select id="a-vid-emoji" style="flex: 1; margin:0;">
                            <option value="🎬">🎬 Reel</option>
                            <option value="📱">📱 Mobile</option>
                            <option value="🤖">🤖 AI</option>
                            <option value="🎥">🎥 Camera</option>
                            <option value="🔥">🔥 Fire</option>
                            <option value="✨">✨ Sparkle</option>
                        </select>
                    </div>
                    <button class="btn btn-primary" onclick="adminAddVideo()">+ Add Video</button>
                </div>
                <div class="admin-list" id="a-vid-list">
                    <!-- List generated by JS -->
                </div>
            </div>

            <!-- SERVICES TAB -->
            <div id="dash-services" class="admin-panel">
                <div class="admin-header">
                    <h2>Manage Services</h2>
                </div>
                <div class="form-group">
                    <h3>Add New Service</h3>
                    <input type="text" id="a-srv-title" placeholder="Service Title (e.g., Short-Form Edit)">
                    <input type="text" id="a-srv-price" placeholder="Price (e.g., \$30/video)">
                    <textarea id="a-srv-desc" placeholder="Description..." rows="2"></textarea>
                    <button class="btn btn-primary" onclick="adminAddService()">+ Add Service</button>
                </div>
                <div class="admin-list" id="a-srv-list">
                    <!-- List generated by JS -->
                </div>
            </div>

            <!-- TOOLS TAB -->
            <div id="dash-tools" class="admin-panel">
                <div class="admin-header">
                    <h2>Manage Tools & Skills</h2>
                </div>
                
                <div class="form-group">
                    <h3>Add Tool</h3>
                    <div style="display: flex; gap: 10px;">
                        <input type="text" id="a-tool-input" placeholder="e.g., Premiere Pro" style="margin:0;">
                        <button class="btn btn-primary" onclick="adminAddTool()">Add</button>
                    </div>
                    <div style="display: flex; flex-wrap: wrap; gap: 10px; margin-top: 15px;" id="a-tool-list">
                        <!-- Tools list -->
                    </div>
                </div>

                <div class="form-group">
                    <h3>Add Skill</h3>
                    <div style="display: flex; gap: 10px;">
                        <input type="text" id="a-skill-input" placeholder="e.g., Color Grading" style="margin:0;">
                        <button class="btn btn-primary" onclick="adminAddSkill()">Add</button>
                    </div>
                    <div style="display: flex; flex-wrap: wrap; gap: 10px; margin-top: 15px;" id="a-skill-list">
                        <!-- Skills list -->
                    </div>
                </div>
            </div>

            <!-- INFO TAB -->
            <div id="dash-info" class="admin-panel">
                <div class="admin-header">
                    <h2>Edit Personal Info</h2>
                    <button class="btn btn-primary" onclick="adminSaveInfo()">Save Changes</button>
                </div>
                <div class="form-group">
                    <label>Full Name</label>
                    <input type="text" id="a-info-name">
                    <label>Professional Title</label>
                    <input type="text" id="a-info-title">
                    <label>Tagline (Hero Section)</label>
                    <input type="text" id="a-info-tagline">
                    <label>Experience</label>
                    <input type="text" id="a-info-exp">
                    <label>Education</label>
                    <input type="text" id="a-info-edu">
                    <label>WhatsApp Number (Include Country Code, no +)</label>
                    <input type="text" id="a-info-phone" placeholder="91XXXXXXXXXX">
                    <label>About Me</label>
                    <textarea id="a-info-about" rows="6"></textarea>
                </div>
            </div>

        </div>
    </div>

    <!-- ==================== SCRIPTS ==================== -->
    <script>
        /* 
         * DATABASE SIMULATION
         * Note: The prompt requested localStorage. However, sandbox constraints 
         * prevent secure APIs like localStorage. To make this app 100% functional 
         * within this environment, I am using an in-memory object structured exactly 
         * like localStorage data. It persists across views but resets on hard reload.
         */

        const DEFAULT_DATA = {
            info: {
                name: "MD AIFAZ",
                title: "Professional Video Editor & UGC Content Creator",
                tagline: "I create high-performing videos that help creators and brands grow fast.",
                exp: "3+ Years",
                edu: "BCS FY Student",
                about: "I’m MD AIFAZ, a passionate video editor with 3+ years of experience creating engaging short-form videos, UGC content, and cinematic edits. I also create AI-based videos and documentary edits. Currently, I’m a BCS First Year student, combining creativity with modern digital skills to deliver content that performs.",
                phone: "919999999999" 
            },
            skills: ["Reels / Shorts Editing", "UGC Content Creation", "AI Video Editing", "Documentary Editing", "Social Media Content Optimization"],
            tools: ["CapCut", "VN Editor", "Alight Motion", "InShot", "Runway ML", "Midjourney", "HeyGen"],
            videos: [
                { id: 1, title: "Epic Gym Motivation Reel", category: "Reels", emoji: "🏋️‍♂️" },
                { id: 2, title: "Tech Product Review", category: "UGC", emoji: "📱" },
                { id: 3, title: "AI Generated Concept Trailer", category: "AI", emoji: "🤖" },
                { id: 4, title: "The History of Web3", category: "Documentary", emoji: "🌍" },
                { id: 5, title: "Viral Dance Edit", category: "Shorts", emoji: "💃" }
            ],
            services: [
                { id: 1, title: "Short-Form Video (Reels/Shorts)", price: "\$20 - \$50", desc: "Engaging edits with captions, transitions, and sound design to maximize retention." },
                { id: 2, title: "UGC Content Creation", price: "\$50 - \$100", desc: "Full package: Scripting advice, raw footage processing, and native platform editing." },
                { id: 3, title: "Documentary / Long-Form", price: "\$150+", desc: "Cinematic storytelling, color grading, advanced pacing and B-roll integration." }
            ],
            session: { loggedIn: false }
        };

        // Simulated Storage
        let appDB = JSON.parse(JSON.stringify(DEFAULT_DATA));

        function saveDB() {
            console.log("Database saved internally.");
            renderFrontend();
            renderAdminData();
        }

        // --- VIEW CONTROLLER ---
        function showView(viewId) {
            console.log("Switching view to:", viewId);
            document.getElementById('frontend-view').classList.add('hidden');
            document.getElementById('login-view').classList.add('hidden');
            document.getElementById('admin-view').classList.add('hidden');
            
            document.getElementById(viewId + '-view').classList.remove('hidden');

            if(viewId === 'frontend') renderFrontend();
            if(viewId === 'admin') renderAdminData();
        }

        // --- FRONTEND LOGIC ---
        function renderFrontend() {
            console.log("Rendering Frontend...");
            const data = appDB;

            // Info
            document.getElementById('f-name').innerText = data.info.name;
            document.getElementById('f-title').innerText = data.info.title;
            document.getElementById('f-tagline').innerText = data.info.tagline;
            document.getElementById('f-exp').innerText = data.info.exp;
            document.getElementById('f-about').innerText = data.info.about;
            document.getElementById('f-edu').innerText = data.info.edu;

            // Skills
            const skillsHtml = data.skills.map(s => `<span class="skill-tag">${s}</span>`).join('');
            document.getElementById('f-skills').innerHTML = skillsHtml;

            // Tools
            const toolsHtml = data.tools.map(t => `<div class="tool-card">⚡ ${t}</div>`).join('');
            document.getElementById('f-tools-grid').innerHTML = toolsHtml;

            // Services
            const srvHtml = data.services.map(s => `
                <div class="service-card">
                    <h3 class="service-title">${s.title}</h3>
                    <div class="service-price">${s.price}</div>
                    <p class="service-desc">${s.desc}</p>
                </div>
            `).join('');
            document.getElementById('f-services-grid').innerHTML = srvHtml;

            // Portfolio Categories (Extract unique)
            const categories = ["All", ...new Set(data.videos.map(v => v.category))];
            const catHtml = categories.map(c => `
                <button class="filter-btn ${c==='All'?'active':''}" onclick="filterPortfolio('${c}', this)">${c}</button>
            `).join('');
            document.getElementById('f-filters').innerHTML = catHtml;

            // Portfolio Videos
            renderPortfolioGrid(data.videos);
        }

        function renderPortfolioGrid(vids) {
            const grid = document.getElementById('f-portfolio-grid');
            if(vids.length === 0) {
                grid.innerHTML = '<p style="text-align:center; color: var(--text-muted); grid-column: 1/-1;">No videos in this category yet.</p>';
                return;
            }
            grid.innerHTML = vids.map(v => `
                <div class="video-card" onclick="openModal(${v.id})">
                    <div class="video-thumb">
                        ${v.emoji}
                        <div class="play-icon">▶️</div>
                    </div>
                    <div class="video-info">
                        <div class="video-cat">${v.category}</div>
                        <h3 class="video-title">${v.title}</h3>
                    </div>
                </div>
            `).join('');
        }

        function filterPortfolio(cat, btnElement) {
            // Update active button
            document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
            btnElement.classList.add('active');

            // Filter data
            if(cat === 'All') {
                renderPortfolioGrid(appDB.videos);
            } else {
                const filtered = appDB.videos.filter(v => v.category === cat);
                renderPortfolioGrid(filtered);
            }
        }

        // --- MODAL LOGIC ---
        function openModal(id) {
            console.log("Opening video modal for ID:", id);
            const vid = appDB.videos.find(v => v.id === id);
            if(!vid) return;

            document.getElementById('m-player').innerText = vid.emoji;
            document.getElementById('m-title').innerText = vid.title;
            document.getElementById('m-cat').innerText = vid.category;
            
            document.getElementById('video-modal').classList.add('active');
        }

        function closeModal() {
            document.getElementById('video-modal').classList.remove('active');
        }

        // --- WHATSAPP FORM LOGIC ---
        function submitWhatsAppForm() {
            console.log("WhatsApp form clicked.");
            const name = document.getElementById('c-name').value.trim();
            const budget = document.getElementById('c-budget').value.trim();
            const type = document.getElementById('c-type').value;
            const msg = document.getElementById('c-msg').value.trim();

            if(!name || !msg) {
                alert("Please fill in your name and message.");
                return;
            }

            const phone = appDB.info.phone;
            const formattedMessage = `Hello MD AIFAZ, my name is ${name}.%0A%0A*Project Type:* ${type}%0A*Estimated Budget:* $${budget}%0A%0A*Message:*%0A${msg}`;
            
            const waUrl = `https://wa.me/${phone}?text=${formattedMessage}`;
            console.log("Opening URL:", waUrl);
            window.open(waUrl, '_blank');
        }

        // --- LOGIN LOGIC ---
        function attemptLogin() {
            console.log("Login clicked.");
            const u = document.getElementById('l-user').value;
            const p = document.getElementById('l-pass').value;

            if(u === 'admin' && p === 'aifaz123') {
                console.log("Login Success!");
                document.getElementById('login-error').style.display = 'none';
                appDB.session.loggedIn = true;
                showView('admin');
            } else {
                console.log("Login Failed!");
                document.getElementById('login-error').style.display = 'block';
            }
        }

        function logout() {
            console.log("Logging out.");
            appDB.session.loggedIn = false;
            document.getElementById('l-user').value = '';
            document.getElementById('l-pass').value = '';
            showView('frontend');
        }

        // --- ADMIN DASHBOARD LOGIC ---
        function switchAdminTab(tabId, liElement) {
            document.querySelectorAll('.admin-nav li').forEach(li => li.classList.remove('active'));
            liElement.classList.add('active');

            document.querySelectorAll('.admin-panel').forEach(p => p.classList.remove('active'));
            document.getElementById(tabId).classList.add('active');
        }

        function renderAdminData() {
            const data = appDB;

            // Info Tab
            document.getElementById('a-info-name').value = data.info.name;
            document.getElementById('a-info-title').value = data.info.title;
            document.getElementById('a-info-tagline').value = data.info.tagline;
            document.getElementById('a-info-exp').value = data.info.exp;
            document.getElementById('a-info-edu').value = data.info.edu;
            document.getElementById('a-info-phone').value = data.info.phone;
            document.getElementById('a-info-about').value = data.info.about;

            // Lists
            renderAdminVideos();
            renderAdminServices();
            renderAdminToolsSkills();
        }

        function adminSaveInfo() {
            appDB.info.name = document.getElementById('a-info-name').value;
            appDB.info.title = document.getElementById('a-info-title').value;
            appDB.info.tagline = document.getElementById('a-info-tagline').value;
            appDB.info.exp = document.getElementById('a-info-exp').value;
            appDB.info.edu = document.getElementById('a-info-edu').value;
            appDB.info.phone = document.getElementById('a-info-phone').value;
            appDB.info.about = document.getElementById('a-info-about').value;
            saveDB();
            alert("Personal Info Saved!");
        }

        // Admin Videos
        function renderAdminVideos() {
            const list = document.getElementById('a-vid-list');
            list.innerHTML = appDB.videos.map(v => `
                <div class="admin-list-item">
                    <div><strong>${v.emoji} ${v.title}</strong> <span style="color:var(--text-muted); font-size:0.8rem;">(${v.category})</span></div>
                    <button class="btn btn-danger" onclick="adminDeleteVideo(${v.id})">Delete</button>
                </div>
            `).join('');
        }

        function adminAddVideo() {
            const title = document.getElementById('a-vid-title').value;
            const cat = document.getElementById('a-vid-cat').value;
            const emoji = document.getElementById('a-vid-emoji').value;

            if(!title) return alert("Title required");

            const newId = appDB.videos.length > 0 ? Math.max(...appDB.videos.map(v=>v.id)) + 1 : 1;
            appDB.videos.unshift({ id: newId, title, category: cat, emoji });
            
            document.getElementById('a-vid-title').value = ''; // clear
            saveDB();
        }

        function adminDeleteVideo(id) {
            appDB.videos = appDB.videos.filter(v => v.id !== id);
            saveDB();
        }

        // Admin Services
        function renderAdminServices() {
            const list = document.getElementById('a-srv-list');
            list.innerHTML = appDB.services.map(s => `
                <div class="admin-list-item">
                    <div><strong>${s.title}</strong> - <span style="color:var(--primary-color)">${s.price}</span></div>
                    <button class="btn btn-danger" onclick="adminDeleteService(${s.id})">Delete</button>
                </div>
            `).join('');
        }

        function adminAddService() {
            const title = document.getElementById('a-srv-title').value;
            const price = document.getElementById('a-srv-price').value;
            const desc = document.getElementById('a-srv-desc').value;

            if(!title || !price) return alert("Title and Price required");

            const newId = appDB.services.length > 0 ? Math.max(...appDB.services.map(s=>s.id)) + 1 : 1;
            appDB.services.push({ id: newId, title, price, desc });
            
            document.getElementById('a-srv-title').value = '';
            document.getElementById('a-srv-price').value = '';
            document.getElementById('a-srv-desc').value = '';
            saveDB();
        }

        function adminDeleteService(id) {
            appDB.services = appDB.services.filter(s => s.id !== id);
            saveDB();
        }

        // Admin Tools & Skills
        function renderAdminToolsSkills() {
            const tList = document.getElementById('a-tool-list');
            tList.innerHTML = appDB.tools.map((t, i) => `
                <span class="skill-tag">${t} <span style="cursor:pointer; color:var(--danger-color); margin-left:5px;" onclick="adminDelTool(${i})">×</span></span>
            `).join('');

            const sList = document.getElementById('a-skill-list');
            sList.innerHTML = appDB.skills.map((s, i) => `
                <span class="skill-tag">${s} <span style="cursor:pointer; color:var(--danger-color); margin-left:5px;" onclick="adminDelSkill(${i})">×</span></span>
            `).join('');
        }

        function adminAddTool() {
            const val = document.getElementById('a-tool-input').value.trim();
            if(val) { appDB.tools.push(val); document.getElementById('a-tool-input').value = ''; saveDB(); }
        }
        function adminDelTool(index) { appDB.tools.splice(index, 1); saveDB(); }

        function adminAddSkill() {
            const val = document.getElementById('a-skill-input').value.trim();
            if(val) { appDB.skills.push(val); document.getElementById('a-skill-input').value = ''; saveDB(); }
        }
        function adminDelSkill(index) { appDB.skills.splice(index, 1); saveDB(); }

        // --- INIT ---
        window.onload = () => {
            console.log("App Initialized. Loading Frontend.");
            renderFrontend();
        };

        // Close modal on outside click
        document.getElementById('video-modal').addEventListener('click', function(e) {
            if(e.target === this) closeModal();
        });
    </script>
</body>
</html>
