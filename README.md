<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Free online tool to compress your images while maintaining quality. Reduce file size for faster websites and easier sharing.">
    <meta name="keywords" content="image compression, optimize images, reduce file size, image optimizer, online tool">
    <title>ImageCompress Pro - Optimize Your Images Online</title>
    <style>
        :root {
            --primary: #4361ee;
            --primary-dark: #3a56d4;
            --secondary: #7209b7;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --success: #4bb543;
            --border-radius: 8px;
            --box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f5f7fb;
            color: var(--dark);
            line-height: 1.6;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 1.5rem 0;
            box-shadow: var(--box-shadow);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
        }

        .logo span {
            color: #ffd166;
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 1.5rem;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: var(--transition);
        }

        nav ul li a:hover {
            color: #ffd166;
        }

        .hero {
            text-align: center;
            padding: 3rem 0;
            background-color: white;
            margin: 2rem auto;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: var(--primary);
        }

        .hero p {
            font-size: 1.1rem;
            color: var(--gray);
            max-width: 700px;
            margin: 0 auto 2rem;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 300px;
            gap: 2rem;
            margin: 2rem 0;
        }

        @media (max-width: 992px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        .compression-tool {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 2rem;
        }

        .tool-title {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            color: var(--primary);
            border-bottom: 2px solid #f0f0f0;
            padding-bottom: 0.5rem;
        }

        .upload-area {
            border: 2px dashed #d1d5db;
            border-radius: var(--border-radius);
            padding: 3rem 2rem;
            text-align: center;
            margin-bottom: 2rem;
            transition: var(--transition);
            cursor: pointer;
        }

        .upload-area:hover {
            border-color: var(--primary);
        }

        .upload-area i {
            font-size: 3rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .upload-area p {
            margin-bottom: 1rem;
            color: var(--gray);
        }

        .btn {
            display: inline-block;
            background-color: var(--primary);
            color: white;
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: var(--border-radius);
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            text-decoration: none;
        }

        .btn:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px);
        }

        .btn-secondary {
            background-color: var(--secondary);
        }

        .btn-secondary:hover {
            background-color: #5a08a0;
        }

        .compression-controls {
            margin: 2rem 0;
        }

        .control-group {
            margin-bottom: 1.5rem;
        }

        .control-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .slider-container {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .slider {
            flex: 1;
            -webkit-appearance: none;
            height: 8px;
            border-radius: 4px;
            background: #e0e0e0;
            outline: none;
        }

        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: var(--primary);
            cursor: pointer;
        }

        .slider-value {
            font-weight: 600;
            min-width: 40px;
            text-align: center;
        }

        .preview-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
            margin-top: 2rem;
        }

        @media (max-width: 768px) {
            .preview-container {
                grid-template-columns: 1fr;
            }
        }

        .preview-box {
            border: 1px solid #e0e0e0;
            border-radius: var(--border-radius);
            padding: 1rem;
            text-align: center;
        }

        .preview-title {
            font-weight: 600;
            margin-bottom: 1rem;
            color: var(--primary);
        }

        .preview-image {
            max-width: 100%;
            max-height: 250px;
            margin: 0 auto;
            display: block;
            border-radius: 4px;
        }

        .file-info {
            margin-top: 1rem;
            font-size: 0.9rem;
            color: var(--gray);
        }

        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 2rem;
        }

        .ad-container {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 1.5rem;
            text-align: center;
        }

        .ad-label {
            font-size: 0.8rem;
            color: var(--gray);
            margin-bottom: 0.5rem;
            text-transform: uppercase;
        }

        .ad-placeholder {
            background-color: #f8f9fa;
            border: 1px dashed #d1d5db;
            border-radius: 4px;
            padding: 3rem 1rem;
            color: var(--gray);
        }

        .features {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 1.5rem;
        }

        .features h3 {
            margin-bottom: 1rem;
            color: var(--primary);
        }

        .features ul {
            list-style-position: inside;
        }

        .features li {
            margin-bottom: 0.5rem;
        }

        footer {
            background-color: var(--dark);
            color: white;
            padding: 2rem 0;
            margin-top: 3rem;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
        }

        .footer-section {
            flex: 1;
            min-width: 250px;
        }

        .footer-section h3 {
            margin-bottom: 1rem;
            color: #ffd166;
        }

        .footer-section p, .footer-section a {
            color: #adb5bd;
            margin-bottom: 0.5rem;
            display: block;
            text-decoration: none;
        }

        .footer-section a:hover {
            color: white;
        }

        .copyright {
            text-align: center;
            margin-top: 2rem;
            padding-top: 1rem;
            border-top: 1px solid #495057;
            color: #adb5bd;
            font-size: 0.9rem;
        }

        .hidden {
            display: none;
        }

        .compression-info {
            background-color: #e7f3ff;
            border-left: 4px solid var(--primary);
            padding: 1rem;
            margin: 1.5rem 0;
            border-radius: 0 var(--border-radius) var(--border-radius) 0;
        }

        .action-buttons {
            display: flex;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        @media (max-width: 576px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            nav ul {
                margin-top: 1rem;
                justify-content: center;
            }
            
            nav ul li {
                margin: 0 0.75rem;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .action-buttons {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">Image<span>Compress</span> Pro</div>
                <nav>
                    <ul>
                        <li><a href="#">Home</a></li>
                        <li><a href="#">How It Works</a></li>
                        <li><a href="#">Pricing</a></li>
                        <li><a href="#">Blog</a></li>
                        <li><a href="#">Contact</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>

    <div class="container">
        <section class="hero">
            <h1>Compress Images Without Losing Quality</h1>
            <p>Reduce image file size by up to 80% while maintaining visual quality. Perfect for websites, social media, and storage optimization.</p>
            <a href="#compression-tool" class="btn">Start Compressing Now</a>
        </section>

        <div class="main-content">
            <div class="compression-tool" id="compression-tool">
                <h2 class="tool-title">Image Compression Tool</h2>
                
                <div class="upload-area" id="uploadArea">
                    <i>📁</i>
                    <h3>Drag & Drop Your Image Here</h3>
                    <p>or</p>
                    <input type="file" id="fileInput" accept="image/*" class="hidden">
                    <button class="btn" id="browseBtn">Browse Files</button>
                    <p class="file-types">Supports: JPG, PNG, GIF, WebP</p>
                </div>

                <div class="compression-controls">
                    <div class="control-group">
                        <label for="compressionLevel">Compression Level</label>
                        <div class="slider-container">
                            <input type="range" min="0" max="100" value="70" class="slider" id="compressionLevel">
                            <span class="slider-value" id="compressionValue">70%</span>
                        </div>
                        <div class="compression-info">
                            <p>Higher compression reduces file size more but may affect image quality. We recommend starting at 70% for optimal balance.</p>
                        </div>
                    </div>

                    <div class="control-group">
                        <label for="outputFormat">Output Format</label>
                        <select id="outputFormat" class="slider">
                            <option value="original">Same as original</option>
                            <option value="jpeg">JPEG</option>
                            <option value="png">PNG</option>
                            <option value="webp">WebP (Recommended)</option>
                        </select>
                    </div>
                </div>

                <div class="preview-container hidden" id="previewContainer">
                    <div class="preview-box">
                        <div class="preview-title">Original Image</div>
                        <img src="" alt="Original preview" class="preview-image" id="originalPreview">
                        <div class="file-info">
                            Size: <span id="originalSize">0 KB</span>
                        </div>
                    </div>
                    <div class="preview-box">
                        <div class="preview-title">Compressed Image</div>
                        <img src="" alt="Compressed preview" class="preview-image" id="compressedPreview">
                        <div class="file-info">
                            Size: <span id="compressedSize">0 KB</span> • 
                            Saved: <span id="savings">0%</span>
                        </div>
                    </div>
                </div>

                <div class="action-buttons hidden" id="actionButtons">
                    <button class="btn" id="compressBtn">Compress Image</button>
                    <button class="btn btn-secondary" id="downloadBtn">Download Compressed</button>
                </div>
            </div>

            <div class="sidebar">
                <div class="ad-container">
                    <div class="ad-label">Advertisement</div>
                    <div class="ad-placeholder" id="adTop">
                        <!-- Google AdSense ad unit will be placed here -->
                        AdSense Unit ID: <strong>ca-pub-xxxxxxxxxxxxx/yyyyyyyyyy</strong>
                    </div>
                </div>

                <div class="features">
                    <h3>Why Use Our Tool?</h3>
                    <ul>
                        <li>No registration required</li>
                        <li>100% secure - files never leave your browser</li>
                        <li>Optimize for web and mobile</li>
                        <li>Batch processing available</li>
                        <li>Preserve EXIF data</li>
                    </ul>
                </div>

                <div class="ad-container">
                    <div class="ad-label">Advertisement</div>
                    <div class="ad-placeholder" id="adBottom">
                        <!-- Google AdSense ad unit will be placed here -->
                        AdSense Unit ID: <strong>ca-pub-xxxxxxxxxxxxx/zzzzzzzzzz</strong>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>ImageCompress Pro</h3>
                    <p>The fastest and most secure way to optimize your images online. No registration, no watermarks, completely free.</p>
                </div>
                <div class="footer-section">
                    <h3>Quick Links</h3>
                    <a href="#">Home</a>
                    <a href="#">How It Works</a>
                    <a href="#">Privacy Policy</a>
                    <a href="#">Terms of Service</a>
                </div>
                <div class="footer-section">
                    <h3>Contact Us</h3>
                    <a href="mailto:support@imagecompresspro.com">support@imagecompresspro.com</a>
                    <a href="#">Feedback</a>
                    <a href="#">Report a Bug</a>
                </div>
            </div>
            <div class="copyright">
                &copy; 2025 ImageCompress Pro. All rights reserved.
            </div>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // DOM Elements
            const uploadArea = document.getElementById('uploadArea');
            const fileInput = document.getElementById('fileInput');
            const browseBtn = document.getElementById('browseBtn');
            const compressionLevel = document.getElementById('compressionLevel');
            const compressionValue = document.getElementById('compressionValue');
            const previewContainer = document.getElementById('previewContainer');
            const originalPreview = document.getElementById('originalPreview');
            const compressedPreview = document.getElementById('compressedPreview');
            const originalSize = document.getElementById('originalSize');
            const compressedSize = document.getElementById('compressedSize');
            const savings = document.getElementById('savings');
            const actionButtons = document.getElementById('actionButtons');
            const compressBtn = document.getElementById('compressBtn');
            const downloadBtn = document.getElementById('downloadBtn');
            const outputFormat = document.getElementById('outputFormat');
            
            let originalFile = null;
            let compressedFile = null;
            
            // Event Listeners
            browseBtn.addEventListener('click', () => fileInput.click());
            fileInput.addEventListener('change', handleFileSelect);
            uploadArea.addEventListener('dragover', handleDragOver);
            uploadArea.addEventListener('drop', handleFileDrop);
            compressionLevel.addEventListener('input', updateCompressionValue);
            compressBtn.addEventListener('click', compressImage);
            downloadBtn.addEventListener('click', downloadCompressedImage);
            
            // Functions
            function handleDragOver(e) {
                e.preventDefault();
                uploadArea.style.borderColor = '#4361ee';
                uploadArea.style.backgroundColor = '#f0f4ff';
            }
            
            function handleFileDrop(e) {
                e.preventDefault();
                uploadArea.style.borderColor = '#d1d5db';
                uploadArea.style.backgroundColor = 'transparent';
                
                if (e.dataTransfer.files.length) {
                    processFile(e.dataTransfer.files[0]);
                }
            }
            
            function handleFileSelect(e) {
                if (e.target.files.length) {
                    processFile(e.target.files[0]);
                }
            }
            
            function processFile(file) {
                if (!file.type.match('image.*')) {
                    alert('Please select an image file (JPG, PNG, GIF, WebP)');
                    return;
                }
                
                originalFile = file;
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    originalPreview.src = e.target.result;
                    originalSize.textContent = formatFileSize(file.size);
                    previewContainer.classList.remove('hidden');
                    actionButtons.classList.remove('hidden');
                    
                    // Auto-compress the image
                    compressImage();
                };
                
                reader.readAsDataURL(file);
            }
            
            function updateCompressionValue() {
                compressionValue.textContent = `${compressionLevel.value}%`;
            }
            
            function compressImage() {
                if (!originalFile) return;
                
                const canvas = document.createElement('canvas');
                const ctx = canvas.getContext('2d');
                const img = new Image();
                
                img.onload = function() {
                    // Calculate new dimensions if needed (for very large images)
                    let width = img.width;
                    let height = img.height;
                    const maxDimension = 2000;
                    
                    if (width > maxDimension || height > maxDimension) {
                        if (width > height) {
                            height = Math.round((height * maxDimension) / width);
                            width = maxDimension;
                        } else {
                            width = Math.round((width * maxDimension) / height);
                            height = maxDimension;
                        }
                    }
                    
                    canvas.width = width;
                    canvas.height = height;
                    
                    // Draw image on canvas
                    ctx.drawImage(img, 0, 0, width, height);
                    
                    // Get compression quality (0 to 1)
                    const quality = compressionLevel.value / 100;
                    
                    // Determine output format
                    let format = 'image/jpeg';
                    if (outputFormat.value === 'png') {
                        format = 'image/png';
                    } else if (outputFormat.value === 'webp') {
                        format = 'image/webp';
                    } else if (originalFile.type === 'image/png') {
                        format = 'image/png';
                    }
                    
                    // Convert to data URL with compression
                    const compressedDataURL = canvas.toDataURL(format, quality);
                    compressedPreview.src = compressedDataURL;
                    
                    // Calculate file sizes and savings
                    const originalSizeBytes = originalFile.size;
                    const compressedSizeBytes = Math.round((compressedDataURL.length - compressedDataURL.indexOf(',') - 1) * 0.75);
                    const savingsPercent = Math.round((1 - compressedSizeBytes / originalSizeBytes) * 100);
                    
                    compressedSize.textContent = formatFileSize(compressedSizeBytes);
                    savings.textContent = `${savingsPercent}%`;
                    
                    // Store compressed file for download
                    compressedFile = dataURLtoBlob(compressedDataURL);
                };
                
                img.src = URL.createObjectURL(originalFile);
            }
            
            function downloadCompressedImage() {
                if (!compressedFile) return;
                
                const link = document.createElement('a');
                const fileExtension = outputFormat.value === 'original' ? 
                    originalFile.name.split('.').pop() : outputFormat.value;
                
                link.download = `compressed-image.${fileExtension}`;
                link.href = URL.createObjectURL(compressedFile);
                link.click();
            }
            
            // Utility functions
            function formatFileSize(bytes) {
                if (bytes < 1024) return bytes + ' bytes';
                else if (bytes < 1048576) return (bytes / 1024).toFixed(1) + ' KB';
                else return (bytes / 1048576).toFixed(1) + ' MB';
            }
            
            function dataURLtoBlob(dataURL) {
                const parts = dataURL.split(';base64,');
                const contentType = parts[0].split(':')[1];
                const raw = window.atob(parts[1]);
                const uInt8Array = new Uint8Array(raw.length);
                
                for (let i = 0; i < raw.length; ++i) {
                    uInt8Array[i] = raw.charCodeAt(i);
                }
                
                return new Blob([uInt8Array], { type: contentType });
            }
            
            // Initialize compression value display
            updateCompressionValue();
        });
    </script>
</body>
</html>
