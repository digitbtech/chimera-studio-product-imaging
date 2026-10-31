# Chimera Studio: product image synthesis

Turns one phone photo of a garment or accessory into a clean, studio style flat-lay image. The platform launched as LayFlat AI and was later renamed Chimera Studio.

Who it is for: online sellers who need many clean product images without a photoshoot or hours of retouching.

Status: delivered. Built for Chimera Compound LLC (Oct 2025 to Dec 2025). This is a live client system, so this repository holds documentation only. No source code, configuration or infrastructure identifiers are published.

Full write-up: https://digitb.tech/case-study/chimera-studio/
Portfolio: https://digitb.tech

## What it does

- Accepts a product photo (including HEIC phone photos) and a product category.
- Removes the background with U2Net.
- Generates a flat, wrinkle-free, centered image with a hosted image model.
- Lets a user edit a result with a short text instruction.
- Shows anonymous users a watermarked preview, and unlocks the clean image after payment or with credits.

## How it works (short)

1. The user uploads a photo through the web app.
2. The API checks the user tier and credit balance.
3. A background job runs the pipeline. With a background: U2Net first, then generation. Transparent output: generation first, then U2Net.
4. The result is stored in object storage and returned as a preview or a full image.

The generation prompt is mostly a set of constraints: keep the logo exactly, keep the fabric texture, remove clutter, no model in the frame. See [docs/architecture.md](docs/architecture.md).

## Stack

Python and FastAPI backend, React and Vite frontend, PostgreSQL with Supabase for data, auth and storage, Stripe for payments, U2Net for cutouts, a hosted Gemini image model for generation. See [docs/stack.md](docs/stack.md).

## Two model stories

The portfolio case study describes a staged research pipeline: SegFormer, ControlNet, InstructPix2Pix, SDXL and Real-ESRGAN, tested against a photographer-approved set. The shipped application source in the project folder runs U2Net plus a hosted image model. Both are part of the work. This repository does not claim that the research models are the ones serving the live site. The case study is the source for the research details.

## Fine-tuning data

The project folder also holds scripts that pair before and after images, convert them to PNG, and build a Hugging Face dataset with one fixed prompt per image. The images are customer material and are not published here.

## Built on

U2Net, Hugging Face models, FastAPI, Supabase, Stripe, shadcn/ui components and Radix UI on the frontend. Full list in [REFERENCES.md](REFERENCES.md).
