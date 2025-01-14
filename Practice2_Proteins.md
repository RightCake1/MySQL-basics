# Creating the Proteins Table

## SQL Statements for Proteins Table

### Creating the Proteins Table

```sql
CREATE TABLE Proteins (
    UniProtID varchar(15) PRIMARY KEY,
    ProteinName VARCHAR(255) NOT NULL,
    ProteinSequence TEXT NOT NULL,
    ExternalPDBID varchar(222) NOT NULL,
    ExternalPubMedID INT
);
```

### Inserting Data into the Proteins Table

```sql
INSERT INTO Proteins (UniProtID, ProteinName, ProteinSequence, ExternalPDBID, ExternalPubMedID) 
VALUES 
('P12346', 'Alpha Protein', 'MTKLVVLAFLQDLVRE', '2ABC', 1234567),
('P12347', 'Beta Enzyme', 'MAGAVAILKDLREGTSA', '3DEF', 2234567),
('P12348', 'Gamma Kinase', 'MKQLREAVTKLRVVVQ', '4GHI', 3234567),
('P12349', 'Delta Peptide', 'MLTGVRETAIKLKDME', '5JKL', 4234567),
('P12350', 'Zeta Protein', 'MAKVRQEILAELTMRT', '6MNO', 5234567),
('P12351', 'Eta Ligase', 'MLRVEAIKLQRTVVGK', '7PQR', 6234567),
('P12352', 'Theta Enzyme', 'MLKTAVRRLAVLVETQ', '8STU', 7234567),
('P12353', 'Iota Kinase', 'MKDLAVRELLTAIVKM', '9VWX', 8234567),
('P12354', 'Kappa Peptide', 'MLTEVRQAVKQLRTAA', '10YZA', 9234567),
('P12355', 'Lambda Protein', 'MAVIKLRETVLVRAET', '11BCD', 10234567);
```

### Selecting All Data from the Proteins Table

```sql
SELECT * FROM Proteins;
```

### Creating an Index on ProteinName

```sql
CREATE INDEX idx_protein_name ON Proteins (ProteinName);
```

### Showing Indexes from the Proteins Table

```sql
SHOW INDEX FROM Proteins;
```

### Altering the Proteins Table to Add GeneName Column

```sql
ALTER TABLE Proteins ADD COLUMN GeneName varchar(299);
```

### Updating GeneName for Multiple Records

```sql
UPDATE Proteins 
SET GeneName = CASE UniProtID
    WHEN 'P12346' THEN 'GATA1'
    WHEN 'P12347' THEN 'BRCA1'
    WHEN 'P12348' THEN 'TP53'
    WHEN 'P12349' THEN 'MYC'
    WHEN 'P12350' THEN 'CFTR'
    WHEN 'P12351' THEN 'EGFR'
    WHEN 'P12352' THEN 'HBB'
    WHEN 'P12353' THEN 'KRAS'
    WHEN 'P12354' THEN 'APOE'
    WHEN 'P12355' THEN 'CDKN2A'
END
WHERE UniProtID IN ('P12346', 'P12347', 'P12348', 'P12349', 'P12350', 'P12351', 'P12352', 'P12353', 'P12354', 'P12355');
```

### Updating GeneName for a Single Record

```sql
UPDATE Proteins SET GeneName = 'GeneOne' WHERE UniProtID = 'P123';
```

## SQL Statements for Diseases Table

### Creating the Diseases Table with Foreign Key

```sql
CREATE TABLE Diseases(
    DiseaseID INT PRIMARY KEY,
    DiseaseNAME varchar(255) NOT NULL,
    UniProtID varchar(15),
    FOREIGN KEY (UniProtID) REFERENCES Proteins (UniProtID)
);
```

### Joining Tables Proteins and Diseases

```sql
SELECT * FROM Proteins
    JOIN Diseases ON Proteins.UniProtID = Diseases.UniProtID;
```

## Sample Queries

### Basic Queries

#### Select UniProtID and ProteinName

```sql
SELECT UniProtID, ProteinName FROM Proteins WHERE ExternalPubMedID > 500000;
```

#### Select All Proteins Ordered by ProteinName

```sql
SELECT * FROM Proteins ORDER BY ProteinName ASC;
```

#### Count Proteins with ExternalPubMedID Greater than 500000

```sql
SELECT COUNT(*) FROM Proteins WHERE ExternalPubMedID > 500000;
```

#### Find Proteins with Sequence Length Greater than 15

```sql
SELECT UniProtID, ProteinName, LENGTH(ProteinSequence) AS SequenceLength 
FROM Proteins 
WHERE LENGTH(ProteinSequence) > 15;
```

