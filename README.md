<!DOCTYPE html>

<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Utopia — Столица Империи Karin</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

```
    body {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        background: #ffffff;
        color: #2c3e50;
        line-height: 1.8;
        overflow-x: hidden;
        position: relative;
    }

    /* Particle Canvas */
    #particleCanvas {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
        pointer-events: none;
    }

    /* Side Panel - MeandEmp */
    .app-panel {
        position: fixed;
        right: 20px;
        bottom: 20px;
        width: 180px;
        padding: 1.5rem 1rem;
        background: rgba(255, 255, 255, 0.5);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border: 2px solid rgba(255, 255, 255, 0.6);
        border-radius: 15px;
        box-shadow: 
            0 8px 32px rgba(102, 126, 234, 0.2),
            inset 0 0 20px rgba(255, 255, 255, 0.3);
        z-index: 999;
        transition: all 0.3s ease;
        cursor: pointer;
    }

    .app-panel:hover {
        transform: translateY(-5px);
        box-shadow: 
            0 12px 48px rgba(102, 126, 234, 0.3),
            inset 0 0 30px rgba(255, 255, 255, 0.4);
    }

    .app-icon {
        width: 50px;
        height: 50px;
        margin: 0 auto 0.8rem;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        border-radius: 12px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.8rem;
        box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        animation: iconPulse 3s ease-in-out infinite;
    }

    @keyframes iconPulse {
        0%, 100% { transform: scale(1); box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4); }
        50% { transform: scale(1.05); box-shadow: 0 6px 25px rgba(102, 126, 234, 0.6); }
    }

    .app-title {
        font-size: 1rem;
        font-weight: 600;
        color: #667eea;
        text-align: center;
        margin-bottom: 0.3rem;
        letter-spacing: 0.05em;
    }

    .app-subtitle {
        font-size: 0.7rem;
        color: #764ba2;
        text-align: center;
        line-height: 1.3;
        font-weight: 500;
    }

    @media (max-width: 768px) {
        .app-panel {
            right: 10px;
            bottom: 10px;
            width: 150px;
            padding: 1rem 0.8rem;
        }
        
        .app-icon {
            width: 40px;
            height: 40px;
            font-size: 1.5rem;
        }
        
        .app-title {
            font-size: 0.9rem;
        }
        
        .app-subtitle {
            font-size: 0.65rem;
        }
    }

    /* MeandEmp App Page */
    .app-page {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #ffffff;
        z-index: 10000;
        opacity: 0;
        pointer-events: none;
        transition: opacity 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        overflow-y: auto;
        overflow-x: hidden;
    }

    .app-page.active {
        opacity: 1;
        pointer-events: all;
    }

    .app-content {
        max-width: 900px;
        margin: 0 auto;
        padding: 4rem 2rem 6rem 2rem;
        text-align: center;
        transform: translateY(40px);
        transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .app-page.active .app-content {
        transform: translateY(0);
    }

    .app-logo {
        width: 120px;
        height: 120px;
        margin: 0 auto 2rem;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        border-radius: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 4rem;
        box-shadow: 0 10px 40px rgba(102, 126, 234, 0.4);
        animation: logoFloat 3s ease-in-out infinite;
    }

    @keyframes logoFloat {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-10px); }
    }

    .app-main-title {
        font-size: 3rem;
        font-weight: 300;
        color: #667eea;
        margin-bottom: 1rem;
        letter-spacing: 0.05em;
    }

    .app-tagline {
        font-size: 1.3rem;
        color: #764ba2;
        font-weight: 500;
        margin-bottom: 3rem;
    }

    .app-description {
        font-size: 1.2rem;
        line-height: 2;
        color: #2c3e50;
        margin-bottom: 3rem;
        background: rgba(255, 255, 255, 0.9);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        padding: 2.5rem;
        border-radius: 20px;
        border: 2px solid rgba(102, 126, 234, 0.2);
        box-shadow: 0 8px 32px rgba(102, 126, 234, 0.1);
    }

    .app-features {
        display: grid;
        gap: 1.5rem;
        margin-bottom: 3rem;
        text-align: left;
    }

    .app-feature {
        background: rgba(255, 255, 255, 0.9);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border-radius: 15px;
        border: 2px solid rgba(102, 126, 234, 0.2);
        overflow: hidden;
        transition: all 0.3s ease;
    }

    .app-feature:hover {
        border-color: rgba(102, 126, 234, 0.5);
        box-shadow: 0 10px 30px rgba(102, 126, 234, 0.2);
    }

    .app-feature-header {
        display: flex;
        align-items: center;
        gap: 1rem;
        padding: 1.5rem;
        cursor: pointer;
        transition: background 0.3s ease;
    }

    .app-feature-header:hover {
        background: rgba(102, 126, 234, 0.05);
    }

    .app-feature-icon {
        font-size: 2.5rem;
        flex-shrink: 0;
    }

    .app-feature-title {
        flex: 1;
        font-size: 1.3rem;
        color: #667eea;
        font-weight: 600;
    }

    .app-feature-arrow {
        font-size: 1.5rem;
        color: #764ba2;
        transition: transform 0.3s ease;
    }

    .app-feature.expanded .app-feature-arrow {
        transform: rotate(180deg);
    }

    .app-feature-content {
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .app-feature.expanded .app-feature-content {
        max-height: 1000px;
    }

    .app-feature-text {
        padding: 0 1.5rem 1.5rem 1.5rem;
        font-size: 1.05rem;
        color: #555;
        line-height: 1.8;
    }

    .back-button {
        display: inline-flex;
        align-items: center;
        gap: 0.5rem;
        padding: 1rem 2.5rem;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        border: none;
        border-radius: 50px;
        font-size: 1.1rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
        position: sticky;
        bottom: 2rem;
        margin-top: 2rem;
    }

    .back-button:hover {
        transform: translateY(-3px);
        box-shadow: 0 8px 30px rgba(102, 126, 234, 0.6);
    }

    .back-button:active {
        transform: translateY(-1px);
    }

    @media (max-width: 768px) {
        .app-main-title {
            font-size: 2rem;
        }

        .app-tagline {
            font-size: 1.1rem;
        }

        .app-description {
            font-size: 1rem;
            padding: 1.5rem;
        }

        .app-logo {
            width: 90px;
            height: 90px;
            font-size: 3rem;
        }

        .app-feature-title {
            font-size: 1.1rem;
        }

        .app-content {
            padding: 3rem 1.5rem 5rem 1.5rem;
        }
    }

    .hero {
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        position: relative;
        overflow: hidden;
    }

    .hero::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 800"><rect fill="%23ffffff" opacity="0.05" width="100%" height="100%"/><circle cx="200" cy="200" r="150" fill="%23ffffff" opacity="0.03"/><circle cx="1000" cy="600" r="200" fill="%23ffffff" opacity="0.03"/></svg>');
        opacity: 0.3;
        animation: float 20s ease-in-out infinite;
    }

    @keyframes float {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-20px); }
    }

    .hero-content {
        position: relative;
        z-index: 1;
        animation: fadeInUp 1.2s ease-out;
    }

    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(40px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    .hero h1 {
        font-size: 5rem;
        font-weight: 300;
        margin-bottom: 1rem;
        letter-spacing: 0.1em;
        text-shadow: 0 4px 20px rgba(0,0,0,0.2);
    }

    .hero .subtitle {
        font-size: 1.5rem;
        font-weight: 300;
        opacity: 0.9;
        margin-bottom: 0.5rem;
    }

    .hero .description {
        font-size: 1.1rem;
        opacity: 0.8;
        max-width: 800px;
        margin: 0 auto;
        padding: 0 2rem;
    }

    .scroll-indicator {
        position: absolute;
        bottom: 40px;
        left: 50%;
        transform: translateX(-50%);
        animation: bounce 2s infinite;
    }

    @keyframes bounce {
        0%, 100% { transform: translateX(-50%) translateY(0); }
        50% { transform: translateX(-50%) translateY(-15px); }
    }

    .scroll-indicator::before {
        content: '↓';
        font-size: 2rem;
        opacity: 0.7;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 6rem 2rem;
    }

    .section {
        margin-bottom: 6rem;
        opacity: 0;
        transform: translateY(40px);
        transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .section.visible {
        opacity: 1;
        transform: translateY(0);
    }

    .section-title {
        font-size: 2.5rem;
        font-weight: 300;
        margin-bottom: 2rem;
        color: #667eea;
        display: flex;
        align-items: center;
        gap: 1rem;
    }

    .section-title::before {
        content: '';
        width: 4px;
        height: 50px;
        background: linear-gradient(180deg, #667eea, #764ba2);
        border-radius: 2px;
    }

    .card {
        background: white;
        padding: 3rem;
        border-radius: 20px;
        box-shadow: 0 10px 40px rgba(0,0,0,0.08);
        margin-bottom: 2rem;
        transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .card:hover {
        transform: translateY(-8px);
        box-shadow: 0 20px 60px rgba(102, 126, 234, 0.15);
    }

    .card h3 {
        font-size: 1.8rem;
        margin-bottom: 1.5rem;
        color: #764ba2;
        font-weight: 400;
    }

    .card p {
        font-size: 1.1rem;
        color: #555;
        line-height: 2;
        margin-bottom: 1rem;
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
        margin-top: 2rem;
    }

    .feature-box {
        background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
        padding: 2.5rem;
        border-radius: 15px;
        transition: all 0.4s ease;
        border: 2px solid transparent;
    }

    .feature-box:hover {
        border-color: #667eea;
        background: white;
        transform: scale(1.05);
    }

    .feature-box h4 {
        font-size: 1.4rem;
        margin-bottom: 1rem;
        color: #667eea;
        font-weight: 500;
    }

    .feature-box p {
        color: #666;
        font-size: 1rem;
    }

    ul.styled-list {
        list-style: none;
        padding-left: 0;
    }

    ul.styled-list li {
        padding: 0.8rem 0;
        padding-left: 2rem;
        position: relative;
        font-size: 1.1rem;
        color: #555;
    }

    ul.styled-list li::before {
        content: '●';
        position: absolute;
        left: 0;
        color: #667eea;
        font-size: 1.5rem;
    }

    .architecture-section {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 3rem;
        margin-top: 2rem;
    }

    .architecture-column {
        background: white;
        padding: 2.5rem;
        border-radius: 15px;
        box-shadow: 0 5px 25px rgba(0,0,0,0.06);
        transition: all 0.4s ease;
    }

    .architecture-column:hover {
        box-shadow: 0 15px 45px rgba(102, 126, 234, 0.12);
    }

    .architecture-column h4 {
        font-size: 1.6rem;
        margin-bottom: 1.5rem;
        color: #764ba2;
        font-weight: 400;
    }

    .highlight {
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        padding: 4rem;
        border-radius: 20px;
        text-align: center;
        margin: 4rem 0;
        box-shadow: 0 20px 60px rgba(102, 126, 234, 0.2);
    }

    .highlight h3 {
        font-size: 2rem;
        margin-bottom: 1.5rem;
        font-weight: 300;
    }

    .highlight p {
        font-size: 1.2rem;
        line-height: 2;
        opacity: 0.95;
    }

    @media (max-width: 768px) {
        .hero h1 {
            font-size: 3rem;
        }

        .hero .subtitle {
            font-size: 1.2rem;
        }

        .architecture-section {
            grid-template-columns: 1fr;
        }

        .section-title {
            font-size: 2rem;
        }

        .container {
            padding: 4rem 1.5rem;
        }
    }

    .fade-in {
        animation: fadeIn 1s ease-out;
    }

    @keyframes fadeIn {
        from { opacity: 0; }
        to { opacity: 1; }
    }

    .pillars-note {
        background: linear-gradient(135deg, #ffeaa7 0%, #fdcb6e 100%);
        padding: 2rem;
        border-radius: 15px;
        margin-top: 1.5rem;
        border-left: 4px solid #d63031;
        font-style: italic;
        color: #2d3436;
    }

    /* Glassmorphism Effects */
    .glass-card {
        background: rgba(255, 255, 255, 0.85);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border: 1px solid rgba(255, 255, 255, 0.9);
        box-shadow: 0 8px 32px 0 rgba(102, 126, 234, 0.15);
    }

    .card {
        background: rgba(255, 255, 255, 0.92);
        backdrop-filter: blur(25px);
        -webkit-backdrop-filter: blur(25px);
        border: 2px solid rgba(255, 255, 255, 0.95);
        box-shadow: 
            0 8px 32px rgba(102, 126, 234, 0.1),
            inset 0 0 20px rgba(255, 255, 255, 0.6);
    }

    .card:hover {
        background: rgba(255, 255, 255, 0.95);
        border: 2px solid rgba(102, 126, 234, 0.3);
    }

    .feature-box {
        background: rgba(255, 255, 255, 0.88);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border: 2px solid rgba(255, 255, 255, 0.92);
        box-shadow: 
            0 4px 20px rgba(102, 126, 234, 0.1),
            inset 0 0 15px rgba(255, 255, 255, 0.5);
    }

    .feature-box:hover {
        background: rgba(255, 255, 255, 0.95);
        border: 2px solid rgba(102, 126, 234, 0.4);
    }

    .architecture-column {
        background: rgba(255, 255, 255, 0.9);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border: 2px solid rgba(255, 255, 255, 0.95);
        box-shadow: 
            0 6px 25px rgba(102, 126, 234, 0.1),
            inset 0 0 18px rgba(255, 255, 255, 0.6);
    }

    .architecture-column:hover {
        background: rgba(255, 255, 255, 0.95);
        border: 2px solid rgba(102, 126, 234, 0.3);
    }

    .archive-mark {
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(30px);
        -webkit-backdrop-filter: blur(30px);
        border: 3px solid rgba(102, 126, 234, 0.4);
        box-shadow: 
            0 10px 40px rgba(102, 126, 234, 0.15),
            inset 0 0 25px rgba(255, 255, 255, 0.7);
    }

    .pillars-note {
        background: rgba(255, 234, 167, 0.9);
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        border: 2px solid rgba(253, 203, 110, 0.7);
        box-shadow: 
            0 4px 20px rgba(253, 203, 110, 0.2),
            inset 0 0 15px rgba(255, 255, 255, 0.5);
    }

    /* Imperial Document Footer */
    .imperial-footer {
        background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
        border-top: 3px solid #667eea;
        margin-top: 6rem;
        padding: 4rem 0;
    }

    .document-info {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 2rem;
    }

    .archive-mark {
        background: rgba(255, 255, 255, 0.8);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        border: 2px solid #667eea;
        border-radius: 15px;
        padding: 3rem;
        margin-bottom: 3rem;
        box-shadow: 0 10px 40px rgba(0,0,0,0.1);
    }

    .archive-title {
        font-size: 1.3rem;
        font-weight: 600;
        color: #764ba2;
        margin-bottom: 1.5rem;
        letter-spacing: 0.2em;
        text-align: center;
    }

    .archive-details {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 1rem;
        font-size: 1rem;
        color: #2c3e50;
        line-height: 1.8;
    }

    .archive-detail {
        padding: 0.5rem 0;
    }

    .archive-detail strong {
        color: #667eea;
        font-weight: 600;
    }

    .signature-section {
        display: flex;
        justify-content: space-between;
        align-items: flex-end;
        margin-top: 3rem;
        padding: 2rem 0;
        border-top: 1px solid rgba(102, 126, 234, 0.3);
    }

    .seal-container {
        display: flex;
        gap: 3rem;
        align-items: center;
    }

    .seal {
        width: 140px;
        height: 140px;
        border: 4px double #667eea;
        border-radius: 50%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background: radial-gradient(circle, rgba(102, 126, 234, 0.15) 0%, rgba(118, 75, 162, 0.08) 100%);
        position: relative;
        animation: sealGlow 3s ease-in-out infinite;
        box-shadow: inset 0 0 20px rgba(102, 126, 234, 0.1);
    }

    @keyframes sealGlow {
        0%, 100% { box-shadow: 0 0 20px rgba(102, 126, 234, 0.3), inset 0 0 20px rgba(102, 126, 234, 0.1); }
        50% { box-shadow: 0 0 40px rgba(102, 126, 234, 0.5), inset 0 0 30px rgba(102, 126, 234, 0.15); }
    }

    .seal::before {
        content: '';
        position: absolute;
        width: 85%;
        height: 85%;
        border: 2px solid #764ba2;
        border-radius: 50%;
        opacity: 0.5;
    }

    .crown-symbol {
        font-size: 3rem;
        color: #667eea;
        margin-bottom: 0.3rem;
        filter: drop-shadow(0 2px 4px rgba(102, 126, 234, 0.3));
        position: relative;
        z-index: 1;
    }

    .chancellery-icon {
        position: relative;
        width: 80px;
        height: 80px;
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1;
    }

    .chancellery-building {
        position: absolute;
        width: 50px;
        height: 40px;
        background: linear-gradient(to bottom, #e0e0e0 0%, #f5f5f5 100%);
        border: 2px solid #333;
        border-radius: 2px 2px 0 0;
    }

    .chancellery-building::before {
        content: '';
        position: absolute;
        top: -8px;
        left: -5px;
        right: -5px;
        height: 8px;
        background: #333;
        clip-path: polygon(0% 100%, 50% 0%, 100% 100%);
    }

    .column {
        position: absolute;
        width: 6px;
        height: 30px;
        background: linear-gradient(to right, #d0d0d0, #f0f0f0, #d0d0d0);
        border: 1px solid #666;
        bottom: 0;
    }

    .column:nth-child(1) { left: 8px; }
    .column:nth-child(2) { left: 18px; }
    .column:nth-child(3) { right: 18px; }
    .column:nth-child(4) { right: 8px; }

    .column::before {
        content: '';
        position: absolute;
        top: -3px;
        left: -2px;
        right: -2px;
        height: 3px;
        background: #999;
        border-radius: 1px 1px 0 0;
    }

    .quill {
        position: absolute;
        width: 45px;
        height: 45px;
        top: 50%;
        left: 55%;
        transform: translate(-50%, -50%) rotate(-25deg);
        z-index: 2;
    }

    .quill::before {
        content: '';
        position: absolute;
        width: 3px;
        height: 35px;
        background: linear-gradient(to bottom, #2c3e50 0%, #34495e 50%, #555 100%);
        left: 50%;
        transform: translateX(-50%);
        border-radius: 1px;
    }

    .quill::after {
        content: '';
        position: absolute;
        width: 0;
        height: 0;
        border-left: 12px solid transparent;
        border-right: 12px solid transparent;
        border-bottom: 25px solid #1a1a1a;
        top: -5px;
        left: 50%;
        transform: translateX(-50%);
        filter: drop-shadow(0 1px 2px rgba(0,0,0,0.3));
    }

    .quill-detail {
        position: absolute;
        width: 1px;
        height: 15px;
        background: rgba(255,255,255,0.3);
        top: 5px;
        left: 48%;
        transform: rotate(-10deg);
    }

    .seal-text {
        font-size: 0.65rem;
        font-weight: 700;
        color: #764ba2;
        text-align: center;
        letter-spacing: 0.1em;
        line-height: 1.2;
        text-transform: uppercase;
        position: relative;
        z-index: 1;
    }

    .signature {
        text-align: center;
    }

    .signature-line {
        width: 300px;
        height: 80px;
        margin: 1rem auto;
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .emperor-signature {
        font-family: 'Brush Script MT', 'Lucida Handwriting', 'Apple Chancery', cursive;
        font-size: 2.5rem;
        color: #2c3e50;
        font-weight: 400;
        font-style: italic;
        transform: rotate(-5deg);
        text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        letter-spacing: 0.05em;
        position: relative;
    }

    .emperor-signature::after {
        content: '';
        position: absolute;
        bottom: -5px;
        left: 0;
        right: 0;
        height: 2px;
        background: linear-gradient(90deg, transparent 0%, #667eea 20%, #764ba2 80%, transparent 100%);
    }

    .signature-title {
        font-size: 1.2rem;
        font-weight: 600;
        color: #764ba2;
        margin-top: 1rem;
    }

    .signature-subtitle {
        font-size: 0.9rem;
        color: #666;
        margin-top: 0.3rem;
    }

    .imperial-motto {
        text-align: center;
        font-size: 1.5rem;
        font-weight: 300;
        letter-spacing: 0.3em;
        color: #667eea;
        margin-top: 3rem;
        padding: 2rem 0;
        border-top: 1px solid rgba(102, 126, 234, 0.3);
        text-transform: uppercase;
    }

    @media (max-width: 768px) {
        .signature-section {
            flex-direction: column;
            gap: 2rem;
            align-items: center;
        }

        .seal-container {
            flex-direction: column;
            gap: 2rem;
        }

        .imperial-motto {
            font-size: 1rem;
            letter-spacing: 0.15em;
        }
    }
</style>
```

