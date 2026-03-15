
<html>
<body>
    <div id="index-container">Loading...</div>

    <script>
        async function buildIndex() {
            const user = 'SuperProxoCz';
            const repo = 'PersonalObsidianVaultExceptForEveryoneCauseHellYeahSoGoAheadAndReadMyPersonalClassNotesOrWhateverI';
            const folder = ''; //empty ensures root folder
            
            const response = await fetch(`https://api.github.com/repos/${user}/${repo}/contents/${folder}`);
            const files = await response.json();

            const container = document.getElementById('index-container');
            container.innerHTML = ''; // Clean up

            files.forEach(file => {                                        // Use the fetch output to make a directory li
                const link = document.createElement('a'); // github doesnt like scripts? we dont add scripts
                link.className = 'file-link';
                link.href = file.html_url; 
                link.textContent = `${file.name}`;
                container.appendChild(link);
            });
        }
        buildIndex();
    </script>
</body>
</html>