#### List Diseases Associated with Proteins with ExternalPubMedID Greater than 7000000

```sql
SELECT Diseases.DiseaseName, Proteins.ProteinName 
FROM Diseases 
JOIN Proteins ON Diseases.UniProtID = Proteins.UniProtID 
WHERE Proteins.ExternalPubMedID > 7000000;
```

#### Retrieve All Proteins Ordered by GeneName Descending

```sql
SELECT UniProtID, ProteinName, GeneName 
FROM Proteins 
ORDER BY GeneName DESC;
```

#### Count Unique ProteinName Entries

```sql
SELECT COUNT(DISTINCT ProteinName) AS UniqueProteins 
FROM Proteins;
```

#### Fetch Proteins with ProteinName Containing "Kinase"

```sql
SELECT * 
FROM Proteins 
WHERE ProteinName LIKE '%Kinase%';
```

#### Find Protein with Longest Sequence

```sql
SELECT UniProtID, ProteinName, LENGTH(ProteinSequence) AS SequenceLength 
FROM Proteins 
ORDER BY LENGTH(ProteinSequence) DESC 
LIMIT 1;
```

#### List Proteins without Associated GeneName

```sql
SELECT UniProtID, ProteinName 
FROM Proteins 
WHERE GeneName IS NULL;
```

#### Retrieve Top 5 Proteins with Smallest ExternalPubMedID

```sql
SELECT UniProtID, ProteinName, ExternalPubMedID 
FROM Proteins 
ORDER BY ExternalPubMedID ASC 
LIMIT 5;
```

#### Find Diseases Not Associated with Any Protein

```sql
SELECT * 
FROM Diseases 
WHERE UniProtID IS NULL;
```

#### Calculate Average ExternalPubMedID for All Proteins

```sql
SELECT AVG(ExternalPubMedID) AS AveragePubMedID 
FROM Proteins;
```

### Intermediate Queries

#### Retrieve Diseases Linked to Proteins with ExternalPubMedID Greater than 7,000,000

```sql
SELECT Diseases.DiseaseName, Proteins.ProteinName
FROM Diseases
JOIN Proteins ON Diseases.UniProtID = Proteins.UniProtID
WHERE Proteins.ExternalPubMedID > 7000000;
```

#### Find the Longest Protein Sequence and Its Associated Disease

```sql
SELECT Proteins.ProteinName, Diseases.DiseaseName, LENGTH(Proteins.ProteinSequence) AS SequenceLength
FROM Proteins
LEFT JOIN Diseases ON Proteins.UniProtID = Diseases.UniProtID
ORDER BY SequenceLength DESC
LIMIT 1;
```

#### List Diseases That Involve Proteins with Names Containing "Enzyme"

```sql
SELECT Diseases.DiseaseName, Proteins.ProteinName
FROM Diseases
JOIN Proteins ON Diseases.UniProtID = Proteins.UniProtID
WHERE Proteins.ProteinName LIKE '%Enzyme%';
```

### Advanced Queries

#### Find the Top 3 Proteins with the Most Associated Diseases

```sql
SELECT Proteins.ProteinName, COUNT(Diseases.DiseaseID) AS DiseaseCount
FROM Proteins
JOIN Diseases ON Proteins.UniProtID = Diseases.UniProtID
GROUP BY Proteins.ProteinName
ORDER BY DiseaseCount DESC
LIMIT 3;
```

#### Retrieve All Diseases and Proteins Where the Gene Name Starts with "B"

```sql
SELECT Proteins.ProteinName, Diseases.DiseaseName
FROM Proteins
JOIN Diseases ON Proteins.UniProtID = Diseases.UniProtID
WHERE Proteins.GeneName LIKE 'B%';
```

#### Find Proteins Linked to Diseases with the Word "Cancer" in Their Name

```sql
SELECT Proteins.ProteinName, Diseases.DiseaseName
FROM Proteins
JOIN Diseases ON Proteins.UniProtID = Diseases.UniProtID
WHERE Diseases.DiseaseName LIKE '%Cancer%';
```

### Aggregation and Analysis

#### Calculate the Average Sequence Length of Proteins Associated with Diseases

```sql
SELECT AVG(LENGTH(ProteinSequence)) AS AvgSequenceLength
FROM Proteins
WHERE UniProtID IN (SELECT UniProtID FROM Diseases);
```

#### Find Diseases with More Than One Associated Protein

```sql
SELECT DiseaseName, COUNT(UniProtID) AS ProteinCount
FROM Diseases
GROUP BY DiseaseName
HAVING ProteinCount > 1;
```
