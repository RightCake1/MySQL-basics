# Practice SQL queries

## 1. Select all bacteria names
```sql
select bacteria_name from Bacteria; -- select only bacteria_name column
```

## 2. Select all samples collected in the year 2019
```sql
select * from Sample where year_of_collection = 2019; -- select all columns from Sample table
```

## 3. Select all genes associated with 'Escherichia coli'
```sql
select Gene.* from Gene -- select all columns from Gene table
join Bacteria on Gene.bacteria_id = Bacteria.bacteria_id -- join Gene table with Bacteria table
where Bacteria.bacteria_name = 'Escherichia coli'; -- filter by bacteria name
```

## 4. Select all sequencing methods used
```sql
select distinct sequencing_method from Sequencing; -- select distinct sequencing methods from Sequencing table
```

## 5. Select all antibiotic resistances for 'Staphylococcus aureus'
```sql
select AntibioticResistance.* from AntibioticResistance -- select all columns from AntibioticResistance table
join Bacteria on AntibioticResistance.bacteria_id = Bacteria.bacteria_id -- join AntibioticResistance table with Bacteria table
where Bacteria.bacteria_name = 'Staphylococcus aureus'; -- filter by bacteria name
```

## 6. Select all plasmids with high copy number
```sql
select * from Plasmid where plasmid_copy_number = 'high'; -- select all columns from Plasmid table
```

## 7. Select all proteins with length greater than 500 amino acids
```sql
select * from Protein where protein_length > 500; -- select all columns from Protein table
```

## 8. Select all pathways related to 'DNA replication'
```sql
select * from Pathway where pathway_name = 'DNA replication'; -- select all columns from Pathway table
```

## 9. Select all bacteria collected from 'USA'
```sql
select Bacteria.* from Bacteria -- select all columns from Bacteria table
join Sample on Bacteria.bacteria_id = Sample.bacteria_id -- join Bacteria table with Sample table
where Sample.country = 'USA'; -- filter by country
```

## 10. Select all bacteria with genome size greater than 5,000,000 base pairs
```sql
select Bacteria.* from Bacteria -- select all columns from Bacteria table
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id -- join Bacteria table with Sequencing table
where Sequencing.genome_size > 5000000; -- filter by genome size
```

## 11. Select all samples of type 'clinical'
```sql
select * from Sample where sample_type = 'clinical'; -- select all columns from Sample table
```

## 12. Select all genes with accession ID starting with 'NC_00'
```sql
select * from Gene where accession_id like 'NC_00%'; -- select all columns from Gene table
```

## 13. Select all proteins with unknown function
```sql
select * from Protein where protein_function = 'unknown'; -- select all columns from Protein table
```

## 14. Select all bacteria with resistance to 'ampicillin'
```sql
select Bacteria.* from Bacteria -- select all columns from Bacteria table
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id -- join Bacteria table with AntibioticResistance table
where AntibioticResistance.antibiotic_name = 'ampicillin'; -- filter by antibiotic name
```

## 15. Select all samples from 'human' host
```sql
select * from Sample where host = 'human'; -- select all columns from Sample table
```

## 16. Select all sequencing records published in 2019
```sql
select * from Sequencing where year_of_publication = 2019; -- select all columns from Sequencing table
```

## 17. Select all plasmids with size less than 3000 base pairs
```sql
select * from Plasmid where plasmid_size < 3000; -- select all columns from Plasmid table
```

## 18. Select all pathways with description containing 'synthesis'
```sql
select * from Pathway where pathway_description like '%synthesis%'; -- select all columns from Pathway table
```

## 19. Select all bacteria with at least one associated gene
```sql
select distinct Bacteria.* from Bacteria -- select distinct bacteria records
join Gene on Bacteria.bacteria_id = Gene.bacteria_id; -- join Bacteria table with Gene table
```

## 20. Select all samples from 'clinical' type collected in 'USA'
```sql
select * from Sample where sample_type = 'clinical' and country = 'USA'; -- select all columns from Sample table
```

## 21. Select all bacteria names and their associated gene names
```sql
select Bacteria.bacteria_name, Gene.gene_name from Bacteria -- select bacteria_name column from Bacteria table
join Gene on Bacteria.bacteria_id = Gene.bacteria_id; -- join Bacteria table with Gene table
```

## 22. Select all samples collected from 'human' host in the year 2020
```sql
select * from Sample where host = 'human' and year_of_collection = 2020; -- select all columns from Sample table
```

