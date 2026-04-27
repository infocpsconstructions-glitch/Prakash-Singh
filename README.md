import wikipediaapi

def get_scam_summary(scam_name):
    # Set up the Wikipedia API (User agent is required by Wikimedia policy)
    wiki = wikipediaapi.Wikipedia(
        user_agent='EducationalScamBot (merlin@example.com)',
        language='en'
    )

    page = wiki.page(scam_name)

    if page.exists():
        print(f"--- {page.title} ---")
        # Get the first 500 characters of the summary
        print(page.summary[:500] + "...")
        print(f"\nRead full Wikipedia here: {page.fullurl}")
    else:
        print("Scam topic not found. Try '1992 Indian stock market scam' or 'Saradha Group'.")

# Example usage
get_scam_summary("1992 Indian stock market scam")





import wikipedia

# 1. Search for a list of related titles
results = wikipedia.search("Financial frauds in India")
print("Search Results:", results)

# 2. Get a summary of the first result
summary = wikipedia.summary(results[0], sentences=2)
print("\nSummary:", summary)

# 3. Get full page details (URL, title, full content)
page = wikipedia.page(results[0])
print("\nPage URL:", page.url)
```

import streamlit as st

# Data for Fraud Types and Actions
fraud_data = {
    "Phishing": {
        "description": "Scammers send fake emails or messages to steal login details or personal info.",
        "action": "Do not click links. Change your passwords immediately and report to your bank."
    },
    "Identity Theft": {
        "description": "Someone uses your personal information to open accounts or make purchases.",
        "action": "Freeze your credit reports and contact the [National Cyber Crime Reporting Portal](https://cybercrime.gov.in/)."
    },
    "Credit Card Fraud": {
        "description": "Unauthorized transactions made using your credit card details.",
        "action": "Block your card via your banking app and dispute the transactions with your bank."
    },
    "KYC Fraud": {
        "description": "Fraudsters impersonate bank officials to steal OTPs or sensitive IDs under the guise of updating KYC.",
        "action": "Never share OTPs. Note that official banks never ask for sensitive info over calls."
    },
    "Investment Scams": {
        "description": "Promising high returns with little risk, often via fake apps or social media.",
        "action": "Cease all payments and report the platform to financial regulators."
    }
}

# Streamlit UI
st.title("Financial Fraud Guide & Action Center")

# Search Button / Input
query = st.text_input("Search for a fraud type (e.g., 'Phishing', 'KYC'):")

if query:
    # Finding matches
    results = {k: v for k, v in fraud_data.items() if query.lower() in k.lower()}
    
    if results:
        for title, info in results.items():
            st.subheader(f"Type: {title}")
            st.write(f"**What it is:** {info['description']}")
            st.warning(f"**Action to take:** {info['action']}")
    else:
        st.error("No fraud type found. Try searching for 'Credit Card' or 'Identity'.")
else:
    st.info("Enter a keyword above to find prevention steps.")




<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FraudInfo | Searchable Database</title>
    <style>
        body { font-family: 'Segoe UI', sans-serif; background: #f4f7f6; margin: 0; padding: 20px; }
        .container { max-width: 800px; margin: auto; }
        header { text-align: center; margin-bottom: 30px; }
        
        /* Search Box */
        #searchBar {
            width: 100%;
            padding: 15px;
            font-size: 18px;
            border: 2px solid #2c3e50;
            border-radius: 25px;
            margin-bottom: 20px;
            box-sizing: border-box;
            outline: none;
        }

        /* Information Cards */
        .info-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 15px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            display: block; /* Hidden via JS if doesn't match search */
            transition: 0.3s;
        }

        .info-card h3 { color: #e74c3c; margin-top: 0; }
        .tag { 
            display: inline-block; 
            background: #eee; 
            padding: 2px 10px; 
            border-radius: 10px; 
            font-size: 12px; 
            color: #666;
            margin-bottom: 10px;
        }

        .highlight { background-color: yellow; }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>Financial Fraud Database</h1>
        <p>Type a keyword (e.g., "ATM", "Bank", "Identity") to find information.</p>
    </header>

    <!-- The Search Bar -->
<input type="text" id="searchBar" onkeyup="searchFraud()" placeholder="Search fraud types, keywords, or laws...">

<!-- The List to search through -->
<ul id="fraudList">
  <li>Phishing</li>
  <li>Identity Theft</li>
  <li>Wire Fraud (Law 18 U.S.C. § 1343)</li>
  <li>Credit Card Fraud</li>
  <li>Ponzi Schemes</li>
</ul>


    <div id="infoList">
        <!-- Content from the PDF -->
        <div class="info-card">
            <span class="tag">Type 4.1</span>
            <h3>Ponzi Schemes</h3>
            <p>Investment fraud that generates returns for earlier investors with money taken from later investors. Promises high returns with little risk.</p>
        </div>

        <div class="info-card">
            <span class="tag">Type 4.3</span>
            <h3>Identity Theft</h3>
            <p>Use of someone's identifying information without permission. Includes shoulder-surfing at ATMs or phishing for bank account numbers.</p>
        </div>

        <div class="info-card">
            <span class="tag">Type 4.8</span>
            <h3>KYC Fraud</h3>
            <p>Fraudsters send SMS saying your card/account will be blocked. They trick you into giving OTPs or installing apps for "verification."</p>
        </div>

        <div class="info-card">
            <span class="tag">Type 4.14</span>
            <h3>UPI-related Frauds</h3>
            <p>Involves "request money" links or fake URLs that infect phones with malware to steal financial information.</p>
        </div>

        <div class="info-card">
            <span class="tag">Law: Section 420</span>
            <h3>Cheating & Dishonesty</h3>
            <p>Under the Indian Penal Code: Punishment includes imprisonment for a term which may extend to 7 years and a fine.</p>
        </div>

        <div class="info-card">
            <span class="tag">Protection</span>
            <h3>Password Security</h3>
            <p>Use strong passwords with multi-factor authentication (MFA). Never click on suspicious pop-ups or links.</p>
        </div>
    </div>
</div>

<script>
    function searchFraud() {
        let input = document.getElementById('searchBar').value.toLowerCase();
        let cards = document.getElementsByClassName('info-card');

        for (let i = 0; i < cards.length; i++) {
            let text = cards[i].innerText.toLowerCase();
            if (text.includes(input)) {
                cards[i].style.display = "block";
            } else {
                cards[i].style.display = "none";
            }
        }
    }
</script>

</body>
</html>


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

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fraud & Law Directory</title>
    <style>
        body { font-family: 'Segoe UI', Arial, sans-serif; background: #f0f2f5; color: #333; line-height: 1.6; padding: 20px; }
        .container { max-width: 900px; margin: auto; }
        h1 { text-align: center; color: #1a2a6c; }
        p.subtitle { text-align: center; color: #666; margin-bottom: 40px; }

        /* Fraud Section */
        .fraud-entry { background: white; margin-bottom: 20px; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0,0,0,0.1); border-left: 5px solid #1a2a6c; }
        .fraud-header { padding: 20px; }
        .fraud-header h3 { margin: 0 0 10px 0; color: #e74c3c; }
        
        /* Law Button */
        .law-btn { background: #3498db; color: white; border: none; padding: 10px 15px; border-radius: 4px; cursor: pointer; font-weight: bold; transition: 0.3s; }
        .law-btn:hover { background: #2980b9; }

        /* Law Content (Hidden by default) */
        .law-info { display: none; background: #f9f9f9; padding: 20px; border-top: 1px solid #ddd; border-left: 5px solid #27ae60; }
        .law-info h4 { margin: 0 0 5px 0; color: #27ae60; }
        .punishment { color: #c0392b; font-weight: bold; margin-top: 10px; display: block; }
    </style>
</head>
<body>

<div class="container">
    <h1>Financial Fraud & Legal Provisions</h1>
    <p class="subtitle">Select a fraud type to view the corresponding Indian laws and punishments.</p>

    <!-- Entry 1 -->
    <div class="fraud-entry">
        <div class="fraud-header">
            <h3>1. Identity Theft & Personation</h3>
            <p>Using someone's electronic signature, password, or unique identification feature fraudulently.</p>
            <button class="law-btn" onclick="toggleLaw('law1')">See Legal Provision ↓</button>
        </div>
        <div id="law1" class="law-info">
            <h4>IT Act, 2000 - Section 66C & 66D</h4>
            <p>Deals with punishment for identity theft and cheating by personation using computer resources.</p>
            <span class="punishment">Punishment: Up to 3 years imprisonment and fine up to ₹1 Lakh.</span>
        </div>
    </div>

    <!-- Entry 2 -->
    <div class="fraud-entry">
        <div class="fraud-header">
            <h3>2. Corporate Fraud</h3>
            <p>Falsification or hiding of a company's financial information to make illegal profits or mislead the public.</p>
            <button class="law-btn" onclick="toggleLaw('law2')">See Legal Provision ↓</button>
        </div>
        <div id="law2" class="law-info">
            <h4>Companies Act, 2013 - Section 447</h4>
            <p>Strict provisions for any person found guilty of fraud involving company affairs or public interest.</p>
            <span class="punishment">Punishment: 6 months to 10 years imprisonment + Fine up to 3x the fraud amount.</span>
        </div>
    </div>

    <!-- Entry 3 -->
    <div class="fraud-entry">
        <div class="fraud-header">
            <h3>3. General Cheating (Ponzi/UPI/KYC)</h3>
            <p>Inducing a person to deliver property or money through deception or dishonest intention.</p>
            <button class="law-btn" onclick="toggleLaw('law3')">See Legal Provision ↓</button>
        </div>
        <div id="law3" class="law-info">
            <h4>Indian Penal Code (IPC) - Section 420</h4>
            <p>The primary law for "Cheating and dishonestly inducing delivery of property."</p>
            <span class="punishment">Punishment: Up to 7 years imprisonment and a fine.</span>
        </div>
    </div>

    <!-- Entry 4 -->
    <div class="fraud-entry">
        <div class="fraud-header">
            <h3>4. Money Laundering</h3>
            <p>Disguising the origins of money obtained illegally to make it appear legitimate.</p>
            <button class="law-btn" onclick="toggleLaw('law4')">See Legal Provision ↓</button>
        </div>
        <div id="law4" class="law-info">
            <h4>Prevention of Money Laundering Act, 2002 - Section 4</h4>
            <p>Provides for the punishment of anyone involved in any process or activity connected with the proceeds of crime.</p>
            <span class="punishment">Punishment: 3 to 7 years rigorous imprisonment and a fine.</span>
        </div>
    </div>

</div>

<script>
    function toggleLaw(id) {
        var x = document.getElementById(id);
        if (x.style.display === "block") {
            x.style.display = "none";
        } else {
            // Close other open laws first (optional)
            var allLaws = document.getElementsByClassName("law-info");
            for (var i = 0; i < allLaws.length; i++) {
                allLaws[i].style.display = "none";
            }
            x.style.display = "block";
        }
    }
</script>

</body>
</html>
