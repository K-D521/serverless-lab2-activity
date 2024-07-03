<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Note Management App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        h1 {
            text-align: center;
            color: #333;
        }
        form {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 8px;
        }
        input[type="text"], textarea, input[type="file"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background: #007BFF;
            color: #fff;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
            border-radius: 4px;
            font-size: 16px;
        }
        button:hover {
            background: #0056b3;
        }
        .notes-list, .note-details {
            margin-top: 20px;
        }
        .notes-list {
            max-height: 300px; /* Set a fixed height for the notes list */
            overflow-y: auto; /* Make it scrollable */
            border: 1px solid #ccc;
            padding: 10px;
            border-radius: 4px;
            background-color: #f9f9f9;
        }
        .note-item {
            border-bottom: 1px solid #ccc;
            padding: 10px 0;
        }
        .note-item:last-child {
            border-bottom: none;
        }
        .note-id {
            font-weight: bold;
            color: #007BFF;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Note Management App</h1>

        <h2>Create Note</h2>
        <form id="noteForm">
            <label for="title">Title</label>
            <input type="text" id="title" placeholder="Note Title" required>
            <label for="content">Content</label>
            <textarea id="content" placeholder="Note Content" required></textarea>
            <label for="file">Attach File</label>
            <input type="file" id="file">
            <button type="submit">Create Note</button>
        </form>

        <h2>All Notes</h2>
        <div class="notes-list" id="notesList"></div>

        <h2>Get Note Details</h2>
        <form id="noteDetailsForm">
            <label for="noteId">Note ID</label>
            <input type="text" id="noteId" placeholder="Enter Note ID" required>
            <button type="submit">Get Note Details</button>
        </form>
        <div class="note-details" id="noteDetails"></div>
    </div>

    <script>
        const createNoteApi = 'https://us-central1-lab-activity-2-428317.cloudfunctions.net/createNote';
        const getNotesApi = 'https://us-central1-lab-activity-2-428317.cloudfunctions.net/getNotes';
        const uploadFileApi = 'https://us-central1-lab-activity-2-428317.cloudfunctions.net/uploadFile';
        const getNoteDetailsApi = 'https://us-central1-lab-activity-2-428317.cloudfunctions.net/getNoteDetails';

        document.getElementById('noteForm').addEventListener('submit', async (e) => {
            e.preventDefault();
            const title = document.getElementById('title').value;
            const content = document.getElementById('content').value;
            const file = document.getElementById('file').files[0];

            let fileUrl = '';
            if (file) {
                fileUrl = await uploadFile(file);
            }

            const response = await fetch(createNoteApi, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ title, content, fileUrl })
            });

            if (response.ok) {
                alert('Note created successfully!');
                loadNotes();
            } else {
                alert('Failed to create note');
            }
        });

        async function uploadFile(file) {
            const reader = new FileReader();
            return new Promise((resolve, reject) => {
                reader.onload = async () => {
                    const base64File = reader.result.split(',')[1];
                    const response = await fetch(uploadFileApi, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({ filename: file.name, fileContent: base64File })
                    });
                    const result = await response.json();
                    resolve(result.fileUrl);
                };
                reader.onerror = error => reject(error);
                reader.readAsDataURL(file);
            });
        }

        async function loadNotes() {
            const response = await fetch(getNotesApi);
            const notes = await response.json();
            const notesList = document.getElementById('notesList');
            notesList.innerHTML = '';
            notes.forEach(note => {
                const noteItem = document.createElement('div');
                noteItem.className = 'note-item';
                noteItem.innerHTML = `
                    <strong>${note.title}</strong>: ${note.content} <br>
                    <a href="${note.fileUrl || '#'}">${note.fileUrl ? 'View File' : ''}</a><br>
                    <span class="note-id">Note ID: ${note.id}</span>
                `;
                notesList.appendChild(noteItem);
            });
        }

        document.getElementById('noteDetailsForm').addEventListener('submit', async (e) => {
            e.preventDefault();
            const noteId = document.getElementById('noteId').value;
            const response = await fetch(`${getNoteDetailsApi}?id=${noteId}`);
            if (response.ok) {
                const note = await response.json();
                const noteDetails = document.getElementById('noteDetails');
                noteDetails.innerHTML = `
                    <h3>${note.title}</h3>
                    <p>${note.content}</p>
                    <a href="${note.fileUrl || '#'}">${note.fileUrl ? 'View File' : ''}</a>
                `;
            } else {
                alert('Note not found');
            }
        });

        // Load all notes on page load
        loadNotes();
    </script>
</body>
</html>
