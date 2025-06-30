<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Sahayak: Student & Counseling Portal</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>🤝</text></svg>">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">

    <style>
        body {
            font-family: 'Poppins', sans-serif; /* Modern and clean font */
            margin: 0;
            padding: 0;
            /* Richer, more sophisticated gradient */
            background: linear-gradient(135deg, #A8C0FF, #3F2B96); /* Light Blue to Deep Purple */
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-y: auto; /* Allow scrolling for smaller screens */
            color: #333; /* Default text color */
        }
        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            /* Subtle education-themed background image */
            background: url('https://cdn.pixabay.com/photo/2015/09/18/18/25/education-944504_960_720.jpg') no-repeat center center / cover;
            opacity: 0.08; /* Keep it very subtle */
            z-index: -1;
        }
        /* --- IMPORTANT CHANGE HERE: Unified Background Color for ALL .container elements and .login-box --- */
        .container, .login-box {
            max-width: 600px;
            width: 90%; /* Responsive width */
            margin: 40px auto;
            padding: 30px;
            background: #FDFDFD; /* <-- THIS IS THE UNIFIED, CONSISTENT COLOR FOR ALL SECTIONS */
            border-radius: 20px; /* More rounded corners */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.25); /* Stronger, more appealing shadow */
            animation: fadeIn 0.5s ease-out; /* Smooth fade-in effect */
        }
        /* --- END OF IMPORTANT CHANGE --- */

        .hidden { display: none; }
        h2, h3 {
            color: #2c3e50; /* Darker, more professional heading color */
            text-align: center;
            margin-bottom: 25px;
            font-weight: 700; /* Bolder headings */
        }

        /* --- General Input, Select, Textarea, Button Styles --- */
        input:not([type="radio"]),
        select,
        textarea {
            width: 100%;
            padding: 14px;
            margin: 10px 0;
            border: 1px solid #dcdcdc;
            border-radius: 10px; /* More rounded inputs */
            font-size: 16px;
            box-sizing: border-box;
            transition: all 0.3s ease;
        }
        input:not([type="radio"]):focus,
        select:focus,
        textarea:focus {
            border-color: #007bff;
            box-shadow: 0 0 8px rgba(0, 123, 255, 0.2);
            outline: none;
        }
        button {
            width: 100%;
            padding: 15px; /* Slightly more padding for better touch targets */
            margin: 12px 0;
            background: linear-gradient(to right, #007bff, #00c6ff); /* Standard button gradient */
            color: white;
            font-weight: 600; /* Bolder text */
            border: none;
            cursor: pointer;
            border-radius: 30px; /* Pill-shaped buttons */
            letter-spacing: 0.5px;
            box-shadow: 0 5px 15px rgba(0, 123, 255, 0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px; /* Space between icon and text */
            transition: all 0.3s ease;
        }
        button:hover {
            background: linear-gradient(to right, #0056b3, #0099cc);
            box-shadow: 0 7px 20px rgba(0, 123, 255, 0.4);
            transform: translateY(-2px); /* Slight lift on hover */
        }

        /* --- Dashboard Grid and Icon Button Styles --- */
        #dashboardPage .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(130px, 1fr)); /* Responsive grid, slightly larger min-width */
            gap: 25px; /* More space between grid items */
            margin-top: 30px;
            justify-items: center;
        }

        #dashboardPage .dashboard-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: linear-gradient(to bottom right, #4CAF50, #8BC34A); /* Green gradient for most items */
            color: white;
            padding: 25px 15px; /* Increased padding */
            border-radius: 18px; /* Nicely rounded corners */
            cursor: pointer;
            box-shadow: 0 6px 15px rgba(0,0,0,0.15); /* Stronger shadow */
            transition: all 0.3s ease;
            text-decoration: none;
            width: 100%;
            box-sizing: border-box;
            text-align: center; /* Center text within the item */
        }

        #dashboardPage .dashboard-item.counseling-item {
            background: linear-gradient(to bottom right, #FFD700, #FFA500); /* Gold/Orange for counseling */
        }

        #dashboardPage .dashboard-item.feedback-item {
            background: linear-gradient(to bottom right, #8A2BE2, #A020F0); /* Purple for Feedback */
        }
        #dashboardPage .dashboard-item.events-item {
            background: linear-gradient(to bottom right, #00BFFF, #1E90FF); /* Sky Blue for Events */
        }
        #dashboardPage .dashboard-item.faq-item {
            background: linear-gradient(to bottom right, #FF69B4, #FF1493); /* Hot Pink for FAQ */
        }

        /* --- IMPORTANT CHANGE HERE: Logout Button Positioning --- */
        #logoutButton {
            position: absolute; /* Position relative to the dashboard container */
            bottom: 20px; /* From the bottom */
            left: 20px; /* From the left */
            width: auto; /* Allow width to be determined by content */
            padding: 10px 20px; /* Smaller padding */
            font-size: 0.9em; /* Smaller font size */
            background: linear-gradient(to right, #FF5722, #F44336); /* Red/Orange gradient */
            border-radius: 20px; /* More rounded, pill shape */
            box-shadow: 0 3px 8px rgba(255, 87, 34, 0.3);
            z-index: 10; /* Ensure it's above other elements if needed */
            display: flex; /* Flexbox for icon and text */
            align-items: center;
            gap: 5px; /* Small gap between icon and text */
        }

        #logoutButton:hover {
            background: linear-gradient(to right, #e64a19, #d32f2f);
            box-shadow: 0 5px 12px rgba(255, 87, 34, 0.4);
            transform: translateY(-2px);
        }
        /* Hide the old logout dashboard item */
        #dashboardPage .dashboard-item.logout-item {
            display: none;
        }
        /* Adjust dashboardPage container to allow absolute positioning for logout button */
        #dashboardPage.container {
            position: relative; /* This is crucial for positioning #logoutButton */
            padding-bottom: 70px; /* Make space for the logout button at the bottom */
        }

        /* --- END OF IMPORTANT CHANGE --- */

        #dashboardPage .dashboard-item:hover {
            transform: translateY(-7px); /* More pronounced lift effect */
            box-shadow: 0 10px 20px rgba(0,0,0,0.25);
        }

        #dashboardPage .dashboard-item .icon-symbol {
            font-size: 4.5em; /* Even larger icons */
            margin-bottom: 12px;
            line-height: 1;
        }

        #dashboardPage .dashboard-item .item-name {
            font-weight: 700; /* Extra bold text */
            font-size: 1.2em; /* Larger text */
        }

        /* --- Chatbot Specific Styles --- */
        .chat-log { /* Replaced #chatLog with a class for reusability */
            height: 280px; /* Taller chat log */
            overflow-y: auto;
            background: #eef2f7; /* Very light blue background for chat */
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 15px;
            font-family: 'Roboto Mono', monospace; /* Monospace for code-like chat */
            border: 1px solid #d4e0ed;
            box-shadow: inset 0 1px 4px rgba(0,0,0,0.08);
            display: flex;
            flex-direction: column;
        }
        .chat-message {
            padding: 10px 15px;
            border-radius: 20px; /* Bubble-like roundedness */
            margin: 8px 0; /* More spacing between bubbles */
            max-width: 85%; /* Max width for bubbles */
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            line-height: 1.5;
            word-wrap: break-word; /* Ensure long words wrap */
        }
        .chat-message.user {
            background-color: #cceeff; /* Lighter blue for user bubbles */
            align-self: flex-end;
            margin-left: auto;
            color: #004085; /* Darker blue text */
        }
        .chat-message.ai {
            background-color: #f7f7f7; /* Off-white for AI bubbles */
            align-self: flex-start;
            margin-right: auto;
            color: #4a4a4a; /* Dark gray text */
        }
        .chat-message strong {
            font-weight: 700;
        }
        #aiIcon {
            position: fixed;
            bottom: 30px; /* Slightly higher */
            right: 30px; /* Slightly inward */
            font-size: 38px; /* Larger icon */
            cursor: pointer;
            background: linear-gradient(to right, #6A11CB, #2575FC); /* Vibrant purple-blue gradient */
            color: white;
            width: 65px; /* Larger circular button */
            height: 65px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            box-shadow: 0 8px 20px rgba(0,0,0,0.3);
            transition: all 0.3s ease;
            z-index: 1000; /* Ensure it's on top */
        }
        #aiIcon:hover {
            transform: scale(1.15); /* More pronounced hover effect */
            box-shadow: 0 12px 25px rgba(0,0,0,0.4);
        }
        #floatingChat {
            position: fixed;
            bottom: 110px; /* Position above the icon */
            right: 30px;
            width: 380px; /* Wider chat window */
            background: white;
            border-radius: 25px; /* More rounded chat window */
            box-shadow: 0 12px 30px rgba(0,0,0,0.3);
            display: none;
            flex-direction: column;
            padding: 25px; /* More padding */
            z-index: 999;
            opacity: 0;
            transform: translateY(20px);
            animation: slideInChat 0.4s forwards ease-out; /* Smoother animation */
        }
        @keyframes slideInChat {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        #floatingChat h3 {
            margin-top: 0;
            margin-bottom: 20px;
            color: #3f2b96; /* Matching heading color */
            font-size: 1.5em;
        }
        #floatingChat button {
            margin-top: 15px;
            background: linear-gradient(to right, #6A11CB, #2575FC); /* Matching AI icon gradient */
            box-shadow: 0 4px 10px rgba(106, 17, 203, 0.3);
        }
        #floatingChat button:hover {
            background: linear-gradient(to right, #5A0FAD, #1C5EC7);
            box-shadow: 0 6px 15px rgba(106, 17, 203, 0.4);
        }


        /* --- Login Box Styles (Integrated with .container for unified background) --- */
        .login-box {
            padding: 45px 35px; /* More padding */
            border-radius: 20px; /* More rounded */
            text-align: center;
            width: 400px; /* Slightly wider login box */
            margin: auto;
            margin-top: 80px; /* Adjusted top margin */
        }
        /* SAHAYAK Logo Customization */
        .logo {
            font-family: 'Poppins', sans-serif; /* Ensuring Poppins is used */
            font-size: 48px; /* Even larger logo text */
            font-weight: 900; /* Extra Black/Heavy weight */
            margin-bottom: 35px;
            color: #3F2B96; /* Deep purple matching gradient */
            text-shadow: 3px 3px 6px rgba(0,0,0,0.15); /* More prominent text shadow */
            letter-spacing: 2px; /* Spacing out letters for better look */
        }
        .login-box input, .login-box button {
            margin-bottom: 20px; /* More space between fields/buttons */
        }
        .login-box button {
            background: linear-gradient(to right, #3897f0, #56c2ff);
            box-shadow: 0 5px 15px rgba(56, 151, 240, 0.3);
        }
        .login-box button:hover {
            background: linear-gradient(to right, #2c7ac9, #429edd);
            box-shadow: 0 7px 20px rgba(56, 151, 240, 0.4);
        }
        .signup-link {
            margin-top: 25px; /* More space */
            font-size: 16px;
            color: #555;
        }
        .signup-link a {
            color: #3897f0;
            text-decoration: none;
            font-weight: 600; /* Bolder link text */
        }
        .signup-link a:hover {
            text-decoration: underline;
        }

        /* --- Quiz Specific Styles --- */
        .quiz-question {
            margin-bottom: 30px; /* More space between questions */
            padding-bottom: 25px;
            border-bottom: 1px dashed #e0e0e0; /* Finer dashed line */
        }

        .quiz-question p {
            font-weight: 600;
            margin-bottom: 20px;
            color: #333;
            font-size: 20px; /* Larger question text */
            line-height: 1.4;
        }

        .quiz-question label {
            display: flex;
            align-items: center;
            margin-bottom: 15px; /* More space between options */
            padding: 16px 20px; /* More padding */
            font-size: 17px;
            cursor: pointer;
            border-radius: 12px; /* More rounded labels */
            background-color: #fcfcfc;
            border: 1px solid #e5e5e5;
            transition: all 0.2s ease;
            box-sizing: border-box;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
        }

        .quiz-question label:hover {
            background-color: #f0f8ff;
            border-color: #a7d9ff;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }

        .quiz-question input[type="radio"] {
            width: 24px; /* Larger radio button */
            height: 24px;
            min-width: 24px;
            margin: 0 18px 0 0; /* More space */
            flex-shrink: 0;
            appearance: none;
            border: 2px solid #999;
            border-radius: 50%;
            outline: none;
            cursor: pointer;
            position: relative;
            transition: all 0.2s ease;
        }

        .quiz-question input[type="radio"]:checked {
            background-color: #007bff;
            border-color: #007bff;
            box-shadow: 0 0 0 5px rgba(0, 123, 255, 0.3); /* Larger shadow */
        }

        .quiz-question input[type="radio"]:checked::before {
            content: '';
            display: block;
            width: 12px; /* Larger inner circle */
            height: 12px;
            background-color: white;
            border-radius: 50%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        /* Style for correct/incorrect answers after submission */
        .quiz-question label.correct {
            background-color: #e8ffee;
            border-color: #28a745;
            box-shadow: 0 2px 8px rgba(40, 167, 69, 0.15);
        }
        .quiz-question label.incorrect {
            background-color: #ffeeee;
            border-color: #dc3545;
            box-shadow: 0 2px 8px rgba(220, 53, 69, 0.15);
        }
        .quiz-question label.correct-highlight {
            background-color: #d4edda;
            border-color: #28a745;
            font-weight: 500;
        }

        /* Disable styling for disabled radio buttons */
        .quiz-question input[type="radio"]:disabled {
            cursor: not-allowed;
            opacity: 0.6;
        }
        .quiz-question input[type="radio"]:disabled + span {
            opacity: 0.8;
            cursor: not-allowed;
        }

        #scoreDisplay {
            font-size: 22px; /* Larger score display */
            color: #3F2B96;
            padding: 12px;
            border-radius: 10px;
            background-color: #e9f5ff;
            border: 1px solid #cceeff;
            margin-top: 30px; /* More margin */
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
            font-weight: 600;
        }

        #performanceSummary {
            font-size: 19px;
            color: #333;
            line-height: 1.7;
            text-align: center;
            padding: 25px;
            background-color: #f0faff;
            border-radius: 18px;
            border: 1px dashed #c0e0ff;
            box-shadow: 0 3px 12px rgba(0,0,0,0.1);
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Specific styles for Counseling Chat */
        #counselingChatLog {
            height: 250px;
            overflow-y: auto;
            background: #fdfdfd;
            padding: 15px;
            border-radius: 12px;
            margin-top: 20px;
            margin-bottom: 15px;
            border: 1px solid #e0e0e0;
            display: flex;
            flex-direction: column;
            box-shadow: inset 0 1px 3px rgba(0,0,0,0.05);
        }
        #counselingChatInput {
            margin-bottom: 15px;
        }
        /* New Counseling Features */
        .counseling-options {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
            gap: 15px;
            margin-top: 20px;
            margin-bottom: 25px;
        }
        .counseling-options button {
            background: linear-gradient(to right, #007bff, #00c6ff);
            color: white;
            padding: 12px;
            border-radius: 25px;
            font-size: 0.95em;
            font-weight: 500;
            box-shadow: 0 3px 8px rgba(0, 123, 255, 0.2);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            width: auto; /* Allow content to determine width */
        }
        .counseling-options button:hover {
            background: linear-gradient(to right, #0056b3, #0099cc);
            box-shadow: 0 5px 12px rgba(0, 123, 255, 0.3);
            transform: translateY(-2px);
        }
        .counseling-options button i {
            font-size: 1.1em;
        }
        #counselorProfiles {
            margin-top: 25px;
            border-top: 1px dashed #e0e0e0;
            padding-top: 20px;
        }
        .counselor-profile {
            background-color: #f9f9f9;
            border: 1px solid #e0e0e0;
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
        }
        .counselor-profile img {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #007bff;
        }
        .counselor-details h4 {
            margin: 0 0 5px 0;
            color: #3F2B96;
            font-size: 1.15em;
        }
        .counselor-details p {
            margin: 0 0 3px 0;
            font-size: 0.9em;
            color: #555;
        }
        .counselor-details .expertise {
            font-weight: 600;
            color: #007bff;
        }
        .counselor-profile button {
            background: linear-gradient(to right, #28a745, #218838);
            width: auto;
            padding: 8px 15px;
            font-size: 0.85em;
            border-radius: 20px;
            margin-top: 10px;
            box-shadow: 0 2px 5px rgba(40, 167, 69, 0.2);
        }
        .counselor-profile button:hover {
            background: linear-gradient(to right, #218838, #1e7e34);
            transform: translateY(-1px);
        }


        /* Events Section Styles */
        .event-item {
            background-color: #f9f9f9;
            border: 1px solid #e0e0e0;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        .event-item h4 {
            color: #3F2B96;
            margin-top: 0;
            margin-bottom: 8px;
            font-size: 1.2em;
        }
        .event-item p {
            font-size: 0.9em;
            color: #555;
            margin-bottom: 5px;
        }
        .event-item a {
            color: #007bff;
            text-decoration: none;
            font-weight: 500;
        }
        .event-item a:hover {
            text-decoration: underline;
        }

        /* FAQ Section Styles */
        .faq-item {
            margin-bottom: 15px;
            padding: 10px 0;
            border-bottom: 1px dashed #eee;
        }
        .faq-question {
            font-weight: 600;
            color: #2c3e50;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            background-color: #f5f5f5;
            border-radius: 8px;
            transition: background-color 0.3s ease;
        }
        .faq-question:hover {
            background-color: #e9e9e9;
        }
        .faq-answer {
            display: none;
            padding: 10px 15px;
            margin-top: 5px;
            background-color: #fefefe;
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            font-size: 0.95em;
            line-height: 1.5;
            color: #444;
        }
        .faq-question.active + .faq-answer {
            display: block;
        }
        .faq-arrow {
            transition: transform 0.3s ease;
        }
        .faq-question.active .faq-arrow {
            transform: rotate(90deg);
        }

        /* Feedback Section Styles */
        .rating-stars {
            text-align: center;
            margin-bottom: 20px;
        }
        .rating-stars .star {
            font-size: 2.5em;
            color: #ccc;
            cursor: pointer;
            transition: color 0.2s;
        }
        .rating-stars .star.selected,
        .rating-stars .star:hover {
            color: #FFD700; /* Gold */
        }
        #feedbackMessage {
            margin-top: 15px;
            font-size: 0.9em;
            color: #555;
            text-align: center;
        }

        /* --- NEW STYLES FOR PATH FINDER CARDS --- */
        #pathFinderPage .interest-cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); /* Responsive columns */
            gap: 20px; /* Space between cards */
            margin-top: 25px;
            margin-bottom: 30px;
            justify-content: center; /* Center the grid items */
        }

        #pathFinderPage .interest-card {
            background: linear-gradient(135deg, #f0f4f8, #e0e6ec); /* Light, subtle gradient */
            border-radius: 15px;
            padding: 25px 20px;
            text-align: center;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1); /* Deeper shadow */
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            border: 1px solid #d0d8e0; /* Subtle border */
        }

        #pathFinderPage .interest-card:hover {
            transform: translateY(-8px) scale(1.03); /* Lift and slight scale */
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2); /* More pronounced shadow */
            background: linear-gradient(135deg, #e0e6ec, #d0d8e0); /* Darker on hover */
        }

        #pathFinderPage .interest-card .icon-large {
            font-size: 4em; /* Large icon */
            margin-bottom: 15px;
            line-height: 1;
            color: #3F2B96; /* Consistent deep purple color */
            transition: color 0.3s ease;
        }

        #pathFinderPage .interest-card:hover .icon-large {
            color: #007bff; /* Change color on hover */
        }

        #pathFinderPage .interest-card .card-title {
            font-size: 1.3em;
            font-weight: 700;
            color: #2c3e50; /* Dark heading color */
            margin-bottom: 0;
        }

        /* Pulse animation for selected card */
        @keyframes pulse {
            0% { transform: scale(1); box-shadow: 0 10px 25px rgba(0, 123, 255, 0.3); }
            50% { transform: scale(1.02); box-shadow: 0 12px 30px rgba(0, 123, 255, 0.4); }
            100% { transform: scale(1); box-shadow: 0 10px 25px rgba(0, 123, 255, 0.3); }
        }

        #pathFinderPage .interest-card.selected-card {
            border: 3px solid #007bff; /* Blue border for selected */
            background: linear-gradient(135deg, #e6f7ff, #cceeff); /* Lighter blue background when selected */
            box-shadow: 0 10px 25px rgba(0, 123, 255, 0.3); /* Stronger blue shadow */
            transform: translateY(-4px); /* Slightly lifted when selected */
            animation: pulse 0.6s ease-out; /* Apply pulse animation */
        }

        /* Styles for study materials */
        #studyMaterialsPage #subjectSelect {
            width: 100%;
            padding: 12px;
            margin-bottom: 20px;
            border: 1px solid #dcdcdc;
            border-radius: 10px;
            font-size: 16px;
            box-sizing: border-box;
            transition: all 0.3s ease;
            background-color: #fcfcfc;
        }
        #studyMaterialsPage #subjectSelect:focus {
            border-color: #007bff;
            box-shadow: 0 0 8px rgba(0, 123, 255, 0.2);
            outline: none;
        }

        #studyMaterialsPage #studyContent {
            list-style: none; /* Remove default list bullets */
            padding: 0;
            margin-top: 20px; /* Space from dropdown/button */
        }

        #studyMaterialsPage #studyContent li {
            background-color: #f9f9f9;
            border: 1px solid #e0e0e0;
            border-radius: 12px;
            padding: 18px 20px;
            margin-bottom: 15px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.07);
            display: flex;
            align-items: flex-start;
            gap: 15px;
            transition: transform 0.2s ease;
        }

        #studyMaterialsPage #studyContent li:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0,0,0,0.1);
        }

        #studyMaterialsPage #studyContent li .material-icon {
            font-size: 2.2em; /* Larger icon */
            color: #3F2B96; /* Matching theme color */
            flex-shrink: 0;
            margin-top: 5px; /* Align icon slightly */
        }

        #studyMaterialsPage #studyContent li .material-details {
            flex-grow: 1;
        }

        #studyMaterialsPage #studyContent li h4 {
            margin: 0 0 8px 0;
            font-size: 1.15em;
            color: #2c3e50;
            text-align: left; /* Align title left */
        }

        #studyMaterialsPage #studyContent li h4 a {
            text-decoration: none;
            color: #007bff; /* Link color */
            transition: color 0.2s ease;
        }

        #studyMaterialsPage #studyContent li h4 a:hover {
            color: #0056b3;
            text-decoration: underline;
        }

        #studyMaterialsPage #studyContent li p {
            margin: 0;
            font-size: 0.9em;
            color: #666;
            line-height: 1.5;
        }

        #loadingIndicator {
            text-align: center;
            margin-top: 20px;
            font-size: 1.1em;
            color: #007bff;
            font-weight: 600;
            display: none; /* Hidden by default */
        }
    </style>
