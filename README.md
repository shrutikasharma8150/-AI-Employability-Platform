# -AI-Employability-Platform
AI-powered readiness and employability platform
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aesthetic Career Guidance Platform</title>
    <style>
        :root {
            --bg-beige: #F5F2EB;
            --chocolate: #4A3319;
            --brown: #8C6239;
            --black: #1A1A1A;
            --white: #FFFFFF;
            --card-bg: #FFFFFF;
            --accent: #D4A373;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-beige);
            color: var(--black);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            margin-top: 10px;
        }

        header h1 {
            color: var(--chocolate);
            font-size: 2.2rem;
            margin-bottom: 8px;
        }

        header p {
            color: var(--brown);
            font-size: 1.1rem;
        }

        .container {
            background-color: var(--card-bg);
            border: 2px solid var(--brown);
            border-radius: 16px;
            padding: 30px;
            width: 100%;
            max-width: 800px;
            box-shadow: 0 10px 25px rgba(74, 51, 25, 0.1);
            margin-bottom: 40px;
        }

        .step {
            display: none;
        }

        .step.active {
            display: block;
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h2 {
            color: var(--chocolate);
            margin-bottom: 20px;
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: var(--black);
            font-weight: 600;
        }

        input[type="text"], select {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--brown);
            border-radius: 8px;
            background-color: var(--bg-beige);
            color: var(--black);
            font-size: 1rem;
        }

        .options-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }

        .option-card {
            background-color: var(--bg-beige);
            border: 2px solid var(--brown);
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            color: var(--chocolate);
        }

        .option-card:hover, .option-card.selected {
            background-color: var(--chocolate);
            color: var(--white);
            border-color: var(--chocolate);
            transform: translateY(-3px);
        }

        button.btn {
            background-color: var(--chocolate);
            color: var(--white);
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            font-size: 1rem;
            cursor: pointer;
            font-weight: bold;
            transition: background-color 0.3s;
            margin-top: 20px;
        }

        button.btn:hover {
            background-color: var(--brown);
        }

        .question-box {
            margin-bottom: 20px;
            padding: 15px;
            background: var(--bg-beige);
            border-radius: 8px;
            border-left: 4px solid var(--brown);
        }

        .question-box p {
            font-weight: 600;
            margin-bottom: 10px;
            color: var(--chocolate);
        }

        .radio-options label {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: normal;
            margin-bottom: 8px;
            cursor: pointer;
        }

        .score-card {
            text-align: center;
            padding: 20px;
            background: var(--bg-beige);
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .score-card h3 {
            font-size: 2.5rem;
            color: var(--chocolate);
            margin-bottom: 10px;
        }

        .roadmap-item, .weakness-item {
            background: var(--bg-beige);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 12px;
            border-left: 4px solid var(--chocolate);
        }

        .roadmap-item h4, .weakness-item h4 {
            color: var(--chocolate);
            margin-bottom: 5px;
        }
    </style>
</head>
<body>

    <header>
        <h1><b>CAREER PATH FINDER</b></h1>
        <p><i>Discover your ideal career path, test your skills, and get personalized guidance</i></p>
    </header>

    <div class="container">
        <!-- Step 1: Student Registration / Profile -->
        <div id="step-1" class="step active">
            <h2>👤 Step 1: Student Registration & Profile</h2>
            <div class="form-group">
                <label for="studentName">Full Name:</label>
                <input type="text" id="studentName" placeholder="Enter your full name">
            </div>
            <div class="form-group">
                <label for="studentEmail">Email Address:</label>
                <input type="text" id="studentEmail" placeholder="Enter your email">
            </div>
            <button class="btn" onclick="nextStep(2)">Next: Select Field ➡️</button>
        </div>

        <!-- Step 2: Select Target Career Field & Role -->
        <div id="step-2" class="step">
            <h2>🎯 Step 2: Select Target Career Field</h2>
            <p>Choose your primary domain of interest:</p>
            <div class="options-grid" id="fieldGrid">
                <div class="option-card" onclick="selectField('Commerce')">📊 Commerce & Finance</div>
                <div class="option-card" onclick="selectField('Maths')">📐 Mathematics & Tech</div>
                <div class="option-card" onclick="selectField('Arts')">🎨 Arts & Humanities</div>
            </div>
            
            <div id="roleSelectionContainer" style="margin-top: 25px; display: none;">
                <label for="careerRole">Select Specific Career Path / Role:</label>
                <select id="careerRole">
                    <!-- Dynamically populated options -->
                </select>
                <button class="btn" onclick="nextStep(3)">Next: Skill Assessment 📝</button>
            </div>
        </div>

        <!-- Step 3: Skill Assessment (20 Questions simulation) -->
        <div id="step-3" class="step">
            <h2>📝 Step 3: Skill Assessment (20 Mini-Questions)</h2>
            <p>Answer the following foundational questions related to your chosen path:</p>
            <div id="questionsContainer" style="max-height: 400px; overflow-y: auto; padding-right: 10px; margin-top: 15px;">
                <!-- Generated dynamically via JS -->
            </div>
            <button class="btn" onclick="submitAssessment()">Submit Assessment 🏁</button>
        </div>

        <!-- Step 4: Assessment Result & Score Card -->
        <div id="step-4" class="step">
            <h2>📊 Step 4: Assessment Result & Skill Indicators</h2>
            <div class="score-card">
                <p>Your Final Score:</p>
                <h3 id="finalScoreDisplay">0 / 20</h3>
                <p id="scoreMessage">Great effort!</p>
            </div>
            <button class="btn" onclick="nextStep(5)">Next: AI Skill-Gap Analysis 🔍</button>
        </div>

        <!-- Step 5: AI-Assisted Skill-Gap Analysis -->
        <div id="step-5" class="step">
            <h2>🔍 Step 5: AI-Assisted Skill-Gap Analysis</h2>
            <p>Here are the areas where you need improvement based on your performance:</p>
            <div id="weaknessContainer" style="margin-top: 15px;">
                <!-- Populated via JS -->
            </div>
            <button class="btn" onclick="nextStep(6)">Next: Personalized Learning Roadmap 🗺️</button>
        </div>

        <!-- Step 6: Personalized Learning & Project Roadmap -->
        <div id="step-6" class="step">
            <h2>🗺️ Step 6: Personalized Learning / Project Roadmap</h2>
            <p>Follow this step-by-step roadmap to bridge your gaps and master your career:</p>
            <div id="roadmapContainer" style="margin-top: 15px;">
                <!-- Populated via JS -->
            </div>
            <button class="btn" onclick="nextStep(7)">Next: Progress Dashboard 📈</button>
        </div>

        <!-- Step 7: Progress Dashboard -->
        <div id="step-7" class="step">
            <h2>📈 Step 7: Progress Dashboard</h2>
            <div class="score-card">
                <p>Status: Profile Complete & Assessment Evaluated</p>
                <h3 style="font-size: 1.8rem; color: var(--brown);">Ready for Success! 🌟</h3>
                <p>You can restart or review your roadmap anytime.</p>
            </div>
            <button class="btn" onclick="resetApp()">Start Over 🔄</button>
        </div>
    </div>

    <script>
        let currentStep = 1;
        let selectedFieldVal = "";
        let selectedRoleVal = "";
        let userAnswers = {};

        const careers = {
            Commerce: ["Financial Analyst", "Chartered Accountant", "Investment Banker", "Marketing Manager"],
            Maths: ["Data Scientist", "Software Engineer", "Actuary", "AI/ML Engineer"],
            Arts: ["UI/UX Designer", "Content Strategist", "Journalist", "Creative Director"]
        };

        function nextStep(stepNum) {
            if (stepNum === 2) {
                const name = document.getElementById('studentName').value;
                if(!name) {
                    alert('Please enter your name to proceed!');
                    return;
                }
            }
            if (stepNum === 3) {
                selectedRoleVal = document.getElementById('careerRole').value;
                if(!selectedRoleVal) {
                    alert('Please select a career role!');
                    return;
                }
                generateQuestions();
            }
            
            document.querySelectorAll('.step').forEach(el => el.classList.remove('active'));
            document.getElementById(`step-${stepNum}`).classList.add('active');
            currentStep = stepNum;
            window.scrollTo(0, 0);
        }

        function selectField(field) {
            selectedFieldVal = field;
            document.querySelectorAll('#fieldGrid .option-card').forEach(card => card.classList.remove('selected'));
            event.currentTarget.classList.add('selected');

            const roleSelect = document.getElementById('careerRole');
            roleSelect.innerHTML = "";
            careers[field].forEach(role => {
                let opt = document.createElement('option');
                opt.value = role;
                opt.textContent = role;
                roleSelect.appendChild(opt);
            });
            document.getElementById('roleSelectionContainer').style.display = 'block';
        }

        function generateQuestions() {
            const container = document.getElementById('questionsContainer');
            container.innerHTML = "";
            // Generating 20 dynamic mock questions for demonstration
            for(let i = 1; i <= 20; i++) {
                let qBox = document.createElement('div');
                qBox.className = 'question-box';
                qBox.innerHTML = `
                    <p>Q${i}: Fundamental concept check regarding ${selectedRoleVal}?</p>
                    <div class="radio-options">
                        <label><input type="radio" name="q${i}" value="A"> Option A: Core theoretical approach</label>
                        <label><input type="radio" name="q${i}" value="B"> Option B: Advanced practical methodology</label>
                        <label><input type="radio" name="q${i}" value="C"> Option C: Standard industrial framework</label>
                    </div>
                `;
                container.appendChild(qBox);
            }
        }

        function submitAssessment() {
            let score = 0;
            for(let i = 1; i <= 20; i++) {
                let radios = document.getElementsByName(`q${i}`);
                for(let r of radios) {
                    if(r.checked) {
                        // Simulate random correct scoring for demo purposes
                        if(r.value === 'C' || r.value === 'B') score++;
                    }
                }
            }
            
            document.getElementById('finalScoreDisplay').textContent = `${score} / 20`;
            let msg = score > 18 ? "Excellent performance! You have strong core foundations. 🌟" : "Good attempt, but there are clear areas for improvement! 💡";
            document.getElementById('scoreMessage').textContent = msg;

            generateAnalysisAndRoadmap(score);
            nextStep(4);
        }

        function generateAnalysisAndRoadmap(score) {
            // Weakness analysis
            const weakContainer = document.getElementById('weaknessContainer');
            weakContainer.innerHTML = `
                <div class="weakness-item">
                    <h4>⚠️ Weakness Area 1: Advanced Applied Problem Solving</h4>
                    <p>You showed gaps in handling complex practical case studies related to ${selectedRoleVal}. Focus more on scenario-based learning.</p>
                </div>
                <div class="weakness-item">
                    <h4>⚠️ Weakness Area 2: Industry Tools & Framework Efficiency</h4>
                    <p>Your conceptual speed can be enhanced by mastering standard tools and up-to-date industry practices.</p>
                </div>
            `;

            // Roadmap
            const roadContainer = document.getElementById('roadmapContainer');
            roadContainer.innerHTML = `
                <div class="roadmap-item">
                    <h4>Phase 1: Foundation Strengthening (Weeks 1-3)</h4>
                    <p>Revisit core textbooks and fundamental terminology of ${selectedFieldVal} and ${selectedRoleVal}.</p>
                </div>
                <div class="roadmap-item">
                    <h4>Phase 2: Practical Projects (Weeks 4-7)</h4>
                    <p>Build at least 2 real-world mini projects to bridge your practical gaps.</p>
                </div>
                <div class="roadmap-item">
                    <h4>Phase 3: Mock Testing & Certification (Weeks 8-10)</h4>
                    <p>Take regular mock tests and earn verified credentials to boost your profile confidence.</p>
                </div>
            `;
        }

        function resetApp() {
            currentStep = 1;
            document.getElementById('studentName').value = "";
            document.getElementById('studentEmail').value = "";
            document.getElementById('roleSelectionContainer').style.display = 'none';
            document.querySelectorAll('.option-card').forEach(c => c.classList.remove('selected'));
            nextStep(1);
        }
    </script>
</body>
</html>