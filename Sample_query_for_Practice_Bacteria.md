# Practice SQL queries

-- 1. Select all bacteria names
select bacteria_name from Bacteria; -- select only bacteria_name column

-- 2. Select all samples collected in the year 2019
select * from Sample where year_of_collection = 2019; -- select all columns from Sample table

-- 3. Select all genes associated with 'Escherichia coli'
select Gene.* from Gene -- select all columns from Gene table
join Bacteria on Gene.bacteria_id = Bacteria.bacteria_id -- join Gene table with Bacteria table
where Bacteria.bacteria_name = 'Escherichia coli'; -- filter by bacteria name

-- 4. Select all sequencing methods used
select distinct sequencing_method from Sequencing; -- select distinct sequencing methods from Sequencing table

-- 5. Select all antibiotic resistances for 'Staphylococcus aureus'
select AntibioticResistance.* from AntibioticResistance -- select all columns from AntibioticResistance table
join Bacteria on AntibioticResistance.bacteria_id = Bacteria.bacteria_id -- join AntibioticResistance table with Bacteria table
where Bacteria.bacteria_name = 'Staphylococcus aureus'; -- filter by bacteria name

-- 6. Select all plasmids with high copy number
select * from Plasmid where plasmid_copy_number = 'high'; -- select all columns from Plasmid table

-- 7. Select all proteins with length greater than 500 amino acids
select * from Protein where protein_length > 500; -- select all columns from Protein table

-- 8. Select all pathways related to 'DNA replication'
select * from Pathway where pathway_name = 'DNA replication'; -- select all columns from Pathway table

-- 9. Select all bacteria collected from 'USA'
select Bacteria.* from Bacteria -- select all columns from Bacteria table
join Sample on Bacteria.bacteria_id = Sample.bacteria_id -- join Bacteria table with Sample table
where Sample.country = 'USA'; -- filter by country

-- 10. Select all bacteria with genome size greater than 5,000,000 base pairs
select Bacteria.* from Bacteria -- select all columns from Bacteria table
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id -- join Bacteria table with Sequencing table
where Sequencing.genome_size > 5000000; -- filter by genome size

-- 11. Select all samples of type 'clinical'
select * from Sample where sample_type = 'clinical'; -- select all columns from Sample table

-- 12. Select all genes with accession ID starting with 'NC_00'
select * from Gene where accession_id like 'NC_00%'; -- select all columns from Gene table

-- 13. Select all proteins with unknown function
select * from Protein where protein_function = 'unknown'; -- select all columns from Protein table

-- 14. Select all bacteria with resistance to 'ampicillin'
select Bacteria.* from Bacteria -- select all columns from Bacteria table
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id -- join Bacteria table with AntibioticResistance table
where AntibioticResistance.antibiotic_name = 'ampicillin'; -- filter by antibiotic name

-- 15. Select all samples from 'human' host
select * from Sample where host = 'human'; -- select all columns from Sample table 

-- 16. Select all sequencing records published in 2019
select * from Sequencing where year_of_publication = 2019; -- select all columns from Sequencing table

-- 17. Select all plasmids with size less than 3000 base pairs
select * from Plasmid where plasmid_size < 3000; -- select all columns from Plasmid table

-- 18. Select all pathways with description containing 'synthesis' 
select * from Pathway where pathway_description like '%synthesis%'; -- select all columns from Pathway table

-- 19. Select all bacteria with at least one associated gene
select distinct Bacteria.* from Bacteria -- select distinct bacteria records
join Gene on Bacteria.bacteria_id = Gene.bacteria_id; -- join Bacteria table with Gene table

-- 20. Select all samples from 'clinical' type collected in 'USA'
select * from Sample where sample_type = 'clinical' and country = 'USA'; -- select all columns from Sample table

-- 21. Select all bacteria names and their associated gene names
select Bacteria.bacteria_name, Gene.gene_name from Bacteria -- select bacteria_name column from Bacteria table
join Gene on Bacteria.bacteria_id = Gene.bacteria_id; -- join Bacteria table with Gene table

-- 22. Select all samples collected from 'human' host in the year 2020
select * from Sample where host = 'human' and year_of_collection = 2020; -- select all columns from Sample table

-- 23. Select all sequencing records with 'high' genome quality and 'complete' genome completeness
select * from Sequencing where genome_quality = 'high' and genome_comepleteness = 'complete'; -- select all columns from Sequencing table

