<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cambridge IGCSE Past Papers</title>
    <style>
        /* Previous CSS remains the same */
        /* Add these new styles */
        .category-filter {
            margin: 1rem 0;
            text-align: center;
        }

        .category-btn {
            margin: 0.5rem;
            padding: 0.5rem 1rem;
            border: 2px solid var(--primary-color);
            border-radius: 20px;
            background: white;
            cursor: pointer;
            transition: all 0.3s;
        }

        .category-btn.active {
            background-color: var(--primary-color);
            color: white;
        }

        .subject-category {
            margin: 2rem 0;
        }

        .category-title {
            color: var(--secondary-color);
            border-bottom: 2px solid var(--secondary-color);
            padding-bottom: 0.5rem;
            margin-bottom: 1rem;
        }
    </style>
</head>
<body>
    <!-- Header and Navigation remains same -->

    <div class="container">
        <div class="category-filter">
            <button class="category-btn active" onclick="filterSubjects('all')">All Subjects</button>
            <button class="category-btn" onclick="filterSubjects('core')">Core Subjects</button>
            <button class="category-btn" onclick="filterSubjects('stem')">STEM</button>
            <button class="category-btn" onclick="filterSubjects('humanities')">Humanities</button>
            <button class="category-btn" onclick="filterSubjects('languages')">Languages</button>
            <button class="category-btn" onclick="filterSubjects('arts')">Creative Arts</button>
        </div>

        <!-- Rest of the container remains same -->
    </div>

    <script>
        // Updated resource data with categories
        const resources = {
            papers: [
                {
                    subject: "Mathematics (0580)",
                    category: "core",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" },
                        { year: "2021", url: "#" }
                    ]
                },
                {
                    subject: "English First Language (0500)",
                    category: "core",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                {
                    subject: "Physics (0625)",
                    category: "stem",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                {
                    subject: "Chemistry (0620)",
                    category: "stem",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                {
                    subject: "Biology (0610)",
                    category: "stem",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                {
                    subject: "History (0470)",
                    category: "humanities",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                {
                    subject: "Geography (0460)",
                    category: "humanities",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                {
                    subject: "French (0520)",
                    category: "languages",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                {
                    subject: "Art & Design (0400)",
                    category: "arts",
                    years: [
                        { year: "2023", url: "#" },
                        { year: "2022", url: "#" }
                    ]
                },
                // Add more subjects following the same pattern
                // Include other subjects like:
                // - Additional Mathematics (0606)
                // - ICT (0417)
                // - Business Studies (0450)
                // - Economics (0455)
                // - Literature in English (0475)
                // - Spanish (0530)
                // - Computer Science (0478)
                // - Sociology (0495)
                // - Environmental Management (0680)
                // - Global Perspectives (0457)
            ],
            // marking and thresholds arrays would follow similar structure
        };

        // Updated filtering functions
        let currentCategory = 'all';

        function filterSubjects(category) {
            currentCategory = category;
            const btns = document.querySelectorAll('.category-btn');
            btns.forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            showContent(currentContent);
        }

        // Modified generateResourcesHTML function
        function generateResourcesHTML(type) {
            return resources[type]
                .filter(subj => currentCategory === 'all' || subj.category === currentCategory)
                .map(subj => `
                    <div class="card">
                        <h3 class="subject-title">${subj.subject}</h3>
                        <ul class="year-list">
                            ${subj.years.map(year => `
                                <li class="year-item">
                                    <span>${year.year}</span>
                                    <div>
                                        <a href="${year.url}" class="download-btn">Paper</a>
                                        <a href="${year.url}-ms" class="download-btn">MS</a>
                                    </div>
                                </li>
                            `).join('')}
                        </ul>
                    </div>
                `).join('');
        }

        // Rest of the JavaScript remains same
    </script>
</body>
</html>
