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
insert into Bacteria (bacteria_name, genus, species, strain) values ('Escherichia coli', 'Escherichia', 'coli', 'K12');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Staphylococcus aureus', 'Staphylococcus', 'aureus', 'MRSA');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Bacillus subtilis', 'Bacillus', 'subtilis', '168');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Pseudomonas aeruginosa', 'Pseudomonas', 'aeruginosa', 'PAO1');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Salmonella enterica', 'Salmonella', 'enterica', 'Typhimurium');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Mycobacterium tuberculosis', 'Mycobacterium', 'tuberculosis', 'H37Rv');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Streptococcus pneumoniae', 'Streptococcus', 'pneumoniae', 'TIGR4');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Clostridium difficile', 'Clostridium', 'difficile', '630');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Neisseria gonorrhoeae', 'Neisseria', 'gonorrhoeae', 'FA1090');
insert into Bacteria (bacteria_name, genus, species, strain) values ('Listeria monocytogenes', 'Listeria', 'monocytogenes', '10403S');
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
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (1, 'human', 'feces', 'clinical', 'USA', 2019);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (2, 'human', 'nasal swab', 'clinical', 'UK', 2020);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (3, 'soil', 'soil', 'environmental', 'India', 2018);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (4, 'plant', 'leaf', 'environmental', 'USA', 2017);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (5, 'human', 'blood', 'clinical', 'France', 2016);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (6, 'human', 'sputum', 'clinical', 'China', 2015);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (7, 'human', 'nasal swab', 'clinical', 'Germany', 2014);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (8, 'human', 'feces', 'clinical', 'Brazil', 2013);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (9, 'human', 'genital swab', 'clinical', 'Australia', 2012);
insert into Sample (bacteria_id, host, source, sample_type, country, year_of_collection) values (10, 'human', 'blood', 'clinical', 'Canada', 2011);
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
insert into Gene (bacteria_id, gene_name, accession_id) values (3, 'spo0A', 'NC_000964.3');
insert into Gene (bacteria_id, gene_name, accession_id) values (4, 'oprD', 'NC_002516.2');
insert into Gene (bacteria_id, gene_name, accession_id) values (5, 'gyrB', 'NC_003197.2');
insert into Gene (bacteria_id, gene_name, accession_id) values (6, 'katG', 'NC_000962.3');
insert into Gene (bacteria_id, gene_name, accession_id) values (7, 'cpsA', 'NC_003028.3');
insert into Gene (bacteria_id, gene_name, accession_id) values (8, 'tcdA', 'NC_009089.1');  
insert into Gene (bacteria_id, gene_name, accession_id) values (9, 'penA', 'NC_002946.2');
insert into Gene (bacteria_id, gene_name, accession_id) values (10, 'lmo0443', 'NC_003210.1');
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
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (1, 'illumina', 4641652, 'high', 'complete', 'yes', 2019);
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (2, 'sanger', 2821362, 'medium', 'complete', 'yes', 2020);
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (3, '454', 4215600, 'low', 'draft', 'no', 2018);    
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (4, 'illumina', 6418600, 'high', 'complete', 'yes', 2017);  
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (5, 'sanger', 4850321, 'medium', 'complete', 'yes', 2016);
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (6, '454', 4411532, 'low', 'draft', 'no', 2015);
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (7, 'illumina', 5123654, 'high', 'complete', 'yes', 2014);  
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (8, 'sanger', 3721542, 'medium', 'complete', 'yes', 2013);
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (9, '454', 4913652, 'low', 'draft', 'no', 2012);
insert into Sequencing (bacteria_id, sequencing_method, genome_size, genome_quality, genome_comepleteness, published_paper, year_of_publication) values (10, 'illumina', 5412365, 'high', 'complete', 'yes', 2011);
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
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (1, 'ampicillin', 'beta-lactamase', 32);
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (2, 'methicillin', 'PBP2a', 64);
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (3, 'chloramphenicol', 'ribosomal protection', 16);
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (4, 'carbapenem', 'porin loss', 8);  
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (5, 'ciprofloxacin', 'gyrase mutation', 4);
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (6, 'isoniazid', 'katG mutation', 2);
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (7, 'penicillin', 'PBP mutation', 32);  
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (8, 'vancomycin', 'cell wall synthesis', 16);
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (9, 'penicillin', 'PBP mutation', 32);  
insert into AntibioticResistance (bacteria_id, antibiotic_name, resistance_mechanism, minimum_inhibitory_concentration) values (10, 'ampicillin', 'beta-lactamase', 32);
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
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (1, 'pUC19', 2686, 'high');
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (2, 'pI258', 2586, 'medium');
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (3, 'pBS32', 3215, 'low');
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (4, 'pPAO1', 2154, 'high');  
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (5, 'pSC101', 1542, 'medium');
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (6, 'pTBN1', 3215, 'low');    
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (7, 'pTIGR4', 2154, 'high');
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (8, 'pCD630', 1542, 'medium');
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (9, 'pFA1090', 3215, 'low');
insert into Plasmid (bacteria_id, plasmid_name, plasmid_size, plasmid_copy_number) values (10, 'p10403S', 2154, 'high');
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
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (1, 'DnaA', 'initiation of chromosomal replication', 507);
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (2, 'PBP2a', 'cell wall synthesis', 670);

insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (3, 'Spo0A', 'sporulation initiation', 302);
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (4, 'OprD', 'porin', 421);insert into Pathway (bacteria_id, pathway_name, pathway_description) values (1, 'DNA replication', 'replication of DNA');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (2, 'Cell wall biosynthesis', 'synthesis of cell wall');
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (5, 'GyrB', 'DNA gyrase subunit B', 804);
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (6, 'KatG', 'catalase-peroxidase', 729);
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (7, 'CpsA', 'capsule biosynthesis', 1023);
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (8, 'TcdA', 'toxin A', 2700);ion of hydrogen peroxide');
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (9, 'PenA', 'penicillin-binding protein', 670); capsule');
insert into Protein (bacteria_id, protein_name, protein_function, protein_length) values (10, 'Lmo0443', 'unknown', 302);
```l');

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
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (1, 'DNA replication', 'replication of DNA');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (2, 'Cell wall biosynthesis', 'synthesis of cell wall');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (3, 'Sporulation', 'formation of spores');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (4, 'Porin', 'transport of molecules');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (5, 'DNA gyrase', 'supercoiling of DNA');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (6, 'Catalase-peroxidase', 'detoxification of hydrogen peroxide');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (7, 'Capsule biosynthesis', 'synthesis of capsule');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (8, 'Toxin production', 'production of toxin');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (9, 'Cell wall biosynthesis', 'synthesis of cell wall');
insert into Pathway (bacteria_id, pathway_name, pathway_description) values (10, 'Unknown', 'unknown');
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