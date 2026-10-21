# Tech Stack Evaluation

## Project
Festival-Aware Blood Donation Forecasting (Klang Valley)

## Requirements that drive the decision
List 3 to 5 requirements from your own docs/requirements.md. Include at
least 2 non-functional requirements.
- FR1: The system shall import daily blood donation records from the MOH open dataset.
- FR2: The system shall combine the Selangor, W.P. Putrajaya and W.P. Kuala Lumpur records into one daily Klang Valley series.
- NFR1: The dashboard shall display the forecast chart within 3 seconds of the page being opened.
- NFR2: The best machine learning model shall have a lower MAPE than the SARIMA baseline on the 2025 test data.

## Options
- Option A: Train the model offline in a Python notebook (pandas, scikit-learn); publish the forecast chart as a static web page on GitHub Pages.
- Option B: Python web app (Flask) with a PostgreSQL database on a cloud host; the model runs live on the server.
- Option C: Python dashboard (Streamlit) hosted on Streamlit Community Cloud; the model and the interactive chart are written in Python.

## Decision matrix
Weight: how important the criterion is for YOUR project (1 = low, 5 = high).
Score: how well each option does (1 = poor, 5 = excellent).
Weighted score = weight x score. Add them up for each option.

| Criterion                          | Weight | A score    | B score    | C score    |
|------------------------------------|--------|------------|------------|------------|
| Fits my requirements               | 5      | 4 (20)     | 4 (20)     | 5 (25)     |
| Skills I already have              | 4      | 4 (16)     | 2 (8)      | 4 (16)     |
| Time to build before my deadline   | 5      | 4 (20)     | 2 (10)     | 5 (25)     |
| Free hosting and tools             | 4      | 5 (20)     | 2 (8)      | 4 (16)     |
| Performance and security needs     | 2      | 5 (10)     | 3 (6)      | 3 (6)      |
| Room to grow later                 | 3      | 2 (6)      | 5 (15)     | 3 (9)      |
| **Total (weighted)**               |        | **92**     | **67**     | **97**     |

## Decision record
- **Context:** I need to build and show a daily blood donation forecast that handles movable festivals, before my semester deadline, with no budget. I know Python but I am new to machine learning, so the stack must not add extra learning on top of ML.
- **Decision:** Option C, a Streamlit dashboard on Streamlit Community Cloud.
- **Reasons:**
    1. It scored highest (97). Everything is in Python, so I can train the model and build the chart in one language, which saves time (deadline weight 5).
    2. It shows an interactive chart with festival periods highlighted, which meets FR3, and it is free to host, which meets NFR2.
    3. Option A was close (92) but its chart is static. Option B needs a database and a paid or limited host, which I do not need for FR1 to FR3. 
- **Consequences:** Easy: fast to build, one language, free deployment from GitHub. Harder: limited control over the page design, and the free plan has limited memory, so a large model or dataset may not fit. The app also sleeps when nobody uses it, so the first load can be slow, which is a risk for NFR1.
- **Risks and next review:** The free plan could change or become too small for my model; then I would switch to Option A and show pre-computed forecasts on GitHub Pages. Next review: after I train the first model, when I know its size and load time.
