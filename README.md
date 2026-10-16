# Resume Shortlisting System

## 📌 Project Overview

The **Resume Shortlisting System** is a Python-based application designed to automate the initial resume screening process by comparing candidate resumes against a given job description.

It uses **Flask** for backend development and **NLTK (Natural Language Toolkit)** for Natural Language Processing (NLP). Text preprocessing, keyword extraction, TF-IDF vectorization, and cosine similarity are used to evaluate how closely each resume matches the job requirements.

The system assigns similarity scores to resumes and ranks candidates based on their relevance to the job description. Extracted candidate details and results can be displayed in JSON format and exported to a CSV file.

## 🎯 Objectives

- Automate the initial resume screening process.
- Extract relevant information and keywords from resumes.
- Compare resumes with predefined job requirements.
- Calculate similarity scores between resumes and job descriptions.
- Rank resumes based on their relevance to the target job profile.
- Display extracted information in JSON format and support CSV output.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Flask | Backend web framework and request handling |
| NLTK | Text preprocessing and NLP |
| Scikit-learn | TF-IDF vectorization and cosine similarity |
| JSON | Structured display of extracted information and results |
| CSV | Exporting candidate details and screening results |

## ⚙️ System Workflow

The resume shortlisting process follows these steps:

1. **Resume Input:** Collect resumes and the target job description.
2. **Text Extraction:** Retrieve textual content from the resumes.
3. **Text Preprocessing:** Clean and normalize the extracted text.
4. **Information Extraction:** Identify relevant keywords and candidate details.
5. **Feature Extraction:** Identify important skills, technologies, and job-related terms.
6. **Vectorization:** Convert the processed text into numerical vectors using TF-IDF.
7. **Similarity Calculation:** Compare resume vectors with the job description vector using cosine similarity.
8. **Score Assignment:** Generate a similarity score for each resume.
9. **Candidate Ranking:** Rank resumes according to their similarity scores.
10. **Result Display:** Display the extracted information and screening results in JSON format and export relevant data to CSV.

## 🧠 NLP Implementation Using NLTK

NLTK is used to preprocess resume text and prepare it for similarity analysis.

### 1. Tokenization

Tokenization breaks text into smaller units, such as words or sentences.

**Example:**

Input:
```text
Experienced Python developer with knowledge of Flask.
```

Output:
```text
["Experienced", "Python", "developer", "with", "knowledge", "of", "Flask"]
```

### 2. Stopword Removal

Stopwords are common words that may contribute little to keyword-based matching, such as *the*, *is*, *and*, and *of*.

Removing them helps focus the analysis on more meaningful terms.

### 3. Stemming and Lemmatization

These techniques normalize words to help identify related word forms.

- **Stemming:** Reduces words to approximate root forms.
- **Lemmatization:** Converts words to their dictionary base forms.

Example:
```text
running → run
```

### 4. Keyword and Entity Extraction

Relevant terms are identified from resumes and job descriptions, including:

- Technical skills such as Python, Flask, and SQL.
- Job-related responsibilities and qualifications.
- Candidate names and email addresses.

Part-of-speech tagging (`pos_tag`) can help identify nouns and verbs that may be relevant to the job description.

Extracted candidate details can be organized for structured display and CSV export.

## 📊 Resume Matching and Similarity Scoring

### 1. TF-IDF Vectorization

TF-IDF stands for **Term Frequency–Inverse Document Frequency**. It converts text into numerical vectors and assigns weights to terms based on their frequency in a document and their relative importance across the document collection.

This representation helps compare the content of a resume with a job description.

### 2. Cosine Similarity

Cosine similarity measures the similarity between two numerical vectors.

The formula is:

\[
\text{Cosine Similarity}(A,B)=
\frac{A \cdot B}{\|A\|\|B\|}
\]

Where:
- `A` represents the job description vector.
- `B` represents the resume vector.
- The score indicates how similar the two vectors are.