</head>
<body>
    <!-- Particle Canvas -->
    <canvas id="particleCanvas"></canvas>

```
<!-- MeandEmp App Page -->
<div class="app-page" id="appPage">
    <div class="app-content">
        <div class="app-logo">👑</div>
        <h1 class="app-main-title">MeandEmp</h1>
        <div class="app-tagline">Императорское всенародное единое приложение</div>
        
        <div class="app-description">
            Скачай Императорское всенародное единое приложение MeandEmp, и следи за новостями, записывайся на приём к императорскому совету, суду, участвуй в мероприятиях, узнавай историю родной земли и Империи, совершенствуйся, получай знания, путешествуй вместе с нами!
        </div>

        <div class="app-features">
            <div class="app-feature" onclick="toggleFeature(this)">
                <div class="app-feature-header">
                    <div class="app-feature-icon">📰</div>
                    <div class="app-feature-title">Новости Империи</div>
                    <div class="app-feature-arrow">▼</div>
                </div>
                <div class="app-feature-content">
                    <div class="app-feature-text">
                        Получайте актуальные новости о жизни Империи Karin, важных решениях императора, культурных событиях и достижениях. Будьте в курсе всех официальных заявлений, указов и важных изменений в законодательстве. Узнавайте первыми о новых проектах развития городов и регионов.
                    </div>
                </div>
            </div>

            <div class="app-feature" onclick="toggleFeature(this)">
                <div class="app-feature-header">
                    <div class="app-feature-icon">📅</div>
                    <div class="app-feature-title">Запись на приём</div>
                    <div class="app-feature-arrow">▼</div>
                </div>
                <div class="app-feature-content">
                    <div class="app-feature-text">
                        Записывайтесь на личный приём к представителям Императорского совета, подавайте прошения и обращения напрямую. Отслеживайте статус ваших запросов в режиме реального времени. Получайте уведомления о датах и времени встреч, а также о ходе рассмотрения ваших дел.
                    </div>
                </div>
            </div>

            <div class="app-feature" onclick="toggleFeature(this)">
                <div class="app-feature-header">
                    <div class="app-feature-icon">⚖️</div>
                    <div class="app-feature-title">Императорский суд</div>
                    <div class="app-feature-arrow">▼</div>
                </div>
                <div class="app-feature-content">
                    <div class="app-feature-text">
                        Подавайте судебные иски и жалобы в электронном виде, следите за ходом разбирательств, получайте уведомления о заседаниях. Доступ к архиву судебных решений и прецедентов. Консультации по юридическим вопросам от императорских юристов и возможность онлайн-участия в открытых судебных процессах.
                    </div>
                </div>
            </div>

            <div class="app-feature" onclick="toggleFeature(this)">
                <div class="app-feature-header">
                    <div class="app-feature-icon">🎭</div>
                    <div class="app-feature-title">Мероприятия</div>
                    <div class="app-feature-arrow">▼</div>
                </div>
                <div class="app-feature-content">
                    <div class="app-feature-text">
                        Участвуйте в имперских праздниках, культурных фестивалях, образовательных семинарах и торжественных церемониях. Регистрируйтесь на мероприятия заранее, получайте пригласительные билеты в электронном виде. Узнавайте о выставках в Главном Имперском архиве, концертах и театральных постановках в столице.
                    </div>
                </div>
            </div>

            <div class="app-feature" onclick="toggleFeature(this)">
                <div class="app-feature-header">
                    <div class="app-feature-icon">📚</div>
                    <div class="app-feature-title">История и знания</div>
                    <div class="app-feature-arrow">▼</div>
                </div>
                <div class="app-feature-content">
                    <div class="app-feature-text">
                        Изучайте историю династии Karin, узнавайте о героях прошлого и великих свершениях Империи. Доступ к образовательным материалам, документальным хроникам и архивным записям. Виртуальные экскурсии по историческим местам Utopia и других городов. Участвуйте в образовательных программах и получайте имперские сертификаты.
                    </div>
                </div>
            </div>

            <div class="app-feature" onclick="toggleFeature(this)">
                <div class="app-feature-header">
                    <div class="app-feature-icon">🗺️</div>
                    <div class="app-feature-title">Путешествия</div>
                    <div class="app-feature-arrow">▼</div>
                </div>
                <div class="app-feature-content">
                    <div class="app-feature-text">
                        Планируйте путешествия по территории Империи Karin с помощью интерактивных карт и путеводителей. Бронируйте официальные экскурсии по Utopia, включая посещение Имперского парламента и исторического центра. Получайте рекомендации о достопримечательностях, отелях и ресторанах. Специальные туристические маршруты от Центрального края до отдалённых регионов.
                    </div>
                </div>
            </div>
        </div>

        <button class="back-button" onclick="closeMeandEmpPage()">
            ← Вернуться к информации о городе
        </button>
    </div>
</div>

<!-- Side App Panel - Bottom Right -->
<div class="app-panel" onclick="openMeandEmpPage()">
    <div class="app-icon">👑</div>
    <div class="app-title">MeandEmp</div>
    <div class="app-subtitle">Императорское приложение</div>
</div>

<div class="hero">
    <div class="hero-content">
        <h1>Utopia</h1>
        <div class="subtitle">Столица Империи Karin</div>
        <div class="description">Сердце Центрального края</div>
    </div>
    <div class="scroll-indicator"></div>
</div>

<div class="container">
    <section class="section">
        <h2 class="section-title">🏛 Главная страница</h2>
        <div class="card">
            <p>Utopia — главный город Империи Karin, её политический, архитектурный и символический центр. Именно отсюда исходит власть, здесь формируется имперская воля и хранится её память.</p>
            <p>Город совмещает в себе монументальность прошлого и вертикаль будущего — от мраморных колонн до стеклянных небоскрёбов.</p>
        </div>
    </section>

    <section class="section">
        <h2 class="section-title">🏙 О городе</h2>
        <div class="card">
            <p>Утопия расположена в Центральном крае и является официальной столицей Империи. Город был основан XXIV императором Koll Lingstor династии Karin, как новый символ централизованной, обновлённой власти.</p>
            <p>Основание Utopia стало поворотной точкой в истории Империи — перенос фокуса с старых столиц на единый, демонстративный центр управления, на центральные острова, которые хотели давно уже заселить и исследовать.</p>
            <p>С самого начала город проектировался не как просто место проживания, а как витрина Империи. Сначала хотели построить воздушный город на четырёх колоннах. Колонны огромные и платформу построили.</p>
            <div class="pillars-note">
                Но потом отказались от этой идеи, платформу разобрали, а колонны оставили
            </div>
        </div>
    </section>

    <section class="section">
        <h2 class="section-title">🏛 Имперские здания и власть</h2>
        <div class="card">
            <h3>Главный Имперский архив</h3>
            <p>Хранилище законов, династических хроник, закрытых документов и переписанной истории. Архив считается священным объектом государства и охраняется сильнее, чем военные базы. Находится в самом центре, прямо от центрального моста.</p>
        </div>

        <div class="card">
            <h3>Имперский парламент</h3>
            <p>Монументальное здание из коричневого кирпича, мрамора и дуба. Архитектура подчёркивает преемственность и тяжесть власти.</p>
            <p>Особенность здания — каменный мостик, соединяющий острова, символ «перехода решений в судьбы».</p>
            
            <h4 style="margin-top: 2rem; color: #764ba2;">Материалы:</h4>
            <ul class="styled-list">
                <li>мрамор</li>
                <li>натуральное дерево</li>
                <li>дуб</li>
                <li>массивные мраморные колонны</li>
            </ul>
        </div>
    </section>

    <section class="section">
        <h2 class="section-title">🏗 Архитектура и облик города</h2>
        <div class="card">
            <p style="margin-bottom: 2rem;">Архитектурно Utopia построена на контрасте:</p>
            
            <div class="architecture-section">
                <div class="architecture-column">
                    <h4>Исторический центр</h4>
                    <p style="margin-bottom: 1.5rem; font-style: italic; color: #888;">(Находится на набережной)</p>
                    <ul class="styled-list">
                        <li>мраморные колонны</li>
                        <li>старинные дома</li>
                        <li>массивные фасады</li>
                        <li>строгая симметрия</li>
                    </ul>
                </div>

                <div class="architecture-column">
                    <h4>Современные районы</h4>
                    <p style="margin-bottom: 1.5rem; font-style: italic; color: #888;">(Вглубь к горам)</p>
                    <ul class="styled-list">
                        <li>плотная застройка небоскрёбами</li>
                        <li>вертикальные линии</li>
                        <li>стекло и металл</li>
                        <li>подчёркнутый масштаб и контроль</li>
                    </ul>
                </div>
            </div>

            <p style="margin-top: 2rem; font-size: 1.2rem; color: #764ba2; font-weight: 500;">Старые дома не сносятся — они встроены в новую структуру, создавая ощущение наслоения эпох.</p>
        </div>
    </section>

    <section class="section">
        <div class="highlight">
            <h3>Значение для Империи</h3>
            <p>Utopia — не просто столица.</p>
        </div>

        <div class="grid">
            <div class="feature-box">
                <h4>Административный центр</h4>
                <p>Место сосредоточения всей имперской власти и управления</p>
            </div>

            <div class="feature-box">
                <h4>Символ стабильности</h4>
                <p>Воплощение постоянства и могущества Империи</p>
            </div>

            <div class="feature-box">
                <h4>Инструмент пропаганды</h4>
                <p>Город, где Империя показывает своё «идеальное лицо»</p>
            </div>
        </div>

        <div class="card" style="margin-top: 3rem;">
            <p><strong>Для жителей других регионов</strong> Utopia — недосягаемый эталон, который ещё не достроен.</p>
            <p><strong>Для элит</strong> — место реальной власти.</p>
            <p><strong>Для истории</strong> — точка, где всё фиксируется и переписывается, точка невозврата, поворот истории, при котором исторический центр находится очень далеко.</p>
        </div>
    </section>
</div>

<footer class="imperial-footer">
    <div class="document-info">
        <div class="archive-mark">
            <div class="archive-title">АРХИВНАЯ МЕТКА</div>
            <div class="archive-details">
                <div class="archive-detail">
                    <strong>Документ №</strong> К-ХР-002
                </div>
                <div class="archive-detail">
                    <strong>Серия:</strong> Основные данные о городах
                </div>
                <div class="archive-detail">
                    <strong>Степень доступа:</strong> открытый
                </div>
                <div class="archive-detail">
                    <strong>Дата составления:</strong> 4129 год
                </div>
                <div class="archive-detail" style="grid-column: 1 / -1;">
                    <strong>Место хранения:</strong> Центральный Императорский Архив, Utopia
                </div>
            </div>

            <div class="signature-section">
                <div class="seal-container">
                    <div class="seal">
                        <div class="crown-symbol">👑</div>
                        <div class="seal-text">Империя<br>Karin</div>
                    </div>
                    <div class="seal">
                        <div class="chancellery-icon">
                            <div class="chancellery-building">
                                <div class="column"></div>
                                <div class="column"></div>
                                <div class="column"></div>
                                <div class="column"></div>
                            </div>
                            <div class="quill">
                                <div class="quill-detail"></div>
                            </div>
                        </div>
                        <div class="seal-text" style="margin-top: 0.5rem;">Имперская<br>Канцелярия</div>
                    </div>
                </div>

                <div class="signature">
                    <div class="signature-line">
                        <div class="emperor-signature">Augof Kronos</div>
                    </div>
                    <div class="signature-title">Император Империи Karin</div>
                </div>
            </div>
        </div>

        <div class="imperial-motto">
            Долгая жизнь Империи Karin
        </div>
    </div>
</footer>

<script>
    // Плавное появление секций при прокрутке
    const observerOptions = {
        threshold: 0.1,
        rootMargin: '0px 0px -100px 0px'
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('visible');
            }
        });
    }, observerOptions);

    document.querySelectorAll('.section').forEach(section => {
        observer.observe(section);
    });

    // Плавная прокрутка при клике на индикатор
    document.querySelector('.scroll-indicator').addEventListener('click', () => {
        window.scrollTo({
            top: window.innerHeight,
            behavior: 'smooth'
        });
    });

    // Particle Animation
    const canvas = document.getElementById('particleCanvas');
    const ctx = canvas.getContext('2d');

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    window.addEventListener('resize', () => {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
    });

    class Particle {
        constructor() {
            this.x = Math.random() * canvas.width;
            this.y = Math.random() * canvas.height;
            this.size = Math.random() * 3 + 1;
            this.speedX = Math.random() * 0.5 - 0.25;
            this.speedY = Math.random() * 0.5 - 0.25;
            
            // Purple to blue colors
            const colors = [
                'rgba(102, 126, 234, 0.3)',  // Blue
                'rgba(118, 75, 162, 0.3)',   // Purple
                'rgba(147, 112, 219, 0.3)',  // Medium purple
                'rgba(138, 151, 234, 0.3)'   // Light purple-blue
            ];
            this.color = colors[Math.floor(Math.random() * colors.length)];
        }

        update() {
            this.x += this.speedX;
            this.y += this.speedY;

            if (this.x > canvas.width) this.x = 0;
            if (this.x < 0) this.x = canvas.width;
            if (this.y > canvas.height) this.y = 0;
            if (this.y < 0) this.y = canvas.height;
        }

        draw() {
            ctx.fillStyle = this.color;
            ctx.beginPath();
            ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
            ctx.fill();
        }
    }

    // Create particles
    const particlesArray = [];
    const numberOfParticles = 100;

    for (let i = 0; i < numberOfParticles; i++) {
        particlesArray.push(new Particle());
    }

    function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        
        for (let i = 0; i < particlesArray.length; i++) {
            particlesArray[i].update();
            particlesArray[i].draw();
            
            // Connect particles
            for (let j = i; j < particlesArray.length; j++) {
                const dx = particlesArray[i].x - particlesArray[j].x;
                const dy = particlesArray[i].y - particlesArray[j].y;
                const distance = Math.sqrt(dx * dx + dy * dy);
                
                if (distance < 100) {
                    ctx.strokeStyle = `rgba(102, 126, 234, ${0.15 * (1 - distance / 100)})`;
                    ctx.lineWidth = 1;
                    ctx.beginPath();
                    ctx.moveTo(particlesArray[i].x, particlesArray[i].y);
                    ctx.lineTo(particlesArray[j].x, particlesArray[j].y);
                    ctx.stroke();
                }
            }
        }
        
        requestAnimationFrame(animate);
    }

    animate();

    // MeandEmp Page Functions
    function openMeandEmpPage() {
        document.getElementById('appPage').classList.add('active');
        document.body.style.overflow = 'hidden';
    }

    function closeMeandEmpPage() {
        document.getElementById('appPage').classList.remove('active');
        document.body.style.overflow = 'auto';
        // Scroll back to top of main page
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function toggleFeature(element) {
        element.classList.toggle('expanded');
    }
</script>
```

</body>
</html>
