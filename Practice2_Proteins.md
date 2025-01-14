# Creating the Proteins Table

```sql
CREATE TABLE Proteins (
    UniProtID varchar(15) PRIMARY KEY,
    ProteinName VARCHAR(255) NOT NULL,
    ProteinSequence TEXT NOT NULL,
    ExternalPDBID varchar(222) NOT NULL,
    ExternalPubMedID INT
);
```

# Inserting Data into the Proteins Table

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

# Selecting All Data from the Proteins Table

```sql
SELECT * FROM Proteins;
```

# Creating an Index on ProteinName

```sql
CREATE INDEX idx_protein_name ON Proteins (ProteinName);
```

# Showing Indexes from the Proteins Table

```sql
SHOW INDEX FROM Proteins;
```

# Altering the Proteins Table to Add GeneName Column

```sql
ALTER TABLE Proteins ADD COLUMN GeneName varchar(299);
```

# Updating GeneName for Multiple Records

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

# Updating GeneName for a Single Record

```sql
UPDATE Proteins SET GeneName = 'GeneOne' WHERE UniProtID = 'P123';
```

# Creating the Diseases Table with Foreign Key

```sql
CREATE TABLE Diseases(
    DiseaseID INT PRIMARY KEY,
    DiseaseNAME varchar(255) NOT NULL,
    UniProtID varchar(15),
    FOREIGN KEY (UniProtID) REFERENCES Proteins (UniProtID)
);
```

# Joining Tables Proteins and Diseases

```sql
SELECT * FROM Proteins
    JOIN Diseases ON Proteins.UniProtID = Diseases.UniProtID;
```

# Sample Queries

```sql
Select UniProtID, ProteinName From Proteins Where ExternalPubMedID > 500000;
```

```sql
Select * from Proteins Order by ProteinName ASC;
```

```sql
Select Count(*) From Proteins Where ExternalPubMedID > 500000;
```
