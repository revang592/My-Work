# My-Work

job-portal/
│
├── index.html
├── candidates.html
├── jobs.html
├── employers.html
├── dashboard-candidate.html
├── dashboard-employer.html
│
├── css/
│   └── style.css
│
├── js/
│   └── main.js
│
├── images/
│   ├── candidates/
│   └── companies/
│
└── data/
    ├── candidates.json
    ├── jobs.json
    ├── companies.json
    └── applications.json

/* General Styles */
body {
    font-family: 'Cairo', sans-serif;
    background-color: #f4f6f9;
    color: #333;
    margin: 0;
    padding: 0;
    direction: rtl;
}

a {
    text-decoration: none;
    color: inherit;
}

/* Header */
header {
    background-color: #007BFF;
    color: white;
    padding: 20px;
    text-align: center;
}

header h1 {
    margin: 0;
}

/* Buttons */
button {
    background-color: #007BFF;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 5px;
}

button:hover {
    background-color: #0056b3;
}

/* Layout */
.container {
    width: 80%;
    margin: 0 auto;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
}

/* Cards */
.card {
    background-color: white;
    border: 1px solid #ddd;
    border-radius: 5px;
    padding: 15px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.card img {
    width: 100%;
    height: auto;
    border-radius: 5px;
}

.card h3 {
    margin-top: 10px;
    font-size: 1.2em;
}

.card p {
    font-size: 0.9em;
    color: #555;
}

/* Forms */
form {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

form input, form select, form textarea {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ddd;
    border-radius: 5px;
}

/* Footer */
footer {
    background-color: #007BFF;
    color: white;
    text-align: center;
    padding: 10px;
    position: fixed;
    bottom: 0;
    width: 100%;
}


<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اعثر على وظيفتك المثالية</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <header>
        <h1>اعثر على وظيفتك المثالية في مدينتك</h1>
        <button onclick="window.location.href='candidates.html'">سجل الآن كـ موظف</button>
        <button onclick="window.location.href='employers.html'">سجل الآن كـ شركة</button>
    </header>
    <div class="container">
        <section>
            <h2>ابحث عن الوظائف</h2>
            <input type="text" id="search-bar" placeholder="ابحث عن الوظائف حسب الصناعة أو المدينة">
        </section>
        <section>
            <h2>الوظائف المميزة</h2>
            <div class="grid" id="featured-jobs">
                <!-- Featured jobs will be loaded here -->
            </div>
        </section>
        <section>
            <h2>الشركات الأكثر نشاطاً</h2>
            <div class="grid" id="active-companies">
                <!-- Active companies will be loaded here -->
            </div>
        </section>
    </div>
    <footer>
        <p>&copy; 2025 Job Portal</p>
    </footer>
    <script src="js/main.js"></script>
</body>
</html>


<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ملفات المرشحين</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <header>
        <h1>ملفات المرشحين</h1>
    </header>
    <div class="container">
        <div class="grid" id="candidate-profiles">
            <!-- Candidate profiles will be loaded here -->
        </div>
    </div>
    <footer>
        <p>&copy; 2025 Job Portal</p>
    </footer>
    <script src="js/main.js"></script>
</body>
</html>


<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>الوظائف</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <header>
        <h1>الوظائف</h1>
    </header>
    <div class="container">
        <input type="text" id="job-search" placeholder="ابحث عن وظيفة">
        <div class="grid" id="job-listings">
            <!-- Job listings will be loaded here -->
        </div>
    </div>
    <footer>
        <p>&copy; 2025 Job Portal</p>
    </footer>
    <script src="js/main.js"></script>
</body>
</html>

// Sample data
const jobs = [
    { title: "مطور ويب", company: "شركة التقنية", city: "الرياض", salary: "5000 ريال" },
    { title: "مصمم جرافيك", company: "شركة الإبداع", city: "جدة", salary: "4000 ريال" },
    { title: "محاسب", company: "شركة المال", city: "الدمام", salary: "6000 ريال" }
];

const companies = [
    { name: "شركة التقنية", logo: "images/companies/tech-company.jpg", openPositions: 5 },
    { name: "شركة الإبداع", logo: "images/companies/creative-company.jpg", openPositions: 3 },
    { name: "شركة المال", logo: "images/companies/finance-company.jpg", openPositions: 2 }
];

// Load featured jobs
function loadFeaturedJobs() {
    const container = document.getElementById('featured-jobs');
    jobs.forEach(job => {
        const card = document.createElement('div');
        card.classList.add('card');
        card.innerHTML = `
            <h3>${job.title}</h3>
            <p>${job.company} - ${job.city}</p>
            <p>الراتب: ${job.salary}</p>
        `;
        container.appendChild(card);
    });
}

// Load active companies
function loadActiveCompanies() {
    const container = document.getElementById('active-companies');
    companies.forEach(company => {
        const card = document.createElement('div');
        card.classList.add('card');
        card.innerHTML = `
            <img src="${company.logo}" alt="${company.name}">
            <h3>${company.name}</h3>
            <p>الوظائف المفتوحة: ${company.openPositions}</p>
        `;
        container.appendChild(card);
    });
}

// Initialize
document.addEventListener('DOMContentLoaded', () => {
    loadFeaturedJobs();
    loadActiveCompanies();
});


[
    {
        "name": "أحمد علي",
        "age": 30,
        "desiredJob": "مطور ويب",
        "experience": "5 سنوات",
        "skills": ["HTML", "CSS", "JavaScript"],
        "cv": "files/cvs/ahmed-ali.pdf",
        "photo": "images/candidates/ahmed-ali.jpg"
    },
    {
        "name": "سارة محمود",
        "age": 28,
        "desiredJob": "مصممة جرافيك",
        "experience": "3 سنوات",
        "skills": ["Photoshop", "Illustrator"],
        "cv": "files/cvs/sarah-mahmoud.pdf",
        "photo": "images/candidates/sarah-mahmoud.jpg"
    }
]

[
    {
        "title": "مطور ويب",
        "company": "شركة التقنية",
        "industry": "تكنولوجيا",
        "city": "الرياض",
        "salary": "5000 ريال"
    },
    {
        "title": "مصمم جرافيك",
        "company": "شركة الإبداع",
        "industry": "إبداع",
        "city": "جدة",
        "salary": "4000 ريال"
    }
]


[
    {
        "name": "شركة التقنية",
        "logo": "images/companies/tech-company.jpg",
        "industry": "تكنولوجيا",
        "openPositions": 5
    },
    {
        "name": "شركة الإبداع",
        "logo": "images/companies/creative-company.jpg",
        "industry": "إبداع",
        "openPositions": 3
    }
]



 
