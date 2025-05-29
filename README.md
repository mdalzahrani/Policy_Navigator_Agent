#  Policy Navigator Agent

##  Overview

The **Policy Navigator Agent** is an AI-powered agent designed to search, extract, and summarize complex policy and regulation documents — such as the GDPR, U.S. privacy laws, and other federal guidelines. It can respond to custom user queries, retrieve policy documents, and provide summarized outputs or citations based on indexed data.

---

##  Data Sources

- **External URL Source:** [FTC Privacy & Security Guidance](https://www.ftc.gov/business-guidance/privacy-security)
- **Default CSV Dataset:** [`GDPR Violations`](https://www.kaggle.com/datasets/jessemostipak/gdpr-violations?select=gdpr_text.csv)
- **External API Source:** [Federal Register](https://www.federalregister.gov/)


---

##  Tool Integration Steps

1. **Index Dataset Content:**
   - Load `GDPR Violations` or any user-uploaded file.
   - Parse and embed into a searchable index using `IndexFactory`.

2. **Federal Register API:**
   - Pull regulation titles, links, and summaries using topic + date filters.

3. **Summarization Tool:**
   - Apply a lightweight LLM (`text-summarization-microsoft`) to compress long policies into readable summaries.

4. **SQL Tool:**
   - Extract query  (`create_sql_tool`) 

---

##  Example Inputs & Outputs

**Input:**  
`Under the GDPR, when does the regulation apply to the processing of personal data? Then summarize it.`

**Output:**  
The GDPR applies to data processing by controllers in the EU, or outside the EU if involving EU citizens. It covers both automated and manual processing of personal data and includes obligations for transparency and data rights.

**Tool Steps Used:**  
- `search-aixplain-general_data_protection_regulation_(eu)`  
- `text-summarization-microsoft`


---

##  Future Improvements

- **Memory/Caching:**  
  - Store past queries for faster inference  

---

##  Setup Instructions


1. Clone the repository or open the `Policy_Navigator_Agent.ipynb` in your Jupyter environment.

2. Install required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Run the notebook:
    - Execute all cells including the one that launches the Gradio UI.

4. Use the web UI to:
    - Enter a policy-related question
    - Upload a CSV file (optional)
    - Provide a custom URL (optional)
    ```

