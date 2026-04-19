# Introduction to Big Data

## What is Big Data?
Big Data refers to extremely large and complex datasets that cannot be processed using traditional data management tools. It involves capturing, storing, processing, and analyzing data at scale.

### Characteristics of Big Data (5 Vs)
- **Volume**: Large amount of data (terabytes, petabytes, etc.)
- **Velocity**: Speed at which data is generated and processed
- **Variety**: Different forms of data (text, images, videos, etc.)
- **Veracity**: Quality and reliability of data
- **Value**: Useful insights derived from data

---

## Big Data vs Data Science vs Data Analytics

| Aspect | Big Data | Data Science | Data Analytics |
|--------|----------|--------------|----------------|
| Definition | Handling massive datasets | Extracting knowledge using algorithms | Finding patterns in data |
| Focus | Storage & processing | ML, statistics, modeling | Visualization & reporting |
| Tools | Hadoop, Spark | Python, R, TensorFlow | Excel, SQL, Power BI |
| Goal | Data management | Prediction & modeling | Decision making |
| Skill Set | Engineering systems | Programming + stats | Analytical thinking |

---

## Types of Data - Data Classification Flowchart

```mermaid
flowchart TD
    A[All Data]

    A --> B[Structured Data]
    A --> C[Semi-Structured Data]
    A --> D[Unstructured Data]

    B --> B1[Tables]
    B --> B2[Relational Databases]
    B --> B3[CSV Files]
    B --> B4[Excel Sheets]
    B --> B5[SQL Databases]

    C --> C1[XML]
    C --> C2[JSON]
    C --> C3[HTML]
    C --> C4[Log Files]

    D --> D1[Text Documents]
    D --> D2[Images]
    D --> D3[Audio Files]
    D --> D4[Video Files]
    D --> D5[Social Media Posts]
    D --> D6[PDFs]
    D --> D7[Sensor Data]

    classDef structured fill:#22c55e,stroke:#166534,color:#fff;
    classDef semistructured fill:#3b82f6,stroke:#1e40af,color:#fff;
    classDef unstructured fill:#ef4444,stroke:#991b1b,color:#fff;

    class B,B1,B2,B3,B4,B5 structured;
    class C,C1,C2,C3,C4 semistructured;
    class D,D1,D2,D3,D4,D5,D6,D7 unstructured;


--- 






---

## Handling Unstructured Data

Unstructured data does not follow a predefined format, making it harder to analyze.

### Challenges
- No fixed schema
- Difficult to search and process
- Large storage requirements

### Techniques to Handle Unstructured Data
- **Data Lakes**: Store raw data in its original format
- **NoSQL Databases**: MongoDB, Cassandra
- **Natural Language Processing (NLP)**: For analyzing text data
- **Machine Learning Algorithms**: For pattern recognition
- **Preprocessing Steps**:
  - Data cleaning
  - Tokenization
  - Feature extraction
  - Normalization

---

## Big Data & Data Science: Understanding XML

### What is XML?
XML (eXtensible Markup Language) is a semi-structured format used to store and transport data.

### Key Features
- Self-descriptive tags
- Hierarchical structure
- Platform independent
- Both human-readable and machine-readable

### XML Example
```xml
<employee>
    <id>101</id>
    <name>Ali</name>
    <department>IT</department>
</employee>


## Uses in Big Data
- Data exchange between systems  
- Web services (SOAP)  
- Configuration files  
- Metadata storage  

---

## Big Data & Data Science: Understanding JSON

### What is JSON?
JSON (JavaScript Object Notation) is a lightweight data-interchange format widely used in modern applications.

### Key Features
- Simple and easy to read  
- Uses key-value pairs  
- Language-independent  
- Faster than XML  

### JSON Example
```json
{
  "id": 101,
  "name": "Ali",
  "department": "IT"
}
