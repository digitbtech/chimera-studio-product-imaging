# Stack

Only what the project source and the portfolio case study show.

| Layer | Technology | Why |
|---|---|---|
| Backend | FastAPI, Uvicorn, Gunicorn, Pydantic | Typed API, background tasks |
| Data | PostgreSQL, SQLAlchemy, Supabase (database, auth, storage) | Managed data and object storage |
| Cutout | U2Net on PyTorch | Clean product masks, runs on CPU or GPU |
| Generation | Hosted Gemini image model through the Google GenAI SDK | One call returns the finished flat-lay |
| Image handling | Pillow, pillow-heif, scikit-image | HEIC phone photos, resize, watermark |
| Payments | Stripe | Plans, credit packs, pay-to-unlock |
| Auth | python-jose, passlib with bcrypt, Google OAuth | JWT sessions, social sign-in |
| Frontend | React 18, Vite, Tailwind CSS, Radix UI, Wouter, Zustand, TanStack Query | Fast single page app |
| Deploy | Docker Compose, Nginx | Two containers behind a proxy |
| Optional cache | Redis client is in the requirements | Case study describes Redis for repeated prompt and image pairs |

## Research models (case study)

SegFormer, ControlNet, InstructPix2Pix, Stable Diffusion XL, Real-ESRGAN. Discarded after testing: DALL-E 3, Runway Gen-2, Runway Inpainting v1. Reasons are in the case study.

## Dataset tooling

Small Python scripts: convert to PNG, pair before and after files, build a Hugging Face dataset, and score pair similarity with a vision model to filter bad pairs.
