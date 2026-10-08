<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Lesson: Inclusive-culturally aware design in HTML and CSS layouts</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Quicksand:wght@500;600;700&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg-maroon-deep: #2d050e;
      --bg-maroon: #4a0e17;
      --card-maroon: #5c1421;
      --card-maroon-inner: #410b14;
      --card-border: #ffb6c1;
      --pink-soft: #ffe4e9;
      --pink-main: #ffb6c1;
      --pink-glow: #ffc0cb;
      --pink-badge: #ffeef2;
      --text-pink-light: #fff0f3;
      --text-pink-accent: #ffd1dc;
      --accent-ribbon: #ff85a1;
      --shadow-kawaii: 0 8px 24px rgba(0, 0, 0, 0.4), 0 0 0 2px rgba(255, 182, 193, 0.25);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Quicksand', sans-serif;
      background-color: var(--bg-maroon-deep);
      background-image: 
        radial-gradient(circle at 15% 20%, rgba(255, 182, 193, 0.08) 0%, transparent 40%),
        radial-gradient(circle at 85% 75%, rgba(255, 192, 203, 0.08) 0%, transparent 45%);
      color: var(--text-pink-light);
      line-height: 1.7;
      font-size: 1.05rem;
      padding-bottom: 4rem;
    }

    .top-toolbar {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(45, 5, 14, 0.92);
      backdrop-filter: blur(10px);
      border-bottom: 2px solid var(--pink-main);
      box-shadow: 0 4px 18px rgba(0, 0, 0, 0.35);
    }

    .toolbar-content {
      max-width: 960px;
      margin: 0 auto;
      padding: 0.75rem 1.5rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 1rem;
    }

    .kawaii-tag {
      font-family: 'Fredoka', cursive;
      font-weight: 600;
      font-size: 0.95rem;
      color: var(--bg-maroon);
      background: var(--pink-main);
      padding: 0.4rem 1rem;
      border-radius: 999px;
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      box-shadow: 0 2px 8px rgba(255, 182, 193, 0.4);
    }

    .btn-pdf {
      font-family: 'Fredoka', cursive;
      font-weight: 600;
      font-size: 0.95rem;
      background: #ff85a1;
      color: #38000d;
      border: 2px solid #fff0f3;
      padding: 0.5rem 1.25rem;
      border-radius: 999px;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      transition: all 0.2s ease-in-out;
      box-shadow: 0 4px 12px rgba(255, 133, 161, 0.35);
    }

    .btn-pdf:hover {
      background: var(--pink-main);
      transform: translateY(-2px) scale(1.02);
      box-shadow: 0 6px 16px rgba(255, 182, 193, 0.5);
    }

    .container {
      max-width: 960px;
      margin: 2rem auto;
      padding: 0 1.5rem;
    }

    .nav-pills {
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      justify-content: center;
      margin: 1.5rem 0 2rem 0;
    }

    .nav-pill {
      font-family: 'Fredoka', cursive;
      text-decoration: none;
      color: var(--pink-soft);
      background: var(--card-maroon);
      border: 1.5px solid var(--pink-main);
      padding: 0.35rem 0.9rem;
      border-radius: 999px;
      font-size: 0.9rem;
      font-weight: 500;
      transition: all 0.2s ease;
    }

    .nav-pill:hover {
      background: var(--pink-main);
      color: var(--bg-maroon-deep);
      transform: translateY(-2px);
    }

    .header-card {
      background: var(--card-maroon);
      border: 3px solid var(--pink-main);
      border-radius: 28px;
      padding: 2.5rem 2rem;
      box-shadow: var(--shadow-kawaii);
      text-align: center;
      position: relative;
      margin-bottom: 2.25rem;
    }

    .sparkle-badge {
      display: inline-block;
      font-size: 1.5rem;
      margin-bottom: 0.5rem;
    }

    .quest-title {
      font-family: 'Fredoka', cursive;
      font-weight: 700;
      font-size: 1.95rem;
      color: var(--text-pink-light);
      line-height: 1.3;
      text-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);
      margin-bottom: 0.5rem;
    }

    .section-card {
      background: var(--card-maroon);
      border: 2px solid var(--pink-main);
      border-radius: 24px;
      padding: 1.85rem 2rem;
      margin-bottom: 1.75rem;
      box-shadow: var(--shadow-kawaii);
      scroll-margin-top: 5.5rem;
    }

    .section-title {
      font-family: 'Fredoka', cursive;
      font-size: 1.45rem;
      color: var(--text-pink-light);
      margin-bottom: 1.15rem;
      display: flex;
      align-items: center;
      gap: 0.6rem;
      border-bottom: 2px dashed rgba(255, 182, 193, 0.4);
      padding-bottom: 0.6rem;
    }

    .section-title .bubble-icon {
      background: var(--pink-main);
      color: var(--bg-maroon);
      width: 34px;
      height: 34px;
      border-radius: 50%;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    }

    p {
      color: var(--text-pink-light);
      margin-bottom: 1rem;
      line-height: 1.75;
    }

    p:last-child {
      margin-bottom: 0;
    }

    .kawaii-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.85rem;
      margin-top: 0.75rem;
    }

    .kawaii-list li {
      background: var(--card-maroon-inner);
      border: 1.5px solid var(--pink-main);
      border-radius: 16px;
      padding: 0.9rem 1.2rem;
      display: flex;
      align-items: flex-start;
      gap: 0.75rem;
      color: var(--text-pink-light);
    }

    .kawaii-list li::before {
      content: "🌸";
      font-size: 1.1rem;
      line-height: 1.4;
      flex-shrink: 0;
    }

    .resource-box {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      margin-top: 0.75rem;
    }

    .resource-item {
      background: var(--card-maroon-inner);
      border: 1.5px solid var(--pink-main);
      border-radius: 16px;
      padding: 1.1rem 1.25rem;
      color: var(--text-pink-light);
    }

    .resource-item a {
      color: #ffc0cb;
      font-weight: 700;
      word-break: break-all;
      text-decoration: underline;
      text-underline-offset: 3px;
      transition: color 0.2s;
    }

    .resource-item a:hover {
      color: #ffffff;
    }

    .highlight-card {
      background: var(--card-maroon-inner);
      border-left: 5px solid var(--pink-main);
      border-radius: 0 16px 16px 0;
      padding: 1.1rem 1.4rem;
      margin-top: 0.5rem;
    }

    @media print {
      body {
        background: #ffffff !important;
        color: #2b060d !important;
        font-size: 10.5pt;
        padding-bottom: 0;
      }

      .top-toolbar, .nav-pills {
        display: none !important;
      }

      .container {
        max-width: 100%;
        margin: 0;
        padding: 0;
      }

      .header-card {
        background: #fdf2f4 !important;
        border: 2px solid #991b34 !important;
        color: #3b0014 !important;
        box-shadow: none !important;
        border-radius: 12px;
        padding: 1.25rem;
        margin-bottom: 1.25rem;
      }

      .quest-title {
        color: #700b20 !important;
        font-size: 1.5rem !important;
        text-shadow: none !important;
      }

      .section-card {
        background: #ffffff !important;
        border: 1.5px solid #d17b88 !important;
        box-shadow: none !important;
        border-radius: 10px;
        padding: 1.1rem 1.25rem;
        margin-bottom: 1.1rem;
        page-break-inside: avoid;
      }

      .section-title {
        color: #700b20 !important;
        border-bottom: 1px solid #d17b88 !important;
        font-size: 1.2rem !important;
      }

      .section-title .bubble-icon {
        background: #700b20 !important;
        color: #ffffff !important;
      }

      p {
        color: #2b060d !important;
      }

      .kawaii-list li, .resource-item, .highlight-card {
        background: #fff8f9 !important;
        border: 1px solid #e09ba5 !important;
        color: #2b060d !important;
      }

      .resource-item a {
        color: #700b20 !important;
      }
    }
  </style>
