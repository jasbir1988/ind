<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Smart Utility Hub - All-in-one converter and calculator tools. Convert PDFs, images, calculate age, taxes, and more.">
    <title>Smart Utility Hub - All-in-One Converter & Calculator Tools</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js"></script>
    <style>
        :root {
            --primary: #2E7D32;
            --primary-light: #4CAF50;
            --secondary: #1976D2;
            --secondary-light: #42A5F5;
            --text: #333333;
            --text-light: #666666;
            --background: #FFFFFF;
            --card-bg: #F5F5F5;
            --border: #E0E0E0;
            --shadow: rgba(0, 0, 0, 0.1);
        }

        .dark-mode {
            --primary: #4CAF50;
            --primary-light: #66BB6A;
            --secondary: #2196F3;
            --secondary-light: #64B5F6;
            --text: #E0E0E0;
            --text-light: #B0B0B0;
            --background: #121212;
            --card-bg: #1E1E1E;
            --border: #333333;
            --shadow: rgba(0, 0, 0, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            transition: background-color 0.3s, color 0.3s;
        }

        body {
            background-color: var(--background);
            color: var(--text);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Styles */
        header {
            background-color: var(--primary);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.5rem;
            font-weight: 700;
        }

        .logo i {
            font-size: 1.8rem;
        }

        .theme-toggle {
            background: none;
            border: none;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
        }

        /* Main Content */
        main {
            padding: 2rem 0;
        }

        .hero {
            text-align: center;
            margin-bottom: 3rem;
            padding: 2rem 0;
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: var(--primary);
        }

        .hero p {
            font-size: 1.2rem;
            color: var(--text-light);
            max-width: 700px;
            margin: 0 auto;
        }

        /* Tools Grid */
        .tools-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 3rem;
        }

        .tool-card {
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px var(--shadow);
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .tool-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px var(--shadow);
        }

        .tool-icon {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
            color: white;
            font-size: 1.8rem;
        }

        .tool-card h3 {
            margin-bottom: 0.5rem;
            color: var(--text);
        }

        .tool-card p {
            color: var(--text-light);
            font-size: 0.9rem;
        }

        /* Recent Tools */
        .recent-tools {
            margin-bottom: 3rem;
        }

        .section-title {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            color: var(--primary);
            border-bottom: 2px solid var(--primary-light);
            padding-bottom: 0.5rem;
            display: inline-block;
        }

        .recent-tools-list {
            display: flex;
            gap: 1rem;
            overflow-x: auto;
            padding: 1rem 0;
        }

        .recent-tool {
            min-width: 200px;
            background-color: var(--card-bg);
            border-radius: 8px;
            padding: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 2px 5px var(--shadow);
            cursor: pointer;
        }

        .recent-tool i {
            color: var(--primary);
            font-size: 1.5rem;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            overflow-y: auto;
        }

        .modal-content {
            background-color: var(--background);
            margin: 2% auto;
            padding: 2rem;
            border-radius: 10px;
            width: 90%;
            max-width: 800px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            position: relative;
        }

        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-light);
        }

        .close-modal:hover {
            color: var(--text);
        }

        .modal-title {
            margin-bottom: 1.5rem;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .tool-form {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .form-group label {
            font-weight: 600;
            color: var(--text);
        }

        .form-control {
            padding: 0.8rem;
            border: 1px solid var(--border);
            border-radius: 5px;
            background-color: var(--card-bg);
            color: var(--text);
            font-size: 1rem;
        }

        .btn {
            padding: 0.8rem 1.5rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: opacity 0.3s;
        }

        .btn:hover {
            opacity: 0.9;
        }

        .btn-secondary {
            background: var(--text-light);
        }

        .file-upload {
            border: 2px dashed var(--border);
            border-radius: 5px;
            padding: 2rem;
            text-align: center;
            cursor: pointer;
            transition: border-color 0.3s;
        }

        .file-upload:hover {
            border-color: var(--primary);
        }

        .file-upload i {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .result {
            margin-top: 1.5rem;
            padding: 1rem;
            background-color: var(--card-bg);
            border-radius: 5px;
            display: none;
        }

        .result.success {
            border-left: 4px solid var(--primary);
        }

        .result.error {
            border-left: 4px solid #f44336;
        }

        /* Footer */
        footer {
            background-color: var(--primary);
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

        .footer-logo {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .footer-links {
            display: flex;
            gap: 2rem;
        }

        .footer-links a {
            color: white;
            text-decoration: none;
        }

        .footer-links a:hover {
            text-decoration: underline;
        }

        .copyright {
            margin-top: 2rem;
            text-align: center;
            font-size: 0.9rem;
            color: rgba(255, 255, 255, 0.8);
        }

        /* AdSense Placeholder */
        .ad-container {
            margin: 2rem 0;
            padding: 1rem;
            background-color: var(--card-bg);
            border-radius: 5px;
            text-align: center;
            color: var(--text-light);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .tools-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .modal-content {
                width: 95%;
                padding: 1.5rem;
            }
            
            .footer-content {
                flex-direction: column;
            }
        }

        .conversion-options {
            display: flex;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .option-btn {
            flex: 1;
            padding: 0.8rem;
            background-color: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 5px;
            cursor: pointer;
            text-align: center;
        }

        .option-btn.active {
            background-color: var(--primary);
            color: white;
        }

        .tax-slabs {
            margin-top: 1rem;
        }

        .slab {
            display: flex;
            justify-content: space-between;
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--border);
        }

        .file-list {
            margin-top: 1rem;
        }

        .file-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.5rem;
            background-color: var(--card-bg);
            border-radius: 5px;
            margin-bottom: 0.5rem;
        }

        .file-item button {
            background: none;
            border: none;
            color: #f44336;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-tools"></i>
                    <span>Smart Utility Hub</span>
                </div>
                <button class="theme-toggle" id="themeToggle">
                    <i class="fas fa-moon"></i>
                </button>
            </div>
        </div>
    </header>

    <main class="container">
        <section class="hero">
            <h1>All-in-One Utility Tools</h1>
            <p>Convert, calculate, and compress files with our comprehensive collection of free online tools. Fast, secure, and easy to use.</p>
        </section>

        <div class="ad-container">
            <!-- AdSense Ad Space -->
            <p>Advertisement</p>
            <div style="background: #f0f0f0; height: 90px; display: flex; align-items: center; justify-content: center; border-radius: 5px;">
                AdSense Ad (8219364137855189)
            </div>
        </div>

        <section class="recent-tools">
            <h2 class="section-title">Recent Tools</h2>
            <div class="recent-tools-list" id="recentTools">
                <!-- Recent tools will be dynamically added here -->
            </div>
        </section>

        <section class="tools-grid">
            <!-- Tool 1: Text to PDF -->
            <div class="tool-card" data-tool="text-to-pdf">
                <div class="tool-icon">
                    <i class="fas fa-file-pdf"></i>
                </div>
                <h3>Text to PDF</h3>
                <p>Convert text to downloadable PDF files instantly</p>
            </div>

            <!-- Tool 2: PDF to Image -->
            <div class="tool-card" data-tool="pdf-to-image">
                <div class="tool-icon">
                    <i class="fas fa-file-image"></i>
                </div>
                <h3>PDF to Image</h3>
                <p>Convert PDF pages to JPG or PNG images</p>
            </div>

            <!-- Tool 3: Image Compressor -->
            <div class="tool-card" data-tool="image-compressor">
                <div class="tool-icon">
                    <i class="fas fa-compress-arrows-alt"></i>
                </div>
                <h3>Image Compressor</h3>
                <p>Reduce image file size without losing quality</p>
            </div>

            <!-- Tool 4: Image to PDF -->
            <div class="tool-card" data-tool="image-to-pdf">
                <div class="tool-icon">
                    <i class="fas fa-images"></i>
                </div>
                <h3>Image to PDF</h3>
                <p>Convert multiple images to a single PDF file</p>
            </div>

            <!-- Tool 5: PDF Merger & Splitter -->
            <div class="tool-card" data-tool="pdf-tools">
                <div class="tool-icon">
                    <i class="fas fa-copy"></i>
                </div>
                <h3>PDF Tools</h3>
                <p>Merge multiple PDFs or split large PDF files</p>
            </div>

            <!-- Tool 6: Age Calculator -->
            <div class="tool-card" data-tool="age-calculator">
                <div class="tool-icon">
                    <i class="fas fa-birthday-cake"></i>
                </div>
                <h3>Age Calculator</h3>
                <p>Calculate exact age in years, months, and days</p>
            </div>

            <!-- Tool 7: Tax Calculator -->
            <div class="tool-card" data-tool="tax-calculator">
                <div class="tool-icon">
                    <i class="fas fa-calculator"></i>
                </div>
                <h3>Tax Calculator</h3>
                <p>Estimate income tax with slab rates and deductions</p>
            </div>

            <!-- Tool 8: Unit Converter -->
            <div class="tool-card" data-tool="unit-converter">
                <div class="tool-icon">
                    <i class="fas fa-balance-scale"></i>
                </div>
                <h3>Unit Converter</h3>
                <p>Convert length, weight, temperature, and currency</p>
            </div>

            <!-- Tool 9: QR Code Tools -->
            <div class="tool-card" data-tool="qr-tools">
                <div class="tool-icon">
                    <i class="fas fa-qrcode"></i>
                </div>
                <h3>QR Code Tools</h3>
                <p>Generate custom QR codes and scan existing ones</p>
            </div>

            <!-- Tool 10: File to ZIP -->
            <div class="tool-card" data-tool="file-to-zip">
                <div class="tool-icon">
                    <i class="fas fa-file-archive"></i>
                </div>
                <h3>File to ZIP</h3>
                <p>Compress files and download as ZIP archive</p>
            </div>
        </section>

        <div class="ad-container">
            <!-- AdSense Ad Space -->
            <p>Advertisement</p>
            <div style="background: #f0f0f0; height: 90px; display: flex; align-items: center; justify-content: center; border-radius: 5px;">
                AdSense Ad (8219364137855189)
            </div>
        </div>
    </main>

    <!-- Modals for each tool -->
    <!-- Text to PDF Modal -->
    <div class="modal" id="text-to-pdf-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 class="modal-title"><i class="fas fa-file-pdf"></i> Text to PDF Converter</h2>
            <div class="tool-form">
                <div class="form-group">
                    <label for="text-input">Enter your text:</label>
                    <textarea id="text-input" class="form-control" rows="10" placeholder="Paste your text here..."></textarea>
                </div>
                <button class="btn" id="convert-text-to-pdf">Convert to PDF</button>
                <div class="result" id="text-to-pdf-result"></div>
            </div>
        </div>
    </div>

    <!-- PDF to Image Modal -->
    <div class="modal" id="pdf-to-image-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 class="modal-title"><i class="fas fa-file-image"></i> PDF to Image Converter</h2>
            <div class="tool-form">
                <div class="form-group">
                    <label for="pdf-upload">Upload PDF file:</label>
                    <div class="file-upload" id="pdf-upload-area">
                        <i class="fas fa-cloud-upload-alt"></i>
                        <p>Click to upload PDF or drag and drop</p>
                        <input type="file" id="pdf-upload" accept=".pdf" style="display: none;">
                    </div>
                    <div id="pdf-preview" style="display: none; margin-top: 1rem;">
                        <p>File: <span id="pdf-file-name"></span></p>
                    </div>
                </div>
                <div class="form-group">
                    <label for="image-format">Output Format:</label>
                    <select id="image-format" class="form-control">
                        <option value="jpg">JPG</option>
                        <option value="png">PNG</option>
                    </select>
                </div>
                <button class="btn" id="convert-pdf-to-image">Convert to Images</button>
                <div class="result" id="pdf-to-image-result"></div>
            </div>
        </div>
    </div>

    <!-- Image Compressor Modal -->
    <div class="modal" id="image-compressor-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 class="modal-title"><i class="fas fa-compress-arrows-alt"></i> Image Compressor</h2>
            <div class="tool-form">
                <div class="form-group">
                    <label for="image-compress-upload">Upload Image:</label>
                    <div class="file-upload" id="image-compress-upload-area">
                        <i class="fas fa-cloud-upload-alt"></i>
                        <p>Click to upload image or drag and drop</p>
                        <input type="file" id="image-compress-upload" accept="image/*" style="display: none;">
                    </div>
                    <div id="image-compress-preview" style="display: none; margin-top: 1rem; text-align: center;">
                        <img id="compressed-image-preview" style="max-width: 100%; max-height: 300px;">
                        <p>Original Size: <span id="original-size"></span></p>
                    </div>
                </div>
                <div class="form-group">
                    <label for="compression-level">Compression Level:</label>
                    <input type="range" id="compression-level" class="form-control" min="0" max="100" value="70">
                    <div style="display: flex; justify-content: space-between;">
                        <span>Low (Larger File)</span>
                        <span>High (Smaller File)</span>
                    </div>
                </div>
                <button class="btn" id="compress-image">Compress Image</button>
                <div class="result" id="image-compressor-result"></div>
            </div>
        </div>
    </div>

    <!-- Age Calculator Modal -->
    <div class="modal" id="age-calculator-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 class="modal-title"><i class="fas fa-birthday-cake"></i> Age Calculator</h2>
            <div class="tool-form">
                <div class="form-group">
                    <label for="birth-date">Enter your date of birth:</label>
                    <input type="date" id="birth-date" class="form-control">
                </div>
                <button class="btn" id="calculate-age">Calculate Age</button>
                <div class="result" id="age-result"></div>
            </div>
        </div>
    </div>

    <!-- Tax Calculator Modal -->
    <div class="modal" id="tax-calculator-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 class="modal-title"><i class="fas fa-calculator"></i> Tax Calculator (India)</h2>
            <div class="tool-form">
                <div class="form-group">
                    <label for="income">Annual Income (₹):</label>
                    <input type="number" id="income" class="form-control" placeholder="Enter your annual income">
                </div>
                <div class="form-group">
                    <label for="deductions">Deductions (₹):</label>
                    <input type="number" id="deductions" class="form-control" placeholder="Enter total deductions">
                </div>
                <div class="form-group">
                    <label for="regime">Tax Regime:</label>
                    <select id="regime" class="form-control">
                        <option value="new">New Regime</option>
                        <option value="old">Old Regime</option>
                    </select>
                </div>
                <button class="btn" id="calculate-tax">Calculate Tax</button>
                <div class="result" id="tax-result"></div>
                <div class="tax-slabs" id="tax-slabs" style="display: none;">
                    <h3>Tax Slabs Applied:</h3>
                    <div id="slabs-container"></div>
                </div>
            </div>
        </div>
    </div>

    <!-- Unit Converter Modal -->
    <div class="modal" id="unit-converter-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 class="modal-title"><i class="fas fa-balance-scale"></i> Unit Converter</h2>
            <div class="tool-form">
                <div class="conversion-options">
                    <div class="option-btn active" data-type="length">Length</div>
                    <div class="option-btn" data-type="weight">Weight</div>
                    <div class="option-btn" data-type="temperature">Temperature</div>
                    <div class="option-btn" data-type="currency">Currency</div>
                </div>
                
                <div class="form-group" id="length-converter">
                    <div style="display: flex; gap: 1rem;">
                        <div style="flex: 1;">
                            <label for="length-from">From:</label>
                            <select id="length-from" class="form-control">
                                <option value="meter">Meter</option>
                                <option value="kilometer">Kilometer</option>
                                <option value="centimeter">Centimeter</option>
                                <option value="millimeter">Millimeter</option>
                                <option value="mile">Mile</option>
                                <option value="yard">Yard</option>
                                <option value="foot">Foot</option>
                                <option value="inch">Inch</option>
                            </select>
                        </div>
                        <div style="flex: 1;">
                            <label for="length-to">To:</label>
                            <select id="length-to" class="form-control">
                                <option value="meter">Meter</option>
                                <option value="kilometer">Kilometer</option>
                                <option value="centimeter">Centimeter</option>
                                <option value="millimeter">Millimeter</option>
                                <option value="mile">Mile</option>
                                <option value="yard">Yard</option>
                                <option value="foot">Foot</option>
                                <option value="inch">Inch</option>
                            </select>
                        </div>
                    </div>
                    <input type="number" id="length-value" class="form-control" placeholder="Enter value">
                    <button class="btn" id="convert-length">Convert</button>
                    <div class="result" id="length-result"></div>
                </div>
                
                <div class="form-group" id="weight-converter" style="display: none;">
                    <div style="display: flex; gap: 1rem;">
                        <div style="flex: 1;">
                            <label for="weight-from">From:</label>
                            <select id="weight-from" class="form-control">
                                <option value="kilogram">Kilogram</option>
                                <option value="gram">Gram</option>
                                <option value="milligram">Milligram</option>
                                <option value="pound">Pound</option>
                                <option value="ounce">Ounce</option>
                            </select>
                        </div>
                        <div style="flex: 1;">
                            <label for="weight-to">To:</label>
                            <select id="weight-to" class="form-control">
                                <option value="kilogram">Kilogram</option>
                                <option value="gram">Gram</option>
                                <option value="milligram">Milligram</option>
                                <option value="pound">Pound</option>
                                <option value="ounce">Ounce</option>
                            </select>
                        </div>
                    </div>
                    <input type="number" id="weight-value" class="form-control" placeholder="Enter value">
                    <button class="btn" id="convert-weight">Convert</button>
                    <div class="result" id="weight-result"></div>
                </div>
                
                <div class="form-group" id="temperature-converter" style="display: none;">
                    <div style="display: flex; gap: 1rem;">
                        <div style="flex: 1;">
                            <label for="temp-from">From:</label>
                            <select id="temp-from" class="form-control">
                                <option value="celsius">Celsius</option>
                                <option value="fahrenheit">Fahrenheit</option>
                                <option value="kelvin">Kelvin</option>
                            </select>
                        </div>
                        <div style="flex: 1;">
                            <label for="temp-to">To:</label>
                            <select id="temp-to" class="form-control">
                                <option value="celsius">Celsius</option>
                                <option value="fahrenheit">Fahrenheit</option>
                                <option value="kelvin">Kelvin</option>
                            </select>
                        </div>
                    </div>
                    <input type="number" id="temp-value" class="form-control" placeholder="Enter value">
                    <button class="btn" id="convert-temp">Convert</button>
                    <div class="result" id="temp-result"></div>
                </div>
                
                <div class="form-group" id="currency-converter" style="display: none;">
                    <div style="display: flex; gap: 1rem;">
                        <div style="flex: 1;">
                            <label for="currency-from">From:</label>
                            <select id="currency-from" class="form-control">
                                <option value="USD">USD</option>
                                <option value="EUR">EUR</option>
                                <option value="GBP">GBP</option>
                                <option value="INR">INR</option>
                                <option value="JPY">JPY</option>
                            </select>
                        </div>
                        <div style="flex: 1;">
                            <label for="currency-to">To:</label>
                            <select id="currency-to" class="form-control">
                                <option value="USD">USD</option>
                                <option value="EUR">EUR</option>
                                <option value="GBP">GBP</option>
                                <option value="INR">INR</option>
                                <option value="JPY">JPY</option>
                            </select>
                        </div>
                    </div>
                    <input type="number" id="currency-value" class="form-control" placeholder="Enter value">
                    <button class="btn" id="convert-currency">Convert</button>
                    <div class="result" id="currency-result"></div>
                </div>
            </div>
        </div>
    </div>

    <!-- QR Code Tools Modal -->
    <div class="modal" id="qr-tools-modal">
        <div class="modal-content">
            <span class="close-modal">&times;</span>
            <h2 class="modal-title"><i class="fas fa-qrcode"></i> QR Code Tools</h2>
            <div class="tool-form">
                <div class="form-group">
                    <label for="qr-content">Enter text or URL for QR code:</label>
                    <input type="text" id="qr-content" class="form-control" placeholder="https://example.com or any text">
                </div>
                <button class="btn" id="generate-qr">Generate QR Code</button>
                <div class="result" id="qr-result">
                    <div id="qr-code" style="text-align: center; margin: 1rem 0;"></div>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <div class="footer-content">
                <div>
                    <div class="footer-logo">Smart Utility Hub</div>
                    <p>Your all-in-one solution for conversion and calculation tools</p>
                </div>
                <div class="footer-links">
                    <a href="#">Privacy Policy</a>
                    <a href="#">Terms of Service</a>
                    <a href="#">Contact Us</a>
                </div>
            </div>
            <div class="copyright">
                &copy; 2023 Smart Utility Hub. All rights reserved.
            </div>
        </div>
    </footer>

    <script>
        // DOM Elements
        const themeToggle = document.getElementById('themeToggle');
        const toolCards = document.querySelectorAll('.tool-card');
        const modals = document.querySelectorAll('.modal');
        const closeButtons = document.querySelectorAll('.close-modal');
        const recentToolsContainer = document.getElementById('recentTools');

        // Dark Mode Toggle
        themeToggle.addEventListener('click', () => {
            document.body.classList.toggle('dark-mode');
            const icon = themeToggle.querySelector('i');
            if (document.body.classList.contains('dark-mode')) {
                icon.classList.remove('fa-moon');
                icon.classList.add('fa-sun');
            } else {
                icon.classList.remove('fa-sun');
                icon.classList.add('fa-moon');
            }
        });

        // Tool Card Click Handler
        toolCards.forEach(card => {
            card.addEventListener('click', () => {
                const toolId = card.getAttribute('data-tool');
                const modal = document.getElementById(`${toolId}-modal`);
                if (modal) {
                    modal.style.display = 'block';
                    addToRecentTools(card);
                }
            });
        });

        // Close Modal Handlers
        closeButtons.forEach(button => {
            button.addEventListener('click', () => {
                const modal = button.closest('.modal');
                modal.style.display = 'none';
            });
        });

        // Close modal when clicking outside
        window.addEventListener('click', (event) => {
            modals.forEach(modal => {
                if (event.target === modal) {
                    modal.style.display = 'none';
                }
            });
        });

        // Recent Tools Functionality
        function addToRecentTools(card) {
            const toolName = card.querySelector('h3').textContent;
            const toolIcon = card.querySelector('i').className;
            const toolId = card.getAttribute('data-tool');
            
            // Check if tool already exists in recent tools
            const existingTools = Array.from(recentToolsContainer.children);
            const existingIndex = existingTools.findIndex(tool => 
                tool.querySelector('span').textContent === toolName
            );
            
            // If exists, remove it first
            if (existingIndex !== -1) {
                recentToolsContainer.removeChild(existingTools[existingIndex]);
            }
            
            // Create recent tool element
            const recentTool = document.createElement('div');
            recentTool.className = 'recent-tool';
            recentTool.innerHTML = `
                <i class="${toolIcon}"></i>
                <span>${toolName}</span>
            `;
            
            // Add click event to open the tool modal
            recentTool.addEventListener('click', () => {
                const modal = document.getElementById(`${toolId}-modal`);
                if (modal) {
                    modal.style.display = 'block';
                }
            });
            
            // Add to the beginning of the recent tools list
            recentToolsContainer.prepend(recentTool);
            
            // Limit to 3 recent tools
            if (recentToolsContainer.children.length > 3) {
                recentToolsContainer.removeChild(recentToolsContainer.lastChild);
            }
        }

        // Text to PDF Converter
        document.getElementById('convert-text-to-pdf').addEventListener('click', () => {
            const textInput = document.getElementById('text-input').value;
            const resultDiv = document.getElementById('text-to-pdf-result');
            
            if (!textInput.trim()) {
                resultDiv.textContent = 'Please enter some text to convert.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            // Create a simple PDF using jsPDF
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF();
            
            // Split text into lines that fit the page
            const lines = doc.splitTextToSize(textInput, 180);
            
            // Add text to PDF
            doc.text(lines, 10, 10);
            
            // Generate PDF and create download link
            const pdfBlob = doc.output('blob');
            const pdfUrl = URL.createObjectURL(pdfBlob);
            
            resultDiv.innerHTML = `
                <p>Your PDF is ready!</p>
                <a href="${pdfUrl}" download="converted-text.pdf" class="btn" style="margin-top: 10px; display: inline-block; text-decoration: none;">Download PDF</a>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // PDF to Image Converter (simulated)
        document.getElementById('pdf-upload-area').addEventListener('click', () => {
            document.getElementById('pdf-upload').click();
        });

        document.getElementById('pdf-upload').addEventListener('change', function() {
            const fileName = this.files[0]?.name || 'No file selected';
            document.getElementById('pdf-file-name').textContent = fileName;
            document.getElementById('pdf-preview').style.display = 'block';
        });

        document.getElementById('convert-pdf-to-image').addEventListener('click', () => {
            const fileInput = document.getElementById('pdf-upload');
            const format = document.getElementById('image-format').value;
            const resultDiv = document.getElementById('pdf-to-image-result');
            
            if (!fileInput.files.length) {
                resultDiv.textContent = 'Please upload a PDF file.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            // In a real implementation, this would use a PDF processing library
            resultDiv.innerHTML = `
                <p>PDF converted to ${format.toUpperCase()} images successfully!</p>
                <p>In a real implementation, this would download images for each page.</p>
                <button class="btn" style="margin-top: 10px;">Download Images as ZIP</button>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // Image Compressor (simulated)
        document.getElementById('image-compress-upload-area').addEventListener('click', () => {
            document.getElementById('image-compress-upload').click();
        });

        document.getElementById('image-compress-upload').addEventListener('change', function() {
            if (this.files && this.files[0]) {
                const file = this.files[0];
                const fileName = file.name;
                const fileSize = (file.size / 1024).toFixed(2);
                
                document.getElementById('original-size').textContent = `${fileSize} KB`;
                
                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById('compressed-image-preview').src = e.target.result;
                    document.getElementById('image-compress-preview').style.display = 'block';
                };
                reader.readAsDataURL(file);
            }
        });

        document.getElementById('compress-image').addEventListener('click', () => {
            const fileInput = document.getElementById('image-compress-upload');
            const compressionLevel = document.getElementById('compression-level').value;
            const resultDiv = document.getElementById('image-compressor-result');
            
            if (!fileInput.files.length) {
                resultDiv.textContent = 'Please upload an image.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            const originalSize = parseFloat(document.getElementById('original-size').textContent);
            const compressedSize = (originalSize * (100 - compressionLevel) / 100).toFixed(2);
            
            resultDiv.innerHTML = `
                <p>Image compressed successfully!</p>
                <p>Original size: ${originalSize} KB</p>
                <p>Compressed size: ${compressedSize} KB</p>
                <p>Reduction: ${((originalSize - compressedSize) / originalSize * 100).toFixed(1)}%</p>
                <button class="btn" style="margin-top: 10px;">Download Compressed Image</button>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // Age Calculator
        document.getElementById('calculate-age').addEventListener('click', () => {
            const birthDate = new Date(document.getElementById('birth-date').value);
            const resultDiv = document.getElementById('age-result');
            
            if (!document.getElementById('birth-date').value) {
                resultDiv.textContent = 'Please select your date of birth.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            const today = new Date();
            let years = today.getFullYear() - birthDate.getFullYear();
            let months = today.getMonth() - birthDate.getMonth();
            let days = today.getDate() - birthDate.getDate();
            
            if (days < 0) {
                months--;
                // Get days in the previous month
                const prevMonth = new Date(today.getFullYear(), today.getMonth(), 0);
                days += prevMonth.getDate();
            }
            
            if (months < 0) {
                years--;
                months += 12;
            }
            
            resultDiv.innerHTML = `
                <p>Your age is: <strong>${years} years, ${months} months, and ${days} days</strong></p>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // Tax Calculator (India)
        document.getElementById('calculate-tax').addEventListener('click', () => {
            const income = parseFloat(document.getElementById('income').value) || 0;
            const deductions = parseFloat(document.getElementById('deductions').value) || 0;
            const regime = document.getElementById('regime').value;
            const resultDiv = document.getElementById('tax-result');
            const taxSlabsDiv = document.getElementById('tax-slabs');
            const slabsContainer = document.getElementById('slabs-container');
            
            if (income <= 0) {
                resultDiv.textContent = 'Please enter a valid income.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                taxSlabsDiv.style.display = 'none';
                return;
            }
            
            let taxableIncome = income - deductions;
            if (taxableIncome < 0) taxableIncome = 0;
            
            let tax = 0;
            let slabs = [];
            
            if (regime === 'new') {
                // New tax regime slabs (FY 2023-24)
                if (taxableIncome <= 300000) {
                    tax = 0;
                    slabs.push({ range: "Up to ₹3,00,000", rate: "0%", amount: "0" });
                } else if (taxableIncome <= 600000) {
                    tax = (taxableIncome - 300000) * 0.05;
                    slabs.push(
                        { range: "Up to ₹3,00,000", rate: "0%", amount: "0" },
                        { range: "₹3,00,001 to ₹6,00,000", rate: "5%", amount: ((taxableIncome - 300000) * 0.05).toFixed(2) }
                    );
                } else if (taxableIncome <= 900000) {
                    tax = 15000 + (taxableIncome - 600000) * 0.10;
                    slabs.push(
                        { range: "Up to ₹3,00,000", rate: "0%", amount: "0" },
                        { range: "₹3,00,001 to ₹6,00,000", rate: "5%", amount: "15000" },
                        { range: "₹6,00,001 to ₹9,00,000", rate: "10%", amount: ((taxableIncome - 600000) * 0.10).toFixed(2) }
                    );
                } else if (taxableIncome <= 1200000) {
                    tax = 15000 + 30000 + (taxableIncome - 900000) * 0.15;
                    slabs.push(
                        { range: "Up to ₹3,00,000", rate: "0%", amount: "0" },
                        { range: "₹3,00,001 to ₹6,00,000", rate: "5%", amount: "15000" },
                        { range: "₹6,00,001 to ₹9,00,000", rate: "10%", amount: "30000" },
                        { range: "₹9,00,001 to ₹12,00,000", rate: "15%", amount: ((taxableIncome - 900000) * 0.15).toFixed(2) }
                    );
                } else if (taxableIncome <= 1500000) {
                    tax = 15000 + 30000 + 45000 + (taxableIncome - 1200000) * 0.20;
                    slabs.push(
                        { range: "Up to ₹3,00,000", rate: "0%", amount: "0" },
                        { range: "₹3,00,001 to ₹6,00,000", rate: "5%", amount: "15000" },
                        { range: "₹6,00,001 to ₹9,00,000", rate: "10%", amount: "30000" },
                        { range: "₹9,00,001 to ₹12,00,000", rate: "15%", amount: "45000" },
                        { range: "₹12,00,001 to ₹15,00,000", rate: "20%", amount: ((taxableIncome - 1200000) * 0.20).toFixed(2) }
                    );
                } else {
                    tax = 15000 + 30000 + 45000 + 60000 + (taxableIncome - 1500000) * 0.30;
                    slabs.push(
                        { range: "Up to ₹3,00,000", rate: "0%", amount: "0" },
                        { range: "₹3,00,001 to ₹6,00,000", rate: "5%", amount: "15000" },
                        { range: "₹6,00,001 to ₹9,00,000", rate: "10%", amount: "30000" },
                        { range: "₹9,00,001 to ₹12,00,000", rate: "15%", amount: "45000" },
                        { range: "₹12,00,001 to ₹15,00,000", rate: "20%", amount: "60000" },
                        { range: "Above ₹15,00,000", rate: "30%", amount: ((taxableIncome - 1500000) * 0.30).toFixed(2) }
                    );
                }
            } else {
                // Old tax regime slabs (FY 2023-24)
                if (taxableIncome <= 250000) {
                    tax = 0;
                    slabs.push({ range: "Up to ₹2,50,000", rate: "0%", amount: "0" });
                } else if (taxableIncome <= 500000) {
                    tax = (taxableIncome - 250000) * 0.05;
                    slabs.push(
                        { range: "Up to ₹2,50,000", rate: "0%", amount: "0" },
                        { range: "₹2,50,001 to ₹5,00,000", rate: "5%", amount: ((taxableIncome - 250000) * 0.05).toFixed(2) }
                    );
                } else if (taxableIncome <= 1000000) {
                    tax = 12500 + (taxableIncome - 500000) * 0.20;
                    slabs.push(
                        { range: "Up to ₹2,50,000", rate: "0%", amount: "0" },
                        { range: "₹2,50,001 to ₹5,00,000", rate: "5%", amount: "12500" },
                        { range: "₹5,00,001 to ₹10,00,000", rate: "20%", amount: ((taxableIncome - 500000) * 0.20).toFixed(2) }
                    );
                } else {
                    tax = 12500 + 100000 + (taxableIncome - 1000000) * 0.30;
                    slabs.push(
                        { range: "Up to ₹2,50,000", rate: "0%", amount: "0" },
                        { range: "₹2,50,001 to ₹5,00,000", rate: "5%", amount: "12500" },
                        { range: "₹5,00,001 to ₹10,00,000", rate: "20%", amount: "100000" },
                        { range: "Above ₹10,00,000", rate: "30%", amount: ((taxableIncome - 1000000) * 0.30).toFixed(2) }
                    );
                }
            }
            
            // Add health and education cess (4%)
            const cess = tax * 0.04;
            const totalTax = tax + cess;
            
            resultDiv.innerHTML = `
                <p>Taxable Income: ₹${taxableIncome.toLocaleString()}</p>
                <p>Income Tax: ₹${tax.toFixed(2)}</p>
                <p>Health & Education Cess (4%): ₹${cess.toFixed(2)}</p>
                <p><strong>Total Tax Liability: ₹${totalTax.toFixed(2)}</strong></p>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
            
            // Display tax slabs
            slabsContainer.innerHTML = '';
            slabs.forEach(slab => {
                const slabElement = document.createElement('div');
                slabElement.className = 'slab';
                slabElement.innerHTML = `
                    <span>${slab.range}</span>
                    <span>${slab.rate}</span>
                    <span>₹${slab.amount}</span>
                `;
                slabsContainer.appendChild(slabElement);
            });
            
            taxSlabsDiv.style.display = 'block';
        });

        // Unit Converter
        const optionBtns = document.querySelectorAll('.option-btn');
        optionBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                // Remove active class from all buttons
                optionBtns.forEach(b => b.classList.remove('active'));
                // Add active class to clicked button
                btn.classList.add('active');
                
                // Hide all converters
                document.getElementById('length-converter').style.display = 'none';
                document.getElementById('weight-converter').style.display = 'none';
                document.getElementById('temperature-converter').style.display = 'none';
                document.getElementById('currency-converter').style.display = 'none';
                
                // Show selected converter
                const type = btn.getAttribute('data-type');
                document.getElementById(`${type}-converter`).style.display = 'block';
            });
        });

        // Length Converter
        document.getElementById('convert-length').addEventListener('click', () => {
            const fromUnit = document.getElementById('length-from').value;
            const toUnit = document.getElementById('length-to').value;
            const value = parseFloat(document.getElementById('length-value').value);
            const resultDiv = document.getElementById('length-result');
            
            if (isNaN(value)) {
                resultDiv.textContent = 'Please enter a valid number.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            // Conversion factors to meters
            const toMeter = {
                meter: 1,
                kilometer: 1000,
                centimeter: 0.01,
                millimeter: 0.001,
                mile: 1609.34,
                yard: 0.9144,
                foot: 0.3048,
                inch: 0.0254
            };
            
            const valueInMeters = value * toMeter[fromUnit];
            const convertedValue = valueInMeters / toMeter[toUnit];
            
            resultDiv.innerHTML = `
                <p>${value} ${fromUnit} = ${convertedValue.toFixed(6)} ${toUnit}</p>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // Weight Converter
        document.getElementById('convert-weight').addEventListener('click', () => {
            const fromUnit = document.getElementById('weight-from').value;
            const toUnit = document.getElementById('weight-to').value;
            const value = parseFloat(document.getElementById('weight-value').value);
            const resultDiv = document.getElementById('weight-result');
            
            if (isNaN(value)) {
                resultDiv.textContent = 'Please enter a valid number.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            // Conversion factors to kilograms
            const toKilogram = {
                kilogram: 1,
                gram: 0.001,
                milligram: 0.000001,
                pound: 0.453592,
                ounce: 0.0283495
            };
            
            const valueInKilograms = value * toKilogram[fromUnit];
            const convertedValue = valueInKilograms / toKilogram[toUnit];
            
            resultDiv.innerHTML = `
                <p>${value} ${fromUnit} = ${convertedValue.toFixed(6)} ${toUnit}</p>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // Temperature Converter
        document.getElementById('convert-temp').addEventListener('click', () => {
            const fromUnit = document.getElementById('temp-from').value;
            const toUnit = document.getElementById('temp-to').value;
            const value = parseFloat(document.getElementById('temp-value').value);
            const resultDiv = document.getElementById('temp-result');
            
            if (isNaN(value)) {
                resultDiv.textContent = 'Please enter a valid number.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            let convertedValue;
            
            // Convert to Celsius first
            let inCelsius;
            if (fromUnit === 'celsius') inCelsius = value;
            else if (fromUnit === 'fahrenheit') inCelsius = (value - 32) * 5/9;
            else if (fromUnit === 'kelvin') inCelsius = value - 273.15;
            
            // Convert from Celsius to target unit
            if (toUnit === 'celsius') convertedValue = inCelsius;
            else if (toUnit === 'fahrenheit') convertedValue = (inCelsius * 9/5) + 32;
            else if (toUnit === 'kelvin') convertedValue = inCelsius + 273.15;
            
            resultDiv.innerHTML = `
                <p>${value}° ${fromUnit.charAt(0).toUpperCase()} = ${convertedValue.toFixed(2)}° ${toUnit.charAt(0).toUpperCase()}</p>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // Currency Converter (simulated with fixed rates)
        document.getElementById('convert-currency').addEventListener('click', () => {
            const fromCurrency = document.getElementById('currency-from').value;
            const toCurrency = document.getElementById('currency-to').value;
            const value = parseFloat(document.getElementById('currency-value').value);
            const resultDiv = document.getElementById('currency-result');
            
            if (isNaN(value)) {
                resultDiv.textContent = 'Please enter a valid number.';
                resultDiv.className = 'result error';
                resultDiv.style.display = 'block';
                return;
            }
            
            // Fixed exchange rates (for demonstration)
            const rates = {
                USD: { USD: 1, EUR: 0.85, GBP: 0.73, INR: 82.5, JPY: 110.5 },
                EUR: { USD: 1.18, EUR: 1, GBP: 0.86, INR: 97.2, JPY: 130.1 },
                GBP: { USD: 1.37, EUR: 1.16, GBP: 1, INR: 112.8, JPY: 151.2 },
                INR: { USD: 0.012, EUR: 0.0103, GBP: 0.0089, INR: 1, JPY: 1.34 },
                JPY: { USD: 0.009, EUR: 0.0077, GBP: 0.0066, INR: 0.75, JPY: 1 }
            };
            
            const convertedValue = value * rates[fromCurrency][toCurrency];
            
            resultDiv.innerHTML = `
                <p>${value} ${fromCurrency} = ${convertedValue.toFixed(2)} ${toCurrency}</p>
                <p><small>Note: Exchange rates are for demonstration only.</small></p>
            `;
            resultDiv.className = 'result success';
            resultDiv.style.display = 'block';
        });

        // QR Code Generator
        document.getElementById('generate-qr').addEventListener('click', () => {
            const qrContent = document.getElementById('qr-content').value;
            const qrResult = document.getElementById('qr-result');
            const qrCodeDiv = document.getElementById('qr-code');
            
            if (!qrContent.trim()) {
                qrResult.textContent = 'Please enter text or URL to generate QR code.';
                qrResult.className = 'result error';
                qrResult.style.display = 'block';
                return;
            }
            
            // Clear previous QR code
            qrCodeDiv.innerHTML = '';
            
            // Generate QR code
            QRCode.toCanvas(qrContent, { width: 200, height: 200 }, function(err, canvas) {
                if (err) {
                    qrResult.textContent = 'Error generating QR code.';
                    qrResult.className = 'result error';
                    qrResult.style.display = 'block';
                    return;
                }
                
                qrCodeDiv.appendChild(canvas);
                qrResult.className = 'result success';
                qrResult.style.display = 'block';
            });
        });

        // Initialize with some recent tools
        window.addEventListener('DOMContentLoaded', () => {
            // Add initial recent tools
            const initialTools = [
                document.querySelector('[data-tool="text-to-pdf"]'),
                document.querySelector('[data-tool="age-calculator"]'),
                document.querySelector('[data-tool="qr-tools"]')
            ];
            
            initialTools.forEach(tool => {
                if (tool) addToRecentTools(tool);
            });
        });
    </script>
</body>
</html>
