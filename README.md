# New-drop-
Project for html 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BLDEA University Jamkhandi - Student Portal</title>
    <style>
        body { font-family: Arial,sans-serif; margin:0; padding:0; background:linear-gradient(to bottom, #f0f8ff, #e6f7ff); color:#333 }
        header { background-color:#004080; color:white; text-align:center; padding:20px }
        nav { display:flex; justify-content:center; background-color:#0066cc }
        nav button { background:none; border:none; color:white; padding:10px 20px; cursor:pointer; font-size:16px }
        nav button:hover { background-color:#004d99 }
        .section { display:none; padding:20px; max-width:800px; margin:20px auto; background:white; border-radius:8px; box-shadow:0 0 10px rgba(0,0,0,0.1) }
        .active { display:block }
        form { display:flex; flex-direction:column }
        input, button { margin:10px 0; padding:10px; border:1px solid #ccc; border-radius:4px }
        button { background-color:#004080; color:white; cursor:pointer }
        button:hover { background-color:#0066cc }
        .history { line-height:1.6 }
        .history img { max-width:100%; height:auto; margin:10px 0 }
        .upload-preview img, .upload-preview video { max-width:100%; margin:10px 0 }
        .website-section a { color:#0066cc; font-weight:bold }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to BLDEA University, Jamkhandi</h1>
        <p>Student Portal: Login, Register, and Explore Our History</p>
    </header>
    
    <nav>
        <button onclick="showSection('login')">Login</button>
        <button onclick="showSection('register')">Register</button>
        <button onclick="showSection('history')">College History</button>
        <button onclick="showSection('upload')">Upload Image/Video</button>
        <button onclick="showSection('website')">Website Link</button>
    </nav>
    
    <div id="login" class="section active">
        <h2>Student Login</h2>
        <form id="loginForm">
            <label for="loginEmail">Email:</label>
            <input type="email" id="loginEmail" required>
            <label for="loginPassword">Password:</label>
            <input type="password" id="loginPassword" required>
            <button type="submit">Login</button>
        </form>
    </div>
    
    <div id="register" class="section">
        <h2>Student Registration</h2>
        <form id="registerForm">
            <label for="name">Full Name:</label>
            <input type="text" id="name" required>
            <label for="email">Email:</label>
            <input type="email" id="email" required>
            <label for="password">Password:</label>
            <input type="password" id="password" required>
            <label for="confirmPassword">Confirm Password:</label>
            <input type="password" id="confirmPassword" required>
            <label for="studentId">Student ID (if applicable):</label>
            <input type="text" id="studentId">
            <button type="submit">Register</button>
        </form>
    </div>
    
    <div id="history" class="section">
        <h2>History of BLDEA University, Jamkhandi</h2>
        <div class="history">
            <p>BLDE University, located in Jamkhandi, Karnataka, India, was established in 2008...</p>
            <!-- (rest unchanged for brevity) -->
            <img src="https://via.placeholder.com/800x400?text=BLDE+University+Campus" alt="BLDE University Campus">
        </div>
    </div>
    
    <div id="upload" class="section">
        <h2>Upload Image or Video</h2>
        <form id="mediaUploadForm">
            <label for="uploadFile">Choose image or video to upload:</label>
            <input type="file" id="uploadFile" accept="image/*,video/*" required>
            <button type="submit">Upload</button>
        </form>
        <div class="upload-preview" id="uploadPreview"></div>
        <p><strong>Note:</strong> This is a demo. Uploaded file is only shown as preview and not saved to a server.</p>
    </div>
    
    <div id="website" class="section website-section">
        <h2>Website Link</h2>
        <p>To securely host your student portal website, you can use:</p>
        <ul>
            <li><strong>GitHub Pages:</strong> <a href="https://pages.github.com/" target="_blank">pages.github.com</a> (for static sites)</li>
            <li><strong>Netlify:</strong> <a href="https://www.netlify.com/" target="_blank">netlify.com</a></li>
            <li><strong>Vercel:</strong> <a href="https://vercel.com/" target="_blank">vercel.com</a></li>
        </ul>
        <p>If you provide a repository on GitHub, I can help you deploy via GitHub Pages. Just let me know your repo link or details!</p>
    </div>
    
    <script>
        function showSection(sectionId) {
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => section.classList.remove('active'));
            document.getElementById(sectionId).classList.add('active');
        }

        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Login successful! (Demo: In reality, verify credentials with a backend.)');
        });
        document.getElementById('registerForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const password = document.getElementById('password').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            if (password !== confirmPassword) {
                alert('Passwords do not match!');
                return;
            }
            alert('Registration successful! (Demo: In reality, save to database.)');
        });

        document.getElementById('mediaUploadForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const uploadFile = document.getElementById('uploadFile').files[0];
            const previewDiv = document.getElementById('uploadPreview');
            previewDiv.innerHTML = '';
            if (uploadFile) {
                const url = URL.createObjectURL(uploadFile);
                if (uploadFile.type.startsWith('image')) {
                    const img = document.createElement('img');
                    img.src = url;
                    img.alt = 'Uploaded Image';
                    previewDiv.appendChild(img);
                } else if (uploadFile.type.startsWith('video')) {
                    const video = document.createElement('video');
                    video.src = url;
                    video.controls = true;
                    previewDiv.appendChild(video);
                } else {
                    previewDiv.innerText = 'File type not supported for preview.';
                }
            }
        });
    </script>
</body>
</html>
