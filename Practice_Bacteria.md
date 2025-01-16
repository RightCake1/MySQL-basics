# Create Database

```sql
Create database BacteriaPracticeDB; -- Create a new database named BacteriaPracticeDB
```

# Use Database

```sql
Use BacteriaPracticeDB; -- Switch to the BacteriaPracticeDB database
```

# Create Bacteria Table

```sql
Create Table Bacteria ( -- Create a new table named Bacteria
    bacteria_id int auto_increment primary key, -- Define bacteria_id as an auto-incrementing primary key
    bacteria_name varchar(50) not null, -- Define bacteria_name as a non-nullable varchar column
    genus varchar(50) not null, -- Define genus as a non-nullable varchar column
    species varchar(50) not null, -- Define species as a non-nullable varchar column
    strain varchar(50) not null -- Define strain as a non-nullable varchar column
);
```

# Insert Records into Bacteria Table

```sql
insert into Bacteria (bacteria_name, genus, species, strain) values 
('Escherichia coli', 'Escherichia', 'coli', 'K12'),
('Staphylococcus aureus', 'Staphylococcus', 'aureus', 'MRSA'),
('Bacillus subtilis', 'Bacillus', 'subtilis', '168'),
('Pseudomonas aeruginosa', 'Pseudomonas', 'aeruginosa', 'PAO1'),
('Salmonella enterica', 'Salmonella', 'enterica', 'Typhimurium'),
('Mycobacterium tuberculosis', 'Mycobacterium', 'tuberculosis', 'H37Rv'),
('Streptococcus pneumoniae', 'Streptococcus', 'pneumoniae', 'TIGR4'),
('Clostridium difficile', 'Clostridium', 'difficile', '630'),
('Neisseria gonorrhoeae', 'Neisseria', 'gonorrhoeae', 'FA1090'),
('Listeria monocytogenes', 'Listeria', 'monocytogenes', '10403S');
```

# Select All Records from Bacteria Table

```sql
select * from Bacteria; -- Select all records from the Bacteria table
```

# Create Sample Table

```sql
Create table Sample( -- Create a new table named Sample
    sample_id int auto_increment primary key, -- Define sample_id as an auto-incrementing primary key
    bacteria_id int not null, -- Define bacteria_id as a non-nullable int column
    host varchar(50) not null, -- Define host as a non-nullable varchar column
    source varchar(50) not null, -- Define source as a non-nullable varchar column
    sample_type ENUM('clinical', 'environmental') not null, -- Define sample_type as a non-nullable ENUM column
    country varchar(50) not null, -- Define country as a non-nullable varchar column
    year_of_collection int not null, -- Define year_of_collection as a non-nullable int column
    foreign key (bacteria_id) references Bacteria(bacteria_id) -- Define a foreign key constraint on bacteria_id referencing Bacteria(bacteria_id)
);
```

# Insert Records into Sample Table

```sql
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values 
(1, 'human', 'feces', 'clinical', 'USA', 2019),
(2, 'human', 'nasal swab', 'clinical', 'UK', 2020),
(3, 'soil', 'soil', 'environmental', 'India', 2018),
(4, 'plant', 'leaf', 'environmental', 'USA', 2017),
(5, 'human', 'blood', 'clinical', 'France', 2016),
(6, 'human', 'sputum', 'clinical', 'China', 2015),
(7, 'human', 'nasal swab', 'clinical', 'Germany', 2014),
(8, 'human', 'feces', 'clinical', 'Brazil', 2013),
(9, 'human', 'genital swab', 'clinical', 'Australia', 2012),
(10, 'human', 'blood', 'clinical', 'Canada', 2011);
```

# Select All Records from Sample Table

```sql
select * from Sample; -- Select all records from the Sample table
```

# Create Gene Table

```sql
Create Table Gene( -- Create a new table named Gene
    gene_id int auto_increment primary key, -- Define gene_id as an auto-incrementing primary key
    bacteria_id int not null, -- Define bacteria_id as a non-nullable int column
    gene_name varchar(50) not null, -- Define gene_name as a non-nullable varchar column
    accession_id varchar(50) not null, -- Define accession_id as a non-nullable varchar column
    foreign key (bacteria_id) references Bacteria(bacteria_id) -- Define a foreign key constraint on bacteria_id referencing Bacteria(bacteria_id)
);
```

# Insert Records into Gene Table

```sql
insert into Gene (bacteria_id, gene_name, accession_id) values 
(3, 'spo0A', 'NC_000964.3'),
(4, 'oprD', 'NC_002516.2'),
(5, 'gyrB', 'NC_003197.2'),
(6, 'katG', 'NC_000962.3'),
(7, 'cpsA', 'NC_003028.3'),
(8, 'tcdA', 'NC_009089.1'),
(9, 'penA', 'NC_002946.2'),
(10, 'lmo0443', 'NC_003210.1');
```

# Select All Records from Gene Table

```sql
select * from Gene;
```

# Create Sequencing Table

```sql
Create table Sequencing (
    sequencing_id int auto_increment primary key,
    bacteria_id int not null,
    sequencing_method ENUM('illumina', 'sanger', '454') not null,
    genome_size int not null, -- in base pairs
    genome_quality ENUM('high', 'medium', 'low') not null,
    genome_comepleteness ENUM('complete', 'draft') not null,
    published_paper ENUM('yes', 'no') not null,
    year_of_publication Year,
    foreign key (bacteria_id) references Bacteria(bacteria_id)
);
```

