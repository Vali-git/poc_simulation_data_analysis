Brand Matching & Priority Scoring PoC

This repository contains a Proof of Concept (PoC) for a data processing pipeline designed to match and rank company brand names against a reference dataset (Veridion results). The system uses fuzzy logic and geographical validation to determine the most relevant matches for a given input.

🎯 Overview
The goal of this project is to automate the validation of brand search results. When searching for a company, many results might be returned; this tool assigns a "Priority Score" to each result to help identify the exact match or the most relevant entities based on name similarity and country of origin.

🛠️ Tech Stack

    Python 3.x: Core logic.

    Pandas: Data manipulation and analysis.

    RapidFuzz: High-performance fuzzy string matching (Levenshtein distance).

    Regex (re): Text cleaning and normalization.

⚙️ How the Scoring Algorithm Works
The core logic is implemented in the calculate_brand_priority_score function, which uses a weighted system (0-100 points):

    Name Similarity (70% weight - Max 70 points):

        Core Brand Check: The algorithm identifies the "core" word of the input brand. If this core word doesn't achieve a high similarity (90%+) with the result, the score is penalized or set to 0.

        Fuzzy Matching: It calculates a partial ratio between the input name and the candidate name.

    Location Validation (30% weight - Max 30 points):

        If the input's ISO Country Code matches the search result, 30 points are added to the final score.

You will need to install the following Python library:

    pip install rapidfuzz pandas

Usage

    Load Data: The notebook is configured to fetch a sample dataset (presales_data_sample.csv) directly from a GitHub source.

    Run Pipeline: The script processes the raw data, cleans the strings (removing special characters), and applies the scoring function.

    Analysis: The results are sorted by final_score and match_type (EXACT/HIGH, MEDIUM, LOW).

📂 Project Structure

    poc_simulation_presale_data_sample.ipynb: The main Jupyter Notebook containing data cleaning, the scoring algorithm, and the simulation results.

    data/: (Contextual) Contains the input CSV files with brand and country information.
