<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Financial Scams in India</title>
    <style>
        body { font-family: 'Segoe UI', sans-serif; line-height: 1.6; margin: 0; background: #f4f4f9; color: #333; }
        header { background: #2c3e50; color: white; padding: 2rem; text-align: center; }
        nav { position: sticky; top: 0; background: #34495e; padding: 10px; text-align: center; }
        nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; }
        section { padding: 40px; max-width: 800px; margin: auto; background: white; margin-bottom: 20px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        h2 { color: #e67e22; border-bottom: 2px solid #eee; padding-bottom: 10px; }
        ul { list-style-type: square; }
        footer { text-align: center; padding: 20px; color: #777; }
        .highlight { font-weight: bold; color: #c0392b; }
    </style>
</head>
<body>

<header>
    <h1>Financial Scams in India</h1>
    <p>Project Presentation by <strong>Prakash Singh</strong></p>
</header>

<nav id="navbar"></nav>

<main id="content-area"></main>

<footer>
    <p>&copy; 2026 Project Presentation</p>
</footer>

<script>
    // DATA FROM THE PDF
    const presentationData = [
        { title: "Introduction", points: ["Financial fraud is rising", "Affects economy", "Digital fraud increasing"] },
        { title: "Types of Fraud", points: ["Ponzi Scheme", "Cyber Fraud", "Bank Fraud", "Identity Theft"] },
        { title: "Ponzi Scheme", points: ["Fake investment returns", "Uses new investors' money"] },
        { title: "Cyber Fraud", points: ["Phishing", "OTP scams", "UPI frauds"] },
        { title: "Major Scams", points: ["Harshad Mehta Scam", "Nirav Modi Scam", "Vijay Mallya Case"] },
        { title: "Impact", points: ["Loss of money", "Loss of trust", "Economic instability"] },
        { title: "Legal Framework", points: ["IPC Sections", "IT Act", "Companies Act"] },
        { title: "Prevention", points: ["Strong passwords", "Avoid unknown links", "Enable 2FA"] },
        { title: "Conclusion", points: ["Awareness is key", "Stay alert", "Be safe"] }
    ];

    const contentArea = document.getElementById('content-area');
    const navbar = document.getElementById('navbar');

    // JAVASCRIPT TO RENDER THE PAGE
    presentationData.forEach((section, index) => {
        // Create Navigation Links
        const navLink = document.createElement('a');
        navLink.href = `#section-${index}`;
        navLink.innerText = section.title;
        navbar.appendChild(navLink);

        // Create Content Sections
        const sectionEl = document.createElement('section');
        sectionEl.id = `section-${index}`;
        
        const h2 = document.createElement('h2');
        h2.innerText = section.title;
        
        const ul = document.createElement('ul');
        section.points.forEach(point => {
            const li = document.createElement('li');
            li.innerText = point;
            ul.appendChild(li);
        });

        sectionEl.appendChild(h2);
        sectionEl.appendChild(ul);
        contentArea.appendChild(sectionEl);
    });
</script>

</body>
</html>








<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FraudGuard | Financial Awareness</title>
    <style>
        /* CSS Styling */
        :root {
            --primary: #2c3e50;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #34495e;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            margin: 0;
            color: #333;
            background-color: var(--light);
        }

        header {
            background: var(--primary);
            color: white;
            padding: 2rem 1rem;
            text-align: center;
        }

        nav {
            background: var(--dark);
            padding: 0.5rem;
            position: sticky;
            top: 0;
            display: flex;
            justify-content: center;
        }

        nav a {
            color: white;
            text-decoration: none;
            padding: 0.5rem 1.5rem;
            transition: 0.3s;
        }

        nav a:hover {
            color: var(--accent);
        }

        .container {
            max-width: 1000px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .card {
            background: white;
            padding: 2rem;
            margin-bottom: 2rem;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        h2 {
            color: var(--primary);
            border-bottom: 2px solid var(--accent);
            padding-bottom: 0.5rem;
        }

        .fraud-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
        }

        .fraud-item {
            border: 1px solid #ddd;
            padding: 1rem;
            border-radius: 5px;
            background: #f9f9f9;
        }

        footer {
            text-align: center;
            padding: 2rem;
            background: var(--primary);
            color: white;
            margin-top: 3rem;
        }

        .btn {
            background: var(--accent);
            color: white;
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>

<header>
    <h1>Financial Fraud Awareness</h1>
    <p>Empowering you against digital and financial scams</p>
</header>

<nav>
    <a href="#about">What is Fraud?</a>
    <a href="#types">Common Types</a>
    <a href="#tips">Protection Tips</a>
</nav>

<div class="container">
    
    <!-- About Section -->
    <section id="about" class="card">
        <h2>What is Financial Fraud?</h2>
        <p>As per the document, financial fraud is an illegal act intended to deprive you of your money for personal gains. It often involves deceit, trickery, or the intentional perversion of truth.</p>
        <blockquote>"Technology has become the weapon of choice for fraudsters."</blockquote>
    </section>

    <!-- Types Section -->
    <section id="types" class="card">
        <h2>Common Fraud Types</h2>
        <div class="fraud-grid">
            <div class="fraud-item">
                <h3>Ponzi Schemes</h3>
                <p>Investment frauds that use money from new investors to pay earlier ones.</p>
            </div>
            <div class="fraud-item">
                <h3>Identity Theft</h3>
                <p>Using someone’s identifying information (like bank details) without permission for economic gain.</p>
            </div>
            <div class="fraud-item">
                <h3>KYC Fraud</h3>
                <p>Unsolicited messages claiming your account will be blocked to trick you into sharing OTPs.</p>
            </div>
            <div class="fraud-item">
                <h3>Phishing</h3>
                <p>Tricky emails or pop-ups appearing to be from legitimate sources like banks.</p>
            </div>
        </div>
    </section>

    <!-- Tips Section -->
    <section id="tips" class="card">
        <h2>How to Protect Yourself</h2>
        <ul>
            <li><strong>Strong Passwords:</strong> Use robust passwords with multi-factor authentication.</li>
            <li><strong>Shoulder Surfing:</strong> Always cover your hand while entering your PIN at an ATM.</li>
            <li><strong>Verify Links:</strong> Never click on unsolicited "request money" links or fake URLs.</li>
            <li><strong>Stay Informed:</strong> Read resources like the RBI’s "Raju and the Forty Thieves" booklet.</li>
        </ul>
        <button class="btn" onclick="alert('Stay vigilant! Never share your OTP with anyone.')">Get Emergency Support</button>
    </section>

</div>

<footer>
    <p>&copy; 2026 FraudGuard Educational Resource. Information based on provided Research Documents.</p>
</footer>

</body>
</html>

