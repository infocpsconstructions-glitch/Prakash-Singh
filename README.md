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
    <p>&copy; 2024 Project Presentation</p>
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
