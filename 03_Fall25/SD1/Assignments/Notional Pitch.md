### David Jackson
COP - 4934 | Senior Design 1



#### Project Description
**I do not want to pitch this to the class, however** a game project that I would could see myself work on is an interactive mystery game where the player takes on the role of a crime investigator in a haunted city. The unique twist is that many clues come from the ghosts of victims and witnesses. Unlike scripted dialogue trees, these non-playable characters (NPCs) are powered by a large language model (LLM). This enables dynamic, realistic conversations that respond directly to what the player says, providing a fresh investigative experience on each playthrough.

The game challenges players to interrogate suspects, analyze evidence, and cross-examine ghost testimonies. Because ghosts may be unreliable, evasive, or even deceptive, players must piece together the truth from imperfect information. The combination of open-ended LLM dialogue and structured crime-solving mechanics makes the gameplay both immersive and unpredictable.

---
#### Concept of Operations

- **Game Loop**:
    1. Player arrives at a new crime scene.
    2. Player explores the environment, collecting physical clues (e.g., fingerprints, notes, murder weapon).
    3. Player summons and converses with the ghost(s) of victims or bystanders using voice or text.
    4. Ghosts respond dynamically through the LLM, sometimes offering useful leads, sometimes red herrings.
    5. Player compiles evidence and ghost testimony into a case file.
    6. Player makes an accusation or submits a final report to solve the crime.
    
- **User Interaction**:
    - **Exploration**: Players navigate a 3D or stylized 2D environment using mouse/keyboard or controller.
    - **Conversation**: Players speak into a microphone or type responses. The LLM interprets the input and generates the ghost’s reply.
    - **Case Management**: A journal system allows players to tag clues, record ghost statements, and connect threads.
        

The end product allows players to experience an evolving detective story where no two interrogations play out the same.

---
#### Notional Tech Stack

- **Frontend/Game Engine**:
    - _Unity_ (C#) for cross-platform support, 3D/2D rendering, and scene management.
    
- **Backend/AI Integration**:
    - _Node.js_ backend service for API requests.
    - Integration with an _LLM API_ (Most likely OpenAI GPT just because thats what I use).
    
- **Voice & Dialogue**:
    - Speech-to-Text: OpenAI Whisper or Google Speech Recognition.
    - Text-to-Speech: Unity’s built-in TTS plugins.
    
- **Database/Storage**:
    - _SQLite_ for storing case data, clue states, and dialogue history.
    
- **Collaboration Tools**:
    - GitHub for version control.
    - Jira for project management.
    

---

An idea like this excites me because it pushes the boundaries of how users can interact with an LLM inside a game. I’m particularly interested in exploring questions such as whether the model should run locally or in the cloud, how response times can be optimized to create seamless player interactions, and how much (or how little) context is truly needed for the model to generate accurate and meaningful replies. These challenges open the door to studying both the technical limitations and the creative possibilities of combining LLMs with immersive gameplay.