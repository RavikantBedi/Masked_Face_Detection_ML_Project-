# Masked Face Detection ML Project

A web-based dashboard for masked face recognition. Upload an image containing a masked face, and the system reconstructs the full face through a multi-stage pipeline (upper-face extraction, candidate selection, rotation estimation via SURF, face reconstruction, and final CNN-based recognition), then returns the identified subject with a confidence score.

![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)

## Features

- **Masked face input** — upload or capture masked face images for recognition
- **Six-stage recognition pipeline** — input validation → upper-face extraction → candidate selection (CNN-2) → rotation estimation (SURF) → face reconstruction → final recognition (CNN-1)
- **Single image & batch processing** modes
- **Recognition results** with confidence scoring and downloadable text/JSON reports
- **Activity logs & metrics** — track recognition history and performance stats
- **Database management** — view subjects and recognition databases (DB-1/DB-2/DB-3)
- **Responsive dashboard** built with shadcn-ui + Tailwind CSS
- **Supabase backend** for auth, storage, and database

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | React 18 + TypeScript |
| Build tool | Vite 5 |
| Styling | Tailwind CSS + shadcn-ui |
| Backend | Supabase (auth, database, storage) |
| State | TanStack Query, React Hook Form |
| Charts | Recharts |
| Testing | Vitest + Testing Library |
| Linting | ESLint |

## Recognition Pipeline

```
Upload Masked Face
        ↓
Extract Upper Face Region (DB-1)
        ↓
Candidate Selection via CNN-2 (DB-1 → DB-2)
        ↓
Rotation Estimation via SURF (DB-2)
        ↓
Face Reconstruction (DB-3)
        ↓
Final Recognition via CNN-1 (FaceNet/VGG16)
        ↓
Identified Subject + Confidence Score
```

## Getting Started

### Prerequisites

- Node.js 18 or higher
- npm / bun / yarn
- A Supabase project (for backend services)

### Installation

```sh
# 1. Clone the repository
git clone https://github.com/RavikantBedi/Masked_Face_Detection_ML_Project-.git

# 2. Navigate to the project directory
cd Masked_Face_Detection_ML_Project-

# 3. Install dependencies
npm install
# or: bun install
```

### Environment Setup

Create a `.env` file in the project root:

```sh
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your-publishable-anon-key
VITE_SUPABASE_PROJECT_ID=your-project-id
```

Get these values from your Supabase project settings → API. Never commit your `.env` file (it is already in `.gitignore`).

### Running Locally

```sh
# Start the development server
npm run dev

# Open the app
# http://localhost:5173
```

### Production Build

```sh
npm run build
npm run preview   # serve the production build locally
```

## Available Scripts

| Script | Description |
|--------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build |
| `npm run lint` | Run ESLint |
| `npm run test` | Run Vitest test suite |

## Project Structure

```
maskface-main/
├── public/              # Static assets
├── src/
│   ├── components/      # Reusable UI components (shadcn-ui)
│   ├── components/dashboard/  # Dashboard-specific components
│   ├── components/layout/     # Layout components (sidebar, header)
│   ├── contexts/      # React context providers (auth)
│   ├── hooks/         # Custom hooks (recognition logs, file upload)
│   ├── integrations/supabase/ # Supabase client & types
│   ├── lib/           # Utility functions
│   ├── pages/         # Route pages (Recognition, Pipeline, Activity, etc.)
│   ├── test/          # Test setup & examples
│   ├── App.tsx        # App entry & routing
│   └── main.tsx       # React mount point
├── supabase/          # Supabase migrations & edge functions
├── index.html
├── vite.config.ts
├── tailwind.config.ts
├── tsconfig.json
└── package.json
```

## Usage

1. Start the app (`npm run dev`) and open `http://localhost:5173`
2. Sign in / sign up via the Auth page
3. Go to **Recognition** → upload a masked face image
4. Click **Recognize** to run the pipeline
5. View the identified subject and confidence score
6. Download the result as a text or JSON report
7. Browse **Activity** for logs and **Metrics** for performance stats

## Supabase Setup

1. Create a new project at [supabase.com](https://supabase.com)
2. Run the migrations under `supabase/migrations/` in the SQL editor
3. Copy your project URL, anon key, and project ID into `.env`
4. Configure storage buckets as needed for uploaded face images

## License

This project is licensed under the MIT License.
