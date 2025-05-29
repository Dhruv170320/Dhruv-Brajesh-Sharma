<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Guide to TVF-Style Listicle Scripts</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js@3.7.1/dist/chart.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- Application Structure Plan: The SPA is structured around key themes from the report to guide users from understanding TVF's core principles to applying them.
    1.  **Hero Section:** Title and brief intro to TVF's magic & the app's purpose.
    2.  **Navigation Bar:** Sticky top nav for "Understanding TVF," "Crafting Your Script," "TVF in Action (Case Studies)," "Key Recommendations," and "Gemini AI Tools."
    3.  **Understanding TVF (The DNA):** Interactive section exploring Relatability, Humor, Characters (with archetype explorer), Dialogue, and Social Commentary. Each element will have concise explanations and examples from the report. Clicking an element (e.g., "Character Archetypes") will expand to show details like Table 2.
    4.  **Crafting Your Script (Step-by-Step Guide):** An interactive accordion or tabbed interface for Steps 1-5. Each step will present report guidance. Step 3 will feature an interactive version of Table 1 (Traditional vs. TVF Script).
    5.  **TVF in Action (Case Studies):** A filterable/searchable card grid showcasing TVF series from Table 3. Clicking a card will open a modal or expand to show details: Core Theme, "List" Function, and how it exemplifies TVF's style, drawing from Section 4 of the report.
    6.  **Key Recommendations:** A summarized list of actionable advice from Section 5.
    7.  **Gemini AI Tools:** New section with LLM-powered features for idea generation and dialogue enhancement.
    8.  **Footer:** Brief credits.
    This structure prioritizes a journey of discovery and practical application, making the dense report more digestible and engaging. The flow moves from foundational knowledge to practical steps and real-world examples. -->
    <!-- Visualization & Content Choices:
    * **Report Info: Executive Summary & Section 1 (Deconstructing Listicle)** -> Goal: Introduce concept -> Presentation: Hero section text, introductory paragraphs in relevant sections. Interaction: None. Justification: Sets context. Library: HTML/Tailwind.
    * **Report Info: Section 2 (DNA of TVF)** -> Goal: Inform & Compare -> Presentation: Dedicated section with sub-parts for each DNA element. Character Archetypes (Table 2) will be interactive cards. Interaction: Click to expand/reveal details for archetypes. Justification: Highlights core principles in an organized, digestible way. Library: HTML/Tailwind, JS for card interactions.
    * **Report Info: Section 3 (Crafting Guide) & Table 1** -> Goal: Organize & Guide -> Presentation: Accordion/Tabs for steps. Table 1 as an interactive side-by-side comparison (click listicle element to see TVF equivalent). Interaction: Click to navigate steps, click for Table 1 details. Justification: Provides actionable steps and clear comparisons. Library: HTML/Tailwind, JS for accordion/tabs and interactive table.
    * **Report Info: Section 4 (Case Studies) & Table 3** -> Goal: Inform & Illustrate -> Presentation: Interactive card grid for TVF shows. Interaction: Click card to show modal/expanded view with show details (theme, list function, analysis). Potentially filter by theme. Justification: Concrete examples make concepts clearer. Library: HTML/Tailwind, JS for card grid and modals.
    * **Report Info: Section 5 (Recommendations)** -> Goal: Summarize & Advise -> Presentation: Bulleted list within a dedicated section. Interaction: None. Justification: Clear, actionable takeaways. Library: HTML/Tailwind.
    * **New LLM Features:** Goals: Brainstorming & Enhancement -> Presentation: Input fields and buttons with output areas. Interaction: User input, button click to trigger API call, display results. Justification: Adds practical, AI-powered tools for script creation, directly enhancing the "Crafting" aspect. Library: HTML/Tailwind, JS for API calls and UI updates.
    CONFIRMING NO SVG/Mermaid used. All visual structuring via HTML/Tailwind and interactions via JS. Chart.js/Plotly not applicable due to lack of quantitative data for charting, but principles of constrained content blocks will be used for interactive tables/cards. -->
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #FFFBF5; color: #4A4A4A; }
        .nav-link { color: #4A4A4A; transition: color 0.3s ease; }
        .nav-link:hover, .nav-link.active { color: #B8860B; }
        .section-title { color: #B8860B; }
        .content-card { background-color: #E0D8CC; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        .interactive-item { background-color: #FFFFFF; border: 1px solid #E0D8CC; transition: transform 0.2s ease, box-shadow 0.2s ease; }
        .interactive-item:hover { transform: translateY(-3px); box-shadow: 0 6px 12px rgba(0,0,0,0.1); }
        .accordion-button { background-color: #5F9EA0; color: white; }
        .accordion-button:hover { background-color: #538C8E; }
        .modal { display: none; position: fixed; z-index: 100; left: 0; top: 0; width: 100%; height: 100%; overflow: auto; background-color: rgba(0,0,0,0.6); }
        .modal-content { background-color: #FFFBF5; margin: 10% auto; padding: 20px; border-radius: 8px; width: 80%; max-width: 700px; position: relative; }
        .close-button { position: absolute; top: 15px; right: 25px; font-size: 30px; font-weight: bold; cursor: pointer; color: #4A4A4A }
        .close-button:hover { color: #B8860B; }
        .tab-button { background-color: #E0D8CC; color: #4A4A4A; }
        .tab-button.active { background-color: #5F9EA0; color: white; }
        .chart-container { position: relative; width: 100%; max-width: 600px; margin-left: auto; margin-right: auto; height: auto; max-height: 400px; padding: 1rem; background-color: #FFFFFF; border-radius: 0.5rem; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        .loading-spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #5F9EA0;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            animation: spin 1s linear infinite;
            display: inline-block;
            vertical-align: middle;
            margin-left: 8px;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="antialiased">

    <header class="bg-[#E0D8CC] shadow-md sticky top-0 z-50">
        <nav class="container mx-auto px-6 py-3 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-[#B8860B]">TVF Script Secrets</a>
            <div class="space-x-4">
                <a href="#dna" class="nav-link text-sm font-semibold">Understanding TVF</a>
                <a href="#crafting" class="nav-link text-sm font-semibold">Crafting Your Script</a>
                <a href="#case-studies" class="nav-link text-sm font-semibold">TVF in Action</a>
                <a href="#recommendations" class="nav-link text-sm font-semibold">Recommendations</a>
                <a href="#gemini-features" class="nav-link text-sm font-semibold">Gemini AI Tools</a>
            </div>
        </nav>
    </header>

    <main class="container mx-auto px-6 py-8">
        <section id="hero" class="text-center py-12">
            <h1 class="text-4xl font-bold mb-4 section-title">Unlock the Magic of TVF-Style Storytelling</h1>
            <p class="text-lg max-w-3xl mx-auto mb-6">
                This guide deconstructs The Viral Fever's (TVF) unique narrative approach, helping you create engaging "listicle-like" video scripts that resonate deeply with digital audiences. Explore TVF's core principles, learn to craft compelling content, and see their methods in action.
            </p>
        </section>

        <section id="dna" class="py-12">
            <h2 class="text-3xl font-bold text-center mb-10 section-title">The DNA of TVF's Storytelling</h2>
            <p class="text-center mb-8 max-w-2xl mx-auto">TVF's success lies in a potent mix of authenticity, humor, and heart. These core elements are key to crafting content that connects. Click on each element to learn more.</p>
            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="content-card p-6 interactive-item cursor-pointer" onclick="showDnaDetail('relatability')">
                    <h3 class="text-xl font-semibold mb-2 text-[#5F9EA0]">🧬 Relatability</h3>
                    <p class="text-sm">Tapping into universal themes and everyday experiences. TVF makes stories feel real and engaging.</p>
                </div>
                <div class="content-card p-6 interactive-item cursor-pointer" onclick="showDnaDetail('humor')">
                    <h3 class="text-xl font-semibold mb-2 text-[#5F9EA0]">😂 Observational Humor</h3>
                    <p class="text-sm">Finding comedy in the mundane, exaggerating everyday details for laughs.</p>
                </div>
                <div class="content-card p-6 interactive-item cursor-pointer" onclick="showDnaDetail('characters')">
                    <h3 class="text-xl font-semibold mb-2 text-[#5F9EA0]">👥 Character Archetypes</h3>
                    <p class="text-sm">Crafting memorable, flawed, and authentic personalities that drive the narrative.</p>
                </div>
                <div class="content-card p-6 interactive-item cursor-pointer" onclick="showDnaDetail('dialogue')">
                    <h3 class="text-xl font-semibold mb-2 text-[#5F9EA0]">💬 Dialogue That Pops</h3>
                    <p class="text-sm">Witty banter, natural exchanges, and perfect comedic timing that bring scenes to life.</p>
                </div>
                <div class="content-card p-6 interactive-item cursor-pointer" onclick="showDnaDetail('social-commentary')">
                    <h3 class="text-xl font-semibold mb-2 text-[#5F9EA0]">🌍 Social Commentary with a Smile</h3>
                    <p class="text-sm">Subtly weaving in meaningful messages about society, politics, and culture.</p>
                </div>
            </div>
        </section>

        <section id="crafting" class="py-12 bg-[#E0D8CC] rounded-lg my-8 p-8">
            <h2 class="text-3xl font-bold text-center mb-10 section-title">Crafting Your TVF-Style Listicle Script</h2>
            <p class="text-center mb-8 max-w-2xl mx-auto">A step-by-step guide to developing video scripts that embody TVF's signature "listicle-like" storytelling.</p>
            <div id="crafting-accordion">
            </div>
        </section>

        <section id="case-studies" class="py-12">
            <h2 class="text-3xl font-bold text-center mb-10 section-title">TVF in Action: Case Studies</h2>
            <p class="text-center mb-8 max-w-2xl mx-auto">Explore how iconic TVF series embody the "listicle-like" principles of categorization, relatability, and humor. Click on a show to see its analysis.</p>
            <div id="case-studies-grid" class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
            </div>
        </section>

        <section id="recommendations" class="py-12 bg-[#E0D8CC] rounded-lg my-8 p-8">
            <h2 class="text-3xl font-bold text-center mb-10 section-title">Key Recommendations for Success</h2>
             <p class="text-center mb-8 max-w-2xl mx-auto">Practical advice to help you create TVF-style listicle scripts that achieve viral relatability.</p>
            <ul id="recommendations-list" class="list-disc list-inside space-y-3 max-w-3xl mx-auto text-left">
            </ul>
        </section>

        <section id="gemini-features" class="py-12">
            <h2 class="text-3xl font-bold text-center mb-10 section-title">✨ Gemini AI Tools for Scripting</h2>
            <p class="text-center mb-8 max-w-2xl mx-auto">Leverage the power of AI to brainstorm ideas and refine your dialogue in true TVF style!</p>

            <div class="grid md:grid-cols-2 gap-8">
                <div class="content-card p-6">
                    <h3 class="text-xl font-semibold mb-4 text-[#5F9EA0]">✨ Generate Listicle Ideas</h3>
                    <p class="text-sm mb-4">Enter a broad topic, and Gemini will suggest TVF-style listicle themes.</p>
                    <input type="text" id="ideaTopicInput" placeholder="e.g., College life, Office woes, Indian weddings" class="w-full p-2 border border-gray-300 rounded-md mb-4 focus:outline-none focus:ring-2 focus:ring-[#5F9EA0]">
                    <button id="generateIdeaBtn" class="bg-[#5F9EA0] text-white py-2 px-4 rounded-md hover:bg-[#538C8E] transition-colors flex items-center">
                        Generate Ideas
                        <span id="ideaSpinner" class="loading-spinner hidden"></span>
                    </button>
                    <div id="ideaOutput" class="mt-4 p-3 bg-white rounded-md border border-gray-200 min-h-[80px] text-sm overflow-auto max-h-48"></div>
                </div>

                <div class="content-card p-6">
                    <h3 class="text-xl font-semibold mb-4 text-[#5F9EA0]">✨ Enhance Dialogue</h3>
                    <p class="text-sm mb-4">Paste a line of dialogue, and Gemini will suggest TVF-style enhancements.</p>
                    <textarea id="dialogueInput" placeholder="e.g., 'I'm so tired of this job.'" rows="3" class="w-full p-2 border border-gray-300 rounded-md mb-4 focus:outline-none focus:ring-2 focus:ring-[#5F9EA0]"></textarea>
                    <button id="enhanceDialogueBtn" class="bg-[#5F9EA0] text-white py-2 px-4 rounded-md hover:bg-[#538C8E] transition-colors flex items-center">
                        Enhance Dialogue
                        <span id="dialogueSpinner" class="loading-spinner hidden"></span>
                    </button>
                    <div id="dialogueOutput" class="mt-4 p-3 bg-white rounded-md border border-gray-200 min-h-[80px] text-sm overflow-auto max-h-48"></div>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-[#4A4A4A] text-white text-center py-6 mt-12">
        <p class="text-sm">&copy; 2024 TVF Script Secrets Explorer. Inspired by the "Crafting Engaging Digital Narratives" report.</p>
    </footer>

    <div id="detailsModal" class="modal">
        <div class="modal-content">
            <span class="close-button" onclick="closeModal()">&times;</span>
            <h3 id="modalTitle" class="text-2xl font-bold mb-4 section-title"></h3>
            <div id="modalBody" class="text-sm space-y-3"></div>
        </div>
    </div>

<script>
    const dnaDetailsData = {
        relatability: {
            title: "🧬 Relatability as the Cornerstone",
            content: `
                <p>At the heart of TVF's success is its unwavering commitment to relatability. Their narratives skillfully tap into "universal emotions and experiences" such as friendship, family bonds, personal ambition, and individual growth.</p>
                <p><strong>Key Aspects:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Focus on everyday struggles and slice-of-life scenarios (e.g., 'Gullak', 'Panchayat').</li>
                    <li>Evokes "I've been there" or "I know someone like that" feelings.</li>
                    <li>Fosters emotional connection and a sense of shared community.</li>
                    <li>Drives engagement and virality through validation of audience experiences.</li>
                </ul>
                <p class="mt-2"><em>Example Insight:</em> "The relatability achieved by TVF extends beyond merely depicting common situations; it evokes a powerful sense of 'I've been there'..."</p>
            `
        },
        humor: {
            title: "😂 Mastering Observational Humor",
            content: `
                <p>TVF strategically launched with humor, recognizing it as highly sharable. Their comedy is rooted in observing the intricacies of daily life – "the weird, the mundane, the thing that everyone else ignores."</p>
                <p><strong>Techniques:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Keen eye for detail in everyday situations.</li>
                    <li>Systematic inquiry (who, what, when, where, why, how) to find comedic connections.</li>
                    <li>Skillful exaggeration of "little small points" to heighten laughter.</li>
                    <li>Transforms familiar situations into fresh, often absurd, perspectives.</li>
                </ul>
                <p class="mt-2"><em>Example Insight:</em> "Observational humor... functions as a magnifying glass, using comedy to highlight and amplify subtle truths about human behavior and societal norms..."</p>
            `
        },
        characters: {
            title: "👥 Character Archetypes and Dynamics",
            content: `
                <p>Compelling characters are essential. TVF characters possess clear motivations, real-life traits, and relatable flaws, making them feel authentic and human.</p>
                <p><strong>Crafting Memorable Personalities:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Develop comprehensive character profiles for depth and consistency.</li>
                    <li>Utilize distinctive quirks and habits for humor and running gags.</li>
                    <li>Employ common archetypes (The Straight Person, The Buffoon, The Cynic) but infuse them with unique flaws to avoid stereotypes and enhance authenticity.</li>
                </ul>
                <div class="mt-4 p-4 bg-white rounded-md shadow chart-container">
                    <h4 class="font-semibold text-md mb-2 text-[#B8860B]">Common TVF Character Archetypes (Examples from Report Table 2):</h4>
                    <div class="overflow-x-auto">
                        <table class="min-w-full text-sm">
                            <thead class="bg-[#E0D8CC]"><tr><th class="p-2 text-left">Archetype</th><th class="p-2 text-left">TVF Example</th><th class="p-2 text-left">Humorous Role</th></tr></thead>
                            <tbody>
                                <tr class="border-b"><td class="p-2">The Straight Person</td><td class="p-2">Jitendra (Panchayat)</td><td class="p-2">Voice of reason, audience perspective.</td></tr>
                                <tr class="border-b"><td class="p-2">The Buffoon</td><td class="p-2">Prahlad (Panchayat)</td><td class="p-2">Ineptitude leads to comedic situations.</td></tr>
                                <tr class="border-b"><td class="p-2">The Cynic</td><td class="p-2">Arnub (Barely Speaking)</td><td class="p-2">Sarcasm highlights societal absurdities.</td></tr>
                                <tr><td class="p-2">The Eccentric</td><td class="p-2">Mandal (Pitchers)</td><td class="p-2">Unconventional behavior, bizarre comedic turns.</td></tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                <p class="mt-2"><em>Example Insight:</em> "TVF's effective use of archetypes... involves employing these familiar starting points to facilitate immediate audience connection... infusing them with specific, relatable flaws..."</p>
            `
        },
        dialogue: {
            title: "💬 Dialogue That Pops",
            content: `
                <p>Dialogue in TVF reveals character, advances plot, and provides exposition naturally. It mirrors "how people talk in real life."</p>
                <p><strong>Elements of Effective Dialogue:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Witty banter, sarcasm, quick replies, and clever wordplay.</li>
                    <li>What's unsaid can be as impactful as what's spoken.</li>
                    <li>Precise comedic timing: set-up/pay-off, natural rhythm, anticipation, strategic delays.</li>
                    <li>Relatable phrases and one-liners (e.g., 'Pitchers').</li>
                </ul>
                <p class="mt-2"><em>Example Insight:</em> "The effectiveness of TVF's dialogue stems from its authentic reflection of real-life conversations. This naturalistic dialogue facilitates more organic comedic timing..."</p>
            `
        },
        'social-commentary': {
            title: "🌍 Social Commentary with a Smile",
            content: `
                <p>TVF often delves into Indian politics, cinema, lifestyle, and social issues, skillfully tackling human complexities.</p>
                <p><strong>Subtle Integration:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Humor and relatability act as a vehicle for social messages (e.g., collaborations with Ministry of Panchayati Raj for 'Asli Pradhan Kaun?').</li>
                    <li>Avoids being didactic or preachy; messages are embedded in relatable, funny scenarios.</li>
                    <li>Effective for reaching younger, digital-native audiences.</li>
                    <li>Represents a subtle form of observational learning.</li>
                </ul>
                <p class="mt-2"><em>Example Insight:</em> "Humor acts as a 'Trojan horse,' allowing the social message to bypass the resistance that might arise from overtly instructional content."</p>
            `
        }
    };

    const craftingStepsData = [
        {
            title: "Step 1: Identifying Your 'List' – Themes, Types, or Situations",
            content: `
                <p>Conceptualize a thematic "list" of relatable experiences, distinct types of people, or common situations. The topic must resonate with your audience and ideally align with current trends. Ensure the content genuinely fits this format.</p>
                <p><strong>Key Considerations:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Find a universal theme expressed within a specific, relatable context (e.g., Indian startup culture, rural life).</li>
                    <li>Specificity ensures genuine connection, while the universal theme guarantees broader appeal.</li>
                </ul>
                <p class="mt-2"><em>Example Themes:</em> "5 Types of Awkward Family Dinners," "7 Things Only Indian Parents Say."</p>
            `
        },
        {
            title: "Step 2: Character Conception for Relatable Comedy",
            content: `
                <p>Create multidimensional characters with clear motivations, real-life traits, and relatable flaws. Develop detailed character profiles.</p>
                <p><strong>Building Characters:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Use established comedic archetypes as a starting point (Straight Person, Buffoon, Cynic).</li>
                    <li>Infuse archetypes with unique quirks and unexpected reactions.</li>
                    <li>Relatable imperfections are paramount; they are catalysts for relatability and humor.</li>
                </ul>
                <p class="mt-2"><em>Insight:</em> "It is through the struggles, awkwardness, and missteps caused by their imperfections that characters become truly human and generate comedic situations."</p>
            `
        },
        {
            title: "Step 3: Structuring Your Script – From Concept to Scene",
            content: `
                <p>Conceive your script as a series of short, interconnected sketches or scenes, each representing a "list item."</p>
                <div class="my-4 p-3 bg-white rounded-md shadow chart-container">
                    <h4 class="font-semibold text-md mb-2 text-[#B8860B]">Traditional Listicle vs. TVF Script Equivalents (Interactive - Click an element)</h4>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div>
                            <strong class="block mb-1 text-[#5F9EA0]">Traditional Listicle Element:</strong>
                            <ul class="space-y-1">
                                <li class="p-2 border rounded hover:bg-gray-100 cursor-pointer" onclick="showTable1Detail('title')">Clear, Catchy Title</li>
                                <li class="p-2 border rounded hover:bg-gray-100 cursor-pointer" onclick="showTable1Detail('intro')">Introduction</li>
                                <li class="p-2 border rounded hover:bg-gray-100 cursor-pointer" onclick="showTable1Detail('items')">Numbered/Bulleted List Items</li>
                                <li class="p-2 border rounded hover:bg-gray-100 cursor-pointer" onclick="showTable1Detail('points')">Concise yet Informative Points</li>
                                <li class="p-2 border rounded hover:bg-gray-100 cursor-pointer" onclick="showTable1Detail('takeaways')">Valuable Takeaways</li>
                                <li class="p-2 border rounded hover:bg-gray-100 cursor-pointer" onclick="showTable1Detail('conclusion')">Strong Conclusion/CTA</li>
                            </ul>
                        </div>
                        <div>
                            <strong class="block mb-1 text-[#5F9EA0]">TVF-Style Video Script Equivalent:</strong>
                            <div id="table1-detail-view" class="p-2 border rounded bg-gray-50 min-h-[100px]">Select an element on the left.</div>
                        </div>
                    </div>
                </div>
                <p><strong>Key Structural Parts:</strong></p>
                <ul class="list-disc pl-5">
                    <li><strong>Introduction:</strong> Hook the audience, set the tone, provide context. For TVF, it subtly promises reflection of audience experiences.</li>
                    <li><strong>"List Items" as Mini-Sketches/Scenes:</strong> Each illustrates a point with examples, realistic situations, character interactions. The narrative vignette serves as humorous evidence.</li>
                    <li><strong>Conclusion:</strong> Summarize, deliver a final punchline/message, or include a "tag" scene.</li>
                </ul>
            `
        },
        {
            title: "Step 4: Writing Engaging Dialogue and Action",
            content: `
                <p>Craft dialogue and action that are authentic and engaging.</p>
                <p><strong>Dialogue Tips:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Aim for natural, conversational tone. Read aloud to check.</li>
                    <li>Use witty banter, sarcasm, quick replies, wordplay.</li>
                    <li>Incorporate relatable phrases and one-liners.</li>
                    <li>Unspoken subtext and natural human reactions are key.</li>
                </ul>
                <p><strong>Action Tips:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Concise descriptions, present tense, what's seen/heard.</li>
                    <li>Every scene/action advances story or comedic point.</li>
                    <li>Physical comedy needs precise timing and choreography.</li>
                </ul>
                <p class="mt-2"><em>Insight:</em> "TVF's most impactful moments often derive humor and relatability... from the unspoken subtext and the natural, sometimes awkward, human reactions."</p>
            `
        },
        {
            title: "Step 5: Incorporating Visuals and Pacing for Maximum Impact",
            content: `
                <p>Visual and temporal elements are crucial for engagement and comedic effect.</p>
                <p><strong>Visuals:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Integrate high-quality related images, graphics, or videos.</li>
                    <li>Optimize for digital platforms (file names, alt text).</li>
                    <li>Consider how visuals contribute to comedic timing (reaction shots, gags).</li>
                </ul>
                <p><strong>Pacing:</strong></p>
                <ul class="list-disc pl-5">
                    <li>Balance fast-moving and slower, reflective moments.</li>
                    <li>Rhythm and speed of dialogue influence joke delivery.</li>
                    <li>Use strategic pauses ("breathing room") or rapid exchanges.</li>
                    <li>Optimize for mobile viewing (fast loading, responsive layouts).</li>
                </ul>
                <p class="mt-2"><em>Insight:</em> "Effective pacing in TVF-style content orchestrates the audience's emotional journey... It acts as an unseen force guiding the viewer's experience."</p>
            `
        }
    ];
    const table1Equivalents = {
        title: "<strong>Compelling Video Title/Hook:</strong> A strong title (e.g., 'Things Indian Parents Say') establishes the theme and promises relatability, drawing viewers in.",
        intro: "<strong>Opening Sketch/Cold Open/Teaser:</strong> Sets the tone, introduces the overarching theme, and establishes the comedic premise, often designed to immediately engage the audience (TVF frequently uses cold opens).",
        items: "<strong>Thematic Mini-Sketches/Vignettes:</strong> Each 'list item' is a self-contained scene or short narrative that illustrates a specific type of situation, person, or observation. This is implicit in TVF's episodic style.",
        points: "<strong>Focused Scene Development:</strong> Each mini-sketch is tightly written to deliver its comedic or insightful point efficiently, avoiding unnecessary embellishment or 'fluff'.",
        takeaways: "<strong>Implied Learnings/Punchlines:</strong> The humor and relatability embedded within each vignette provide the 'takeaway,' often conveyed through character reactions, dialogue, or the resolution of the scene.",
        conclusion: "<strong>Concluding Sketch/Tag/Thematic Wrap-up:</strong> A final scene that delivers a concluding punchline, reinforces the overall message, or subtly offers a call to action."
    };

    const caseStudiesData = [
        {
            id: 'gullak', name: 'Gullak', image: 'https://placehold.co/300x200/E0D8CC/4A4A4A?text=Gullak',
            coreTheme: "Everyday Indian Middle-Class Family Life",
            listFunction: "A collection of relatable family struggles, quirks, and heartwarming moments, offering an intimate inventory of common household experiences.",
            analysis: "'Gullak' is celebrated as a 'collection of disarming and relatable tales of the Mishra family.' Each episode highlights a distinct 'tale' or 'struggle,' implicitly creating a 'list' of universal family experiences like arguments, financial issues, and generational gaps. It transforms the mundane into extraordinary through humor and authenticity."
        },
        {
            id: 'pitchers', name: 'TVF Pitchers', image: 'https://placehold.co/300x200/E0D8CC/4A4A4A?text=TVF+Pitchers',
            coreTheme: "Indian Startup Culture & Entrepreneurship",
            listFunction: "The trials, tribulations, and triumphs inherent in starting a new venture; common challenges faced by young entrepreneurs in India.",
            analysis: "'Pitchers' details the intricate journey of startup culture. Its dialogues are famed for being 'awesome one-liners' and 'very general dialogues commonly used by us daily,' which contribute to its relatability. Each episode or challenge can be seen as an item in the 'startup experience list'."
        },
        {
            id: 'panchayat', name: 'Panchayat', image: 'https://placehold.co/300x200/E0D8CC/4A4A4A?text=Panchayat',
            coreTheme: "Rural Indian Life & Local Governance",
            listFunction: "The bureaucratic quirks, cultural nuances, and evolving dynamics of village administration and community life.",
            analysis: "'Panchayat' masterfully captures an engineering graduate's journey as a Panchayat secretary in a remote village. It presents a thematic 'list' of bureaucratic quirks, local customs, and the urban-rural mindset clash. The 'Asli Pradhan Kaun?' sketches within this universe also address social issues like women empowerment."
        },
        {
            id: 'kota-factory', name: 'Kota Factory', image: 'https://placehold.co/300x200/E0D8CC/4A4A4A?text=Kota+Factory',
            coreTheme: "Academic Pressure & Coaching Culture",
            listFunction: "The intense pressures, friendships, and rites of passage within India's highly competitive exam preparation ecosystem.",
            analysis: "'Kota Factory' starkly depicts the life of students in coaching centers. It functions as a thematic 'list' of struggles, friendships, aspirations, and anxieties, creating a 'checklist' for young viewers navigating similar academic pressures."
        },
        {
            id: 'arnub', name: 'Barely Speaking with Arnub', image: 'https://placehold.co/300x200/E0D8CC/4A4A4A?text=BSWA',
            coreTheme: "Indian News Media & Celebrity Interviews",
            listFunction: "The absurdities, theatrics, and sensationalism prevalent in Indian news broadcasting and celebrity talk shows.",
            analysis: "This satirical talk show parodies a prominent news anchor, using humor to critique media sensationalism. Each interview highlights a different 'type' of media absurdity or public figure quirk, building a 'critique list' of media observations, making social commentary palatable."
        }
    ];

    const recommendationsData = [
        "Embrace Authenticity and Relatability: Prioritize stories resonating with everyday lives.",
        "Sharpen Observational Skills: Find humor and truth in mundane details.",
        "Master Comedic Timing and Dialogue: Study joke delivery, craft natural, witty dialogue.",
        "Structure for Engagement: Use mini-sketches for list items, with a strong hook and conclusion.",
        "Integrate Subtle Social Commentary: Use humor to address social issues without preaching.",
        "Prioritize Production Quality and Optimization: High-quality visuals/audio, mobile optimization.",
        "Learn from Analytics and Feedback: Analyze viewership, seek audience feedback."
    ];

    const modal = document.getElementById('detailsModal');
    const modalTitle = document.getElementById('modalTitle');
    const modalBody = document.getElementById('modalBody');

    function showDnaDetail(dnaKey) {
        const detail = dnaDetailsData[dnaKey];
        modalTitle.textContent = detail.title;
        modalBody.innerHTML = detail.content;
        modal.style.display = 'block';
    }
    
    function showTable1Detail(key) {
        const detailView = document.getElementById('table1-detail-view');
        detailView.innerHTML = table1Equivalents[key] || 'Select an element on the left.';
    }

    function showCaseStudyDetail(caseStudy) {
        modalTitle.textContent = caseStudy.name;
        modalBody.innerHTML = `
            <img src="${caseStudy.image}" alt="${caseStudy.name}" class="w-full h-48 object-cover rounded-md mb-4">
            <p><strong>Core Theme:</strong> ${caseStudy.coreTheme}</p>
            <p><strong>Thematic "List" Function:</strong> ${caseStudy.listFunction}</p>
            <p class="mt-2"><strong>Analysis Snippet:</strong> ${caseStudy.analysis}</p>
        `;
        modal.style.display = 'block';
    }

    function closeModal() {
        modal.style.display = 'none';
        modalTitle.textContent = '';
        modalBody.innerHTML = '';
    }

    window.onclick = function(event) {
        if (event.target == modal) {
            closeModal();
        }
    }

    document.addEventListener('DOMContentLoaded', () => {
        const craftingAccordion = document.getElementById('crafting-accordion');
        craftingStepsData.forEach((step, index) => {
            const stepDiv = document.createElement('div');
            stepDiv.classList.add('mb-2');
            stepDiv.innerHTML = `
                <button class="accordion-button w-full text-left p-4 rounded-md font-semibold flex justify-between items-center" data-index="${index}">
                    ${step.title}
                    <span class="transform transition-transform duration-300">&#9662;</span>
                </button>
                <div class="accordion-content bg-white p-4 rounded-b-md hidden">
                    ${step.content}
                </div>
            `;
            craftingAccordion.appendChild(stepDiv);
        });

        craftingAccordion.addEventListener('click', (e) => {
            if (e.target.closest('.accordion-button')) {
                const button = e.target.closest('.accordion-button');
                const content = button.nextElementSibling;
                const arrow = button.querySelector('span');
                
                const allContents = craftingAccordion.querySelectorAll('.accordion-content');
                const allArrows = craftingAccordion.querySelectorAll('.accordion-button span');

                allContents.forEach(c => {
                    if (c !== content && !c.classList.contains('hidden')) {
                        c.classList.add('hidden');
                    }
                });
                allArrows.forEach(a => {
                     if (a !== arrow) {
                        a.innerHTML = '&#9662;'; // Down arrow
                        a.classList.remove('rotate-180');
                     }
                });

                content.classList.toggle('hidden');
                if (content.classList.contains('hidden')) {
                    arrow.innerHTML = '&#9662;'; // Down arrow
                    arrow.classList.remove('rotate-180');
                } else {
                    arrow.innerHTML = '&#9652;'; // Up arrow
                    arrow.classList.add('rotate-180');
                }
            }
        });

        const caseStudiesGrid = document.getElementById('case-studies-grid');
        caseStudiesData.forEach(study => {
            const card = document.createElement('div');
            card.className = 'content-card p-5 interactive-item cursor-pointer flex flex-col justify-between';
            card.innerHTML = `
                <div>
                    <img src="${study.image}" alt="${study.name}" class="w-full h-40 object-cover rounded-md mb-3">
                    <h3 class="text-xl font-semibold mb-2 text-[#5F9EA0]">${study.name}</h3>
                    <p class="text-xs text-gray-600 mb-1"><strong>Theme:</strong> ${study.coreTheme}</p>
                </div>
                <button class="mt-3 text-sm bg-[#5F9EA0] text-white py-1 px-3 rounded hover:bg-[#538C8E] transition-colors w-full">View Details</button>
            `;
            card.onclick = () => showCaseStudyDetail(study);
            caseStudiesGrid.appendChild(card);
        });
        
        const recommendationsList = document.getElementById('recommendations-list');
        recommendationsData.forEach(rec => {
            const listItem = document.createElement('li');
            listItem.textContent = rec;
            recommendationsList.appendChild(listItem);
        });

        const navLinks = document.querySelectorAll('.nav-link');
        const sections = document.querySelectorAll('main section[id]');

        function changeNavOnScroll() {
            let index = sections.length;
            while(--index && window.scrollY + 100 < sections[index].offsetTop) {}
            
            navLinks.forEach((link) => link.classList.remove('active'));
            if (index >=0 && sections[index] && navLinks[index]) {
                 navLinks[index].classList.add('active');
            }
        }
        changeNavOnScroll();
        window.addEventListener('scroll', changeNavOnScroll);

        navLinks.forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetSection = document.querySelector(targetId);
                if (targetSection) {
                    window.scrollTo({
                        top: targetSection.offsetTop - 70, 
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Gemini API Integration
        const generateIdeaBtn = document.getElementById('generateIdeaBtn');
        const ideaTopicInput = document.getElementById('ideaTopicInput');
        const ideaOutput = document.getElementById('ideaOutput');
        const ideaSpinner = document.getElementById('ideaSpinner');

        const enhanceDialogueBtn = document.getElementById('enhanceDialogueBtn');
        const dialogueInput = document.getElementById('dialogueInput');
        const dialogueOutput = document.getElementById('dialogueOutput');
        const dialogueSpinner = document.getElementById('dialogueSpinner');

        async function callGeminiAPI(prompt, outputElement, spinnerElement) {
            spinnerElement.classList.remove('hidden');
            outputElement.innerHTML = ''; // Clear previous output
            outputElement.textContent = 'Generating...';

            let chatHistory = [];
            chatHistory.push({ role: "user", parts: [{ text: prompt }] });
            const payload = { contents: chatHistory };
            const apiKey = ""; // If you want to use models other than gemini-2.0-flash or imagen-3.0-generate-002, provide an API key here. Otherwise, leave this as-is.
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                const result = await response.json();

                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const text = result.candidates[0].content.parts[0].text;
                    outputElement.innerHTML = text.replace(/\n/g, '<br>'); // Display newlines as <br>
                } else {
                    outputElement.textContent = 'Error: Could not generate content. Please try again.';
                    console.error('Gemini API response structure unexpected:', result);
                }
            } catch (error) {
                outputElement.textContent = 'Error: Failed to connect to the API. Check console for details.';
                console.error('Gemini API fetch error:', error);
            } finally {
                spinnerElement.classList.add('hidden');
            }
        }

        generateIdeaBtn.addEventListener('click', () => {
            const topic = ideaTopicInput.value.trim();
            if (topic) {
                const prompt = `Generate 3-5 TVF-style listicle themes based on the topic "${topic}". Focus on relatability, observational humor, and common Indian experiences. Present them as a numbered list.`;
                callGeminiAPI(prompt, ideaOutput, ideaSpinner);
            } else {
                ideaOutput.textContent = 'Please enter a topic to generate ideas.';
            }
        });

        enhanceDialogueBtn.addEventListener('click', () => {
            const dialogue = dialogueInput.value.trim();
            if (dialogue) {
                const prompt = `Take the following dialogue and suggest 2-3 variations to make it more TVF-like, incorporating witty banter, observational humor, and relatable Indian conversational nuances. Present each variation clearly.\n\nOriginal Dialogue: "${dialogue}"`;
                callGeminiAPI(prompt, dialogueOutput, dialogueSpinner);
            } else {
                dialogueOutput.textContent = 'Please enter some dialogue to enhance.';
            }
        });
    });
</script>
</body>
</html>