## 23. Select all sequencing records with 'high' genome quality and 'complete' genome completeness
```sql
select * from Sequencing where genome_quality = 'high' and genome_comepleteness = 'complete'; -- select all columns from Sequencing table
```

## 24. Select all antibiotic resistances with minimum inhibitory concentration greater than 16
```sql
select * from AntibioticResistance where minimum_inhibitory_concentration > 16; -- select all columns from AntibioticResistance table
```

## 25. Select all plasmids associated with 'Escherichia coli'
```sql
select Plasmid.* from Plasmid -- select all columns from Plasmid table
join Bacteria on Plasmid.bacteria_id = Bacteria.bacteria_id -- join Plasmid table with Bacteria table
where Bacteria.bacteria_name = 'Escherichia coli'; -- filter by bacteria name
```

## 26. Select all proteins associated with 'Staphylococcus aureus'
```sql
select Protein.* from Protein -- select all columns from Protein table
join Bacteria on Protein.bacteria_id = Bacteria.bacteria_id -- join Protein table with Bacteria table
where Bacteria.bacteria_name = 'Staphylococcus aureus'; -- filter by bacteria name
```

## 27. Select all pathways associated with 'Bacillus subtilis'
```sql
select Pathway.* from Pathway -- select all columns from Pathway table
join Bacteria on Pathway.bacteria_id = Bacteria.bacteria_id -- join Pathway table with Bacteria table
where Bacteria.bacteria_name = 'Bacillus subtilis'; -- filter by bacteria name
```

## 28. Select all bacteria names and their associated sequencing methods
```sql
select Bacteria.bacteria_name, Sequencing.sequencing_method from Bacteria -- select bacteria_name column from Bacteria table
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id; -- join Bacteria table with Sequencing table
```

## 29. Select all samples collected from 'soil' source
```sql
select * from Sample where source = 'soil'; -- select all columns from Sample table
```

## 30. Select all genes with resistance to 'methicillin'
```sql
select Gene.* from Gene -- select all columns from Gene table
join AntibioticResistance on Gene.resistance_id = AntibioticResistance.resistance_id -- join Gene table with AntibioticResistance table
where AntibioticResistance.antibiotic_name = 'methicillin'; -- filter by antibiotic name
```

## 31. Select all proteins with length less than 500 amino acids
```sql
select * from Protein where protein_length < 500; -- select all columns from Protein table
```

## 32. Select all bacteria names and their associated plasmid names
```sql
select Bacteria.bacteria_name, Plasmid.plasmid_name from Bacteria -- select bacteria_name column from Bacteria table
join Plasmid on Bacteria.bacteria_id = Plasmid.bacteria_id; -- join Bacteria table with Plasmid table
```

## 33. Select all samples collected in 'UK' or 'France'
```sql
select * from Sample where country in ('UK', 'France'); -- select all columns from Sample table
```

## 34. Select all genes associated with 'Bacillus subtilis' and their accession IDs
```sql
select Gene.gene_name, Gene.accession_id from Gene -- select gene_name and accession_id columns from Gene table
join Bacteria on Gene.bacteria_id = Bacteria.bacteria_id -- join Gene table with Bacteria table
where Bacteria.bacteria_name = 'Bacillus subtilis'; -- filter by bacteria name
```

## 35. Select all sequencing records with 'medium' genome quality
```sql
select * from Sequencing where genome_quality = 'medium'; -- select all columns from Sequencing table
```

## 36. Select all antibiotic resistances with resistance mechanism 'beta-lactamase'
```sql
select * from AntibioticResistance where resistance_mechanism = 'beta-lactamase'; -- select all columns from AntibioticResistance table
```

## 37. Select all plasmids with 'medium' copy number and size greater than 2000 base pairs
```sql
select * from Plasmid where plasmid_copy_number = 'medium' and plasmid_size > 2000; -- select all columns from Plasmid table
```

## 38. Select all proteins with function containing 'synthesis'
```sql
select * from Protein where protein_function like '%synthesis%'; -- select all columns from Protein table
```

## 39. Select all pathways associated with 'Pseudomonas aeruginosa'
```sql
select Pathway.* from Pathway -- select all columns from Pathway table
join Bacteria on Pathway.bacteria_id = Bacteria.bacteria_id -- join Pathway table with Bacteria table
where Bacteria.bacteria_name = 'Pseudomonas aeruginosa'; -- filter by bacteria name
```

