# MedScope AI

[![IEEE TechSangam 2025](https://img.shields.io/badge/IEEE-TechSangam%202025-orange)](https://techsangam.mitadtc.edu.in/)
[![Theme: Healthcare](https://img.shields.io/badge/Theme-Healthcare-green)](https://techsangam.mitadtc.edu.in/)
[![PS Category: Software](https://img.shields.io/badge/PS_Category-Software-blue)](https://techsangam.mitadtc.edu.in/)
[![Team: Pragati](https://img.shields.io/badge/Team-Pragati-purple)](https://techsangam.mitadtc.edu.in/)

## Overview

MedScope AI is an innovative, full-stack AI-powered web application designed to bridge the communication gap between patients and healthcare providers. It addresses the challenge of complex medical images (e.g., brain MRIs, chest X-rays, CT scans) and diagnostic reports by providing easy-to-understand, plain-language explanations, pseudo-3D visualizations, and interactive insights. 

The platform empowers patients with instant AI-generated summaries and aids professionals in triage and workflow efficiency. Key innovations include multimodal AI interpretation, 2D-to-3D scan reconstruction, multilingual support, an AI chatbot for queries, and automated PDF report generation/parsing.

Built for the IEEE TechSangam 2025 hackathon (Theme: Healthcare, Domain: Healthcare, PS Category: Software) by Team **Pragati** at MIT-ADT University.

### Problem It Solves
- **Patient Confusion & Anxiety**: Technical medical data is hard for non-experts to interpret, leading to poor decisions.
- **Provider Overload**: Doctors lack time to simplify reports for every patient.
- **Accessibility Gaps**: Especially in rural/underserved areas with limited specialist access.

### Core Value Proposition
One platform to analyze medical data and empower patients—delivering secure, smart insights from scans and reports.

## Features

### Patient-Facing
- **Upload & Analyze**: Securely upload MRIs, X-rays, CT scans, or diagnosis PDFs.
- **Pseudo-3D Visualizations**: Convert 2D scans to interactive 3D-like models for enhanced clarity (using depth estimation).
- **Plain-Language Summaries**: AI-generated reports highlighting abnormalities, in simple English (downloadable PDFs).
- **Multilingual Support**: Translations for global accessibility.
- **AI Chatbot**: Interactive Q&A on diagnoses, symptoms, or reports.
- **Expert Matching**: Connect with relevant medical specialists for consultations (future integration).

### Provider-Facing
- **Triage Tools**: Initial analysis, abnormality detection, and prioritization.
- **Workflow Efficiency**: Reduces diagnostic delays with automated insights.
- **Feedback Loop**: Doctor annotations and report sharing.

### Innovation Highlights
- **Multimodal AI Interpretation**: Combines image segmentation, depth estimation, and NLP for comprehensive analysis.
- **2D-to-3D Reconstruction**: Generates interactive 3D models from 2D inputs.
- **Automated Report Generation**: Custom PDF summaries with confidence scores and disclaimers.
- **Privacy-First**: Anonymized, encrypted data handling; modular design for scalability.

### Impact & Benefits
| Audience | Benefits |
|----------|----------|
| **Patients & Caregivers** | Instant summaries of complex data; enhances diagnosis understanding; reduces anxiety in remote areas. |
| **Healthcare Professionals** | Assists in triage/prioritization; cuts delays and improves efficiency. |
| **Social** | Boosts healthcare literacy in underserved communities. |
| **Economic** | Lowers hospital visits and pre-consultation costs. |
| **Technological** | Bridges AI innovations to real-world healthcare. |
| **Scalability** | Extensible to new scan types, languages, and telehealth. |

## Tech Stack

### Frontend
- **React.js** with **Tailwind CSS** for responsive, interactive UI (e.g., visual viewer, upload dashboard).

### Backend
- **Next.js/Django** with **Python** for API handling, user auth, and file processing.
- **PostgreSQL** for secure data storage (user profiles, anonymized scans, reports).

### AI/ML
- **PyTorch/TensorFlow** for core models.
- **OpenCV** for image preprocessing.
- **MiDaS/DenseDepth** for depth estimation (2D-to-3D conversion).
- **U-Net/nnU-Net** for medical image segmentation (e.g., MRI abnormality detection).
- **PDF Parsers**: PyMuPDF/PDFPlumber for report extraction.
- **NLP Tools**: For plain-language summaries and multilingual translation (e.g., Hugging Face models).
- **AI Chatbot**: Integrated via LangChain or similar for conversational insights.

### Infrastructure
- **Cloud Storage**: AWS/Hugging Face for GPU-accelerated processing.
- **Deployment**: Flask/FastAPI for modular backend; supports simulated data for development.

### Unique Tech Points
- AI-driven 3D visualization from 2D scans.
- Integrated expert consultation matching.
- Multi-language chatbot with PDF parsing for accessibility.

## Installation & Setup

### Prerequisites
- Node.js (v18+)
- Python 3.10+
- PostgreSQL 13+
- Git

### Quick Start
1. **Clone the Repo**:
   ```
   git clone https://github.com/yourusername/medscope-ai.git
   cd medscope-ai
   ```

2. **Frontend Setup**:
   ```
   cd frontend
   npm install
   npm run dev  # Runs on http://localhost:3000
   ```

3. **Backend Setup**:
   ```
   cd backend
   pip install -r requirements.txt  # Includes PyTorch, TensorFlow, OpenCV, etc.
   cp .env.example .env  # Add DB creds, API keys
   python manage.py migrate  # For Django/Next.js setup
   python manage.py runserver  # Runs on http://localhost:8000
   ```

4. **Database**:
   - Create a PostgreSQL DB: `createdb medscope_db`
   - Update `.env` with connection strings.

5. **AI Models**:
   - Pre-trained models (U-Net, MiDaS) auto-download on first run.
   - For GPU: Ensure CUDA setup; fallback to CPU/Colab for dev.

6. **Run the App**:
   - Access via `http://localhost:3000`.
   - Test uploads with sample DICOM/PDF files (included in `/samples`).

### Environment Variables
| Key | Description | Example |
|-----|-------------|---------|
| `DATABASE_URL` | Postgres connection | `postgresql://user:pass@localhost/medscope_db` |
| `SECRET_KEY` | App secret | `your-secret-key` |
| `AWS_ACCESS_KEY` | Cloud storage (optional) | `your-aws-key` |
| `HUGGINGFACE_TOKEN` | For model downloads | `hf_your_token` |

## Usage

1. **Register/Login**: Patients create accounts for secure access.
2. **Upload Data**:
   - Drag-and-drop scans (DICOM/JPG) or PDFs.
   - App processes: Segments abnormalities → Estimates depth → Generates 3D model → Creates summary.
3. **View Insights**:
   - Interactive 3D viewer (rotate/zoom).
   - Chatbot: "Explain this MRI in Hindi."
   - Download PDF report with disclaimers.
4. **Expert Flow**: Submit for doctor review; receive feedback.
5. **Demo Mode**: Use `/samples` for simulated data (no real uploads needed).

**Example Workflow**:
```
Upload MRI → AI Segments Tumor → 2D-to-3D Render → Generate Summary: "A small lesion detected in the left hemisphere—non-cancerous, monitor recommended." → Chat: "What does this mean?" → PDF Export.
```

## Challenges & Mitigations
| Challenge | Mitigation |
|-----------|------------|
| **High Compute for 3D Processing** | Cloud GPUs (AWS/Hugging Face/Colab). |
| **Data Quality Variability** | Confidence scores + preprocessing filters. |
| **AI Misinterpretation Risk** | Medical disclaimers; expert review integration; no unsupervised learning (uses labeled datasets). |

## Contributing
- Fork the repo and submit PRs for features (e.g., new languages, scan types).
- Report issues: Data privacy bugs or model inaccuracies.
- Guidelines: Follow PEP8 for Python; ESLint for JS.

## License
MIT License—free for non-commercial use. For production healthcare deployment, consult HIPAA/GDPR compliance.

## Research & References
1. **nnU-Net: Self-Configuring Method for Medical Image Segmentation**  
   Isensee et al. [arXiv:1809.10486](https://arxiv.org/abs/1809.10486)  
   *Overview*: Robust U-Net framework for biomedical segmentation.  
   *Limitations*: GPU-heavy; supervised only.

2. **CheXNet: Deep Learning for Pneumonia Detection on Chest X-Rays**  
   Rajpurkar et al. [arXiv:1711.05225](https://arxiv.org/abs/1711.05225)  
   *Overview*: DenseNet model achieving radiologist-level accuracy.  
   *Limitations*: Lacks clinical context; label noise.

### Acknowledgments
- IEEE TechSangam 2025 & MIT-ADT University.
- Open-source: Hugging Face, PyTorch, scikit-image.

**Contact**: teampragati@mitadtc.edu.in  
 

---

*MedScope AI: Empowering healthcare, one insight at a time.* 🚀
