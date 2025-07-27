# Resume-Refiner-AI

## Overview

![Diagram.png](https://github.com/BerlynseaTyler/Resume-Refiner-AI/blob/4bca9f8ea85dd700dc8ef496ad57711adb3dc5a3/Diagram)

## AI Agent Flow Diagram

![n8n](https://github.com/BerlynseaTyler/Resume-Refiner-AI/blob/ac4eb81ce47f567123628096fff9e0e77f4e6509/n8n_flow.png)

### Approch Used
This workflow leverages n8n to automate personalized resume feedback using AI. The process begins when a user submits their resume along with the job they’re targeting through a web form. The uploaded resume is parsed into plain text using the Extract from File node, while the job posting is retrieved via an HTTP Request node through a direct URL. Both the resume and job description are then passed to an AI agent node (e.g., OpenAI's GPT model) via the ChatGPT node. The AI is prompted to act as an expert resume writer, analyzing the alignment between the resume and the job requirements. It provides a summary of fit, tailored suggestions for improvement, and a list of relevant ATS (Applicant Tracking System) keywords. The AI’s response is parsed into structured JSON using the Output Parser node, ensuring clean formatting and downstream usability. Finally, the feedback is compiled into an email and delivered to the user via the Send Email node. This end-to-end flow creates a seamless and scalable system for generating high-quality, AI-powered resume insights.

### Challenges Faced
I encountered several challenges during the development of this workflow, particularly around parsing, formatting, and integration. One notable issue was testing the AI output reliably—since the workflow depends on calls to OpenAI, I ran into limitations after exhausting the class' token quota, which made it difficult to iterate quickly on prompt formatting and output structure. Additionally, ensuring that the AI's response remained consistent and parsable across different resume/job combinations required careful prompt engineering and error handling and integrating the parsed data cleanly into the final email also involved fine-tuning the Output Parser to accommodate variations in AI responses while maintaining a user-friendly format.


## Troubleshooting

## Optimization 