-- 24. Select all antibiotic resistances with minimum inhibitory concentration greater than 16
select * from AntibioticResistance where minimum_inhibitory_concentration > 16; -- select all columns from AntibioticResistance table

-- 25. Select all plasmids associated with 'Escherichia coli'
select Plasmid.* from Plasmid -- select all columns from Plasmid table
join Bacteria on Plasmid.bacteria_id = Bacteria.bacteria_id -- join Plasmid table with Bacteria table
where Bacteria.bacteria_name = 'Escherichia coli'; -- filter by bacteria name

-- 26. Select all proteins associated with 'Staphylococcus aureus'
select Protein.* from Protein -- select all columns from Protein table
join Bacteria on Protein.bacteria_id = Bacteria.bacteria_id -- join Protein table with Bacteria table
where Bacteria.bacteria_name = 'Staphylococcus aureus'; -- filter by bacteria name

-- 27. Select all pathways associated with 'Bacillus subtilis'
select Pathway.* from Pathway -- select all columns from Pathway table
join Bacteria on Pathway.bacteria_id = Bacteria.bacteria_id -- join Pathway table with Bacteria table
where Bacteria.bacteria_name = 'Bacillus subtilis'; -- filter by bacteria name

-- 28. Select all bacteria names and their associated sequencing methods
select Bacteria.bacteria_name, Sequencing.sequencing_method from Bacteria -- select bacteria_name column from Bacteria table
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id; -- join Bacteria table with Sequencing table

-- 29. Select all samples collected from 'soil' source
select * from Sample where source = 'soil'; -- select all columns from Sample table

-- 30. Select all genes with resistance to 'methicillin'
select Gene.* from Gene -- select all columns from Gene table
join AntibioticResistance on Gene.resistance_id = AntibioticResistance.resistance_id -- join Gene table with AntibioticResistance table
where AntibioticResistance.antibiotic_name = 'methicillin'; -- filter by antibiotic name

-- 31. Select all proteins with length less than 500 amino acids
select * from Protein where protein_length < 500; -- select all columns from Protein table

-- 32. Select all bacteria names and their associated plasmid names
select Bacteria.bacteria_name, Plasmid.plasmid_name from Bacteria -- select bacteria_name column from Bacteria table
join Plasmid on Bacteria.bacteria_id = Plasmid.bacteria_id; -- join Bacteria table with Plasmid table

-- 33. Select all samples collected in 'UK' or 'France' 
select * from Sample where country in ('UK', 'France'); -- select all columns from Sample table

-- 34. Select all genes associated with 'Bacillus subtilis' and their accession IDs
select Gene.gene_name, Gene.accession_id from Gene -- select gene_name and accession_id columns from Gene table
join Bacteria on Gene.bacteria_id = Bacteria.bacteria_id -- join Gene table with Bacteria table
where Bacteria.bacteria_name = 'Bacillus subtilis'; -- filter by bacteria name

-- 35. Select all sequencing records with 'medium' genome quality
select * from Sequencing where genome_quality = 'medium'; -- select all columns from Sequencing table

-- 36. Select all antibiotic resistances with resistance mechanism 'beta-lactamase'
select * from AntibioticResistance where resistance_mechanism = 'beta-lactamase'; -- select all columns from AntibioticResistance table

-- 37. Select all plasmids with 'medium' copy number and size greater than 2000 base pairs
select * from Plasmid where plasmid_copy_number = 'medium' and plasmid_size > 2000; -- select all columns from Plasmid table

-- 38. Select all proteins with function containing 'synthesis'
select * from Protein where protein_function like '%synthesis%'; -- select all columns from Protein table

-- 39. Select all pathways associated with 'Pseudomonas aeruginosa'
select Pathway.* from Pathway -- select all columns from Pathway table
join Bacteria on Pathway.bacteria_id = Bacteria.bacteria_id -- join Pathway table with Bacteria table
where Bacteria.bacteria_name = 'Pseudomonas aeruginosa'; -- filter by bacteria name

-- 40. Select all bacteria names and their associated antibiotic names
select Bacteria.bacteria_name, AntibioticResistance.antibiotic_name from Bacteria -- select bacteria_name column from Bacteria table
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id; -- join Bacteria table with AntibioticResistance table