</head>
<body>

<div id="loginPage">
    <div class="login-box">
        <h1 class="logo">SAHAYAK</h1>
        <input type="text" id="username" placeholder="👤 Username" />
        <input type="password" id="password" placeholder="🔒 Password" />
        <button onclick="login()"><i class="fas fa-sign-in-alt"></i> Log In</button>
        <p class="signup-link">Don’t have an account? <a onclick="showSection('signupPage')">Sign up</a></p>
        <p class="signup-link"><a onclick="showSection('forgotPage')">Forgot Password?</a></p>
    </div>
</div>

<div class="container hidden" id="signupPage">
    <h2>Create Account</h2>
    <input type="text" id="newUsername" placeholder="✨ Choose a username" />
    <input type="password" id="newPassword" placeholder="🔐 Choose a password" />
    <button onclick="signup()"><i class="fas fa-user-plus"></i> Sign Up</button>
    <button onclick="showSection('loginPage')"><i class="fas fa-arrow-left"></i> Back to Login</button>
</div>

<div class="container hidden" id="forgotPage">
    <h2>Forgot Password</h2>
    <p>Please contact support or try remembering your credentials.</p>
    <button onclick="showSection('loginPage')"><i class="fas fa-arrow-left"></i> Back to Login</button>
</div>


<div class="container hidden" id="dashboardPage">
    <h2>SAHAYAK Dashboard</h2>
    <div class="dashboard-grid">
        <a class="dashboard-item" onclick="showSection('pathFinderPage')">
            <span class="icon-symbol">🧭</span>
            <span class="item-name">Path Finder</span>
        </a>
        <a class="dashboard-item" onclick="showSection('studyMaterialsPage')">
            <span class="icon-symbol">📚</span>
            <span class="item-name">Study Materials</span>
        </a>
        <a class="dashboard-item" onclick="showSection('assignmentsPage')">
            <span class="icon-symbol">📝</span>
            <span class="item-name">Assignments</span>
        </a>
        <a class="dashboard-item" onclick="showSection('notesPage')">
            <span class="icon-symbol">🗒️</span>
            <span class="item-name">Notes</span>
        </a>
        <a class="dashboard-item" onclick="showSection('performancePage')">
            <span class="icon-symbol">📊</span>
            <span class="item-name">Performance</span>
        </a>
        <a class="dashboard-item counseling-item" onclick="showSection('counselingPage')">
            <span class="icon-symbol">🤝</span>
            <span class="item-name">Counseling</span>
        </a>
        <a class="dashboard-item events-item" onclick="showSection('eventsPage')">
            <span class="icon-symbol">🗓️</span>
            <span class="item-name">Events</span>
        </a>
        <a class="dashboard-item faq-item" onclick="showSection('faqPage')">
            <span class="icon-symbol">❓</span>
            <span class="item-name">FAQs</span>
        </a>
        <a class="dashboard-item feedback-item" onclick="showSection('feedbackPage')">
            <span class="icon-symbol">🌟</span>
            <span class="item-name">Feedback</span>
        </a>
    </div>
    <button id="logoutButton" onclick="logout()">
        <i class="fas fa-sign-out-alt"></i> Logout
    </button>