## 40. Select all bacteria names and their associated antibiotic names
```sql
select Bacteria.bacteria_name, AntibioticResistance.antibiotic_name from Bacteria -- select bacteria_name column from Bacteria table
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id; -- join Bacteria table with AntibioticResistance table
```

## 41. Select all samples collected from 'plant' host
```sql
select * from Sample where host = 'plant'; -- select all columns from Sample table
```

## 42. Select the average genome size for each sequencing method
```sql
select sequencing_method, avg(genome_size) as average_genome_size from Sequencing
group by sequencing_method;
```

## 43. Select the number of antibiotic resistances for each bacteria
```sql
select Bacteria.bacteria_name, count(AntibioticResistance.resistance_id) as resistance_count from Bacteria
left join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id
group by Bacteria.bacteria_name;
```

## 44. Select the top 3 bacteria with the highest number of associated genes
```sql
select Bacteria.bacteria_name, count(Gene.gene_id) as gene_count from Bacteria
join Gene on Bacteria.bacteria_id = Gene.bacteria_id
group by Bacteria.bacteria_name
order by gene_count desc
limit 3;
```

## 45. Select the bacteria with the highest minimum inhibitory concentration for 'ampicillin'
```sql
select Bacteria.bacteria_name, max(AntibioticResistance.minimum_inhibitory_concentration) as max_mic from Bacteria
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id
where AntibioticResistance.antibiotic_name = 'ampicillin'
group by Bacteria.bacteria_name
order by max_mic desc
limit 1;
```

## 46. Select the total number of samples collected each year
```sql
select year_of_collection, count(sample_id) as total_samples from Sample
group by year_of_collection;
```

## 47. Select the bacteria with the most diverse sample sources
```sql
select Bacteria.bacteria_name, count(distinct Sample.source) as source_count from Bacteria
join Sample on Bacteria.bacteria_id = Sample.bacteria_id
group by Bacteria.bacteria_name
order by source_count desc;
```

## 48. Select the average protein length for each bacteria
```sql
select Bacteria.bacteria_name, avg(Protein.protein_length) as average_protein_length from Bacteria
join Protein on Bacteria.bacteria_id = Protein.bacteria_id
group by Bacteria.bacteria_name;
```

## 49. Select the bacteria with the highest number of associated pathways
```sql
select Bacteria.bacteria_name, count(Pathway.pathway_id) as pathway_count from Bacteria
join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id
group by Bacteria.bacteria_name
order by pathway_count desc
limit 1;
```

## 50. Select the bacteria with the highest genome quality and completeness
```sql
select Bacteria.bacteria_name, Sequencing.genome_quality, Sequencing.genome_comepleteness from Bacteria
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id
where Sequencing.genome_quality = 'high' and Sequencing.genome_comepleteness = 'complete';
```

## 51. Select the bacteria with the most antibiotic resistances
```sql
select Bacteria.bacteria_name, count(AntibioticResistance.resistance_id) as resistance_count from Bacteria
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id
group by Bacteria.bacteria_name
order by resistance_count desc
limit 1;
```

## 52. Select the bacteria with the longest average protein length
```sql
select Bacteria.bacteria_name, avg(Protein.protein_length) as average_protein_length from Bacteria
join Protein on Bacteria.bacteria_id = Protein.bacteria_id
group by Bacteria.bacteria_name
order by average_protein_length desc
limit 1;
```

## 53. Select the bacteria with the highest number of clinical samples
```sql
select Bacteria.bacteria_name, count(Sample.sample_id) as clinical_sample_count from Bacteria
join Sample on Bacteria.bacteria_id = Sample.bacteria_id
where Sample.sample_type = 'clinical'
group by Bacteria.bacteria_name
order by clinical_sample_count desc
limit 1;
```

## 54. Select the bacteria with the most diverse antibiotic resistance mechanisms
```sql
select Bacteria.bacteria_name, count(distinct AntibioticResistance.resistance_mechanism) as mechanism_count from Bacteria
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id
group by Bacteria.bacteria_name
order by mechanism_count desc
limit 1;
```

## 55. Select the bacteria with the highest number of associated plasmids
```sql
select Bacteria.bacteria_name, count(Plasmid.plasmid_id) as plasmid_count from Bacteria
join Plasmid on Bacteria.bacteria_id = Plasmid.bacteria_id
group by Bacteria.bacteria_name
order by plasmid_count desc
limit 1;
```