-- 41. Select all samples collected from 'plant' host
select * from Sample where host = 'plant'; -- select all columns from Sample table

-- 42. Select the average genome size for each sequencing method
select sequencing_method, avg(genome_size) as average_genome_size from Sequencing -- select sequencing_method column and average genome_size
group by sequencing_method; -- group by sequencing method

-- 43. Select the number of antibiotic resistances for each bacteria
select Bacteria.bacteria_name, count(AntibioticResistance.resistance_id) as resistance_count from Bacteria -- select bacteria_name column and count of resistance_id
left join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id -- left join Bacteria table with AntibioticResistance table
group by Bacteria.bacteria_name; -- group by bacteria name

-- 44. Select the top 3 bacteria with the highest number of associated genes
select Bacteria.bacteria_name, count(Gene.gene_id) as gene_count from Bacteria -- select bacteria_name column and count of gene_id
join Gene on Bacteria.bacteria_id = Gene.bacteria_id -- join Bacteria table with Gene table
group by Bacteria.bacteria_name -- group by bacteria name
order by gene_count desc -- order by gene count in descending order
limit 3; -- limit to top 3 records

-- 45. Select the bacteria with the highest minimum inhibitory concentration for 'ampicillin'
select Bacteria.bacteria_name, max(AntibioticResistance.minimum_inhibitory_concentration) as max_mic from Bacteria -- select bacteria_name column and max minimum_inhibitory_concentration
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id -- join Bacteria table with AntibioticResistance table
where AntibioticResistance.antibiotic_name = 'ampicillin' -- filter by antibiotic name
group by Bacteria.bacteria_name -- group by bacteria name
order by max_mic desc -- order by max minimum inhibitory concentration in descending order
limit 1; -- limit to top 1 record

-- 46. Select the total number of samples collected each year
select year_of_collection, count(sample_id) as total_samples from Sample -- select year_of_collection column and count of sample_id
group by year_of_collection; -- group by year_of_collection

-- 47. Select the bacteria with the most diverse sample sources
select Bacteria.bacteria_name, count(distinct Sample.source) as source_count from Bacteria -- select bacteria_name column and count of distinct source
join Sample on Bacteria.bacteria_id = Sample.bacteria_id -- join Bacteria table with Sample table
group by Bacteria.bacteria_name -- group by bacteria name
order by source_count desc; -- order by source count in descending order

-- 48. Select the average protein length for each bacteria
select Bacteria.bacteria_name, avg(Protein.protein_length) as average_protein_length from Bacteria -- select bacteria_name column and average protein_length
join Protein on Bacteria.bacteria_id = Protein.bacteria_id -- join Bacteria table with Protein table
group by Bacteria.bacteria_name; -- group by bacteria name

-- 49. Select the bacteria with the highest number of associated pathways
select Bacteria.bacteria_name, count(Pathway.pathway_id) as pathway_count from Bacteria -- select bacteria_name column and count of pathway_id
join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id -- join Bacteria table with Pathway table
group by Bacteria.bacteria_name -- group by bacteria name
order by pathway_count desc -- order by pathway count in descending order
limit 1; -- limit to top 1 record

-- 50. Select the bacteria with the highest genome quality and completeness
select Bacteria.bacteria_name, Sequencing.genome_quality, Sequencing.genome_comepleteness from Bacteria -- select bacteria_name, genome_quality, and genome_completeness columns
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id -- join Bacteria table with Sequencing table
where Sequencing.genome_quality = 'high' and Sequencing.genome_comepleteness = 'complete'; -- filter by genome quality and completeness

-- 51. Select the bacteria with the most antibiotic resistances
select Bacteria.bacteria_name, count(AntibioticResistance.resistance_id) as resistance_count from Bacteria -- select bacteria_name column and count of resistance_id
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id -- join Bacteria table with AntibioticResistance table
group by Bacteria.bacteria_name -- group by bacteria name
order by resistance_count desc -- order by resistance count in descending order
limit 1; -- limit to top 1 record

-- 52. Select the bacteria with the longest average protein length
select Bacteria.bacteria_name, avg(Protein.protein_length) as average_protein_length from Bacteria -- select bacteria_name column and average protein_length
join Protein on Bacteria.bacteria_id = Protein.bacteria_id -- join Bacteria table with Protein table
group by Bacteria.bacteria_name -- group by bacteria name
order by average_protein_length desc -- order by average protein length in descending order
limit 1; -- limit to top 1 record

