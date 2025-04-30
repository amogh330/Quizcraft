# Quizcraft  
Developed an end-to-end system that automatically creates multiple-choice quizzes from a given syllabus, question count, and difficulty level. Built a simple Streamlit interface powered by Meta-Llama-3.2 for AI-driven question generation, with one-click export to Google Forms and secure backup on Google Drive—cutting quiz-preparation time by over 80% and ensuring consistency across assessments.


Step-by-step workflow of the project:
---

## 1. Setup & Installation  
1. **Clone Repository**  
   ```bash
   git clone https://github.com/your-org/ai-mcq-generator.git  
   cd ai-mcq-generator
   ```  
2. **Install Dependencies**  
   ```bash
   pip install -r requirements.txt
   ```  
3. **Configure Environment**  
   - Create a `.env` file with:  
     ```
     SECRET_KEY=your_secret_key
     GOOGLE_CLIENT_ID=…
     GOOGLE_CLIENT_SECRET=…
     ```  
   - Enable Google Forms & Drive APIs in your Google Cloud project and download credentials.

---

## 2. Ollama Setup & Configuration  
1. **Install Ollama CLI**  
   - macOS: `brew install ollama`  
   - Linux: follow instructions at https://ollama.com/docs/installation  
2. **Pull the LLM**  
   ```bash
   ollama pull meta/llama-3.2
   ```  
3. **Run the Ollama Server**  
   ```bash
   ollama serve
   ```  
4. **Test the Model Endpoint**  
   ```bash
   ollama run meta/llama-3.2 --prompt "Sample question?"  
   ```  
5. **Configure in App**  
   - Set `OLLAMA_API_URL=http://localhost:11434` (or your host/port) in `.env`.

---

## 3. User Authentication  
- On app start, users enter the **Secret Key** you share with them.  
- For Google export/storage, they complete OAuth 2.0 consent to grant Forms/Drive scopes.

---

## 4. Input & Parameter Collection  
1. **Streamlit UI**  
   - Text field or file upload for **syllabus** description.  
   - Number input for **question count**.  
   - Dropdown or slider for **difficulty/tone**.  
2. **Submit** triggers the backend pipeline.

---

## 5. AI-Powered MCQ Generation  
- Backend receives inputs and calls the **Meta-Llama-3.2** model via the Ollama endpoint.  
- The model returns a list of MCQs, each with:  
  - Question stem  
  - Four options (one correct, three distractors)  
  - (Optional) Explanations or tags

---

## 6. Preview & Editing  
- Generated MCQs are rendered in the Streamlit app.  
- Professors can:  
  - **Edit** question text or options inline  
  - **Delete** any unwanted items  
  - **Re-generate** individual questions if needed

---

## 7. Export to Google Forms  
1. **Google Forms API**  
   - A new form is created with the quiz title and settings.  
2. **Populate Questions**  
   - Each MCQ is added as a multiple-choice item via API calls.  
3. **Retrieve Form Link**  
   - The live Form URL is displayed for sharing.

---

## 8. Backup to Google Drive  
- The finalized Form’s metadata and a JSON export of all questions are saved to a dedicated folder in the user’s Drive.  
- Filenames include timestamp and syllabus name for easy retrieval.

---

## 9. Logging & Monitoring  
- All operations (generation requests, exports, edits) are logged to a local file or cloud logging service.  
- Errors in API calls trigger user notifications and fallbacks.
---
## File is uploaded onto a google drive rather than a zip file 
- so heres the link for it:https://drive.google.com/drive/folders/1B77VqgBei4npwUDmoiMm46CSJDFXGda7?usp=sharing
---
## After this the running is done thru windows powershell
- step1: change directory to the path of folder
- step2: type this command:- venv\Scripts\activate
- step3: then this cmd:- streamlit run C:\your_filepath\streamlitapp.py
after this it must redirect u to the webpage ,if it doesnt work,pls check ur ollama and folder destination
