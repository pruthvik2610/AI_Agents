
POV VIDEO AGENT - README

Overview:
-----------
This is an n8n-based automation workflow that generates immersive first-person POV videos from text prompts. The system takes a topic and environment as inputs from Google Sheets, generates an image prompt, synthesizes the image using Together AI, and renders a video using a custom Flask API.

How It Works:
--------------
1. **Trigger**:
   - Manual trigger via “Test Workflow” or scheduled runs.

2. **Input Source**:
   - Fetches the next row from a connected Google Sheet where `status = pending`.

3. **Prompt Generation**:
   - Uses Google Gemini models to craft a sensory-rich, first-person image prompt based on topic and environment.
   - Follows a structured template with limb interaction, sensory details, and cultural context.

4. **Image Generation**:
   - Calls Together AI API using the `black-forest-labs/FLUX.1-schnell-Free` model.
   - Converts the base64 image response into a binary file and saves it locally.

5. **Video Generation**:
   - Sends the image and prompt to a local Flask API at `http://host.docker.internal:505/run`.
   - Video is rendered and saved as `.mp4`.

6. **Final Processing**:
   - Executes a post-processing step.
   - Updates the status in the Google Sheet to reflect completion.
   - Saves final output for record-keeping.

Credentials Required:
----------------------
- **Google Sheets OAuth2**: For reading and writing Google Sheets.
- **Google Gemini (PaLM) API**: For generating rich language prompts.
- **Together AI API Key**: For image generation using Stable Diffusion-like models.
- **Local Flask Video API**: Must be running and accessible at `localhost:5005`.

File Structure:
----------------
- `images/` — Stores intermediate images.
- `video.mp4` — Final output video.
- Google Sheet — Stores inputs and workflow status.

Customization:
---------------
- Modify the prompt structure in the "Generate Prompt(Agent)" nodes.
- Change image resolution or model settings in the HTTP request node to Together AI.
- Adapt Flask API logic to change video rendering style.

Run Instructions:
------------------
1. Start the local Flask API server.
2. Ensure API keys and OAuth credentials are configured in n8n.
3. Click “Test Workflow” or automate with a trigger.
4. Monitor video and log output in your defined `images/` and `video/` directories.

Author:
--------
Created by Rithvik  
Modular, extensible, and designed for creative POV storytelling using AI.