## 56. Select the bacteria with the highest number of associated proteins
```sql
select Bacteria.bacteria_name, count(Protein.protein_id) as protein_count from Bacteria
join Protein on Bacteria.bacteria_id = Protein.bacteria_id
group by Bacteria.bacteria_name
order by protein_count desc
limit 1;
```

## 57. Select the bacteria with the highest number of associated genes with 'NC_' accession IDs
```sql
select Bacteria.bacteria_name, count(Gene.gene_id) as gene_count from Bacteria
join Gene on Bacteria.bacteria_id = Gene.bacteria_id
where Gene.accession_id like 'NC_%'
group by Bacteria.bacteria_name
order by gene_count desc
limit 1;
```

## 58. Select the bacteria with the highest number of associated sequencing records
```sql
select Bacteria.bacteria_name, count(Sequencing.sequencing_id) as sequencing_count from Bacteria
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id
group by Bacteria.bacteria_name
order by sequencing_count desc
limit 1;
```

## 59. Select the bacteria with the highest number of associated pathways containing 'biosynthesis'
```sql
select Bacteria.bacteria_name, count(Pathway.pathway_id) as pathway_count from Bacteria
join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id
where Pathway.pathway_description like '%biosynthesis%'
group by Bacteria.bacteria_name
order by pathway_count desc
limit 1;
```

## 60. Select the bacteria with the highest number of associated samples from 'human' host
```sql
select Bacteria.bacteria_name, count(Sample.sample_id) as sample_count from Bacteria
join Sample on Bacteria.bacteria_id = Sample.bacteria_id
where Sample.host = 'human'
group by Bacteria.bacteria_name
order by sample_count desc
limit 1;
```

## 61. Select all bacteria names and their associated gene names and accession IDs
```sql
select Bacteria.bacteria_name, Gene.gene_name, Gene.accession_id from Bacteria
join Gene on Bacteria.bacteria_id = Gene.bacteria_id;
```

## 62. Select all samples and their associated bacteria names and sequencing methods
```sql
select Sample.*, Bacteria.bacteria_name, Sequencing.sequencing_method from Sample
join Bacteria on Sample.bacteria_id = Bacteria.bacteria_id
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id;
```

## 63. Select all proteins and their associated bacteria names and pathways
```sql
select Protein.*, Bacteria.bacteria_name, Pathway.pathway_name from Protein
join Bacteria on Protein.bacteria_id = Bacteria.bacteria_id
join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id;
```

## 64. Select all antibiotic resistances and their associated bacteria names and genes
```sql
select AntibioticResistance.*, Bacteria.bacteria_name, Gene.gene_name from AntibioticResistance
join Bacteria on AntibioticResistance.bacteria_id = Bacteria.bacteria_id
left join Gene on Bacteria.bacteria_id = Gene.bacteria_id;
```

## 65. Select all plasmids and their associated bacteria names and proteins
```sql
select Plasmid.*, Bacteria.bacteria_name, Protein.protein_name from Plasmid
join Bacteria on Plasmid.bacteria_id = Bacteria.bacteria_id
right join Protein on Bacteria.bacteria_id = Protein.bacteria_id;
```

## 66. Select all pathways and their associated bacteria names and sequencing records
```sql
select Pathway.*, Bacteria.bacteria_name, Sequencing.sequencing_method from Pathway
join Bacteria on Pathway.bacteria_id = Bacteria.bacteria_id
left join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id;
```

## 67. Select all samples and their associated bacteria names and antibiotic resistances
```sql
select Sample.*, Bacteria.bacteria_name, AntibioticResistance.antibiotic_name from Sample
join Bacteria on Sample.bacteria_id = Bacteria.bacteria_id
left join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id;
```

## 68. Select all genes and their associated bacteria names and plasmids
```sql
select Gene.*, Bacteria.bacteria_name, Plasmid.plasmid_name from Gene
join Bacteria on Gene.bacteria_id = Bacteria.bacteria_id
left join Plasmid on Bacteria.bacteria_id = Plasmid.bacteria_id;
```

## 69. Select all proteins and their associated bacteria names and antibiotic resistances
```sql
select Protein.*, Bacteria.bacteria_name, AntibioticResistance.antibiotic_name from Protein
join Bacteria on Protein.bacteria_id = Bacteria.bacteria_id
left join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id;
```

## 70. Select all sequencing records and their associated bacteria names and pathways
```sql
select Sequencing.*, Bacteria.bacteria_name, Pathway.pathway_name from Sequencing
join Bacteria on Sequencing.bacteria_id = Bacteria.bacteria_id
left join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id;
```



