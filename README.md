<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AFA Member Form & Data Tool</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* COLOR PALETTE: "Brilliant Blues" - #003f5c, #58508d, #bc5090, #ff6361, #ffa600 */
        .header-bg { background-color: #003f5c; }
        .text-primary { color: #003f5c; }
        .text-secondary { color: #58508d; }
        .btn-accent { background-color: #ff6361; }
        .btn-accent:hover { background-color: #e0504d; }
        .border-accent { border-color: #bc5090; }
        .bg-section { background-color: #f8fafc; } /* Light gray for sections */
    </style>
</head>
<body class="bg-gray-50 text-gray-800">
<!-- CONFIRMATION: NEITHER Mermaid JS NOR SVG were used in the creation of this document. All interactive elements are rendered using structured HTML/CSS with Tailwind and JavaScript. -->

    <header class="header-bg text-white text-center p-8 md:p-12 shadow-md">
        <h1 class="text-3xl md:text-5xl font-bold">AFA Member Data Management Tool</h1>
        <p class="text-lg md:text-xl mt-2 text-gray-200">Interactive demonstration of form design and data principles</p>
    </header>

    <main class="container mx-auto p-4 md:p-8">

        <section id="form-fields" class="mb-12 bg-white rounded-lg shadow-md p-6">
            <h2 class="text-3xl font-bold text-center text-primary mb-6">Proposed Member Form Fields</h2>
            <p class="text-center max-w-3xl mx-auto text-gray-600 mb-8">This section outlines the essential and sensitive information fields for the new AFA member form, demonstrating their purpose and privacy considerations.</p>
            
            <div class="overflow-x-auto">
                <table class="min-w-full bg-white border border-gray-200 rounded-lg">
                    <thead>
                        <tr class="bg-gray-100 text-left text-sm font-semibold text-gray-700 uppercase tracking-wider">
                            <th class="py-3 px-4 border-b border-gray-200">Category</th>
                            <th class="py-3 px-4 border-b border-gray-200">Field Name</th>
                            <th class="py-3 px-4 border-b border-gray-200">Rationale</th>
                            <th class="py-3 px-4 border-b border-gray-200">Sensitivity/Consent Notes</th>
                        </tr>
                    </thead>
                    <tbody id="formFieldsTableBody" class="divide-y divide-gray-200">
                        <!-- Table rows will be populated by JavaScript -->
                    </tbody>
                </table>
            </div>
        </section>

        <section id="privacy-generator" class="mb-12 bg-white rounded-lg shadow-md p-6">
            <h2 class="text-3xl font-bold text-center text-primary mb-6">Privacy Notice Generator</h2>
            <p class="text-center max-w-3xl mx-auto text-gray-600 mb-8">Generate a concise privacy policy snippet based on the types of data the AFA collects, emphasizing transparency and consent.</p>
            
            <div class="flex justify-center mb-6">
                <button id="generatePrivacySnippet" class="btn-accent hover:bg-opacity-90 text-white font-bold py-3 px-6 rounded-lg shadow-md transition-all duration-300 transform hover:scale-105">
                    ✨ Generate Privacy Snippet
                </button>
            </div>
            
            <div id="privacySnippetOutput" class="mt-4 p-6 bg-gray-100 rounded-lg text-sm text-gray-700 border-l-4 border-accent hidden">
                <p class="font-semibold mb-2 text-secondary">Generated Privacy Note:</p>
                <div id="snippetContent" class="min-h-[50px] flex items-center justify-center"></div>
                <div id="snippetLoading" class="hidden text-center text-primary mt-2">Loading...</div>
            </div>
        </section>

        <section id="conditional-logic" class="mb-12 bg-white rounded-lg shadow-md p-6">
            <h2 class="text-3xl font-bold text-center text-primary mb-6">Conditional Logic Demonstration</h2>
            <p class="text-center max-w-3xl mx-auto text-gray-600 mb-8">Experience how form fields can dynamically appear based on previous selections, streamlining the user experience for sensitive information.</p>
            
            <div class="max-w-xl mx-auto p-6 border border-gray-200 rounded-lg bg-gray-50">
                <label for="relationshipToAlbinism" class="block text-lg font-semibold text-secondary mb-2">Relationship to Albinism:</label>
                <select id="relationshipToAlbinism" class="block w-full p-3 border border-gray-300 rounded-md shadow-sm focus:ring-primary focus:border-primary">
                    <option value="">Please select...</option>
                    <option value="has_albinism">I have albinism</option>
                    <option value="parent_guardian">Parent/Guardian of someone with albinism</option>
                    <option value="professional">Professional working with albinism</option>
                    <option value="supporter">Supporter/Ally</option>
                </select>

                <div id="sensitiveFields" class="mt-6 p-4 border border-dashed border-accent rounded-md bg-white hidden">
                    <p class="text-secondary font-semibold mb-3">Sensitive Information (Requires Consent):</p>
                    
                    <div class="mb-4">
                        <label for="typeOfAlbinism" class="block text-sm font-medium text-gray-700 mb-1">Type of Albinism (Optional):</label>
                        <input type="text" id="typeOfAlbinism" class="block w-full p-2 border border-gray-300 rounded-md focus:ring-primary focus:border-primary" placeholder="e.g., OCA1, OA1, HPS">
                        <p class="text-xs text-gray-500 mt-1">This helps us connect you with specific research opportunities or highly specialized support groups.</p>
                    </div>

                    <div>
                        <label for="briefDescription" class="block text-sm font-medium text-gray-700 mb-1">Brief Description of Impact (Optional):</label>
                        <textarea id="briefDescription" rows="3" class="block w-full p-2 border border-gray-300 rounded-md focus:ring-primary focus:border-primary" placeholder="e.g., Vision impairment affects daily tasks; Light sensitivity is a major issue."></textarea>
                        <p class="text-xs text-gray-500 mt-1">This helps us understand diverse experiences and inform program development.</p>
                    </div>

                    <div class="mt-4">
                        <input type="checkbox" id="consentCheckbox" class="rounded text-primary focus:ring-primary">
                        <label for="consentCheckbox" class="ml-2 text-sm text-gray-700">I consent to providing this sensitive information, understanding its purpose as described above.</label>
                    </div>
                </div>
            </div>
        </section>

        <section id="outreach-generator" class="mb-12 bg-white rounded-lg shadow-md p-6">
            <h2 class="text-3xl font-bold text-center text-primary mb-6">Personalized Outreach Message Draft</h2>
            <p class="text-center max-w-3xl mx-auto text-gray-600 mb-8">Draft tailored outreach messages for members based on their relationship to albinism and specific interests.</p>
            
            <div class="max-w-xl mx-auto p-6 border border-gray-200 rounded-lg bg-gray-50">
                <div class="mb-4">
                    <label for="outreachRelationship" class="block text-lg font-semibold text-secondary mb-2">Member's Relationship to Albinism:</label>
                    <select id="outreachRelationship" class="block w-full p-3 border border-gray-300 rounded-md shadow-sm focus:ring-primary focus:border-primary">
                        <option value="">Please select...</option>
                        <option value="individual with albinism">Individual with Albinism</option>
                        <option value="parent/guardian of someone with albinism">Parent/Guardian of someone with Albinism</option>
                        <option value="professional working with albinism">Professional working with Albinism</option>
                        <option value="supporter/ally">Supporter/Ally</option>
                    </select>
                </div>

                <div class="mb-6">
                    <label for="outreachInterests" class="block text-lg font-semibold text-secondary mb-2">Key Interests (comma-separated):</label>
                    <input type="text" id="outreachInterests" class="block w-full p-3 border border-gray-300 rounded-md shadow-sm focus:ring-primary focus:border-primary" placeholder="e.g., peer support, youth programs, research updates">
                    <p class="text-xs text-gray-500 mt-1">Enter topics relevant to the member, separated by commas.</p>
                </div>

                <div class="flex justify-center mb-6">
                    <button id="generateOutreachMessage" class="btn-accent hover:bg-opacity-90 text-white font-bold py-3 px-6 rounded-lg shadow-md transition-all duration-300 transform hover:scale-105">
                        ✨ Generate Outreach Message
                    </button>
                </div>
                
                <div id="outreachMessageOutput" class="mt-4 p-6 bg-gray-100 rounded-lg text-sm text-gray-700 border-l-4 border-accent hidden">
                    <p class="font-semibold mb-2 text-secondary">Generated Message Draft:</p>
                    <div id="messageContent" class="min-h-[80px] flex items-center justify-center"></div>
                    <div id="messageLoading" class="hidden text-center text-primary mt-2">Generating message...</div>
                </div>
            </div>
        </section>

    </main>

    <footer class="header-bg text-white text-center p-6 mt-8">
        <p>&copy; 2025 Albinism Fellowship of Australia. This tool demonstrates principles for member data management.</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // Data for the form fields table, extracted from the provided document.
            const formFieldsData = [
                { category: 'Essential Contact Information', field: 'Full Name', rationale: 'Primary identifier for member records and personalized communication.', sensitivity: 'Standard personal information.' },
                { category: 'Essential Contact Information', field: 'Preferred Name', rationale: 'Allows for respectful and personalized communication.', sensitivity: 'Standard personal information.' },
                { category: 'Essential Contact Information', field: 'Address Line 1', rationale: 'For postal communications (e.g., magazine) and geographical segmentation.', sensitivity: 'Standard personal information.' },
                { category: 'Essential Contact Information', field: 'Suburb', rationale: 'For postal communications and geographical segmentation.', sensitivity: 'Standard personal information.' },
                { category: 'Essential Contact Information', field: 'State', rationale: 'For postal communications and geographical segmentation.', sensitivity: 'Standard personal information.' },
                { category: 'Essential Contact Information', field: 'Postcode', rationale: 'For postal communications and geographical segmentation.', sensitivity: 'Standard personal information.' },
                { category: 'Essential Contact Information', field: 'Email Address', rationale: 'Primary digital communication channel for newsletters, updates, event invitations.', sensitivity: 'Standard personal information.' },
                { category: 'Essential Contact Information', field: 'Phone Number (Mobile)', rationale: 'For urgent contact or alternative communication.', sensitivity: 'Standard personal information.' },
                { category: 'Membership Details', field: 'Membership Type', rationale: 'To manage benefits, access levels, and tiered services.', sensitivity: 'Standard organizational data.' },
                { category: 'Membership Details', field: 'Membership Start Date', rationale: 'For tracking tenure, renewal cycles, and automated anniversary messages.', sensitivity: 'Standard organizational data.' },
                { category: 'Membership Details', field: 'Membership Renewal Date', rationale: 'For automated renewal reminders and billing.', sensitivity: 'Standard organizational data.' },
                { category: 'Demographic Information', field: 'Date of Birth', rationale: 'Relevant for governance roles, voting rights with age restrictions, and age-appropriate program development.', sensitivity: 'Standard personal information.' },
                { category: 'Sensitive Information (Requires Explicit Consent)', field: 'Relationship to Albinism', rationale: 'Crucial for segmenting members to provide highly tailored information, support, and services.', sensitivity: '**Sensitive Health Information.** Requires explicit, informed consent. Clearly state purpose: "To help us tailor support, resources, and connect you with relevant community members/programs." [11, 12]' },
                { category: 'Sensitive Information (Requires Explicit Consent)', field: 'Type of Albinism (Optional)', rationale: 'For highly specialized support, research participation, or targeted medical information.', sensitivity: '**Highly Sensitive Health Information.** Requires explicit, informed consent. Clearly state purpose: "To help us connect you with specific research opportunities or highly specialized support groups, if available." [11, 12]' },
                { category: 'Sensitive Information (Requires Explicit Consent)', field: 'Brief Description of Impact (Optional)', rationale: 'To help AFA understand the diverse needs of its community and inform program development.', sensitivity: '**Highly Sensitive Health Information.** Requires explicit, informed consent. Clearly state purpose: "To help us understand the diverse experiences within our community and inform the development of relevant support programs." [11, 12]' },
                { category: 'Engagement Preferences & Interests', field: 'Areas of Interest', rationale: 'To segment members for targeted communication, event invitations, and volunteer opportunities.', sensitivity: 'Standard preference data.' },
                { category: 'Engagement Preferences & Interests', field: 'How did you hear about us?', rationale: 'For marketing and outreach strategy evaluation.', sensitivity: 'Standard preference data.' },
                { category: 'Engagement Preferences & Interests', field: 'Preferred Communication Method', rationale: 'To ensure members receive information via their preferred channel.', sensitivity: 'Standard preference data.' },
                { category: 'Engagement Preferences & Interests', field: 'Opt-in/Opt-out for Communications', rationale: 'To respect member autonomy and reduce unwanted communications, improving engagement.', sensitivity: 'Standard preference data.' }
            ];

            const formFieldsTableBody = document.getElementById('formFieldsTableBody');
            formFieldsData.forEach(field => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="py-3 px-4 border-b border-gray-200">${field.category}</td>
                    <td class="py-3 px-4 border-b border-gray-200 font-medium">${field.field}</td>
                    <td class="py-3 px-4 border-b border-gray-200 text-sm">${field.rationale}</td>
                    <td class="py-3 px-4 border-b border-gray-200 text-xs text-gray-500">${field.sensitivity}</td>
                `;
                formFieldsTableBody.appendChild(row);
            });

            // Gemini API Integration for Privacy Snippet
            const generatePrivacySnippetBtn = document.getElementById('generatePrivacySnippet');
            const privacySnippetOutputDiv = document.getElementById('privacySnippetOutput');
            const snippetContentDiv = document.getElementById('snippetContent');
            const snippetLoadingDiv = document.getElementById('snippetLoading');

            generatePrivacySnippetBtn.addEventListener('click', async () => {
                privacySnippetOutputDiv.classList.remove('hidden');
                snippetContentDiv.innerHTML = '';
                snippetLoadingDiv.classList.remove('hidden');

                const prompt = `Generate a very concise, plain-language privacy policy snippet (2-3 sentences, maximum 60 words) for a non-profit organization called "Albinism Fellowship of Australia". It should mention that we collect:
                - Essential contact and membership information for operational purposes.
                - Optional engagement preferences to tailor communications.
                - Sensitive health-related information with explicit consent, used only for providing specific support and services.
                Emphasize that data is handled securely and with respect for privacy, adhering to Australian Privacy Principles.`;

                let chatHistory = [];
                chatHistory.push({ role: "user", parts: [{ text: prompt }] });
                const payload = { contents: chatHistory };
                const apiKey = ""; // Canvas will automatically provide this in runtime
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
                        snippetContentDiv.innerHTML = text;
                    } else {
                        snippetContentDiv.innerHTML = 'Error: Could not generate snippet. Please try again.';
                    }
                } catch (error) {
                    console.error('Error calling Gemini API:', error);
                    snippetContentDiv.innerHTML = 'Error: Failed to connect to the generation service. Check console for details.';
                } finally {
                    snippetLoadingDiv.classList.add('hidden');
                }
            });

            // Conditional Logic Demonstration
            const relationshipSelect = document.getElementById('relationshipToAlbinism');
            const sensitiveFieldsDiv = document.getElementById('sensitiveFields');

            relationshipSelect.addEventListener('change', () => {
                const selectedValue = relationshipSelect.value;
                if (selectedValue === 'has_albinism' || selectedValue === 'parent_guardian') {
                    sensitiveFieldsDiv.classList.remove('hidden');
                } else {
                    sensitiveFieldsDiv.classList.add('hidden');
                    // Optionally clear fields when hidden
                    document.getElementById('typeOfAlbinism').value = '';
                    document.getElementById('briefDescription').value = '';
                    document.getElementById('consentCheckbox').checked = false;
                }
            });

            // Gemini API Integration for Personalized Outreach Message
            const generateOutreachMessageBtn = document.getElementById('generateOutreachMessage');
            const outreachRelationshipSelect = document.getElementById('outreachRelationship');
            const outreachInterestsInput = document.getElementById('outreachInterests');
            const outreachMessageOutputDiv = document.getElementById('outreachMessageOutput');
            const messageContentDiv = document.getElementById('messageContent');
            const messageLoadingDiv = document.getElementById('messageLoading');

            generateOutreachMessageBtn.addEventListener('click', async () => {
                outreachMessageOutputDiv.classList.remove('hidden');
                messageContentDiv.innerHTML = '';
                messageLoadingDiv.classList.remove('hidden');

                const relationship = outreachRelationshipSelect.value;
                const interests = outreachInterestsInput.value.trim();

                if (!relationship) {
                    messageContentDiv.innerHTML = 'Please select a relationship to albinism.';
                    messageLoadingDiv.classList.add('hidden');
                    return;
                }

                let prompt = `Draft a concise, friendly outreach message for a member of the Albinism Fellowship of Australia. The member is an "${relationship}".`;
                if (interests) {
                    prompt += ` Their key interests include: ${interests}.`;
                }
                prompt += ` The message should encourage engagement with relevant AFA activities or resources. Keep it to 3-4 sentences.`;

                let chatHistory = [];
                chatHistory.push({ role: "user", parts: [{ text: prompt }] });
                const payload = { contents: chatHistory };
                const apiKey = ""; // Canvas will automatically provide this in runtime
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
                        messageContentDiv.innerHTML = text;
                    } else {
                        messageContentDiv.innerHTML = 'Error: Could not generate message. Please try again.';
                    }
                } catch (error) {
                    console.error('Error calling Gemini API:', error);
                    messageContentDiv.innerHTML = 'Error: Failed to connect to the generation service. Check console for details.';
                } finally {
                    messageLoadingDiv.classList.add('hidden');
                }
            });
        });
    </script>
</body>
</html>