-- 53. Select the bacteria with the highest number of clinical samples
select Bacteria.bacteria_name, count(Sample.sample_id) as clinical_sample_count from Bacteria -- select bacteria_name column and count of sample_id
join Sample on Bacteria.bacteria_id = Sample.bacteria_id -- join Bacteria table with Sample table
where Sample.sample_type = 'clinical' -- filter by sample type
group by Bacteria.bacteria_name -- group by bacteria name
order by clinical_sample_count desc -- order by clinical sample count in descending order
limit 1; -- limit to top 1 record

-- 54. Select the bacteria with the most diverse antibiotic resistance mechanisms
select Bacteria.bacteria_name, count(distinct AntibioticResistance.resistance_mechanism) as mechanism_count from Bacteria -- select bacteria_name column and count of distinct resistance_mechanism
join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id -- join Bacteria table with AntibioticResistance table
group by Bacteria.bacteria_name -- group by bacteria name
order by mechanism_count desc -- order by mechanism count in descending order
limit 1; -- limit to top 1 record

-- 55. Select the bacteria with the highest number of associated plasmids
select Bacteria.bacteria_name, count(Plasmid.plasmid_id) as plasmid_count from Bacteria -- select bacteria_name column and count of plasmid_id
join Plasmid on Bacteria.bacteria_id = Plasmid.bacteria_id -- join Bacteria table with Plasmid table
group by Bacteria.bacteria_name -- group by bacteria name
order by plasmid_count desc -- order by plasmid count in descending order
limit 1; -- limit to top 1 record

-- 56. Select the bacteria with the highest number of associated proteins
select Bacteria.bacteria_name, count(Protein.protein_id) as protein_count from Bacteria -- select bacteria_name column and count of protein_id
join Protein on Bacteria.bacteria_id = Protein.bacteria_id -- join Bacteria table with Protein table
group by Bacteria.bacteria_name -- group by bacteria name
order by protein_count desc -- order by protein count in descending order
limit 1; -- limit to top 1 record

-- 57. Select the bacteria with the highest number of associated genes with 'NC_' accession IDs
select Bacteria.bacteria_name, count(Gene.gene_id) as gene_count from Bacteria -- select bacteria_name column and count of gene_id
join Gene on Bacteria.bacteria_id = Gene.bacteria_id -- join Bacteria table with Gene table
where Gene.accession_id like 'NC_%' -- filter by accession ID
group by Bacteria.bacteria_name -- group by bacteria name
order by gene_count desc -- order by gene count in descending order
limit 1; -- limit to top 1 record

-- 58. Select the bacteria with the highest number of associated sequencing records
select Bacteria.bacteria_name, count(Sequencing.sequencing_id) as sequencing_count from Bacteria -- select bacteria_name column and count of sequencing_id
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id -- join Bacteria table with Sequencing table
group by Bacteria.bacteria_name -- group by bacteria name
order by sequencing_count desc -- order by sequencing count in descending order
limit 1; -- limit to top 1 record

-- 59. Select the bacteria with the highest number of associated pathways containing 'biosynthesis'
select Bacteria.bacteria_name, count(Pathway.pathway_id) as pathway_count from Bacteria --  select bacteria_name column and count of pathway_id 
join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id -- join Bacteria table with Pathway table
where Pathway.pathway_description like '%biosynthesis%' -- filter by pathway description
group by Bacteria.bacteria_name -- group by bacteria name
order by pathway_count desc -- order by pathway count in descending order
limit 1; -- limit to top 1 record

-- 60. Select the bacteria with the highest number of associated samples from 'human' host
select Bacteria.bacteria_name, count(Sample.sample_id) as sample_count from Bacteria -- select bacteria_name column and count of sample_id
join Sample on Bacteria.bacteria_id = Sample.bacteria_id -- join Bacteria table with Sample table
where Sample.host = 'human' -- filter by host
group by Bacteria.bacteria_name -- group by bacteria name
order by sample_count desc -- order by sample count in descending order
limit 1; -- limit to top 1 record

-- 61. Select all bacteria names and their associated gene names and accession IDs
select Bacteria.bacteria_name, Gene.gene_name, Gene.accession_id from Bacteria -- select bacteria_name, gene_name, and accession_id columns
join Gene on Bacteria.bacteria_id = Gene.bacteria_id; -- join Bacteria table with Gene table

