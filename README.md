# MyGenome
## Created a directory to keep my sequences in 
mkdir MyGenome 
## Downloaded the samples being used in the project to the MyGenome directory 
scp 
## Downloaded necesary tools for analyzing and processing the sequences
wget https://d3gcli72yxqn2z.cloudfront.net/downloads/connect/latest/bin/ibm-aspera-connect_4.2.13.820_linux_x86_64.tar.gz
tar zxvf ibm-aspera-connect_4.2.13.820_linux_x86_64.tar.gz
scp "C:\Users\rhyst\Downloads\aspera.openssh" rdta226@rdta226.cs.uky.edu:unix/MyGenome
## uploading my sequences to NCBI database for SRA/submission 
 ~/.aspera/connect/bin/ascp -i MyGenome/aspera.openssh -QT -l100m -k1 -d MyGenome/Po17/sequences/ subasp@upload.ncbi.nlm.nih.gov:uploads/Rhys.Talbot_uky.edu_f1AchzO0
## running my samples through fastqc 
fastqc Ec883_1.fq.gz Ec883_2.fq.gz
## Fastqc reports for each file (basic stats) 
# Ec883_1
![Screenshot 2025-02-27 142740](https://github.com/user-attachments/assets/5b8b7ef5-06b4-41fe-a15b-1bb3f3ae5589)
# Ec883_2
![Screenshot 2025-02-27 142807](https://github.com/user-attachments/assets/6f2ebcee-c81c-4d64-ba1d-3afce8a054f4)
## Fastqc quality reports 
# Ec883_1
![Screenshot 2025-02-27 142753](https://github.com/user-attachments/assets/0be20d38-f999-4e14-bfc3-912d67373209)
# Ec883_2
![Screenshot 2025-02-27 142818](https://github.com/user-attachments/assets/e8a8bb1c-8263-4fa5-a0bc-5cfae1f37584)
## Fastqc Adaptor report
# Ec883_1
![Screenshot 2025-02-27 142802](https://github.com/user-attachments/assets/388e9b12-99d4-4408-9945-d7eade9f5a38)
# Ec883_2
![Screenshot 2025-02-27 142830](https://github.com/user-attachments/assets/f72bd4e0-f0b1-4ae2-8e22-4e60099bad6c)
## Trimming the samples to remove adaptor contamination 
 java -jar ~/sequences/trimmomatic-0.38.jar PE -threads 2 -phred33 -trimlog Ec883_errorlog.txt Ec883_1_paired.fq Ec883_2_paired.fq Ec883_3_paired.fq Ec883_3_unpaired.fq Ec883_4_paired.fq Ec883_4_unpaired.fq ILLUMINACLIP:adaptors.fa:2:30:10 SLIDINGWINDOW:20:20 MINLEN:100
 ## Fastqc after trimming (basic stats) 
 # Ec883_3
![Screenshot 2025-02-27 142840](https://github.com/user-attachments/assets/1509574e-95b7-41d6-9c31-f378602fadbf)
 # Ec883_4
 ![Screenshot 2025-02-27 142906](https://github.com/user-attachments/assets/30773bf5-ce90-46be-8103-eca404bbd176)
 ## Fastqc quality report
 # Ec883_3
 ![Screenshot 2025-02-27 142850](https://github.com/user-attachments/assets/e89ef9b5-f2f4-4f0b-a5fb-81cae51dbe01)
 # Ec883_4 
 ![Screenshot 2025-02-27 142912](https://github.com/user-attachments/assets/04ed3376-18e9-4e71-9a36-90ed3728e37d)
 ## Fastqc Adaptor contamination 
 # Ec883_3
 ![Screenshot 2025-02-27 142859](https://github.com/user-attachments/assets/0b1ad0b6-ccac-4196-8adb-dad782e5b278)
 # Ec883_4 
 ![Screenshot 2025-02-27 142920](https://github.com/user-attachments/assets/30f98a67-7b70-4577-9b44-40eaa1aa572c)
