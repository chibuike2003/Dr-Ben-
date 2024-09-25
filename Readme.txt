<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Language Filter</title>
    <style>
        #languages-list {
            border: 1px solid #ccc;
            max-height: 150px;
            overflow-y: auto;
            display: none; /* Hide initially */
        }
        .language-item {
            padding: 8px;
            cursor: pointer;
        }
        .language-item:hover {
            background-color: #f0f0f0;
        }
    </style>
</head>
<body>
    <h1>Select a Language</h1>
    <input type="text" id="language-input" placeholder="Type a language..." onkeyup="filterLanguages()">
    <div id="languages-list"></div>

    <script>
        const languages = [
            "Arabic", "Berber", "Portuguese", "French", "English", "Tswana",
            "Kirundi", "Spanish", "Tigrinya", "Amharic", "Oromo", "Sesotho",
            "Kpelle", "Malagasy", "Chichewa", "Bambara", "Wolof", "Kinyarwanda",
            "Hausa", "Yoruba", "Igbo", "Afrikaans", "Shona", "Nyanja", "Tonga",
            "Sindebele", "Fulfulde", "Ewe", "Emakhuwa", "Sango", "Malinke",
            "Seychellois Creole", "Kriol", "Pulaar", "Mina", "Jola", "Swahili"
        ];

        function filterLanguages() {
            const input = document.getElementById('language-input').value.toLowerCase();
            const languagesList = document.getElementById('languages-list');
            languagesList.innerHTML = ''; // Clear previous results

            if (input) {
                const filteredLanguages = languages.filter(language => language.toLowerCase().includes(input));
                if (filteredLanguages.length > 0) {
                    languagesList.style.display = 'block'; // Show the list
                    filteredLanguages.forEach(language => {
                        const item = document.createElement('div');
                        item.textContent = language;
                        item.classList.add('language-item');
                        item.onclick = () => selectLanguage(language); // Handle selection
                        languagesList.appendChild(item);
                    });
                } else {
                    languagesList.style.display = 'none'; // Hide if no results
                }
            } else {
                languagesList.style.display = 'none'; // Hide if input is empty
            }
        }

        function selectLanguage(language) {
            document.getElementById('language-input').value = language; // Set input value
            document.getElementById('languages-list').style.display = 'none'; // Hide list after selection
        }
    </script>
</body>
</html>
