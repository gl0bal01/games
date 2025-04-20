# CYBER Challenge: The Insider's Diary ****

**Sunday, April 20, 2025**

## Scenario Overview

You've intercepted a large compressed file containing what appear to be the recovered journal entries or blog posts of a disgruntled employee of OmniCorp, a shadowy global technology company. The text is dense, full of technical jargon, banal complaints, personal angst and potential code names, making manual review extremely tedious. In addition, another folder entitled projectX appears to be locked with a password.

Intel suggests that the insider was aware of, and potentially involved in, a highly secretive and ethically dubious internal project. Your task is to sift through this digital diary to extract crucial information about this operation.

## Starting Information

You are provided with one file:

1.  `insider_notes.txt`: A large text file (approx. 800+ lines) containing the journal entries/blog posts.

## Objective

Analyze the provided `insider_notes.txt` file to identify three key pieces of information regarding OmniCorp's secret operation:

1.  The **codename** of the secret project.
2.  The **full name** of the key operative heavily involved.
3.  The **specific location/sector designation** critical to the project.

Your goal is to find these three pieces of information and combine them into the flag format specified below.

## Key Tools & Techniques

The sheer volume of text makes manual keyword searching inefficient and prone to errors. This challenge requires leveraging **Natural Language Processing (NLP)**, specifically **Named Entity Recognition (NER)**, to automatically identify and categorize key entities (like people, locations, and organizations) within the text.

* **Recommended Platform:** [Hugging Face](https://huggingface.co/) - A hub for pre-trained AI models.
* **Recommended NER Model:** `dslim/bert-base-NER` - A robust model trained to identify Person (PER), Location (LOC), Organization (ORG), and Miscellaneous (MISC) entities.
* **Automation Tool:** A Python script using the `transformers` library is highly recommended to process the entire text file and count entity occurrences efficiently. A pre-built script (`ner_counter.py`) is provided to assist with this.

## Challenge Steps Guide

1.  **Receive Data:** Obtain the `insider_notes.txt` file.
2.  **Initial Assessment:** Open the file and observe its size and density. Recognize that manual analysis is impractical.
3.  **Identify Need for Automation:** Determine that automated entity extraction (NER) is the most effective approach.
4.  **Select Tooling:**
    * Locate the recommended NER model (`dslim/bert-base-NER`) on Hugging Face (or use it directly via the provided script).
    * Prepare to use the provided Python script (`ner.py`) or develop your own based on the `transformers` library.
5.  **Process Text:**
    * Ensure the `insider_notes.txt` file is in the same directory as the script.
    * Build the script (e.g., `python ner.py`). This will load the model, process the entire text file, and count the occurrences of each PER, LOC, ORG or Other entity. *(Note: This step may take several minutes, especially on CPU)*.
6.  **Analyze Output:** Carefully review the script's output, which lists the identified Persons, Locations, and Organizations, sorted by frequency (most common first).
7.  **Identify Key Entities:** Look for recurring entities that seem central to the narrative's suspicious undertones. Pay close attention to:
    * A frequently mentioned **Person (PER)** associated with sensitive activities.
    * A frequently mentioned **Location (LOC)** linked to secrecy or unusual events.
    * An entity potentially representing the **Project Codename**. NER models might tag project names as `MISC` or sometimes `ORG`. You may need to look at the raw text snippets associated with key entities or infer the project name from context if it's not directly tagged perfectly. (*Hint: Look for mentions related to Q4 deadlines, ethical concerns, or specific arguments.*)
8.  **Correlate Findings:** Confirm that the identified Person, Location, and Project Name appear connected within the narrative (e.g., the person works on the project at that location).
9.  **Construct the Flag:** Once you have identified the three key pieces of information, combine them into the specified flag format.

## Required Files

* `insider_notes.txt` (Contains the diary entries - **must be provided**)

## Setup / Prerequisites

* **Python 3:** Ensure you have Python 3 installed.
* **Libraries:** You need to install the `transformers` library and a backend (like `torch` or `tensorflow`). You can usually install them using pip:
    ```bash
    pip install transformers torch
    # OR
    # pip install transformers tensorflow
    ```

## Flag Format

The flag should be constructed using the identified Project Codename, Person's Full Name (including title like Dr.), and Location/Sector Designation, separated by underscores (`_`).

Format: `flag{ProjectName_PersonName_LocationName}`

*Example based on clues:* `flag{Project_Pollux_Dr_MISS_Reed_Sector_7G}`

**Good luck, investigator!**
