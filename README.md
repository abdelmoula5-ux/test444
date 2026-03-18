import express from 'express';
import { fileURLToPath } from 'url';
import path from 'path';

const app = express();
const __dirname = path.dirname(fileURLToPath(import.meta.url));

// Serve static files from current directory
app.use(express.static(__dirname));

// All routes → quizpulse.html (SPA)
app.get('*', (req, res) => {
  res.sendFile(path.join(__dirname, 'quizpulse.html'));
});

const PORT = process.env.PORT || 8080;
app.listen(PORT, () => {
  console.log(`QuizPulse running on port ${PORT}`);
});