</div>

<div class="container hidden" id="pathFinderPage">
    <h3>Path Finder: Explore Your Future</h3>
    <p style="text-align: center; color: #555; margin-bottom: 30px;">Choose an interest area to find relevant study materials and resources.</p>
    <div class="interest-cards-grid">
        <div class="interest-card" data-interest="tech" onclick="selectInterest(this, 'tech')">
            <span class="icon-large">💻</span>
            <span class="card-title">Technology</span>
        </div>
        <div class="interest-card" data-interest="medicine" onclick="selectInterest(this, 'medicine')">
            <span class="icon-large">⚕️</span>
            <span class="card-title">Medicine</span>
        </div>
        <div class="interest-card" data-interest="commerce" onclick="selectInterest(this, 'commerce')">
            <span class="icon-large">💰</span>
            <span class="card-title">Commerce</span>
        </div>
        <div class="interest-card" data-interest="arts" onclick="selectInterest(this, 'arts')">
            <span class="icon-large">🎨</span>
            <span class="card-title">Arts & Humanities</span>
        </div>
        <div class="interest-card" data-interest="science" onclick="selectInterest(this, 'science')">
            <span class="icon-large">🔬</span>
            <span class="card-title">Pure Science</span>
        </div>
        <div class="interest-card" data-interest="business" onclick="selectInterest(this, 'business')">
            <span class="icon-large">💼</span>
            <span class="card-title">Business & Finance</span>
        </div>
    </div>
    <button onclick="loadSubjectDropdown()" id="getPathFinderMaterialsBtn"><i class="fas fa-search"></i> Find Subjects</button>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back</button>
</div>

<div class="container hidden" id="studyMaterialsPage">
    <h3>Study Materials</h3>
    <p id="loadingIndicator">Loading subjects...</p>
    <div id="subjectSelectionArea" class="hidden">
        <p style="text-align: center; color: #555; margin-bottom: 15px;">Select a subject to view materials:</p>
        <select id="subjectSelect" onchange="loadSubjectMaterials(this.value)"></select>
    </div>
    <ul id="studyContent"></ul>
    <button onclick="showSection('assignmentsPage')"><i class="fas fa-question-circle"></i> Go to Quiz</button>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back</button>
</div>

<div class="container hidden" id="assignmentsPage">
    <h3>Quiz</h3>
    <ol id="quizContent"></ol>
    <button onclick="submitQuiz()" style="margin-top: 20px;"><i class="fas fa-check-circle"></i> Submit Quiz</button>
    <p id="scoreDisplay" style="text-align: center; font-weight: bold; margin-top: 15px;"></p>
    <button onclick="showSection('performancePage')"><i class="fas fa-chart-line"></i> See Performance</button>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back</button>
</div>

<div class="container hidden" id="notesPage">
    <h3>Your Notes</h3>
    <textarea id="userNotes" rows="6" placeholder="✍️ Write your notes here..."></textarea>
    <button onclick="saveNotes()"><i class="fas fa-save"></i> Save</button>
    <p id="savedNotes"></p>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back</button>
</div>

<div class="container hidden" id="performancePage">
    <h3>Performance</h3>
    <p id="performanceSummary">Your result will show here.</p>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back</button>
</div>

<div class="container hidden" id="counselingPage">
    <h3>SAHAYAK: Your Wellbeing Hub</h3>
    <p>Welcome! Our AI can provide initial guidance, and you can also explore resources and connect with professionals.</p>
    <div id="counselingChatLog" class="chat-log">
        <div class="chat-message ai"><strong>AI:</strong> Hi there! What's on your mind today? Are you facing academic stress, career confusion, or just need someone to talk to?</div>
    </div>
    <input type="text" id="counselingChatInput" placeholder="Tell me what you're going through..." onkeydown="if(event.key==='Enter') sendChatMessage('counselingChatInput', 'counselingChatLog', 'counseling')">
    <button onclick="sendChatMessage('counselingChatInput', 'counselingChatLog', 'counseling')"><i class="fas fa-comment-dots"></i> Get AI Guidance</button>
    <p style="margin-top: 20px; text-align: center; font-size: 0.9em; color: #555;"> *Remember, this AI provides general guidance. For personal and in-depth support, consult a human counselor.* </p>
    <hr style="margin: 30px 0; border: 0; border-top: 1px dashed #e0e0e0;">
    <h4 style="text-align: center; margin-bottom: 20px;">Explore Counseling Options</h4>
    <div class="counseling-options">
        <button onclick="showCounselingType('academic')"><i class="fas fa-book-open"></i> Academic Support</button>
        <button onclick="showCounselingType('career')"><i class="fas fa-briefcase"></i> Career Guidance</button>
        <button onclick="showCounselingType('personal')"><i class="fas fa-heart"></i> Personal Wellbeing</button>
        <button onclick="showCounselingType('stress')"><i class="fas fa-brain"></i> Stress Management</button>
    </div>
    <div id="counselorProfiles">
        <h4 style="text-align: center; margin-bottom: 20px;">Recommended Counselors</h4>
        <p style="text-align: center; color: #777;">Select an option above to see specialized counselors.</p>
    </div>
    <button onclick="showSection('dashboardPage')" style="margin-top: 30px;"><i class="fas fa-arrow-left"></i> Back to Dashboard</button>
</div>

<div class="container hidden" id="eventsPage">
    <h3>Events & Workshops</h3>
    <p>Stay updated with upcoming events, workshops, and opportunities!</p>
    <div class="event-item">
        <h4>FutureTech Summit 2025</h4>
        <p><strong>Date:</strong> July 20, 2025</p>
        <p><strong>Time:</strong> 10:00 AM - 4:00 PM</p>
        <p><strong>Venue:</strong> Online (Zoom)</p>
        <p>Join experts from the tech industry for insights into AI, Data Science, and Web3.</p>
        <a href="#" target="_blank"><i class="fas fa-external-link-alt"></i> Register Here</a>
    </div>
    <div class="event-item">
        <h4>Career Guidance Workshop</h4>
        <p><strong>Date:</strong> August 5, 2025</p>
        <p><strong>Time:</strong> 2:00 PM - 5:00 PM</p>
        <p><strong>Venue:</strong> College Auditorium</p>
        <p>Explore various career paths and learn resume building tips.</p>
        <a href="#" target="_blank"><i class="fas fa-external-link-alt"></i> Register Here</a>
    </div>
    <div class="event-item">
        <h4>Mindfulness for Students Session</h4>
        <p><strong>Date:</strong> September 10, 2025</p>
        <p><strong>Time:</strong> 11:00 AM - 12:30 PM</p>
        <p><strong>Venue:</strong> Virtual Classroom</p>
        <p>Learn practical techniques to manage stress and improve focus.</p>
        <a href="#" target="_blank"><i class="fas fa-external-link-alt"></i> Join Session</a>
    </div>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back to Dashboard</button>
</div>

<div class="container hidden" id="faqPage">
    <h3>FAQs & Support</h3>
    <p>Find answers to common questions or submit a support request.</p>
    <div class="faq-item">
        <div class="faq-question" onclick="toggleFAQ(this)">
            How do I log in? <span class="faq-arrow">▶</span>
        </div>
        <div class="faq-answer">
            You can log in using the username and password you created during registration. If you forgot your password, use the "Forgot Password" link.
        </div>
    </div>
    <div class="faq-item">
        <div class="faq-question" onclick="toggleFAQ(this)">
            Where can I find study materials? <span class="faq-arrow">▶</span>
        </div>
        <div class="faq-answer">
            Study materials are available in the "Study Materials" section of your dashboard. You can select your interest area to find relevant content.
        </div>
    </div>
    <div class="faq-item">
        <div class="faq-question" onclick="toggleFAQ(this)">
            How can I get counseling support? <span class="faq-arrow">▶</span>
        </div>
        <div class="faq-answer">
            Navigate to the "Counseling" section on your dashboard. You can chat with our AI for initial guidance or explore recommended human counselors based on your needs.
        </div>
    </div>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back to Dashboard</button>
</div>

<div class="container hidden" id="feedbackPage">
    <h3>Feedback</h3>
    <p style="text-align: center; margin-bottom: 25px;">We'd love to hear your thoughts! Rate your experience:</p>
    <div class="rating-stars">
        <span class="star" data-value="1" onclick="rateApp(1)">★</span>
        <span class="star" data-value="2" onclick="rateApp(2)">★</span>
        <span class="star" data-value="3" onclick="rateApp(3)">★</span>
        <span class="star" data-value="4" onclick="rateApp(4)">★</span>
        <span class="star" data-value="5" onclick="rateApp(5)">★</span>
    </div>
    <textarea id="feedbackText" rows="4" placeholder="Share your feedback here..."></textarea>
    <button onclick="submitFeedback()"><i class="fas fa-paper-plane"></i> Submit Feedback</button>
    <p id="feedbackMessage"></p>
    <button onclick="showSection('dashboardPage')"><i class="fas fa-arrow-left"></i> Back to Dashboard</button>
</div>

<div id="aiIcon" onclick="toggleFloatingChat()">
    <i class="fas fa-robot"></i>
</div>

<div id="floatingChat" class="container hidden">
    <h3>SAHAYAK AI Chatbot</h3>
    <div id="chatLog" class="chat-log">
        <div class="chat-message ai"><strong>AI:</strong> Hello! How can I help you today?</div>
    </div>
    <input type="text" id="chatInput" placeholder="Type your message..." onkeydown="if(event.key==='Enter') sendChatMessage('chatInput', 'chatLog', 'general')">
    <button onclick="sendChatMessage('chatInput', 'chatLog', 'general')"><i class="fas fa-comment-dots"></i> Send</button>
    <button onclick="toggleFloatingChat()"><i class="fas fa-times-circle"></i> Close Chat</button>
</div>

