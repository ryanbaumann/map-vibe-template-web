# Map Vibe Template - Web

![GeoMob SF Presentation](./GeoMob%20SF%20Vibe%20with%20Maps%20Presentation%20-%20April%2015%202025%20-%20Ryan%20Baumann.pdf)

![Screenshot 2025-04-13 at 11 03 59 AM](https://github.com/user-attachments/assets/bdea5752-5bcf-4fa6-b12b-6d3e3bbbe00a)

Context and examples for "vibe coding" with Google Maps Platform (GMP) on the web using Large Language Models (LLMs).

## Overview

This template provides the necessary context and structure to enable rapid prototyping and development of GMP web applications using AI assistants like Google's Gemini, integrated into various developer tools and IDEs. This approach, often called "vibe coding," leverages LLMs to generate functional map application code based on natural language prompts and curated context.

The core idea is to provide the LLM with high-quality, minimal, complete code examples and structured templates (`gmp_llms_v2.txt`) along with specific instructions (`system_prompt_gmp.txt`) to guide its code generation process effectively.

## Prerequisites

Before you start, you will need:

1.  **A Google Maps Platform API Key:**
    *   Create one in the Google Cloud Console.
    *   **Crucially, secure your API key!** Apply both **HTTP referrer restrictions** (to limit usage to your specific web domains/localhost) and **API restrictions** (to limit the key to only the necessary GMP APIs like Maps JavaScript API, Places API, Routes API, etc.).
2.  **A Map ID (for 2D Vector Maps):**
    *   Create a Map ID in the Google Cloud Console associated with the Vector map type. This is required for using modern features like 2D Vector Maps and Advanced Markers. 3D Maps do not use a Map ID.

**Note:** Do not commit your API key or Map ID directly into code or shared context files. Use placeholders or environment variables.

## Core Components

*   **`gmp_llms_v2.txt`:** This is the primary context file. It contains curated best practices, modern API usage patterns (Maps JavaScript API, Places API (New), Routes API), code snippets, and complete HTML/CSS/JS templates for both 2D and 3D map applications using vanilla JavaScript and Tailwind CSS. This file is designed to be fed into the LLM's context window to guide code generation. **It explicitly instructs the LLM not to include code comments in the output.**
*   **`system_prompt_gmp.txt`:** This file provides high-level instructions for the LLM assistant, defining its role, the desired tech stack (Vanilla JS, Tailwind), core principles (security, modern APIs, cost control), and the expected output format (single `index.html`). You should customize this prompt, especially by replacing the placeholder `YOUR_API_KEY` and `YOUR_MAP_ID` with your actual credentials *within your specific tool's configuration or prompt*, not directly in this template file.

## How to Use (General Workflow)

1.  **Provide Context:** Load the contents of `gmp_llms_v2.txt` into your chosen AI assistant's context window or knowledge base.
2.  **Provide System Instructions:** Load the contents of `system_prompt_gmp.txt` as the system prompt or initial instructions for the AI assistant. **Remember to replace the placeholder API Key and Map ID within your tool's settings or your prompt.**
3.  **"Vibe" / Prompt:** Give the AI assistant natural language instructions for the map application you want to build. Be specific about features (e.g., "Show nearby coffee shops," "Calculate a route," "Display 3D buildings," "Use the Place Details UI Kit component").
    *   *Example Prompt:* "Create a 2D map centered on San Francisco that searches for nearby parks within 2km using the Places API (New). Display the results as markers and in a list. When a marker or list item is clicked, show the place details using the `gmp-place-details` web component in a side panel."
4.  **Generate Code:** The AI assistant will use the provided context and system prompt to generate a single `index.html` file containing all the necessary HTML, CSS (via Tailwind CDN and minimal inline styles), and modern vanilla JavaScript (`<script type="module">`).
5.  **Test & Iterate:**
    *   Save the generated code as `index.html`.
    *   Open the file in your web browser.
    *   If you encounter errors or want changes, copy the error message or describe the desired modification back to the AI assistant. It will refine the code based on your feedback.
    *   Commit working versions frequently.

## Usage Examples with Different Tools

The core principle is always to provide the `gmp_llms_v2.txt` as context and `system_prompt_gmp.txt` (with your keys filled in) as instructions.

### Google AI Studio / Gemini Web UI

1.  Start a new chat.
2.  In the initial prompt area or system instructions section, paste the content of `system_prompt_gmp.txt`. **Replace `YOUR_API_KEY` and `YOUR_MAP_ID` with your actual values.**
3.  In a separate message or attached file, provide the content of `gmp_llms_v2.txt`. You might need to tell the model explicitly: "Use the following text as detailed context and instructions for generating Google Maps Platform code:" followed by the content.
4.  Start prompting with your desired map features.

### Cline in VS Code

Cline is particularly well-suited for this workflow as it's an agent integrated into your IDE.

1.  Open your project folder (containing these template files) in VS Code with the Cline extension installed.
2.  Start a new chat with Cline.
3.  **Provide Context:** Use the `@` symbol to reference the files:
    *   Type `@gmp_llms_v2.txt` and press Enter/Tab to add its content to the chat context.
    *   Type `@system_prompt_gmp.txt` and press Enter/Tab.
4.  **Instruct Cline:** Tell Cline how to use the context and provide your keys (do this securely, perhaps via instructions rather than pasting keys directly in chat if possible, or ensure your chat history is managed appropriately):
    *   "Use `system_prompt_gmp.txt` as the main instructions. Use `gmp_llms_v2.txt` as the detailed technical guide and template source. My API key is [Your Actual API Key] and my Map ID is [Your Actual Map ID]. Now, [Your map request, e.g., 'create a 3D map showing markers for major landmarks in London']."
5.  Cline will generate the `index.html` file. You can ask it to create/overwrite the file directly in your workspace.

### Other Tools (Cursor, GitHub Copilot Chat, etc.)

1.  Consult the specific tool's documentation on how to provide large context files or system prompts.
2.  **Context:** Find the mechanism to provide the content of `gmp_llms_v2.txt` (e.g., pasting into a context field, referencing a file, using a specific command).
3.  **System Prompt:** Find the mechanism to set the system prompt or initial instructions using the content of `system_prompt_gmp.txt`. **Remember to securely insert your API Key and Map ID.**
4.  Start prompting with your map requirements.

## Tips for Success

*   **Be Specific:** Clear, detailed prompts lead to better results. Mention desired APIs, features, and map types.
*   **Iterate:** Don't expect perfection on the first try. Use errors and feedback to refine the generated code with the AI assistant.
*   **Focus on Patterns:** The context file emphasizes modern JavaScript (async/await, modules) and specific GMP patterns. Stick to these when prompting.
*   **Security:** Always handle your API keys securely and apply the necessary restrictions in the Cloud Console.
