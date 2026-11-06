---
title: recruiter-dashboard
emoji: 💼
colorFrom: blue
colorTo: indigo
sdk: streamlit
sdk_version: 1.30.0
app_file: app.py
pinned: false
---

# AI Talent Vetting & Intelligent Ranking System

An AI-powered candidate ranking and vetting system built for the Redrob Challenge. Instead of relying on shallow keyword matching, it evaluates candidate quality with profile integrity checks, experience fit, and behavioral signals to surface stronger matches.

---

## Key Features

1. **Robust Profile Integrity & Honeypot Vetting**
   - Filters out synthetic anomalies and trap candidates, including salary range contradictions, impossible date sequences, and duplicate or inconsistent profile markers.

2. **Consulting Exclusions & Product Experience Prioritization**
   - Excludes candidates who have only worked at IT consulting firms, while preserving profiles with product or platform experience.

3. **Cross-Referenced Skills Vetting**
   - Evaluates required skills such as Embeddings, Vector Search, LLM Fine-Tuning, and ML Evaluation against career descriptions to detect keyword stuffing and weak matches.

4. **Behavioral Availability Weighting**
   - Scores candidates based on notice periods, login activity cadence, and recruiter response patterns to prioritize active, available talent.

5. **Interactive Recruiter Dashboard**
   - Presents a dark-themed Streamlit interface with candidate uploads, interactive ranking leaderboards, verified badges, career timeline cards, and pool intelligence views.

---

## Quick Start & Reproduction

### 1. Requirements
Ensure Python 3.10+ is installed, then install the required dependencies:

```bash
pip install -r requirements.txt
```

### 2. Generate the Ranked Candidate Output
To produce the ranked candidate CSV (`submission.csv`) from the candidate database, run:

```bash
python rank.py --candidates ./[PUB] India_runs_data_and_ai_challenge/India_runs_data_and_ai_challenge/candidates.jsonl --out ./submission.csv
```

*Note: the script also handles gzip-compressed files such as `./candidates.jsonl.gz`.*

### 3. Run the Dashboard Locally
Launch the recruiter-facing dashboard with:

```bash
streamlit run app.py
```

---

## Vetting & Scoring Methodology

The composite score is calculated on a 0–100% scale using a weighted model across four core vectors:

- **Technical Skills Alignment (35%)**: Evaluates domain requirements such as Embeddings, Vector Search, Evaluation, and Fine-Tuning. Partial credit is given when skills appear in experience history but not in explicit role descriptions.
- **Position & Experience Fit (25%)**: Prioritizes candidates in the 5–9 years of experience range while reducing scores for profiles that are too junior or too senior relative to the target hiring profile.
- **Location Preference (15%)**: Favors local and India-based candidates, particularly in Noida, Pune, and NCR, while down-weighting international applicants due to visa sponsorship constraints.
- **Behavioral & Availability Signals (25%)**: Rewards active candidates and penalizes long notice periods above 60 days.

---

## Hosted Sandbox Deployment

The app is designed to be fully self-contained and ready for hosted deployment.

### Streamlit Community Cloud / Hugging Face Spaces
1. Push this workspace to a GitHub repository.
2. Sign in to [Streamlit Community Cloud](https://share.streamlit.io/) or [Hugging Face Spaces](https://huggingface.co/spaces).
3. Connect the repository and set `app.py` as the main entrypoint.
4. Configure the build environment; the app will run on the standard free-tier CPU setup.
5. Upload a small candidate sample, such as `sample_candidates.json`, in the sidebar to verify the ranking flow end-to-end.
