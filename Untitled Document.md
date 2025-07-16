gamebet-arena-backend

gamebet-arena-backend/package.json

{
  "name": "gamebet-arena-backend",
  "version": "1.0.0",
  "main": "src/index.ts",
  "scripts": {
    "start": "ts-node src/index.ts"
  },
  "dependencies": {
    "cors": "^2.8.5",
    "dotenv": "^16.0.3",
    "express": "^4.18.2",
    "pg": "^8.8.0",
    "drizzle-orm": "^0.29.2"
  },
  "devDependencies": {
    "@types/express": "^4.17.17",
    "ts-node": "^10.9.1",
    "typescript": "^5.0.4"
  }
}


gamebet-arena-backend/tsconfig.json

{
  "compilerOptions": {
    "target": "ES2020",
    "module": "CommonJS",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
  }
}


gamebet-arena-backend/.env

DATABASE_URL=postgres://username:password@host:port/dbname
PORT=3000

gamebet-arena-backend/src

gamebet-arena-backend/src/index.ts

import express from "express";
import cors from "cors";
import dotenv from "dotenv";

dotenv.config();

const app = express();
app.use(cors());
app.use(express.json());

app.get("/", (req, res) => {
  res.send("🎮 GameBet Arena API is running!");
});

// Example API route:
app.get("/api/currencies", (req, res) => {
  res.json([
    { code: "USD", name: "US Dollar", symbol: "$" },
    { code: "NGN", name: "Naira", symbol: "₦" }
  ]);
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});