</head>
<body>

  <header class="top-toolbar">
    <div class="toolbar-content">
      <div class="kawaii-tag">
        <span>🎀</span> WebQuest Activity <span>✨</span>
      </div>
      <button class="btn-pdf" onclick="window.print()">
        <span>🌸</span> Print / Save as PDF
      </button>
    </div>
  </header>

  <main class="container">

    <div class="header-card">
      <div class="sparkle-badge">✨ 🎀 ✨</div>
      <h1 class="quest-title">Lesson:<br>Inclusive-culturally aware design in HTML and CSS layouts for introductory computer science students</h1>
    </div>

    <nav class="nav-pills" aria-label="WebQuest Sections">
      <a href="#overview" class="nav-pill">🌸 Overview</a>
      <a href="#task" class="nav-pill">🎀 Task</a>
      <a href="#process" class="nav-pill">✨ Process</a>
      <a href="#resources" class="nav-pill">🌷 Resources</a>
      <a href="#evaluation" class="nav-pill">⭐ Evaluation</a>
      <a href="#conclusion" class="nav-pill">💖 Conclusion</a>
      <a href="#teacher" class="nav-pill">🧸 Teacher's Page</a>
    </nav>

    <section id="overview" class="section-card">
      <h2 class="section-title">
        <span class="bubble-icon">🌸</span>
        Overview
      </h2>
      <p>As a brief overview this is a lesson that teaches how design choices can affect accessibility from people with different backgrounds. Thes backgrounds may vary in terms of language, culture, and abilities. One key question that will be addressed is how a basic web page can be built to welcome a wider range of people.</p>
    </section>

    <section id="task" class="section-card">
      <h2 class="section-title">
        <span class="bubble-icon">🎀</span>
        Task
      </h2>
      <p>The main task for students is to improve a sample webpage that is more welcoming to people of different backgrounds. Students will work either in groups, in pairs, or alone. They will also identify a community (for example multilingual families, screen-reader users, or people without stable internet access) and redesign the page’s HTML and CSS. In the case where some of these elements are already incorporated in the webpage, students will explain why the website is doing a good job.</p>
    </section>

    <section id="process" class="section-card">
      <h2 class="section-title">
        <span class="bubble-icon">✨</span>
        Process
      </h2>
      <p>The process involves students</p>
      <ul class="kawaii-list">
        <li>Exploring the resources first to take notes on the design practices that could help different users access and get value out of a webpage</li>
        <li>Followed by an initial inspection of the web page of a computer and phone screen. Barriers include things like language, navigation, and content.</li>
        <li>Planning the redesign of the web page to include where the new elements go.</li>
        <li>The implementation of the webpage by building out the elements.</li>
        <li>Testing the design with real users.</li>
        <li>Presentations where design choices are explained</li>
      </ul>
    </section>

    <section id="resources" class="section-card">
      <h2 class="section-title">
        <span class="bubble-icon">🌷</span>
        Resources
      </h2>
      <p>Some resources include:</p>
      <div class="resource-box">
        <div class="resource-item">
          <strong>W3C: Easy Checks for Web Accessibility</strong> which allows students to check text contrast, headings, image descriptions, and keyboard access.<br>
          <a href="https://www.w3.org/WAI/test-evaluate/easy-checks/" target="_blank" rel="noopener noreferrer">https://www.w3.org/WAI/test-evaluate/easy-checks/</a>
        </div>
        <div class="resource-item">
          <strong>MDN: HTML basics</strong> for students if they choose to review page structure, headings, links, and images.<br>
          <a href="https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content" target="_blank" rel="noopener noreferrer">https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content</a>
        </div>
        <div class="resource-item">
          <strong>W3C: Accessibility Principles:</strong> This resource is a very broad introduction to accessibility, including language and visual design considerations. W3C guide
        </div>
      </div>
    </section>

    <section id="evaluation" class="section-card">
      <h2 class="section-title">
        <span class="bubble-icon">⭐</span>
        Evaluation
      </h2>
      <div class="highlight-card">
        <p>Evaluation will consist of the submission of work, with the presentation holding the most weight followed by the design of the webpage.</p>
      </div>
    </section>

    <section id="conclusion" class="section-card">
      <h2 class="section-title">
        <span class="bubble-icon">💖</span>
        Conclusion
      </h2>
      <p>Overall, by completing the WebQuest above, students will understand how HTML and CSS design choices can affect people of many backgrounds and cultures. Practices like responsive design, language aware techniques. In the end, students will see how inclusive design is important to responsible computer science rather than just an extra consideration.</p>
    </section>

    <section id="teacher" class="section-card">
      <h2 class="section-title">
        <span class="bubble-icon">🧸</span>
        Teacher’s Page: Lesson Relevance
      </h2>
      <p>This lesson is culturally relevant because it affords students the opportunity to reflect on language, culture, ability, and access to technology in the context of web design. They will do things like considering choices on text, image, and layout and how it affects them, then allow them to apply inclusive practices using HTML and CSS as tools. Cultural awareness is also addressed and relevant to the lesson because it asks students who needs to be represented in design and who will encounter barriers. This lesson is instructionally flexible as students may demonstrate the learning via a coded webpage or a mere prototype. This lesson also deals with real world choices that are made at industrial level web production which may be used in their future careers down the line.</p>
    </section>

  </main>
</body>
</html>
