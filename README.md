# Steam Review AI Analyzer 

## Project Overview
This project focuses on automating a repetitive information task: **reading and analyzing large volumes of player feedback.** Instead of manually sifting through hundreds of reviews, this system uses **n8n** and **AI** to collect, clean, and summarize Steam reviews into actionable intelligence.

## The Problem
Researching a game can be difficult because you often have to sift through hundreds of opinions. Many are subjective, written in foreign languages, or even intended as jokes. This lack of reliability makes it hard to make an informed decision.

## The Goal
The goal of this project is to create an automated pipeline that eliminates manual effort by autonomously collecting, translating, and structuring raw player feedback into actionable intelligence.​

---

## Workflow Logic (n8n)
The system follows these logical steps to process information:
1.  **Webhook Trigger:** The system is initiated by a request containing a `game_id`.
2.  **Steam API Fetch:** It automatically calls the Steam Web API to retrieve the latest 80 reviews.
3.  **Split Out:** A dedicated node breaks the data array into individual items for processing.
4.  **Edit Fields:** The system extracts only the raw review text, removing metadata.
5.  **JavaScript Code:** A custom script combines all reviews into one clean block and removes newlines for the AI.
6.  **AI Analysis (Groq/LLM):** The AI reads the combined text to perform sentiment analysis and identify bugs.
7.  **Webhook Response:** The final human-readable summary is sent back to the user.

---

## Inputs and Outputs
* **Inputs:** A Steam `game_id` (AppID) sent via a Webhook GET request.
* **Outputs:** A human-readable AI summary highlighting polished features and technical flaws.

## Role of AI
* **Data Transformation:** Converts "chaotic" raw text into structured insights.
* **Summarization:** Replaces hours of manual reading with a 10-second analysis.
* **Pattern Recognition:** Identifies specific technical problems like "memory leaks" or "stutters" across hundreds of comments.

---

##  How to Run
Trigger the Webhook using a URL like: 
   `https://<your-n8n-url>/webhook/review?game_id=<game_id>`

[Proofread with Gemini 3]