-- 62. Select all samples and their associated bacteria names and sequencing methods
select Sample.*, Bacteria.bacteria_name, Sequencing.sequencing_method from Sample -- select all columns from Sample table, and bacteria_name and sequencing_method columns
join Bacteria on Sample.bacteria_id = Bacteria.bacteria_id -- join Sample table with Bacteria table
join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id; -- join Bacteria table with Sequencing table

-- 63. Select all proteins and their associated bacteria names and pathways
select Protein.*, Bacteria.bacteria_name, Pathway.pathway_name from Protein -- select all columns from Protein table, and bacteria_name and pathway_name columns
join Bacteria on Protein.bacteria_id = Bacteria.bacteria_id -- join Protein table with Bacteria table
join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id; -- join Bacteria table with Pathway table

-- 64. Select all antibiotic resistances and their associated bacteria names and genes
select AntibioticResistance.*, Bacteria.bacteria_name, Gene.gene_name from AntibioticResistance -- select all columns from AntibioticResistance table, and bacteria_name and gene_name columns
join Bacteria on AntibioticResistance.bacteria_id = Bacteria.bacteria_id -- join AntibioticResistance table with Bacteria table
left join Gene on Bacteria.bacteria_id = Gene.bacteria_id; -- left join Bacteria table with Gene table

-- 65. Select all plasmids and their associated bacteria names and proteins
select Plasmid.*, Bacteria.bacteria_name, Protein.protein_name from Plasmid -- select all columns from Plasmid table, and bacteria_name and protein_name columns
join Bacteria on Plasmid.bacteria_id = Bacteria.bacteria_id -- join Plasmid table with Bacteria table
right join Protein on Bacteria.bacteria_id = Protein.bacteria_id; -- right join Bacteria table with Protein table

-- 66. Select all pathways and their associated bacteria names and sequencing records
select Pathway.*, Bacteria.bacteria_name, Sequencing.sequencing_method from Pathway -- select all columns from Pathway table, and bacteria_name and sequencing_method columns
join Bacteria on Pathway.bacteria_id = Bacteria.bacteria_id -- join Pathway table with Bacteria table
left join Sequencing on Bacteria.bacteria_id = Sequencing.bacteria_id; -- left join Bacteria table with Sequencing table

-- 67. Select all samples and their associated bacteria names and antibiotic resistances
select Sample.*, Bacteria.bacteria_name, AntibioticResistance.antibiotic_name from Sample -- select all columns from Sample table, and bacteria_name and antibiotic_name columns
join Bacteria on Sample.bacteria_id = Bacteria.bacteria_id -- join Sample table with Bacteria table
left join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id; -- left join Bacteria table with AntibioticResistance table

-- 68. Select all genes and their associated bacteria names and plasmids
select Gene.*, Bacteria.bacteria_name, Plasmid.plasmid_name from Gene -- select all columns from Gene table, and bacteria_name and plasmid_name columns
join Bacteria on Gene.bacteria_id = Bacteria.bacteria_id -- join Gene table with Bacteria table
left join Plasmid on Bacteria.bacteria_id = Plasmid.bacteria_id; -- left join Bacteria table with Plasmid table

-- 69. Select all proteins and their associated bacteria names and antibiotic resistances
select Protein.*, Bacteria.bacteria_name, AntibioticResistance.antibiotic_name from Protein -- select all columns from Protein table, and bacteria_name and antibiotic_name columns
join Bacteria on Protein.bacteria_id = Bacteria.bacteria_id -- join Protein table with Bacteria table
left join AntibioticResistance on Bacteria.bacteria_id = AntibioticResistance.bacteria_id; -- left join Bacteria table with AntibioticResistance table

-- 70. Select all sequencing records and their associated bacteria names and pathways
select Sequencing.*, Bacteria.bacteria_name, Pathway.pathway_name from Sequencing -- select all columns from Sequencing table, and bacteria_name and pathway_name columns
join Bacteria on Sequencing.bacteria_id = Bacteria.bacteria_id -- join Sequencing table with Bacteria table
left join Pathway on Bacteria.bacteria_id = Pathway.bacteria_id; -- left join Bacteria table with Pathway table