# Insert Records into Sequencing Table
```sql
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values 
(1, 'illumina', 4641652, 'high', 'complete', 'yes', 2019),
(2, 'sanger', 2821362, 'medium', 'complete', 'yes', 2020),
(3, '454', 4215600, 'low', 'draft', 'no', 2018),
(4, 'illumina', 6418600, 'high', 'complete', 'yes', 2017),
(5, 'sanger', 4850321, 'medium', 'complete', 'yes', 2016),
(6, '454', 4411532, 'low', 'draft', 'no', 2015),
(7, 'illumina', 5123654, 'high', 'complete', 'yes', 2014),
(8, 'sanger', 3721542, 'medium', 'complete', 'yes', 2013),
(9, '454', 4913652, 'low', 'draft', 'no', 2012),
(10, 'illumina', 5412365, 'high', 'complete', 'yes', 2011);
```

## Select Sequencing Data
```sql
select * from Sequencing;
```

## Create AntibioticResistance Table
```sql
Create table AntibioticResistance (
    resistance_id int auto_increment primary key,
    bacteria_id int not null,
    antibiotic_name varchar(50) not null,
    resistance_mechanism varchar(50) not null,
    minimum_inhibitory_concentration int not null,
    foreign key (bacteria_id) references Bacteria(bacteria_id)
);
```

## Insert Data into AntibioticResistance Table

```sql
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values 
(1, 'ampicillin', 'beta-lactamase', 32),
(2, 'methicillin', 'PBP2a', 64),
(3, 'chloramphenicol', 'ribosomal protection', 16),
(4, 'carbapenem', 'porin loss', 8),
(5, 'ciprofloxacin', 'gyrase mutation', 4),
(6, 'isoniazid', 'katG mutation', 2),
(7, 'penicillin', 'PBP mutation', 32),
(8, 'vancomycin', 'cell wall synthesis', 16),
(9, 'penicillin', 'PBP mutation', 32),
(10, 'ampicillin', 'beta-lactamase', 32);
```

## Select AntibioticResistance Data
```sql
select * from AntibioticResistance;
```

## Create Plasmid Table
```sql
Create table Plasmid (
    plasmid_id int auto_increment primary key,
    bacteria_id int not null,
    plasmid_name varchar(50) not null,
    plasmid_size int not null, -- in base pairs
    plasmid_copy_number ENUM('low', 'medium', 'high') not null,
    foreign key (bacteria_id) references Bacteria(bacteria_id)
);
```

## Insert Data into Plasmid Table

```sql
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values 
(1, 'pUC19', 2686, 'high'),
(2, 'pI258', 2586, 'medium'),
(3, 'pBS32', 3215, 'low'),
(4, 'pPAO1', 2154, 'high'),
(5, 'pSC101', 1542, 'medium'),
(6, 'pTBN1', 3215, 'low'),
(7, 'pTIGR4', 2154, 'high'),
(8, 'pCD630', 1542, 'medium'),
(9, 'pFA1090', 3215, 'low'),
(10, 'p10403S', 2154, 'high');
```

## Select Plasmid Data
```sql
select * from Plasmid;
```

## Create Protein Table
```sql
Create table Protein (
    protein_id int auto_increment primary key,
    bacteria_id int not null,
    protein_name varchar(50) not null,
    protein_function varchar(50) not null,
    protein_length int not null, -- in amino acids
    foreign key (bacteria_id) references Bacteria(bacteria_id)
);
```

## Insert Data into Protein Table

```sql
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values 
(1, 'DnaA', 'initiation of chromosomal replication', 507),
(2, 'PBP2a', 'cell wall synthesis', 670),
(3, 'Spo0A', 'sporulation initiation', 302),
(4, 'OprD', 'porin', 421),
(5, 'GyrB', 'DNA gyrase subunit B', 804),
(6, 'KatG', 'catalase-peroxidase', 729),
(7, 'CpsA', 'capsule biosynthesis', 1023),
(8, 'TcdA', 'toxin A', 2700),
(9, 'PenA', 'penicillin-binding protein', 670),
(10, 'Lmo0443', 'unknown', 302);
```

## Select Protein Data
```sql
select * from Protein;select * from Pathway;
```

## Create Pathway Tablealter table Gene
```sqladd column resistance_id int,
Create table Pathway ((resistance_id) references AntibioticResistance(resistance_id);
    pathway_id int auto_increment primary key,
    bacteria_id int not null,
    pathway_name varchar(50) not null,alter table Gene
    pathway_description varchar(50) not null,add column plasmid_id int,
    foreign key (bacteria_id) references Bacteria(bacteria_id)(plasmid_id) references Plasmid(plasmid_id);
);
```

## Insert Data into Pathway Table

```sql
insert into Pathway (bacteria_id, pathway_name, pathway_description) values 
(1, 'DNA replication', 'replication of DNA'),
(2, 'Cell wall biosynthesis', 'synthesis of cell wall'),
(3, 'Sporulation', 'formation of spores'),
(4, 'Porin', 'transport of molecules'),
(5, 'DNA gyrase', 'supercoiling of DNA'),
(6, 'Catalase-peroxidase', 'detoxification of hydrogen peroxide'),
(7, 'Capsule biosynthesis', 'synthesis of capsule'),
(8, 'Toxin production', 'production of toxin'),
(9, 'Cell wall biosynthesis', 'synthesis of cell wall'),
(10, 'Unknown', 'unknown');
```

## Select Pathway Data
```sql
select * from Pathway;
```

## Alter Gene Table to Add Foreign Keys
```sql
alter table Gene
add column resistance_id int,
add foreign key (resistance_id) references AntibioticResistance(resistance_id);
```

```sql
alter table Gene
add column plasmid_id int,
add foreign key (plasmid_id) references Plasmid(plasmid_id);
```

## Practice SQL Queries
Refer to [Sample_query_for_Practice_Bacteria.md](Sample_query_for_Practice_Bacteria.md)