For non-zero TF-IDF vectors, cosine similarity ranges from 0 to 1.

### 3. Score Assignment and Ranking

After calculating similarity scores:

- Each resume receives a score based on its similarity to the job description.
- Resumes with higher scores are ranked higher.
- A ranking or threshold can be used to identify resumes that meet the selected matching criteria.

**Example:**

| Candidate | Similarity Score | Rank |
|---|---:|---:|
| Candidate A | 0.85 | 1 |
| Candidate B | 0.72 | 2 |
| Candidate C | 0.58 | 3 |

*Note: These scores are illustrative examples, not actual project results.*

The ranking can be adjusted to account for specific skills, qualifications, or experience requirements.

**In simple terms:** The system extracts relevant information from each resume, compares it with the job description, calculates a matching score, and ranks candidates from the strongest textual match to the weakest.

## 🌐 Flask Backend

Flask is a lightweight Python web framework used to build the backend of the application.

### Why Flask?

Flask was selected for the following reasons:

- **Lightweight:** Provides the core features needed for a small application without unnecessary framework overhead.
- **Flexibility:** Allows the integration of libraries such as NLTK and Scikit-learn.
- **Simplicity:** Supports straightforward route and request handling.
- **Easy integration:** Makes it convenient to connect the resume-processing logic to a web interface or API.

Unlike Django, which includes a broader set of built-in features, Flask allows developers to choose the components needed for the application.

For this project, Flask provides the backend structure while the NLP and similarity-matching logic is handled by Python libraries.

## 🔗 Flask and NLTK Integration

Flask and NLTK serve different purposes and work together in the application.

**Flask handles:**
- Incoming HTTP requests.
- Backend routes and application logic.
- Passing resume text to the processing pipeline.
- Returning screening results to the client.

**NLTK handles:**
- Tokenization.
- Stopword removal.
- Stemming and lemmatization.
- Part-of-speech tagging.
- Text preparation for keyword analysis.

Scikit-learn complements NLTK by handling TF-IDF vectorization and cosine similarity calculations.

## 📤 Output and Results

The system supports structured output for extracted candidate information and screening results.

### JSON Output

JSON provides a structured representation of the results, making them easy to consume in a frontend or through an API.

Example:
```json
{
  "candidate_name": "Candidate A",
  "email": "candidate@example.com",
  "similarity_score": 0.85,
  "rank": 1
}
```

*This is an illustrative output structure.*

### CSV Export

Extracted information can be exported to a CSV file for further analysis. Depending on the implemented fields, the CSV may contain candidate names, email addresses, similarity scores, and rankings.

## 🚀 Key Features

- Automated resume text preprocessing.
- NLP-based keyword identification.
- Candidate information extraction.
- TF-IDF-based text representation.
- Cosine similarity-based resume matching.
- Similarity score calculation and candidate ranking.
- JSON-formatted result display.
- CSV export for screening results.
- Flask-based backend integration.

## 🔮 Future Enhancements

- Support for additional resume formats.
- Semantic matching using sentence embeddings or transformer models.
- Skill-based scoring with configurable weights.
- Improved handling of synonyms and related technical skills.
- A dashboard for reviewing and filtering candidates.
- Integration with databases to manage resumes and screening history.
- Evaluation against manually reviewed resumes to measure ranking quality.

## ⚠️ Limitations

TF-IDF and cosine similarity primarily measure textual overlap rather than a candidate's full qualifications or actual ability. A high similarity score does not guarantee that a candidate is suitable for a role.

The system should therefore be treated as a screening aid, with final hiring decisions made through human review. Candidate data should also be handled securely and only for appropriate purposes.

## 📌 Conclusion

The Resume Shortlisting System demonstrates how Python, Flask, NLTK, and Scikit-learn can be combined to automate resume preprocessing, extract useful candidate information, compare resumes against job descriptions, and rank candidates using text similarity.

The project provides a foundation for building more advanced recruitment tools using semantic search, machine learning, and transformer-based NLP techniques.
