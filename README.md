# Toonie

Toonie is a web platform where you describe an animation in plain English and it generates the actual p5.js code and shows you a live preview instantly. You can record those animation previews as clips, arrange them on a timeline, and export them all as a single video. It's basically a creative tool that sits between a text editor and a video editor, powered by AI.


## 🛠️ Technologies

- React + Vite (Frontend)
- NestJS (Backend)
- p5.js (Animation engine)
- OpenRouter API (LLM for code generation)
- TypeScript
- CSS



## ✨ Features

- You type a prompt like "make a bouncing ball that changes color" and the AI generates the p5.js code and runs it live on screen
- You can chat with the AI to ask questions about animations or request changes to what's already generated
- The generated code is fully visible — you can edit it yourself too, not just rely on the AI
- Record any running animation as a video clip and save it
- A timeline-based video editor where you can drag, drop, and reorder all your saved clips
- Export the final assembled timeline as one single video file
- Non-animation queries are filtered out so the AI stays on topic



## 🎬 The Loop Is Closed — And That Changes Everything

The fact that the AI doesn't just return code — it returns *runnable* code that immediately previews in the browser. Most AI code tools give you code and then you have to go somewhere else to run it. Here, the loop is closed. You prompt, you see it move, you record it. That's a genuinely different experience.



## 🔧 Process

I started by figuring out the core loop — prompt in, animation out. The frontend needed to send a user's text to the backend, get p5.js code back, and then render that code live in a canvas element without refreshing the page. That part took some thinking because dynamically executing p5.js in a React app isn't as straightforward as just dumping code into a script tag.

Once the generation and preview were working, I built the chat layer on top of it. The AI needed context about what it had already generated so it could make adjustments when you asked for changes. The backend handled conversation history to keep the context alive across messages.

After the core was solid, I added clip recording using the browser's MediaRecorder API. Users can hit record while the animation is running and it saves that segment as a downloadable clip. This was honestly one of the more finicky parts — getting the canvas stream into a proper video format took some trial and error.

Finally, I built the video editor — a timeline where you can drop all your clips, reorder them, and export them as one merged video. This tied everything together and made the tool feel complete rather than just a code generator.



## 📚 What I Learned

- **Dynamic code execution in the browser** — how to safely evaluate and run p5.js sketch code inside a React component without blowing up the app
- **MediaRecorder API** — how to capture a canvas stream, record it in chunks, and assemble those chunks into a downloadable video blob
- **NestJS basics** — this was my first real exposure to it; setting up modules, controllers, and services felt very different from Express
- **Managing AI context** — how to pass conversation history back and forth so the AI remembers what it generated and can build on it
- **Timeline UI logic** — handling drag-and-drop ordering on a custom video editor without a library



## 🌱 Overall Growth

This project pushed me into territory I hadn't been in before — real-time canvas manipulation, browser-native video recording, and building a product that actually feels creative and fun to use. It made me think about AI tools differently: not just "what can the AI do" but "what does the full loop around the AI look like for the user."



## 🚀 Running the Project
```bash
git clone https://github.com/SarthakKala/Toonie.git
cd Toonie

cd Frontend
npm install
# Create Frontend/.env with:
# FRONTEND_URL=http://localhost:5173
# BACKEND_URL=http://localhost:3000
npm run dev

# In a separate terminal:
cd ../backend
npm install
# Create backend/.env with:
# PORT=3000
# FRONTEND_URL=http://localhost:5173
# OPENROUTER_API_KEY=your_key_here
npm run start:dev
```

<!--
---

## 🎥 Video
-->

<!-- Attach your demo video here -->
