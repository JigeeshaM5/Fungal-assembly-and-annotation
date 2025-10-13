Strains mentioned in this repository
1	OphiostomaipsWIN(M) 1478	PQ043840	TB 3.11 = UAMH12572	TB, Canada
2	O.ipsWIN(M) 1480	PQ043832	TB 3.10 = UAMH12573	TB, Canada

Included Pipelines

AAFTF genome assembly and filtering
Mitochondrial genome assembly (NOVOPlasty, GetOrganelle)
Genome annotation (Funannotate, antiSMASH)
FASTQ trimming (bbduk, Trimmomatic)
Repeat annotation (RepeatModeler)

# 🧬 Unified Fungal Genome Analysis Pipeline

This repository integrates multiple modular pipelines for fungal genome analysis, including:

- AAFTF genome assembly and filtering
- Mitochondrial genome assembly (NOVOPlasty, GetOrganelle)
- Genome annotation (Funannotate, antiSMASH)
- FASTQ trimming (bbduk, Trimmomatic)
- Repeat annotation (RepeatModeler)

Each pipeline is containerized with Docker and orchestrated using Snakemake.

---

## 📦 Pipeline Modules

### 1. AAFTF Assembly Pipeline
- Tools: bbduk, SPAdes, vecscreen, sourpurge, rmdup
- Input: Illumina paired-end reads
- Output: Cleaned and filtered genome assembly
- Location: `aaftf_pipeline/`

### 2. Mitochondrial Assembly
- Tools: NOVOPlasty, GetOrganelle
- Input: Paired-end reads and seed/reference sequence
- Output: Circularized and rotated mitochondrial genome
- Location: `novoplasty_pipeline/`, `fungal_mitogenome_pipeline/`

### 3. Genome Annotation
- Tools: Funannotate, antiSMASH
- Input: Masked genome, strain-specific template
- Output: Annotated GFF and GenBank files
- Location: `funannotate_pipeline/`

### 4. FASTQ Trimming
- Tools: bbduk, Trimmomatic
- Input: Raw FASTQ files
- Output: Quality-trimmed paired reads
- Location: `trimming_pipeline/`

### 5. Repeat Annotation
- Tools: RepeatModeler
- Input: Masked genome
- Output: Repeat library and combined repeat database
- Location: `repeatmodeler_pipeline/`

---

## 🐳 Docker Usage

Each pipeline includes a Dockerfile. To run any pipeline:

```bash
# Build Docker image
cd <pipeline_folder>
docker build -t <pipeline_name> .

# Run Snakemake workflow
docker run -v $(pwd):/app <pipeline_name> snakemake --cores 4
```

---

## ⚙️ Configuration

Each pipeline uses a `config/config.yaml` file to specify input files, parameters, and sample metadata.

---

## 📚 References

- AAFTF: https://github.com/stajichlab/AAFTF
- NOVOPlasty: https://github.com/ndierckx/NOVOPlasty
- GetOrganelle: https://github.com/Kinggerm/GetOrganelle
- Funannotate: https://github.com/nextgenusfs/funannotate
- antiSMASH: https://antismash.secondarymetabolites.org
- Trimmomatic: http://www.usadellab.org/cms/?page=trimmomatic
- bbduk: https://jgi.doe.gov/data-and-tools/bbtools/
- RepeatModeler: https://www.repeatmasker.org/RepeatModeler/

---




Each pipeline is modular, Dockerized, and orchestrated with Snakemake.