<script>
    // Global state variables
    let users = JSON.parse(localStorage.getItem('users')) || {};
    let currentUser = localStorage.getItem('currentUser') || null;
    let userNotes = JSON.parse(localStorage.getItem('userNotes')) || {}; // Initialize as an object for multiple users
    let quizScores = JSON.parse(localStorage.getItem('quizScores')) || {}; // Store quiz scores per user
    let selectedPathFinderInterest = null; // New global variable to store selected interest
    let selectedSubjectForQuiz = null; // NEW: Global variable to store the selected subject for the quiz

    // --- Core Navigation Function ---
    function showSection(id) {
        document.querySelectorAll('.container').forEach(section => {
            section.classList.add('hidden');
        });
        document.getElementById('loginPage').classList.add('hidden'); // Ensure login page is hidden too
        document.getElementById(id).classList.remove('hidden');

        // Special handling for dashboard and notes on section change
        if (id === 'dashboardPage') {
            document.getElementById('aiIcon').style.display = 'flex'; // Show AI icon on dashboard
        } else {
            document.getElementById('aiIcon').style.display = 'none'; // Hide AI icon on other pages
            document.getElementById('floatingChat').classList.add('hidden'); // Hide floating chat when navigating away
            document.getElementById('floatingChat').style.opacity = 0; // Reset animation
            document.getElementById('floatingChat').style.transform = 'translateY(20px)'; // Reset animation
        }

        if (id === 'notesPage' && currentUser) {
            document.getElementById('userNotes').value = userNotes[currentUser] || ''; // Load notes for current user
            document.getElementById('savedNotes').innerText = userNotes[currentUser] ? 'Notes loaded.' : '';
        } else if (id === 'notesPage' && !currentUser) {
            // If somehow on notes page without user, redirect to login
            showSection('loginPage');
            alert('Please log in to access your notes.');
        }

        if (id === 'assignmentsPage') {
            loadQuiz(); // Load quiz when assignments page is shown
        }
        if (id === 'performancePage' && currentUser) {
            displayPerformance();
        }

        // Reset Path Finder selection when entering the page
        if (id === 'pathFinderPage') {
            resetPathFinderSelection();
        }
        // Reset study materials page
        if (id === 'studyMaterialsPage') {
            document.getElementById('subjectSelectionArea').classList.add('hidden');
            document.getElementById('subjectSelect').innerHTML = '';
            document.getElementById('studyContent').innerHTML = '';
            document.getElementById('loadingIndicator').innerText = 'Loading subjects...';
            document.getElementById('loadingIndicator').style.display = 'none';
        }
    }

    // --- Authentication Functions ---
    function login() {
        const usernameInput = document.getElementById('username');
        const passwordInput = document.getElementById('password');
        const username = usernameInput.value;
        const password = passwordInput.value;

        if (users[username] && users[username].password === password) {
            currentUser = username;
            localStorage.setItem('currentUser', currentUser);
            showSection('dashboardPage');
            alert('Login successful!');
        } else {
            alert('Invalid username or password.');
        }
    }

    function signup() {
        const newUsernameInput = document.getElementById('newUsername');
        const newPasswordInput = document.getElementById('newPassword');
        const newUsername = newUsernameInput.value;
        const newPassword = newPasswordInput.value;

        if (newUsername.length < 3 || newPassword.length < 6) {
            alert('Username must be at least 3 characters and password at least 6 characters.');
            return;
        }
        if (users[newUsername]) {
            alert('Username already exists. Please choose another.');
            return;
        }

        users[newUsername] = { password: newPassword, score: 0 }; // Initialize score for new user
        localStorage.setItem('users', JSON.stringify(users));
        alert('Account created successfully! Please log in.');
        showSection('loginPage');
        newUsernameInput.value = '';
        newPasswordInput.value = '';
    }

    function logout() {
        currentUser = null;
        localStorage.removeItem('currentUser');
        alert('Logged out successfully.');
        showSection('loginPage');
    }

    // --- AI Chatbot Functions (Generalized) ---
    function toggleFloatingChat() {
        const floatingChat = document.getElementById('floatingChat');
        if (floatingChat.classList.contains('hidden')) {
            floatingChat.classList.remove('hidden');
            floatingChat.style.opacity = 0; // Start hidden for animation
            floatingChat.style.transform = 'translateY(20px)'; // Start offset for animation
            setTimeout(() => {
                floatingChat.style.transition = 'opacity 0.4s ease-out, transform 0.4s ease-out';
                floatingChat.style.opacity = 1;
                floatingChat.style.transform = 'translateY(0)';
            }, 10); // Small delay to ensure transition applies
        } else {
            floatingChat.style.opacity = 0;
            floatingChat.style.transform = 'translateY(20px)';
            floatingChat.addEventListener('transitionend', function handler() {
                floatingChat.classList.add('hidden');
                floatingChat.removeEventListener('transitionend', handler);
            }, { once: true });
        }
    }

    function sendChatMessage(inputElementId, chatLogElementId, context) {
        const chatInput = document.getElementById(inputElementId);
        const chatLog = document.getElementById(chatLogElementId);
        const message = chatInput.value.trim();

        if (message === '') return;

        // Add user message
        const userMessageDiv = document.createElement('div');
        userMessageDiv.classList.add('chat-message', 'user');
        userMessageDiv.innerText = message;
        chatLog.appendChild(userMessageDiv);
        chatLog.scrollTop = chatLog.scrollHeight; // Scroll to bottom

        chatInput.value = ''; // Clear input

        // Simulate AI response
        setTimeout(() => {
            const aiMessageDiv = document.createElement('div');
            aiMessageDiv.classList.add('chat-message', 'ai');
            aiMessageDiv.innerHTML = `<strong>AI:</strong> ${getAIResponse(message, context)}`;
            chatLog.appendChild(aiMessageDiv);
            chatLog.scrollTop = chatLog.scrollHeight; // Scroll to bottom
        }, 500);
    }

    function getAIResponse(message, context) {
        const lowerCaseMessage = message.toLowerCase();

        if (context === 'counseling') {
             if (lowerCaseMessage.includes('stress') || lowerCaseMessage.includes('anxiety')) {
                return 'It sounds like you\'re dealing with stress. Remember to take breaks, practice mindfulness, and ensure you\'re getting enough rest. Consider exploring our "Stress Management" counselors if you need more personalized strategies.';
            } else if (lowerCaseMessage.includes('academic') || lowerCaseMessage.includes('studies')) {
                return 'Facing academic challenges is common. Try breaking down your tasks, setting small goals, and seeking help from teachers or tutors. Our "Academic Support" counselors can also provide study tips and guidance.';
            } else if (lowerCaseMessage.includes('career') || lowerCaseMessage.includes('future')) {
                return 'Thinking about your career path is a big step. Reflect on your interests, skills, and values. Our "Career Guidance" counselors can help you explore options and plan your next steps.';
            } else if (lowerCaseMessage.includes('feeling down') || lowerCaseMessage.includes('sad')) {
                return 'I hear you. It\'s important to acknowledge your feelings. Reach out to a trusted friend, family member, or consider connecting with one of our "Personal Wellbeing" counselors. They can offer a safe space and professional support.';
            } else if (lowerCaseMessage.includes('exam')) {
                return 'Exams can be tough. Focus on consistent study, practice past papers, and ensure you have a healthy routine. Don\'t forget to manage exam anxiety – deep breathing exercises can help!';
            }
            return 'Thank you for sharing. Please elaborate on what\'s on your mind, or consider exploring the specific counseling options for more tailored support.';
        }
        // General Chatbot Responses
        if (lowerCaseMessage.includes('hello') || lowerCaseMessage.includes('hi')) {
            return 'Hello! How can I assist you today?';
        } else if (lowerCaseMessage.includes('study materials')) {
            return 'You can find study materials in the "Study Materials" section on your dashboard. What subject are you interested in?';
        } else if (lowerCaseMessage.includes('quiz') || lowerCaseMessage.includes('assignment')) {
            return 'The quiz is available in the "Assignments" section. You can test your knowledge there!';
        } else if (lowerCaseMessage.includes('counseling')) {
            return 'For counseling, please visit the "Counseling" section. You can chat with me there for initial guidance or explore professional counselors.';
        } else if (lowerCaseMessage.includes('notes')) {
            return 'You can save your personal notes in the "Notes" section of your dashboard. Just type and save!';
        } else if (lowerCaseMessage.includes('events')) {
            return 'Check out the "Events & Workshops" section for upcoming activities and important dates.';
        } else if (lowerCaseMessage.includes('help') || lowerCaseMessage.includes('support')) {
            return 'I am here to help! Please ask your question, or visit the "FAQs" section for common inquiries.';
        } else if (lowerCaseMessage.includes('thank you') || lowerCaseMessage.includes('thanks')) {
            return 'You\'re welcome! Is there anything else I can help you with?';
        } else if (lowerCaseMessage.includes('performance')) {
            return 'Your quiz results and overall performance summary are available in the "Performance" section.';
        }
        return 'I am still learning. Could you please rephrase or ask something else related to the portal features?';
    }


    // --- Path Finder & Study Materials (MODIFIED) ---
    const studyMaterials = {
        tech: [
            { name: "Web Development", materials: [
                { title: 'Introduction to HTML & CSS', link: '#', description: 'Basics of web page structure and styling.', icon: 'fas fa-file-code' },
                { title: 'JavaScript Fundamentals', link: '#', description: 'Interactive web with JS.', icon: 'fab fa-js' },
                { title: 'React JS Framework', link: '#', description: 'Building dynamic user interfaces.', icon: 'fab fa-react' }
            ]},
            { name: "Data Science", materials: [
                { title: 'Python for Data Analysis', link: '#', description: 'Pandas and NumPy for data manipulation.', icon: 'fas fa-database' },
                { title: 'Machine Learning Concepts', link: '#', description: 'Introduction to supervised and unsupervised learning.', icon: 'fas fa-brain' },
                { title: 'Data Visualization with Matplotlib', link: '#', description: 'Creating charts and graphs.', icon: 'fas fa-chart-bar' }
            ]},
            { name: "Cybersecurity", materials: [
                { title: 'Network Security Basics', link: '#', description: 'Understanding network vulnerabilities and defenses.', icon: 'fas fa-lock' },
                { title: 'Ethical Hacking Intro', link: '#', description: 'Principles of penetration testing.', icon: 'fas fa-user-secret' },
                { title: 'Cryptography Explained', link: '#', description: 'Fundamentals of secure communication.', icon: 'fas fa-shield-alt' }
            ]}
        ],
        medicine: [
            { name: "Human Anatomy", materials: [
                { title: 'Skeletal System Overview', link: '#', description: 'Bones and their functions.', icon: 'fas fa-bone' },
                { title: 'Muscular System Essentials', link: '#', description: 'Muscles and movement.', icon: 'fas fa-user-injured' },
                { title: 'Circulatory System', link: '#', description: 'Heart, blood, and vessels.', icon: 'fas fa-heartbeat' }
            ]},
            { name: "Pharmacology", materials: [
                { title: 'Drug Classification', link: '#', description: 'Types of drugs and their uses.', icon: 'fas fa-prescription-bottle-alt' },
                { title: 'Drug Interactions', link: '#', description: 'Understanding how drugs affect each other.', icon: 'fas fa-exchange-alt' }
            ]},
            { name: "Medical Ethics", materials: [
                { title: 'Patient Confidentiality', link: '#', description: 'Importance of privacy in healthcare.', icon: 'fas fa-user-md' },
                { title: 'Informed Consent Principles', link: '#', description: 'Rights of patients in medical decisions.', icon: 'fas fa-clipboard-check' }
            ]}
        ],
        commerce: [
            { name: "Accounting", materials: [
                { title: 'Financial Accounting Basics', link: '#', description: 'Introduction to balance sheets and income statements.', icon: 'fas fa-file-invoice-dollar' },
                { title: 'Managerial Accounting', link: '#', description: 'Using accounting for internal decision making.', icon: 'fas fa-chart-pie' }
            ]},
            { name: "Economics", materials: [
                { title: 'Microeconomics Principles', link: '#', description: 'Individual markets and consumer behavior.', icon: 'fas fa-chart-line' },
                { title: 'Macroeconomics Concepts', link: '#', description: 'National economies and global markets.', icon: 'fas fa-globe-americas' }
            ]},
            { name: "Business Management", materials: [
                { title: 'Principles of Marketing', link: '#', description: 'Strategies for promoting products and services.', icon: 'fas fa-bullhorn' },
                { title: 'Human Resource Management', link: '#', description: 'Managing talent and employee relations.', icon: 'fas fa-users' }
            ]}
        ],
        arts: [
            { name: "Literature", materials: [
                { title: 'Introduction to Poetry', link: '#', description: 'Forms, meters, and themes in poetry.', icon: 'fas fa-book-open' },
                { title: 'Literary Criticism', link: '#', description: 'Analyzing and interpreting texts.', icon: 'fas fa-feather-alt' }
            ]},
            { name: "Fine Arts", materials: [
                { title: 'History of Painting', link: '#', description: 'Major movements and artists.', icon: 'fas fa-paint-brush' },
                { title: 'Sculpture Techniques', link: '#', description: 'Materials and methods in 3D art.', icon: 'fas fa-hand-holding-box' }
            ]},
            { name: "History", materials: [
                { title: 'World History Overview', link: '#', description: 'Key events and civilizations.', icon: 'fas fa-landmark' },
                { title: 'Art History through Eras', link: '#', description: 'Evolution of art alongside historical periods.', icon: 'fas fa-palette' }
            ]}
        ],
        science: [
            { name: "Physics", materials: [
                { title: 'Classical Mechanics', link: '#', description: 'Motion, force, and energy.', icon: 'fas fa-atom' },
                { title: 'Electromagnetism', link: '#', description: 'Electric and magnetic fields.', icon: 'fas fa-bolt' }
            ]},
            { name: "Chemistry", materials: [
                { title: 'Organic Chemistry Basics', link: '#', description: 'Carbon compounds and reactions.', icon: 'fas fa-flask' },
                { title: 'Inorganic Chemistry', link: '#', description: 'Properties and reactions of inorganic compounds.', icon: 'fas fa-vials' }
            ]},
            { name: "Biology", materials: [
                { title: 'Cell Biology', link: '#', description: 'Structure and function of cells.', icon: 'fas fa-microscope' },
                { title: 'Genetics and Heredity', link: '#', description: 'Inheritance patterns and DNA.', icon: 'fas fa-dna' }
            ]}
        ],
        business: [
            { name: "Finance", materials: [
                { title: 'Investment Fundamentals', link: '#', description: 'Stocks, bonds, and mutual funds.', icon: 'fas fa-money-bill-wave' },
                { title: 'Personal Finance Management', link: '#', description: 'Budgeting, saving, and debt.', icon: 'fas fa-wallet' }
            ]},
            { name: "Marketing", materials: [
                { title: 'Digital Marketing Strategies', link: '#', description: 'SEO, social media, and content marketing.', icon: 'fas fa-share-alt' },
                { title: 'Brand Management', link: '#', description: 'Building and maintaining brand identity.', icon: 'fas fa-copyright' }
            ]},
            { name: "Entrepreneurship", materials: [
                { title: 'Startup Essentials', link: '#', description: 'Developing business ideas and plans.', icon: 'fas fa-lightbulb' },
                { title: 'Funding Your Venture', link: '#', description: 'Sources of capital for new businesses.', icon: 'fas fa-handshake' }
            ]}
        ]
    };

    function selectInterest(cardElement, interest) {
        // Remove 'selected-card' class from all cards
        document.querySelectorAll('.interest-card').forEach(card => {
            card.classList.remove('selected-card');
        });
        // Add 'selected-card' class to the clicked card
        cardElement.classList.add('selected-card');
        selectedPathFinderInterest = interest; // Store the selected interest globally
    }

    function resetPathFinderSelection() {
        document.querySelectorAll('.interest-card').forEach(card => {
            card.classList.remove('selected-card');
        });
        selectedPathFinderInterest = null; // Clear selection
    }

    function loadSubjectDropdown() {
        if (!selectedPathFinderInterest) {
            alert('Please select an interest area first!');
            return;
        }

        const subjectSelect = document.getElementById('subjectSelect');
        const loadingIndicator = document.getElementById('loadingIndicator');
        const subjectSelectionArea = document.getElementById('subjectSelectionArea');
        const studyContentList = document.getElementById('studyContent');

        subjectSelect.innerHTML = '<option value="">Select a subject...</option>'; // Reset dropdown
        studyContentList.innerHTML = ''; // Clear materials
        subjectSelectionArea.classList.add('hidden'); // Hide dropdown area initially
        loadingIndicator.style.display = 'block'; // Show loading indicator
        loadingIndicator.innerText = 'Loading subjects...'; // Update loading text

        showSection('studyMaterialsPage'); // Navigate to study materials page

        // Simulate network delay for loading subjects
        setTimeout(() => {
            const subjects = studyMaterials[selectedPathFinderInterest];
            if (subjects && subjects.length > 0) {
                subjects.forEach(subject => {
                    const option = document.createElement('option');
                    option.value = subject.name;
                    option.innerText = subject.name;
                    subjectSelect.appendChild(option);
                });
                subjectSelectionArea.classList.remove('hidden'); // Show dropdown area
            } else {
                subjectSelect.innerHTML = '<option value="">No subjects found for this category.</option>';
            }
            loadingIndicator.style.display = 'none'; // Hide loading indicator
        }, 800); // 800ms delay
    }

    function loadSubjectMaterials(subjectName) {
        const studyContentList = document.getElementById('studyContent');
        const loadingIndicator = document.getElementById('loadingIndicator');

        studyContentList.innerHTML = ''; // Clear previous materials
        loadingIndicator.style.display = 'block'; // Show loading indicator
        loadingIndicator.innerText = 'Loading materials...'; // Update loading text
        
        selectedSubjectForQuiz = subjectName; // NEW: Store selected subject for quiz

        if (!subjectName) {
            loadingIndicator.style.display = 'none';
            studyContentList.innerHTML = '<li>Please select a subject to view materials.</li>';
            return;
        }

        // Find the selected subject's materials
        const selectedCategory = studyMaterials[selectedPathFinderInterest];
        const selectedSubject = selectedCategory.find(subj => subj.name === subjectName);

        // Simulate network delay for loading materials
        setTimeout(() => {
            if (selectedSubject && selectedSubject.materials.length > 0) {
                selectedSubject.materials.forEach(material => {
                    const listItem = document.createElement('li');
                    listItem.innerHTML = `
                        <span class="material-icon"><i class="${material.icon}"></i></span>
                        <div class="material-details">
                            <h4><a href="${material.link}" target="_blank">${material.title} <i class="fas fa-external-link-alt"></i></a></h4>
                            <p>${material.description}</p>
                        </div>
                    `;
                    studyContentList.appendChild(listItem);
                });
            } else {
                studyContentList.innerHTML = '<li>No study materials found for this subject yet.</li>';
            }
            loadingIndicator.style.display = 'none'; // Hide loading indicator
        }, 500); // 500ms delay
    }

    // --- Assignments (Quiz) Functions ---
    // NEW: Quiz questions structured by subject
    const quizQuestionsBySubject = {
        tech: {
            "Web Development": [
                { question: "What does HTML stand for?", options: ["Hyper Text Markup Language", "Hyperlink and Text Markup Language", "Home Tool Markup Language", "Hypertext Markdown Language"], answer: "Hyper Text Markup Language" },
                { question: "Which CSS property is used to control the spacing between elements?", options: ["margin", "padding", "spacing", "border-spacing"], answer: "margin" },
                { question: "Which of the following is NOT a JavaScript data type?", options: ["String", "Boolean", "Float", "Object"], answer: "Float" },
                { question: "What is the correct HTML element for the largest heading?", options: ["<head>", "<heading>", "<h6>", "<h1>"], answer: "<h1>" },
                { question: "How do you apply a class to an HTML element?", options: ["id='myClass'", "class='myClass'", "style='myClass'", "data-class='myClass'"], answer: "class='myClass'" },
                { question: "Which CSS property changes the text color?", options: ["text-color", "font-color", "color", "background-color"], answer: "color" },
                { question: "Inside which HTML element do we put the JavaScript?", options: ["<js>", "<script>", "<javascript>", "<scripting>"], answer: "<script>" },
                { question: "What does 'DOM' stand for in web development?", options: ["Document Object Model", "Data Object Model", "Dynamic Object Manager", "Document Order Module"], answer: "Document Object Model" },
                { question: "Which keyword is used to declare a constant in JavaScript?", options: ["var", "let", "const", "static"], answer: "const" },
                { question: "What is the purpose of 'flexbox' in CSS?", options: ["Creating 3D animations", "Layout elements in a one-dimensional row or column", "Storing data in the browser", "Handling server-side logic"], answer: "Layout elements in a one-dimensional row or column" }
            ],
            "Data Science": [
                { question: "Which Python library is commonly used for numerical operations?", options: ["Pandas", "Matplotlib", "NumPy", "Scikit-learn"], answer: "NumPy" },
                { question: "What is the primary function of a 'DataFrame' in Pandas?", options: ["To store images", "To represent tabular data", "To perform complex calculations", "To manage network connections"], answer: "To represent tabular data" },
                { question: "Which type of machine learning uses labeled data?", options: ["Unsupervised learning", "Reinforcement learning", "Supervised learning", "Semi-supervised learning"], answer: "Supervised learning" },
                { question: "What is 'EDA' in data science?", options: ["Efficient Data Analysis", "Exploratory Data Analysis", "External Data Access", "Essential Data Algorithm"], answer: "Exploratory Data Analysis" },
                { question: "Which plot is best for showing distribution of a single numerical variable?", options: ["Scatter plot", "Bar chart", "Histogram", "Line plot"], answer: "Histogram" },
                { question: "What is 'feature engineering'?", options: ["Designing new software features", "Creating new input features from existing ones", "Managing version control", "Debugging code errors"], answer: "Creating new input features from existing ones" },
                { question: "In machine learning, what is 'overfitting'?", options: ["Model performing well on training data but poorly on unseen data", "Model performing poorly on both training and test data", "Model training too slowly", "Model having too few parameters"], answer: "Model performing well on training data but poorly on unseen data" },
                { question: "Which metric measures the accuracy of a classification model?", options: ["R-squared", "Mean Absolute Error", "Precision", "RMSE"], answer: "Precision" },
                { question: "What is the purpose of 'K-Means' algorithm?", options: ["Regression", "Classification", "Clustering", "Dimensionality Reduction"], answer: "Clustering" },
                { question: "Which term describes a row in a dataset?", options: ["Feature", "Attribute", "Observation", "Column"], answer: "Observation" }
            ],
            "Cybersecurity": [
                { question: "What is 'phishing'?", options: ["A type of malware", "Attempting to obtain sensitive information by disguising as a trustworthy entity", "A network vulnerability scanner", "A data encryption technique"], answer: "Attempting to obtain sensitive information by disguising as a trustworthy entity" },
                { question: "Which protocol is used for secure web Browse?", options: ["HTTP", "FTP", "SSL/TLS", "SMTP"], answer: "SSL/TLS" },
                { question: "What is a 'firewall' in network security?", options: ["A physical barrier against intruders", "A system that prevents unauthorized access to or from a private network", "A type of antivirus software", "A data backup solution"], answer: "A system that prevents unauthorized access to or from a private network" },
                { question: "What does 'DDoS' stand for?", options: ["Direct Data Operation System", "Distributed Denial of Service", "Dynamic Defense Optimization System", "Data Duplication over System"], answer: "Distributed Denial of Service" },
                { question: "Which of these is a common method for authentication?", options: ["Encryption", "Hashing", "Multi-factor authentication", "Port scanning"], answer: "Multi-factor authentication" },
                { question: "What is the purpose of a VPN?", options: ["To speed up internet connection", "To create a secure and encrypted connection over a public network", "To block ads", "To monitor website traffic"], answer: "To create a secure and encrypted connection over a public network" },
                { question: "Which concept refers to ensuring information is accurate and reliable?", options: ["Confidentiality", "Integrity", "Availability", "Non-repudiation"], answer: "Integrity" },
                { question: "What is malware?", options: ["Hardware components of a computer", "Software designed to cause damage or gain unauthorized access", "A type of network cable", "A cybersecurity professional"], answer: "Software designed to cause damage or gain unauthorized access" },
                { question: "What is 'social engineering' in cybersecurity?", options: ["Designing social media campaigns", "Manipulating people to divulge confidential information", "Analyzing social networks for trends", "Developing ethical guidelines for AI"], answer: "Manipulating people to divulge confidential information" },
                { question: "What is the role of an 'Intrusion Detection System' (IDS)?", options: ["To prevent all cyber attacks", "To detect malicious activity and policy violations", "To encrypt data on a network", "To manage user passwords"], answer: "To detect malicious activity and policy violations" }
            ]
        },
        medicine: {
            "Human Anatomy": [
                { question: "Which is the largest organ in the human body?", options: ["Heart", "Brain", "Skin", "Liver"], answer: "Skin" },
                { question: "How many bones are in the adult human skeleton?", options: ["206", "212", "198", "220"], answer: "206" },
                { question: "What is the function of the red blood cells?", options: ["Fighting infection", "Clotting blood", "Carrying oxygen", "Producing antibodies"], answer: "Carrying oxygen" },
                { question: "Which part of the brain controls balance and coordination?", options: ["Cerebrum", "Cerebellum", "Brainstem", "Thalamus"], answer: "Cerebellum" },
                { question: "What are the two main divisions of the nervous system?", options: ["Skeletal and Muscular", "Central and Peripheral", "Cardiovascular and Respiratory", "Digestive and Endocrine"], answer: "Central and Peripheral" },
                { question: "Which organ produces insulin?", options: ["Liver", "Kidney", "Pancreas", "Stomach"], answer: "Pancreas" },
                { question: "What is the smallest bone in the human body?", options: ["Femur", "Stapes", "Tibia", "Radius"], answer: "Stapes" },
                { question: "Which of these is part of the respiratory system?", options: ["Esophagus", "Trachea", "Kidney", "Gallbladder"], answer: "Trachea" },
                { question: "What is the primary function of the kidneys?", options: ["Pump blood", "Filter waste from blood", "Digest food", "Produce hormones"], answer: "Filter waste from blood" },
                { question: "Where is the quadriceps femoris muscle located?", options: ["Arm", "Chest", "Thigh", "Calf"], answer: "Thigh" }
            ],
            "Pharmacology": [
                { question: "What does 'OTC' stand for in pharmacology?", options: ["Order To Combat", "Over The Counter", "Oncology Treatment Center", "Oral Therapeutic Compound"], answer: "Over The Counter" },
                { question: "Which of these is a common route of drug administration?", options: ["Topical", "Optical", "Auditory", "Olfactory"], answer: "Topical" },
                { question: "What is a 'placebo' effect?", options: ["A side effect of medication", "A beneficial psychological effect due to a patient's belief in a treatment", "An allergic reaction to a drug", "The interaction between two drugs"], answer: "A beneficial psychological effect due to a patient's belief in a treatment" },
                { question: "Which drug class is used to treat bacterial infections?", options: ["Antivirals", "Antifungals", "Antibiotics", "Anticoagulants"], answer: "Antibiotics" },
                { question: "What is 'pharmacokinetics'?", options: ["Study of drug effects on the body", "Study of how the body affects the drug (absorption, distribution, metabolism, excretion)", "Study of herbal medicines", "Study of drug discovery process"], answer: "Study of how the body affects the drug (absorption, distribution, metabolism, excretion)" },
                { question: "Which term describes a severe, life-threatening allergic reaction to a drug?", options: ["Tolerance", "Dependence", "Anaphylaxis", "Idiosyncrasy"], answer: "Anaphylaxis" },
                { question: "What is the primary target of antiviral drugs?", options: ["Bacteria", "Fungi", "Viruses", "Parasites"], answer: "Viruses" },
                { question: "Which organ is primarily responsible for drug metabolism?", options: ["Kidney", "Lung", "Liver", "Heart"], answer: "Liver" },
                { question: "What is a 'contraindication' for a drug?", options: ["A recommended use for the drug", "A condition or factor that makes the use of a drug inadvisable", "The maximum effective dose of a drug", "The brand name of a drug"], answer: "A condition or factor that makes the use of a drug inadvisable" },
                { question: "What does 'ADME' stand for in pharmacology?", options: ["Acute Drug Management Experience", "Administration, Dosage, Metabolism, Excretion", "Absorption, Distribution, Metabolism, Excretion", "Adverse Drug Monitoring Evaluation"], answer: "Absorption, Distribution, Metabolism, Excretion" }
            ],
            "Medical Ethics": [
                { question: "Which ethical principle emphasizes doing good for the patient?", options: ["Autonomy", "Justice", "Beneficence", "Non-maleficence"], answer: "Beneficence" },
                { question: "What is 'informed consent' in medical practice?", options: ["A doctor's permission to treat a patient", "The patient's voluntary agreement to a medical procedure after understanding its risks and benefits", "A legal document protecting hospitals", "A mandatory blood test before surgery"], answer: "The patient's voluntary agreement to a medical procedure after understanding its risks and benefits" },
                { question: "The principle of 'non-maleficence' means:", options: ["To always do good", "To do no harm", "To treat all patients equally", "To respect patient choices"], answer: "To do no harm" },
                { question: "Which organization sets ethical guidelines for medical research in many countries?", options: ["WHO", "UNICEF", "IRB (Institutional Review Board)", "Red Cross"], answer: "IRB (Institutional Review Board)" },
                { question: "What is 'patient confidentiality'?", options: ["Keeping patient information private", "Sharing patient information with family members only", "Discussing patient cases openly with colleagues", "Using patient data for marketing purposes"], answer: "Keeping patient information private" },
                { question: "Which ethical dilemma arises when resources are scarce and choices must be made about who receives treatment?", options: ["Autonomy", "Beneficence", "Justice", "Fidelity"], answer: "Justice" },
                { question: "What is the role of an 'ethics committee' in a hospital?", options: ["To manage hospital finances", "To review and advise on ethical issues in patient care", "To organize staff training", "To handle patient complaints"], answer: "To review and advise on ethical issues in patient care" },
                { question: "The concept of 'respect for autonomy' means:", options: ["Doctors make all decisions for patients", "Patients have the right to make decisions about their own medical care", "Medical staff must follow all patient requests regardless of medical validity", "Hospitals can decide treatment plans without patient input"], answer: "Patients have the right to make decisions about their own medical care" },
                { question: "What is a 'living will'?", options: ["A document specifying how property should be distributed after death", "A legal document outlining a person's wishes for medical treatment in the future", "A request for organ donation", "A record of past medical treatments"], answer: "A legal document outlining a person's wishes for medical treatment in the future" },
                { question: "Which ethical principle relates to truthfulness and honesty in medical communication?", options: ["Confidentiality", "Veracity", "Privacy", "Equity"], answer: "Veracity" }
            ]
        },
        commerce: {
            "Accounting": [
                { question: "What is the basic accounting equation?", options: ["Assets = Liabilities - Equity", "Assets = Liabilities + Equity", "Assets + Liabilities = Equity", "Assets / Liabilities = Equity"], answer: "Assets = Liabilities + Equity" },
                { question: "Which financial statement shows a company's financial position at a specific point in time?", options: ["Income Statement", "Cash Flow Statement", "Balance Sheet", "Statement of Retained Earnings"], answer: "Balance Sheet" },
                { question: "What does 'revenue' represent in an income statement?", options: ["Expenses incurred", "Money earned from sales", "Profit for the period", "Debts owed"], answer: "Money earned from sales" },
                { question: "What is 'depreciation' in accounting?", options: ["Increase in asset value", "Decrease in asset value over time due to use or obsolescence", "Cash outflow for asset purchase", "Sale of an asset"], answer: "Decrease in asset value over time due to use or obsolescence" },
                { question: "What is the 'matching principle'?", options: ["Matching assets with liabilities", "Matching revenues with expenses in the period they are incurred", "Matching cash inflows with outflows", "Matching inventory with sales"], answer: "Matching revenues with expenses in the period they are incurred" },
                { question: "What is 'accounts receivable'?", options: ["Money owed by the company", "Money owed to the company by customers", "Cash in hand", "Investments made by the company"], answer: "Money owed to the company by customers" },
                { question: "Which type of accounting is primarily for external users (investors, creditors)?", options: ["Managerial Accounting", "Tax Accounting", "Financial Accounting", "Cost Accounting"], answer: "Financial Accounting" },
                { question: "What is 'liquidity' in financial terms?", options: ["Ability to pay short-term obligations", "Profitability of a company", "Amount of debt a company has", "Growth rate of a company"], answer: "Ability to pay short-term obligations" },
                { question: "What does 'FIFO' stand for in inventory valuation?", options: ["First In, First Out", "Funds In, Funds Out", "Fixed Income, Fixed Overhead", "Financial Information, Financial Operations"], answer: "First In, First Out" },
                { question: "What is the purpose of a 'trial balance'?", options: ["To summarize revenues and expenses", "To ensure debits equal credits in the ledger", "To calculate net income", "To record daily transactions"], answer: "To ensure debits equal credits in the ledger" }
            ],
            "Economics": [
                { question: "What is 'supply' in economics?", options: ["The quantity of goods and services demanded by consumers", "The total amount of money in circulation", "The quantity of goods and services producers are willing to offer for sale", "The government's budget deficit"], answer: "The quantity of goods and services producers are willing to offer for sale" },
                { question: "What does 'demand' in economics refer to?", options: ["The quantity of goods and services producers offer", "The quantity of goods and services consumers are willing and able to purchase", "The total wealth of a nation", "The amount of a country's exports"], answer: "The quantity of goods and services consumers are willing and able to purchase" },
                { question: "What is 'inflation'?", options: ["A decrease in the general price level", "A sustained increase in the general price level of goods and services", "A period of economic recession", "An increase in unemployment rates"], answer: "A sustained increase in the general price level of goods and services" },
                { question: "What is 'GDP'?", options: ["Gross Domestic Production", "General Development Plan", "Global Demand Projection", "Government Debt Percentage"], answer: "Gross Domestic Production" },
                { question: "Which of these is a factor of production?", options: ["Demand", "Supply", "Capital", "Inflation"], answer: "Capital" },
                { question: "What is 'scarcity' in economics?", options: ["Unlimited resources", "Limited resources to meet unlimited wants", "Abundant goods and services", "Low demand for products"], answer: "Limited resources to meet unlimited wants" },
                { question: "What is a 'monopoly' in market structure?", options: ["Many sellers, identical products", "Few sellers, similar products", "A single seller dominates the market", "Many sellers, differentiated products"], answer: "A single seller dominates the market" },
                { question: "Which type of unemployment occurs due to seasonal changes in labor demand?", options: ["Cyclical unemployment", "Frictional unemployment", "Structural unemployment", "Seasonal unemployment"], answer: "Seasonal unemployment" },
                { question: "What is the 'Law of Diminishing Returns'?", options: ["Increasing production leads to higher profits", "Adding more of one factor of production, while keeping others constant, eventually yields lower per-unit output", "Decreasing costs as production increases", "Government intervention reduces market efficiency"], answer: "Adding more of one factor of production, while keeping others constant, eventually yields lower per-unit output" },
                { question: "What does a 'fiscal policy' primarily involve?", options: ["Controlling money supply", "Government spending and taxation to influence the economy", "Setting interest rates", "Regulating international trade"], answer: "Government spending and taxation to influence the economy" }
            ],
            "Business Management": [
                { question: "What is the primary goal of a for-profit business?", options: ["Social responsibility", "Customer satisfaction", "Maximizing shareholder wealth", "Employee happiness"], answer: "Maximizing shareholder wealth" },
                { question: "Which management function involves setting goals and determining how to achieve them?", options: ["Organizing", "Leading", "Controlling", "Planning"], answer: "Planning" },
                { question: "What is a 'SWOT analysis' used for?", options: ["Evaluating employee performance", "Analyzing a company's Strengths, Weaknesses, Opportunities, and Threats", "Calculating financial ratios", "Developing marketing campaigns"], answer: "Analyzing a company's Strengths, Weaknesses, Opportunities, and Threats" },
                { question: "What is 'delegation' in management?", options: ["Taking on all tasks yourself", "Assigning authority and responsibility to subordinates", "Ignoring employee feedback", "Centralizing all decision-making"], answer: "Assigning authority and responsibility to subordinates" },
                { question: "Which leadership style involves minimal leader involvement, allowing employees to make decisions?", options: ["Autocratic", "Democratic", "Laissez-faire", "Transformational"], answer: "Laissez-faire" },
                { question: "What is a 'mission statement'?", options: ["A company's financial report", "A brief statement defining the purpose and primary objectives of a company", "A marketing slogan", "A detailed operational plan"], answer: "A brief statement defining the purpose and primary objectives of a company" },
                { question: "Which department is responsible for recruiting, hiring, and training employees?", options: ["Marketing", "Finance", "Human Resources", "Operations"], answer: "Human Resources" },
                { question: "What is 'supply chain management'?", options: ["Managing only the production process", "Overseeing the flow of goods and services from raw materials to end consumer", "Selling products directly to customers", "Handling customer complaints"], answer: "Overseeing the flow of goods and services from raw materials to end consumer" },
                { question: "What does 'CSR' stand for in business?", options: ["Customer Service Representative", "Corporate Social Responsibility", "Company Sales Report", "Consumer Spending Research"], answer: "Corporate Social Responsibility" },
                { question: "Which type of organizational structure has a clear hierarchy with top-down communication?", options: ["Matrix structure", "Flat structure", "Functional structure", "Divisional structure"], answer: "Functional structure" }
            ]
        },
        arts: {
            "Literature": [
                { question: "Who wrote 'Romeo and Juliet'?", options: ["Charles Dickens", "William Shakespeare", "Jane Austen", "Mark Twain"], answer: "William Shakespeare" },
                { question: "What is a 'sonnet'?", options: ["A long narrative poem", "A 14-line poem with a specific rhyme scheme", "A type of prose fiction", "A dramatic monologue"], answer: "A 14-line poem with a specific rhyme scheme" },
                { question: "Which literary device involves a contrast between what is said and what is actually meant?", options: ["Metaphor", "Simile", "Irony", "Alliteration"], answer: "Irony" },
                { question: "What genre is 'The Great Gatsby'?", options: ["Fantasy", "Science Fiction", "Tragedy", "Modernist Novel"], answer: "Modernist Novel" },
                { question: "Who is the author of 'To Kill a Mockingbird'?", options: ["J.K. Rowling", "Harper Lee", "Ernest Hemingway", "F. Scott Fitzgerald"], answer: "Harper Lee" },
                { question: "What is 'alliteration'?", options: ["Repetition of vowel sounds", "Repetition of consonant sounds at the beginning of words", "A direct comparison", "An exaggeration for effect"], answer: "Repetition of consonant sounds at the beginning of words" },
                { question: "What is the main purpose of 'foreshadowing' in literature?", options: ["To create a happy ending", "To provide hints or clues about future events", "To introduce new characters", "To summarize past events"], answer: "To provide hints or clues about future events" },
                { question: "A 'bildungsroman' is a novel about what?", options: ["A mystery solving", "A journey of moral or psychological growth", "A historical event", "A scientific discovery"], answer: "A journey of moral or psychological growth" },
                { question: "Which poetic form typically tells a story and is often sung?", options: ["Haiku", "Limerick", "Ballad", "Free Verse"], answer: "Ballad" },
                { question: "What is 'symbolism' in literature?", options: ["Using direct statements", "Using an object or idea to represent something else", "Telling a story chronologically", "Writing in a very simple style"], answer: "Using an object or idea to represent something else" }
            ],
            "Fine Arts": [
                { question: "Who painted the Mona Lisa?", options: ["Vincent van Gogh", "Pablo Picasso", "Leonardo da Vinci", "Claude Monet"], answer: "Leonardo da Vinci" },
                { question: "Which art movement is characterized by distorted figures and dream-like scenes?", options: ["Impressionism", "Cubism", "Surrealism", "Renaissance"], answer: "Surrealism" },
                { question: "What is 'chiaroscuro' in painting?", options: ["A technique using bright colors only", "The use of strong contrasts between light and dark", "A type of abstract art", "Painting on wet plaster"], answer: "The use of strong contrasts between light and dark" },
                { question: "Which famous sculpture depicts a shepherd boy with a sling?", options: ["Venus de Milo", "The Thinker", "David", "Laocoön and His Sons"], answer: "David" },
                { question: "What material is typically used for 'fresco' painting?", options: ["Canvas", "Wood panel", "Wet plaster", "Paper"], answer: "Wet plaster" },
                { question: "Which artist is known for pioneering 'Cubism' with Georges Braque?", options: ["Salvador Dalí", "Jackson Pollock", "Pablo Picasso", "Andy Warhol"], answer: "Pablo Picasso" },
                { question: "What is a 'still life' painting?", options: ["A portrait of a person", "A landscape painting", "A depiction of inanimate objects", "A historical scene"], answer: "A depiction of inanimate objects" },
                { question: "Which architectural style features pointed arches, ribbed vaults, and flying buttresses?", options: ["Romanesque", "Gothic", "Neoclassical", "Baroque"], answer: "Gothic" },
                { question: "What is 'perspective' in art?", options: ["The use of bright colors", "Creating an illusion of depth and distance on a flat surface", "Painting historical events", "Representing emotions"], answer: "Creating an illusion of depth and distance on a flat surface" },
                { question: "Which of these is a primary color?", options: ["Green", "Purple", "Orange", "Blue"], answer: "Blue" }
            ],
            "History": [
                { question: "In which year did World War II officially end?", options: ["1941", "1945", "1950", "1939"], answer: "1945" },
                { question: "Who was the first emperor of Rome?", options: ["Julius Caesar", "Nero", "Augustus", "Constantine"], answer: "Augustus" },
                { question: "What ancient civilization built the pyramids of Giza?", options: ["Roman", "Greek", "Egyptian", "Mesopotamian"], answer: "Egyptian" },
                { question: "The Renaissance originated in which country?", options: ["France", "England", "Italy", "Germany"], answer: "Italy" },
                { question: "Who was the leader of the Soviet Union during World War II?", options: ["Vladimir Lenin", "Leon Trotsky", "Joseph Stalin", "Nikita Khrushchev"], answer: "Joseph Stalin" },
                { question: "Which document was signed in 1215 and limited the power of the English king?", options: ["Bill of Rights", "Declaration of Independence", "Magna Carta", "Treaty of Versailles"], answer: "Magna Carta" },
                { question: "The fall of the Berlin Wall occurred in which year?", options: ["1985", "1991", "1989", "1979"], answer: "1989" },
                { question: "Who was the principal author of the Declaration of Independence?", options: ["George Washington", "Benjamin Franklin", "Thomas Jefferson", "John Adams"], answer: "Thomas Jefferson" },
                { question: "Which major event sparked World War I?", options: ["The sinking of the Titanic", "The assassination of Archduke Franz Ferdinand", "The Great Depression", "The Russian Revolution"], answer: "The assassination of Archduke Franz Ferdinand" },
                { question: "What was the 'Silk Road'?", options: ["A modern highway in China", "An ancient network of trade routes connecting East and West", "A type of fabric", "A naval battle strategy"], answer: "An ancient network of trade routes connecting East and West" }
            ]
        },
        science: {
            "Physics": [
                { question: "What is the SI unit of force?", options: ["Joule", "Watt", "Newton", "Pascal"], answer: "Newton" },
                { question: "What is the law of conservation of energy?", options: ["Energy can be created but not destroyed", "Energy can be destroyed but not created", "Energy can neither be created nor destroyed, only transformed", "Energy is always lost as heat"], answer: "Energy can neither be created nor destroyed, only transformed" },
                { question: "Which of these is a scalar quantity?", options: ["Velocity", "Acceleration", "Mass", "Force"], answer: "Mass" },
                { question: "What does 'E=mc²' represent?", options: ["Newton's Law of Motion", "Ohm's Law", "Einstein's Mass-Energy Equivalence", "Law of Gravity"], answer: "Einstein's Mass-Energy Equivalence" },
                { question: "What is the phenomenon where light bends as it passes from one medium to another?", options: ["Reflection", "Diffraction", "Refraction", "Interference"], answer: "Refraction" },
                { question: "Which type of current reverses its direction periodically?", options: ["Direct Current (DC)", "Alternating Current (AC)", "Static Current", "Pulsating Current"], answer: "Alternating Current (AC)" },
                { question: "What is the SI unit of electric current?", options: ["Volt", "Ohm", "Ampere", "Watt"], answer: "Ampere" },
                { question: "What is 'gravity'?", options: ["A type of electromagnetic force", "A force that attracts any two objects with mass", "The force that pushes objects apart", "The energy of moving objects"], answer: "A force that attracts any two objects with mass" },
                { question: "Which law states that for every action, there is an equal and opposite reaction?", options: ["Newton's First Law", "Newton's Second Law", "Newton's Third Law", "Law of Conservation of Momentum"], answer: "Newton's Third Law" },
                { question: "What is the speed of light in a vacuum (approximately)?", options: ["3 x 10^5 m/s", "3 x 10^8 km/s", "3 x 10^8 m/s", "3 x 10^6 km/s"], answer: "3 x 10^8 m/s" }
            ],
            "Chemistry": [
                { question: "What is the chemical symbol for Gold?", options: ["Ag", "Fe", "Au", "Cu"], answer: "Au" },
                { question: "What is the pH value of a neutral solution?", options: ["0", "7", "14", "1"], answer: "7" },
                { question: "Which element is the most abundant in Earth's atmosphere?", options: ["Oxygen", "Carbon Dioxide", "Argon", "Nitrogen"], answer: "Nitrogen" },
                { question: "What is the process of converting a liquid into a gas?", options: ["Melting", "Condensation", "Sublimation", "Evaporation"], answer: "Evaporation" },
                { question: "Which type of bond involves the sharing of electrons between atoms?", options: ["Ionic bond", "Metallic bond", "Covalent bond", "Hydrogen bond"], answer: "Covalent bond" },
                { question: "What is the formula for water?", options: ["CO2", "H2SO4", "NaCl", "H2O"], answer: "H2O" },
                { question: "What are atoms of the same element with different numbers of neutrons called?", options: ["Ions", "Isotopes", "Allotropes", "Polymers"], answer: "Isotopes" },
                { question: "Which gas do plants absorb from the atmosphere during photosynthesis?", options: ["Oxygen", "Nitrogen", "Carbon Dioxide", "Hydrogen"], answer: "Carbon Dioxide" },
                { question: "What is an 'acid' in chemistry (Arrhenius definition)?", options: ["A substance that produces OH- ions in solution", "A substance that produces H+ ions in solution", "A substance that accepts electrons", "A substance that donates electrons"], answer: "A substance that produces H+ ions in solution" },
                { question: "What is 'oxidation' in a chemical reaction?", options: ["Gain of electrons", "Loss of electrons", "Gain of protons", "Loss of neutrons"], answer: "Loss of electrons" }
            ],
            "Biology": [
                { question: "What is the powerhouse of the cell?", options: ["Nucleus", "Ribosome", "Mitochondria", "Endoplasmic Reticulum"], answer: "Mitochondria" },
                { question: "Which process do plants use to convert light energy into chemical energy?", options: ["Respiration", "Fermentation", "Photosynthesis", "Transpiration"], answer: "Photosynthesis" },
                { question: "What are the building blocks of proteins?", options: ["Glucose", "Amino Acids", "Fatty Acids", "Nucleotides"], answer: "Amino Acids" },
                { question: "What is the primary function of DNA?", options: ["Transporting oxygen", "Storing genetic information", "Producing energy", "Digesting food"], answer: "Storing genetic information" },
                { question: "Which organelle is responsible for protein synthesis?", options: ["Lysosome", "Golgi apparatus", "Ribosome", "Vacuole"], answer: "Ribosome" },
                { question: "What is the term for an organism that produces its own food, typically through photosynthesis?", options: ["Heterotroph", "Decomposer", "Autotroph", "Consumer"], answer: "Autotroph" },
                { question: "Which of the following is a prokaryotic cell?", options: ["Animal cell", "Plant cell", "Fungal cell", "Bacterial cell"], answer: "Bacterial cell" },
                { question: "What is 'meiosis'?", options: ["Cell division for growth and repair", "Cell division that produces gametes (sex cells)", "The process of photosynthesis", "The breakdown of glucose"], answer: "Cell division that produces gametes (sex cells)" },
                { question: "Which blood type is considered the universal donor?", options: ["A+", "B-", "AB+", "O-"], answer: "O-" },
                { question: "What is the function of the circulatory system?", options: ["To digest food", "To transport blood, nutrients, oxygen, and waste", "To control body movements", "To produce hormones"], answer: "To transport blood, nutrients, oxygen, and waste" }
            ]
        },
        business: {
            "Finance": [
                { question: "What is a 'stock'?", options: ["A type of bond", "A loan to a company", "A share of ownership in a company", "A form of real estate investment"], answer: "A share of ownership in a company" },
                { question: "What is the purpose of diversification in investing?", options: ["To maximize risk", "To minimize taxes", "To spread risk across various investments", "To invest in only one type of asset"], answer: "To spread risk across various investments" },
                { question: "What does 'ROI' stand for?", options: ["Return on Investment", "Risk of Interest", "Rate of Income", "Revenue on Infrastructure"], answer: "Return on Investment" },
                { question: "What is a 'bond'?", options: ["An ownership stake in a company", "A loan made to a borrower (typically a corporation or government) that promises to pay back a principal amount plus interest", "A type of mutual fund", "A commodity contract"], answer: "A loan made to a borrower (typically a corporation or government) that promises to pay back a principal amount plus interest" },
                { question: "What is the primary function of a central bank (e.g., Federal Reserve)?", options: ["To provide loans to individuals", "To control the money supply and regulate banks", "To manage government spending", "To issue corporate bonds"], answer: "To control the money supply and regulate banks" },
                { question: "What is 'compounding' in finance?", options: ["Earning interest only on the principal amount", "Earning interest on both the principal and accumulated interest", "Losing money on investments", "Paying taxes on investments"], answer: "Earning interest on both the principal and accumulated interest" },
                { question: "Which financial ratio measures a company's ability to meet its short-term obligations?", options: ["Debt-to-Equity Ratio", "Profit Margin", "Current Ratio", "Return on Assets"], answer: "Current Ratio" },
                { question: "What is a 'mutual fund'?", options: ["A single stock investment", "A collection of stocks, bonds, or other securities managed by a professional", "A type of bank account", "A government-issued bond"], answer: "A collection of stocks, bonds, or other securities managed by a professional" },
                { question: "What does 'liquidity' mean for an asset?", options: ["How quickly it loses value", "How easily it can be converted into cash without losing significant value", "Its long-term growth potential", "Its tax implications"], answer: "How easily it can be converted into cash without losing significant value" },
                { question: "What is 'budgeting' in personal finance?", options: ["Spending money without tracking it", "Creating a plan for how to spend and save money", "Investing all your money in stocks", "Ignoring financial goals"], answer: "Creating a plan for how to spend and save money" }
            ],
            "Marketing": [
                { question: "What are the '4 Ps' of marketing?", options: ["People, Process, Profit, Place", "Product, Price, Promotion, Place", "Planning, Public Relations, Packaging, Profit", "Promotion, Price, People, Process"], answer: "Product, Price, Promotion, Place" },
                { question: "What is 'market segmentation'?", options: ["Dividing a market into distinct groups of buyers with different needs, characteristics, or behaviors", "Selling products globally", "Lowering prices to attract more customers", "Advertising products on social media"], answer: "Dividing a market into distinct groups of buyers with different needs, characteristics, or behaviors" },
                { question: "What does 'SEO' stand for?", options: ["Sales Engagement Optimization", "Search Engine Optimization", "Social Events Organization", "Strategic Expense Oversight"], answer: "Search Engine Optimization" },
                { question: "Which of these is a form of 'digital marketing'?", options: ["Newspaper ads", "Billboard advertising", "Email marketing", "Radio commercials"], answer: "Email marketing" },
                { question: "What is 'branding'?", options: ["The process of creating a unique name and image for a product in the consumer's mind", "Selling products at a discount", "Distributing products through multiple channels", "Conducting market research"], answer: "The process of creating a unique name and image for a product in the consumer's mind" },
                { question: "What is a 'target market'?", options: ["All consumers in a market", "A specific group of consumers a company aims to reach with its products/services", "The location of a market", "A competitor's customer base"], answer: "A specific group of consumers a company aims to reach with its products/services" },
                { question: "What is 'public relations' (PR)?", options: ["Direct selling to customers", "Managing the spread of information between an individual or organization and the public", "Creating product designs", "Analyzing sales data"], answer: "Managing the spread of information between an individual or organization and the public" },
                { question: "What is 'content marketing'?", options: ["Selling physical products", "Creating and distributing valuable, relevant, and consistent content to attract and retain a clearly defined audience", "Running TV commercials", "Cold calling potential customers"], answer: "Creating and distributing valuable, relevant, and consistent content to attract and retain a clearly defined audience" },
                { question: "Which pricing strategy involves setting a high price for a new product to skim maximum revenues layer by layer from the segments willing to pay the high price?", options: ["Penetration pricing", "Cost-plus pricing", "Price skimming", "Competitive pricing"], answer: "Price skimming" },
                { question: "What is the main goal of 'promotion' in marketing?", options: ["To set product prices", "To make a product or service known and persuade potential customers to buy it", "To design product packaging", "To manage supply chains"], answer: "To make a product or service known and persuade potential customers to buy it" }
            ],
            "Entrepreneurship": [
                { question: "What is an 'entrepreneur'?", options: ["A factory worker", "Someone who starts a business, taking on financial risks in the hope of profit", "A government employee", "A financial investor only"], answer: "Someone who starts a business, taking on financial risks in the hope of profit" },
                { question: "What is a 'business plan'?", options: ["A list of employees", "A document outlining a company's goals, strategies, and financial projections", "A marketing brochure", "A daily schedule of tasks"], answer: "A document outlining a company's goals, strategies, and financial projections" },
                { question: "What does 'MVP' stand for in startup terms?", options: ["Most Valuable Player", "Minimum Viable Product", "Main Venture Project", "Market Value Proposition"], answer: "Minimum Viable Product" },
                { question: "Which of these is a common source of startup funding?", options: ["Retirement pensions", "Friends, Family, and Fools (FFF)", "Government salaries", "Public transport fares"], answer: "Friends, Family, and Fools (FFF)" },
                { question: "What is 'bootstrapping' in business?", options: ["Taking out large bank loans", "Funding a business using personal savings or operating revenues", "Seeking venture capital funding", "Selling off assets"], answer: "Funding a business using personal savings or operating revenues" },
                { question: "What is the primary role of an 'angel investor'?", options: ["To provide bank loans to large corporations", "To provide capital for startup companies, usually in exchange for convertible debt or equity", "To manage daily business operations", "To advise on legal matters"], answer: "To provide capital for startup companies, usually in exchange for convertible debt or equity" },
                { question: "What is a 'pitch deck'?", options: ["A detailed financial spreadsheet", "A brief presentation used to provide an audience with an overview of a business plan", "A document for hiring employees", "A user manual for a product"], answer: "A brief presentation used to provide an audience with an overview of a business plan" },
                { question: "What does 'scale' mean for a startup?", options: ["Reducing business operations", "Increasing revenue with a more than proportional increase in costs", "Increasing revenue with a less than proportional increase in costs", "Selling the business to a larger company"], answer: "Increasing revenue with a less than proportional increase in costs" },
                { question: "What is the 'value proposition' of a business?", options: ["The price of the product", "The core value or benefit a business offers to its customers", "The size of the market", "The number of employees"], answer: "The core value or benefit a business offers to its customers" },
                { question: "Which type of risk is unique to a specific business or investment?", options: ["Market risk", "Systematic risk", "Unsystematic risk", "Inflation risk"], answer: "Unsystematic risk" }
            ]
        }
    };


    function loadQuiz() {
        const quizContentDiv = document.getElementById('quizContent');
        quizContentDiv.innerHTML = ''; // Clear previous questions
        document.getElementById('scoreDisplay').innerText = ''; // Clear score display

        if (!selectedPathFinderInterest || !selectedSubjectForQuiz) {
            quizContentDiv.innerHTML = '<p style="text-align: center; color: #555;">Please go to "Path Finder", select an interest, then choose a subject from "Study Materials" to load a specific quiz.</p>';
            document.getElementById('scoreDisplay').innerText = ''; // Ensure score is clear
            return;
        }

        const questionsForSubject = quizQuestionsBySubject[selectedPathFinderInterest]?.[selectedSubjectForQuiz];

        if (!questionsForSubject || questionsForSubject.length === 0) {
            quizContentDiv.innerHTML = `<p style="text-align: center; color: #555;">No quiz questions found for "${selectedSubjectForQuiz}" yet. Please check back later!</p>`;
            return;
        }

        questionsForSubject.forEach((q, index) => {
            const questionItem = document.createElement('div');
            questionItem.classList.add('quiz-question');
            questionItem.innerHTML = `<p>${index + 1}. ${q.question}</p>`;

            q.options.forEach(option => {
                const label = document.createElement('label');
                label.innerHTML = `
                    <input type="radio" name="question${index}" value="${option}">
                    <span>${option}</span>
                `;
                questionItem.appendChild(label);
            });
            quizContentDiv.appendChild(questionItem);
        });
    }

    function submitQuiz() {
        if (!currentUser) {
            alert('Please log in to submit the quiz.');
            return;
        }

        if (!selectedPathFinderInterest || !selectedSubjectForQuiz) {
            alert('No quiz loaded. Please select an interest and subject first.');
            return;
        }

        const currentQuizQuestions = quizQuestionsBySubject[selectedPathFinderInterest]?.[selectedSubjectForQuiz];
        if (!currentQuizQuestions || currentQuizQuestions.length === 0) {
            alert('Cannot submit. No quiz questions available for the selected subject.');
            return;
        }


        let score = 0;
        const quizContentDiv = document.getElementById('quizContent');
        const questions = quizContentDiv.querySelectorAll('.quiz-question');

        questions.forEach((questionElem, index) => {
            const selectedOption = questionElem.querySelector(`input[name="question${index}"]:checked`);
            const correctAnswer = currentQuizQuestions[index].answer; // Use dynamic questions
            const labels = questionElem.querySelectorAll('label');

            labels.forEach(label => {
                const radio = label.querySelector('input[type="radio"]');
                radio.disabled = true; // Disable all radio buttons after submission

                if (radio.value === correctAnswer) {
                    label.classList.add('correct-highlight'); // Highlight correct answer
                }

                if (selectedOption) {
                    if (selectedOption.value === correctAnswer) { // If this is the correct answer
                         label.classList.add('correct');
                    } else if (selectedOption.value === radio.value) { // If this is the incorrect selected answer
                        label.classList.add('incorrect');
                    }
                }
            });

            if (selectedOption && selectedOption.value === correctAnswer) {
                score++;
            }
        });

        document.getElementById('scoreDisplay').innerText = `You scored ${score} out of ${currentQuizQuestions.length}!`;
        
        // Update user's score for the specific subject
        if (!quizScores[currentUser]) {
            quizScores[currentUser] = {};
        }
        if (!quizScores[currentUser][selectedPathFinderInterest]) {
            quizScores[currentUser][selectedPathFinderInterest] = {};
        }
        quizScores[currentUser][selectedPathFinderInterest][selectedSubjectForQuiz] = score;
        localStorage.setItem('quizScores', JSON.stringify(quizScores));

        displayPerformance(); // Update performance immediately
    }

    // --- Notes Functions ---
    function saveNotes() {
        if (!currentUser) {
            alert('Please log in to save notes.');
            return;
        }
        const notes = document.getElementById('userNotes').value;
        userNotes[currentUser] = notes; // Save notes specific to the current user
        localStorage.setItem('userNotes', JSON.stringify(userNotes));
        document.getElementById('savedNotes').innerText = 'Notes saved successfully!';
        setTimeout(() => {
            document.getElementById('savedNotes').innerText = '';
        }, 3000);
    }

    // --- Performance Functions ---
    function displayPerformance() {
        const performanceSummary = document.getElementById('performanceSummary');
        if (!currentUser) {
            performanceSummary.innerText = 'Please log in to view your performance.';
            return;
        }

        let summaryText = '<h3>Your Quiz Performance</h3>';
        let hasScores = false;

        if (quizScores[currentUser]) {
            for (const interest in quizScores[currentUser]) {
                summaryText += `<p><strong>${interest.charAt(0).toUpperCase() + interest.slice(1)}:</strong></p><ul>`;
                for (const subject in quizScores[currentUser][interest]) {
                    const score = quizScores[currentUser][interest][subject];
                    const totalQuestions = quizQuestionsBySubject[interest]?.[subject]?.length || 0;
                    if (totalQuestions > 0) {
                        summaryText += `<li>${subject}: ${score} out of ${totalQuestions}</li>`;
                        hasScores = true;
                    }
                }
                summaryText += `</ul>`;
            }
        }

        if (!hasScores) {
            summaryText = 'No quiz scores recorded yet. Complete a quiz to see your performance!';
        }
        performanceSummary.innerHTML = summaryText;
    }

    // --- Counseling Functions ---
    const counselors = {
        academic: [
            { name: "Dr. Anya Sharma", expertise: "Study Skills, Exam Anxiety, Time Management", img: "https://via.placeholder.com/150/FFD700/FFFFFF?text=AS" },
            { name: "Prof. David Lee", expertise: "Research Methods, Thesis Support, Academic Writing", img: "https://via.placeholder.com/150/FFA500/FFFFFF?text=DL" }
        ],
        career: [
            { name: "Ms. Emily Chen", expertise: "Career Planning, Resume Building, Interview Prep", img: "https://via.placeholder.com/150/FFD700/FFFFFF?text=EC" },
            { name: "Mr. Robert Green", expertise: "Industry Insights, Job Search Strategies, Networking", img: "https://via.placeholder.com/150/FFA500/FFFFFF?text=RG" }
        ],
        personal: [
            { name: "Ms. Sarah White", expertise: "Stress, Relationships, Self-Esteem, Family Issues", img: "https://via.placeholder.com/150/FFD700/FFFFFF?text=SW" },
            { name: "Dr. Michael Brown", expertise: "Anxiety, Depression, Grief, Personal Growth", img: "https://via.placeholder.com/150/FFA500/FFFFFF?text=MB" }
        ],
        stress: [
            { name: "Dr. Olivia Wilson", expertise: "Mindfulness, Coping Mechanisms, Burnout Prevention", img: "https://via.placeholder.com/150/FFD700/FFFFFF?text=OW" },
            { name: "Mr. Chris Davis", expertise: "Relaxation Techniques, Emotional Regulation, Resilience", img: "https://via.placeholder.com/150/FFA500/FFFFFF?text=CD" }
        ]
    };

    function showCounselingType(type) {
        const counselorProfilesDiv = document.getElementById('counselorProfiles');
        let profilesHtml = '<h4 style="text-align: center; margin-bottom: 20px;">Recommended Counselors</h4>';

        const selectedCounselors = counselors[type] || [];

        if (selectedCounselors.length > 0) {
            selectedCounselors.forEach(counselor => {
                profilesHtml += `
                    <div class="counselor-profile">
                        <img src="${counselor.img}" alt="${counselor.name}">
                        <div class="counselor-details">
                            <h4>${counselor.name}</h4>
                            <p><span class="expertise">Expertise:</span> ${counselor.expertise}</p>
                            <button onclick="alert('Booking feature coming soon for ${counselor.name}!')"><i class="fas fa-calendar-alt"></i> Book Session</button>
                        </div>
                    </div>
                `;
            });
        } else {
            profilesHtml += '<p style="text-align: center; color: #777;">No counselors found for this category yet. Please check back later!</p>';
        }

        counselorProfilesDiv.innerHTML = profilesHtml;
        counselorProfilesDiv.scrollIntoView({ behavior: 'smooth', block: 'start' }); // Scroll to profiles
    }

    // --- FAQ Functions ---
    function toggleFAQ(element) {
        const answer = element.nextElementSibling;
        const arrow = element.querySelector('.faq-arrow');
        if (answer.style.display === 'block') {
            answer.style.display = 'none';
            element.classList.remove('active');
            arrow.style.transform = 'rotate(0deg)'; // Reset arrow
        } else {
            // Close all other open FAQs
            document.querySelectorAll('.faq-question.active').forEach(activeQuestion => {
                activeQuestion.classList.remove('active');
                activeQuestion.nextElementSibling.style.display = 'none';
                activeQuestion.querySelector('.faq-arrow').style.transform = 'rotate(0deg)';
            });
            answer.style.display = 'block';
            element.classList.add('active');
            arrow.style.transform = 'rotate(90deg)'; // Rotate arrow
        }
    }

    // --- Feedback Functions ---
    let selectedRating = 0;

    function rateApp(stars) {
        selectedRating = stars;
        const starElements = document.querySelectorAll('.rating-stars .star');
        starElements.forEach((star, index) => {
            if (index < stars) {
                star.classList.add('selected');
            } else {
                star.classList.remove('selected');
            }
        });
    }

    function submitFeedback() {
        const feedbackText = document.getElementById('feedbackText').value.trim();
        const feedbackMessageDiv = document.getElementById('feedbackMessage');

        if (selectedRating === 0) {
            feedbackMessageDiv.innerText = 'Please select a star rating.';
            feedbackMessageDiv.style.color = '#dc3545';
            return;
        }

        if (feedbackText === '') {
            feedbackMessageDiv.innerText = 'Please enter your feedback.';
            feedbackMessageDiv.style.color = '#dc3545';
            return;
        }

        // Simulate feedback submission
        console.log(`Feedback submitted: Rating = ${selectedRating}, Text = "${feedbackText}"`);
        feedbackMessageDiv.innerText = 'Thank you for your feedback!';
        feedbackMessageDiv.style.color = '#28a745';

        // Clear after submission
        document.getElementById('feedbackText').value = '';
        selectedRating = 0;
        document.querySelectorAll('.rating-stars .star').forEach(star => star.classList.remove('selected'));
        
        setTimeout(() => {
            feedbackMessageDiv.innerText = '';
        }, 3000);
    }

    // --- Initial Load ---
    document.addEventListener('DOMContentLoaded', () => {
        // If a user is logged in, show dashboard, otherwise show login
        if (currentUser) {
            showSection('dashboardPage');
        } else {
            showSection('loginPage');
        }
    });

</script>
</body>
</html>
