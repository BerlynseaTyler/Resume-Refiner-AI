# Resume-Refiner-AI

## Overview

![Diagram.png](https://github.com/BerlynseaTyler/Resume-Refiner-AI/blob/4bca9f8ea85dd700dc8ef496ad57711adb3dc5a3/Diagram)

## AI Agent

### Diagram

![n8n](https://github.com/BerlynseaTyler/Resume-Refiner-AI/blob/ac4eb81ce47f567123628096fff9e0e77f4e6509/n8n_flow.png)

### Approch Used
This workflow leverages n8n to automate personalized resume feedback using AI. The process begins when a user submits their resume along with the job they’re targeting through a web form. The uploaded resume is parsed into plain text using the Extract from File node, while the job posting is retrieved via an HTTP Request node through a direct URL. Both the resume and job description are then passed to an AI agent node (e.g., OpenAI's GPT model) via the ChatGPT node. The AI is prompted to act as an expert resume writer, analyzing the alignment between the resume and the job requirements. It provides a summary of fit, tailored suggestions for improvement, and a list of relevant ATS (Applicant Tracking System) keywords. The AI’s response is parsed into structured JSON using the Output Parser node, ensuring clean formatting and downstream usability. Finally, the feedback is compiled into an email and delivered to the user via the Send Email node. This end-to-end flow creates a seamless and scalable system for generating high-quality, AI-powered resume insights.

### Challenges Faced
I encountered several challenges during the development of this workflow, particularly around parsing, formatting, and integration. One notable issue was testing the AI output reliably—since the workflow depends on calls to OpenAI, I ran into limitations after exhausting the class' token quota, which made it difficult to iterate quickly on prompt formatting and output structure. Additionally, ensuring that the AI's response remained consistent and parsable across different resume/job combinations required careful prompt engineering and error handling and integrating the parsed data cleanly into the final email also involved fine-tuning the Output Parser to accommodate variations in AI responses while maintaining a user-friendly format.

### JSON Reliability 
To ensure that the AI returned JSON reliably, I structured the prompt with clear, strict formatting instructions and specified the exact JSON keys and structure expected in the output. However, due to running out of OpenAI tokens during development, I wasn’t able to fully test and iterate on the prompt to guarantee consistent formatting across different inputs. Had I had enough tokens, I would have conducted a wider range of test cases using varied resume and job post inputs to identify edge cases where the AI might deviate from the expected format. I also would have refined the prompt incrementally, validating the response through the Output Parser in n8n to catch and correct inconsistencies early in the flow.

## Troubleshooting
During troubleshooting, I ran into several issues with getting consistent and structured output from the AI, especially when working with dynamic resume and job posting content. To work through these challenges, I visited the Kura Labs study room and collaborated with a few of my classmates. They helped me walk through the workflow step by step, using classmates' workflows who were completed before ethe expirations of Open AI tokens, identify where breakdowns were occurring—particularly with the AI response formatting—and suggested strategies for making the prompt more robust. This peer support was instrumental in clarifying where the problem was rooted and reinforced the value of community and being vunerable when asking for help when tackling technical blockers.

## Optimization 
In future iterations, I would focus on optimizing the AI to perform deeper contextual analysis—specifically, enabling it to detect when software, tools, or methodologies mentioned in the job posting may have already been used by the applicant in a previous role but were not explicitly highlighted in their resume. By doing so, the AI could suggest more targeted and impactful bullet points that help the user better showcase relevant experience. This would enhance the personalization and relevance of the suggestions, making the resume more competitive. 
