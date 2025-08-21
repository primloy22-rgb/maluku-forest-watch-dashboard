# maluku-forest-watch-dashboard
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Maluku Forest Watch - Project Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Earthy Neutrals -->
    <!-- Application Structure Plan: The SPA is designed as a narrative journey. It starts with a compelling hero section stating the vision. It then flows into the core problem ("The Challenge"), presenting the inefficiencies of the old system. This is immediately contrasted with "The Solution," which introduces the 'Maluku Forest Watch' app. The "Impact" section uses dynamic charts to quantify success criteria, making the goals tangible. The "Action Plan" section provides a clear, interactive roadmap. This thematic, storytelling structure was chosen over a direct 1:1 mapping of the report to create a more engaging and persuasive experience for stakeholders, guiding them from the 'why' to the 'how'. -->
    <!-- Visualization & Content Choices: 
        - Report Info: Project Vision -> Goal: Inspire -> Viz/Method: Hero section with a strong headline -> Interaction: None -> Justification: Immediately grabs attention and sets a positive, forward-looking tone.
        - Report Info: Assess (The Problem) -> Goal: Compare -> Viz/Method: Side-by-side comparison cards (HTML/CSS) for "Old vs. New" -> Interaction: Subtle hover effects -> Justification: Clearly illustrates the inefficiencies and the benefits of the proposed solution.
        - Report Info: Gaps (Readiness Scores) -> Goal: Inform -> Viz/Method: Radar Chart (Chart.js) -> Interaction: Tooltips on hover -> Justification: A radar chart provides a quick, holistic view of the project's strengths and weaknesses across different domains.
        - Report Info: Success Criteria -> Goal: Inform/Compare -> Viz/Method: Dynamic Bar Chart (Chart.js) -> Interaction: Tooltips on hover -> Justification: Bar charts are excellent for comparing discrete quantitative targets, making the success metrics easy to grasp.
        - Report Info: Next Steps (Timeline) -> Goal: Organize/Change -> Viz/Method: Interactive vertical timeline (HTML/CSS/JS) -> Interaction: Clicking on a step reveals details -> Justification: An interactive timeline makes the project plan digestible and allows users to explore the roadmap at their own pace.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FDFBF8;
            color: #3A3A3A;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 500px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .nav-link {
            transition: color 0.3s ease;
        }
        .nav-link:hover {
            color: #4A5568;
        }
        .timeline-item::before {
            content: '';
            position: absolute;
            left: -31px;
            top: 50%;
            transform: translateY(-50%);
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: #D4C4A3;
            border: 4px solid #FDFBF8;
        }
    </style>
