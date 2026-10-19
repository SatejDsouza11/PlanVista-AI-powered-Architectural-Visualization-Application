# PlanVista: AI Architectural Visualization

PlanVista turns 2D floor plans into photorealistic 3D-style renders using AI image models. Upload a floor plan, generate a render, compare the two side by side, and keep a gallery of your projects.

## Features

- **2D to 3D rendering**: AI-generated renders from an uploaded floor plan
- **Side-by-side comparison**: slider to compare the source plan with the render
- **Project gallery**: history of your visualizations with saved metadata
- **Persistent hosting**: uploads and renders get permanent public URLs
- **Public / private toggle**: choose whether a project is visible to others
- **Export**: download renders as images

## Tech Stack

| Area | Technology |
|---|---|
| Frontend | React 19, React Router 7, TypeScript, Tailwind CSS 4, Vite |
| Cloud / AI | [Puter.js](https://developer.puter.com/): auth, file storage, key-value store, serverless worker, AI image generation |
| UI | lucide-react, react-compare-slider |
| Deployment | Docker (Node 20) |

## Project Structure

```
app/            Routes and root layout (home, visualizer)
components/     Navbar, Upload, UI components
lib/            Puter actions, AI call, hosting, constants, utilities, worker
public/         Static assets
```

## Getting Started

**Prerequisites:** Node.js 20+ and npm.

```bash
npm install
cp .env.example .env     # Windows: copy .env.example .env
npm run dev
```

Set `VITE_PUTER_WORKER_URL` in `.env` to the URL of your deployed Puter worker (`lib/puter.worker.js`). Create a free account at [puter.com](https://puter.com) to deploy it.

The app runs at http://localhost:3000.

### Scripts

| Command | Description |
|---|---|
| `npm run dev` | Start the dev server |
| `npm run build` | Production build |
| `npm start` | Serve the production build |
| `npm run typecheck` | Generate route types and run `tsc` |

### Docker

```bash
docker build -t planvista .
docker run -p 3000:3000 planvista
```
