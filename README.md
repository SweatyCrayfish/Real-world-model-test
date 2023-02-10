# Real-world-model-test
BERT pre trained dataset:
As recent word representation models such as Word2Vec (Mikolov et al., 2013), ELMo (Peters et al., 2018) and BERT (Devlin et al., 2019) are trained and tested mainly on datasets containing general domain texts (e.g. Wikipedia) it is difficult to estimate their performance on datasets containing biomedical texts. In other words, hypothetically BERT can produce a better result, but it will be difficult to determine a success criteria and justify produced results in Bio Related text.
BioBERT pre trained data set:
Pre-train BioBERT on PubMed abstracts (PubMed) and PubMed Central full-text articles (PMC)
BioBERT (+PubMed)	Wiki + Books + PubMed
BioBERT (+PMC)	Wiki + Books + PMC
BioBERT (+PubMed + PMC)	Wiki + Books + PubMed + PMC

As it is shown from the above the difference between BERT and BioBERT is that BioBERT includes an additional 2 data set PubMed and PMC
PubMed: https://pubmed.ncbi.nlm.nih.gov/28881963/ 
PMC: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6538547/ 
PMC consist of 
JNLPBA (Kim et al., 2004)	Gene/Proteins	22,562	35,336	2404 abstracts
				
We used the pre-processed versions of all the NER datasets provided by Wang et al. (2018) except the 2010 i2b2/VA, JNLPBA and Species-800 datasets.
Comparison QA model BERT vs BioBERT:
Table 9.
Prediction samples from BERT and BioBERT on NER and QA datasets
Task	Dataset	Model	Sample
NER	NCBI disease	BERT	WT1 missense mutations, associated with male pseudohermaphroditism in Denys–Drash syndrome, fail to …
		BioBERT	WT1 missense mutations, associated with male pseudohermaphroditism in Denys–Drash syndrome, fail to …
	BC5CDR (Drug/Chem.)	BERT	… a case of oral penicillin anaphylaxis is described, and the terminology …
		BioBERT	… a case of oral penicillin anaphylaxis is described, and the terminology …
	BC2GM	BERT	Like the DMA, but unlike all other mammalian class II A genes, the zebrafish gene codes for two cysteine residues …
		BioBERT	Like the DMA, but unlike all other mammalian class II A genes, the zebrafish gene codes for two cysteine residues …
QA	BioASQ 6b-factoid		Q: Which type of urinary incontinence is diagnosed with the Q tip test?
		BERT	A total of 25 women affected by clinical stress urinary incontinence (SUI) were enrolled. After undergoing (…) Q-tip test, …
		BioBERT	A total of 25 women affected by clinical stress urinary incontinence (SUI) were enrolled. After undergoing (…) Q-tip test, …
			Q: Which bacteria causes erythrasma?
		BERT	Corynebacterium minutissimum is the bacteria that leads to cutaneous eruptions of erythrasma …
		BioBERT	Corynebacterium minutissimum is the bacteria that leads to cutaneous eruptions of erythrasma …

Note: Predicted named entities for NER and predicted answers for QA are in bold.



Stanza test data:
CRAFT data set:
•	67 full text articles
•	>560,000 Tokens
•	>21,000 Sentences
•	~100,000 concept annotations to 7 different biomedical ontologies/terminologies
•	Chemical Entities of Biological Interest
•	Cell Ontology
•	Entrez Gene
•	Gene Ontology (biological process, cellular component, and molecular function)
•	NCBI Taxonomy
•	Protein Ontology
•	Sequence Ontology
•	Coreference annotations
•	Penn Treebank markup for each sentence
•	Multiple output formats available
•	Integrated with UIMA
Link to the data set: http://bionlp-corpora.sourceforge.net/CRAFT/ 
We use the CRAFT test set, which contains about 1.2 million raw characters, for benchmarking the syntactic analysis pipeline, and the test split of the JNLPBA NER dataset, which contains about 101k tokens, for benchmarking the NER task. PubMed data set was used.
Table 3.
Named entity recognition performance across different datasets in the biomedical and clinical domains
Category	Dataset	Domain (# of Entities)	Stanza	BioBERT	scispaCy
Bio	AnatEM	Anatomy (1)	88.18	–	84.14
	BC5CDR	Chemical, Disease (2)	88.08	–	83.92
	BC4CHEMD	Chemical (1)	89.65	92.36	84.55
	BioNLP13CG	Cancer Genetics (16)	84.34	–	77.60
	JNLPBA	Protein, DNA, RNA, Cell line, Cell type (5)	76.09	77.49	73.21
	Linnaeus	Species (1)	88.27	88.24	81.74
	NCBI-Disease	Disease (1)	87.49	89.71	81.65
	S800	Species (1)	76.35	74.06	–
Clinical	i2b2	Problem, Test, Treatment (3)	88.13	86.73	–
	Radiology	Radiology Report (5)	84.80	–	–

All scores reported are entity micro-averaged test F1. For each dataset, we also list the domain and number of its entity types. BioBERT results are from the v1.1 models reported by Lee et al; scispaCy results are from the scispacy-medium models reported by Neumann et al. 
In addition to BioBERT, we also compare Stanza’s performance with SciBERT,43 which achieves F1 scores of 90.01, 77.28, and 88.57 on the BC5CDR, JNLPBA, and NCBI-Disease datasets, respectively, and ClinicalBERT,44 which achieves an F1 score of 86.4 on the i2b2 dataset. We find that Stanza’s performance is on par with or better than the strong performance offered by SciBERT and ClinicalBERT, too.


Legal aspects
	When we use Stanza package we must cite Stanza’s paper to avoid legal actions
https://academic.oup.com/jamia/article/28/9/1892/6307885 
	When we use BioBERT package we must cite them to avoid legal penalties
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7703786/#__sec1title 
Conclusion
	If data set consist of many different summaries related to different biological subjects than Stanza could produce better results. However, if data set is consist of Protein, DNA, RNA, Cell line, Cell type sets than BioBERT is a better solution mainly because BioBERT has BC2GM(gene/protein) model. On the other hand BioBERT does not include cancer gene/protein model such as BioNLP13CG(cancer gene/protein).