</head>
<body class="antialiased">

    <header class="bg-white/80 backdrop-blur-md sticky top-0 z-50 shadow-sm">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <div class="text-xl font-bold text-[#2C5234]">
                Maluku Forest Watch
            </div>
            <div class="hidden md:flex space-x-8">
                <a href="#challenge" class="nav-link text-gray-600">The Challenge</a>
                <a href="#solution" class="nav-link text-gray-600">The Solution</a>
                <a href="#impact" class="nav-link text-gray-600">Impact</a>
                <a href="#plan" class="nav-link text-gray-600">Action Plan</a>
            </div>
            <button id="mobile-menu-button" class="md:hidden focus:outline-none">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path></svg>
            </button>
        </nav>
        <div id="mobile-menu" class="hidden md:hidden px-6 pb-4">
            <a href="#challenge" class="block py-2 nav-link text-gray-600">The Challenge</a>
            <a href="#solution" class="block py-2 nav-link text-gray-600">The Solution</a>
            <a href="#impact" class="block py-2 nav-link text-gray-600">Impact</a>
            <a href="#plan" class="block py-2 nav-link text-gray-600">Action Plan</a>
        </div>
    </header>

    <main>
        <section id="hero" class="py-20 md:py-32 bg-cover bg-center" style="background-color: #F0EBE3;">
            <div class="container mx-auto px-6 text-center">
                <h1 class="text-4xl md:text-6xl font-bold text-[#2C5234] mb-4">Empowering Conservation with Green Technology</h1>
                <p class="text-lg md:text-xl text-gray-700 max-w-3xl mx-auto">
                    Transforming forest monitoring in Maluku with a real-time, data-driven platform to protect our vital ecosystems and reduce our digital carbon footprint.
                </p>
            </div>
        </section>

        <section id="challenge" class="py-16 md:py-24">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold text-[#2C5234]">The Challenge: A Digital Carbon Gap</h2>
                    <p class="mt-4 text-lg text-gray-600 max-w-2xl mx-auto">The current forest monitoring process is inefficient and unsustainable, relying on outdated methods that hinder rapid response to environmental threats.</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8 max-w-4xl mx-auto">
                    <div class="bg-white p-6 rounded-lg shadow-md border border-gray-200">
                        <h3 class="text-xl font-semibold mb-3 text-red-700">The Old Way: Manual & Inefficient</h3>
                        <ul class="space-y-2 text-gray-600 list-disc list-inside">
                            <li>Heavy reliance on paper forms</li>
                            <li>Data stored in decentralized, offline files</li>
                            <li>Prone to human error and data loss</li>
                            <li>High carbon footprint from travel and paper</li>
                            <li>Slow data processing and delayed insights</li>
                        </ul>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-md border border-gray-200">
                        <h3 class="text-xl font-semibold mb-3 text-green-700">The New Vision: Digital & Sustainable</h3>
                        <ul class="space-y-2 text-gray-600 list-disc list-inside">
                            <li>Direct digital input via mobile app</li>
                            <li>Centralized, real-time cloud database</li>
                            <li>Improved data accuracy and security</li>
                            <li>Reduced travel and zero paper waste</li>
                            <li>Instant data analysis for faster action</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <section id="solution" class="py-16 md:py-24 bg-white">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold text-[#2C5234]">The Solution: Maluku Forest Watch App</h2>
                    <p class="mt-4 text-lg text-gray-600 max-w-2xl mx-auto">A mobile-friendly, cloud-based application to streamline data collection, minimize energy consumption, and make conservation efforts more effective.</p>
                </div>
                <div class="grid md:grid-cols-3 gap-8 text-center">
                    <div class="p-4">
                        <div class="text-4xl mb-3 text-[#D4C4A3]">📱</div>
                        <h3 class="text-xl font-semibold mb-2">Field Data Entry</h3>
                        <p class="text-gray-600">Researchers directly input data, GPS coordinates, and photos, even in offline environments.</p>
                    </div>
                    <div class="p-4">
                        <div class="text-4xl mb-3 text-[#D4C4A3]">☁️</div>
                        <h3 class="text-xl font-semibold mb-2">Cloud Sync & Storage</h3>
                        <p class="text-gray-600">Data syncs to a central, secure database, powered by an energy-efficient serverless architecture.</p>
                    </div>
                    <div class="p-4">
                        <div class="text-4xl mb-3 text-[#D4C4A3]">📊</div>
                        <h3 class="text-xl font-semibold mb-2">Real-time Dashboard</h3>
                        <p class="text-gray-600">An admin dashboard provides instant data visualization and analysis for informed decision-making.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="impact" class="py-16 md:py-24">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold text-[#2C5234]">Measuring Success & Readiness</h2>
                    <p class="mt-4 text-lg text-gray-600 max-w-2xl mx-auto">We have defined clear, measurable objectives to track our project's impact and have assessed our current readiness to tackle the challenges ahead.</p>
                </div>
                <div class="grid lg:grid-cols-2 gap-12 items-center">
                    <div>
                        <h3 class="text-2xl font-semibold text-center mb-4">Project Readiness</h3>
                        <div class="chart-container">
                            <canvas id="readinessChart"></canvas>
                        </div>
                    </div>
                    <div>
                        <h3 class="text-2xl font-semibold text-center mb-4">Key Success Metrics</h3>
                        <div class="chart-container h-80 md:h-96">
                            <canvas id="successChart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="plan" class="py-16 md:py-24 bg-white">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold text-[#2C5234]">Our Action Plan</h2>
                    <p class="mt-4 text-lg text-gray-600 max-w-2xl mx-auto">A phased approach to bring our strategy to life, from initial planning to full-scale implementation.</p>
                </div>
                <div class="max-w-2xl mx-auto">
                    <div class="relative border-l-2 border-dashed border-gray-300 ml-4">
                        <div class="timeline-item mb-12 pl-12">
                            <h4 class="text-lg font-semibold text-[#2C5234]">First 7 Days: Foundation</h4>
                            <p class="text-sm text-gray-500 mb-2">Phase 1</p>
                            <p class="text-gray-600">Define app features, form the core project team, and research technology stacks for offline-first development.</p>
                        </div>
                        <div class="timeline-item mb-12 pl-12">
                            <h4 class="text-lg font-semibold text-[#2C5234]">14 Days: Prototyping</h4>
                            <p class="text-sm text-gray-500 mb-2">Phase 2</p>
                            <p class="text-gray-600">Build a low-fidelity UI prototype, secure a pilot group of researchers, and develop a basic cloud backend.</p>
                        </div>
                        <div class="timeline-item mb-12 pl-12">
                            <h4 class="text-lg font-semibold text-[#2C5234]">30 Days: Pilot & Feedback</h4>
                            <p class="text-sm text-gray-500 mb-2">Phase 3</p>
                            <p class="text-gray-600">Launch the pilot program, gather crucial user feedback, refine features, and plan a broader training workshop.</p>
                        </div>
                        <div class="timeline-item pl-12">
                            <h4 class="text-lg font-semibold text-[#2C5234]">60 Days: Scale & Launch</h4>
                            <p class="text-sm text-gray-500 mb-2">Phase 4</p>
                            <p class="text-gray-600">Develop a robust, scalable app version, conduct a formal training workshop, and implement the full-scale platform launch.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-[#2C5234] text-white py-8">
        <div class="container mx-auto px-6 text-center">
            <p>&copy; 2024 Friends of Maluku Forest Foundation. A Green Digital Certificate Capstone Project.</p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');

            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            const readinessData = {
                labels: ['Organizational', 'Functional', 'Technical'],
                datasets: [{
                    label: 'Readiness Score (out of 5)',
                    data: [2, 3, 2],
                    backgroundColor: 'rgba(44, 82, 52, 0.2)',
                    borderColor: 'rgba(44, 82, 52, 1)',
                    pointBackgroundColor: 'rgba(44, 82, 52, 1)',
                    pointBorderColor: '#fff',
                    pointHoverBackgroundColor: '#fff',
                    pointHoverBorderColor: 'rgba(44, 82, 52, 1)'
                }]
            };

            const readinessConfig = {
                type: 'radar',
                data: readinessData,
                options: {
                    maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: {
                                display: true
                            },
                            suggestedMin: 0,
                            suggestedMax: 5,
                            pointLabels: {
                                font: {
                                    size: 14
                                }
                            }
                        }
                    },
                    plugins: {
                        legend: {
                            position: 'top',
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `${context.dataset.label}: ${context.raw}`;
                                }
                            }
                        }
                    }
                }
            };

            const readinessCtx = document.getElementById('readinessChart').getContext('2d');
            new Chart(readinessCtx, readinessConfig);

            const successData = {
                labels: ['User Adoption', 'Data Integrity', 'Operational Efficiency'],
                datasets: [{
                    label: 'Target (%)',
                    data: [75, 90, 50],
                    backgroundColor: [
                        'rgba(212, 196, 163, 0.6)',
                        'rgba(44, 82, 52, 0.6)',
                        'rgba(163, 177, 138, 0.6)',
                    ],
                    borderColor: [
                        'rgba(212, 196, 163, 1)',
                        'rgba(44, 82, 52, 1)',
                        'rgba(163, 177, 138, 1)',
                    ],
                    borderWidth: 1
                }]
            };

            const successConfig = {
                type: 'bar',
                data: successData,
                options: {
                    indexAxis: 'y',
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            beginAtZero: true,
                            max: 100,
                            ticks: {
                                callback: function(value) {
                                    return value + "%"
                                }
                            }
                        }
                    },
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `Target: ${context.raw}%`;
                                }
                            }
                        }
                    }
                }
            };

            const successCtx = document.getElementById('successChart').getContext('2d');
            new Chart(successCtx, successConfig);

        });
    </script>
</body>
</html>
