<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Abdulmalik Khan | Google Enthusiast</title>
    <style>
        :root {
            --google-blue: #4285F4;
            --google-red: #EA4335;
            --google-yellow: #FBBC05;
            --google-green: #34A853;
            --dark-bg: #121212;
            --card-bg: #1e1e1e;
            --text-main: #ffffff;
            --text-dim: #b0b0b0;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--dark-bg);
            color: var(--text-main);
            line-height: 1.6;
            margin: 0;
        }

        .container {
            max-width: 850px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        header {
            text-align: center;
            padding-bottom: 40px;
            border-bottom: 1px solid #333;
        }

        h1 { font-size: 2.8rem; margin-bottom: 10px; }
        .subtitle { font-size: 1.2rem; color: var(--google-blue); font-weight: bold; }

        .about-section { margin: 40px 0; }

        .community-card {
            background: linear-gradient(145deg, #1e1e1e, #252525);
            border-left: 4px solid var(--google-red);
            padding: 25px;
            border-radius: 8px;
            margin: 30px 0;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
            margin-top: 30px;
        }

        .skill-list {
            background: var(--card-bg);
            padding: 20px;
            border-radius: 12px;
            border: 1px solid #333;
        }

        h2 { color: var(--google-green); font-size: 1.5rem; }
        h3 { color: var(--google-yellow); font-size: 1.5rem; }

        ul { list-style: none; padding: 0; }
        li { 
            padding: 8px 0; 
            border-bottom: 1px solid #2a2a2a;
            color: var(--text-dim);
        }
        li:last-child { border-bottom: none; }

        .btn {
            display: inline-block;
            background: var(--google-blue);
            color: white;
            padding: 12px 24px;
            text-decoration: none;
            border-radius: 4px;
            margin-top: 15px;
            transition: 0.3s;
        }

        .btn:hover { background: #3367d6; transform: translateY(-2px); }

        @media (max-width: 600px) {
            .skills-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>Abdulmalik Khan</h1>
        <div class="subtitle">Google Enthusiast & Hardware Optimizer</div>
        <p style="color: var(--text-dim);">Pushing ChromeOS and Android to their absolute limits.</p>
    </header>

    <section class="about-section">
        <h2>The Mission</h2>
        <p>I don't just use Google hardware; I attempt to find its breaking point. My work focuses on extracting every ounce of performance and capability from <strong>Chromebooks</strong> and <strong>Android</strong> devices through deep system-level exploration.</p>
    </section>

    <div class="community-card">
        <h3>Member of Crosbreaker</h3>
        <p>I am an active contributor to the Crosbreaker community. We are a group dedicated to advanced ChromeOS development and modifications.</p>
        <a href="#" class="btn">Join the Community</a>
    </div>

    <div class="skills-grid">
        <div class="skill-list">
            <h2>Current Strengths</h2>
            <ul>
                <li>Bash Scripting</li>
                <li>Low-level Chromebook Dev</li>
                <li>Security Research</li>
                <li>Politics & Economics</li>
            </ul>
        </div>

        <div class="skill-list">
            <h3>Currently Mastering</h3>
            <ul>
                <li>HTML, CSS, & JavaScript</li>
                <li>Reverse Engineering</li>
                <li>Rust / C / C++</li>
                <li>Assembly Language</li>
                <li>Low Level Programming</li>
            </ul>
        </div>
    </div>

    <footer style="margin-top: 60px; text-align: center; color: #555; font-size: 0.9rem;">
        <p>Built by Abdulmalik Khan | &copy; 2024</p>
    </footer>
</div>

</body>
</html>
