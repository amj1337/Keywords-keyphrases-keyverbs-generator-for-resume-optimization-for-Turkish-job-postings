# Keywords-keyphrases-keyverbs generator for resume optimization for Turkish job postings
## The problem that this project addresses
The odds of getting selected for an interview when cold applying to tech jobs have always had a reputation of being inefficient or not worth the effort.
This is understandable taking into consideration that the volume of applications to a single job position in a single department can be huge, so to save manpower and time most companies use an ATS (Applicant Tracking System) to scan and filter the submitted resumes(CVs), making it even harder for some applicants to pass to the next phase of the process even if they qualify for the position, simply, because they made a wrong choice of words causing their resumes(CVs) to be ranked lower by the ATS.

## The solution proposed by this project
An ATS parses resumes(CVs) for relatable technical keywords or/and key terms or/and key sentences or/and key verbs that are often found in the job description and ranks applicants accordingly.
So the aim of this project is to help increase the odds of passing the ATS and making it to the next phase of the process by matching a resume(CV) against the largest number possible of job postings for a specific role.
To achieve this, the main function is to scrape the largest Turkish job posting website https://kariyer.net for job postings of a specific role, then use natural language processing (NLP) techniques (tokenization, generating n-grams and lemmatization) to identify and extract the most frequent keywords/key terms/ key verbs, etc  for that role.

## Steps walkthrough
#### Scraping:
* Generate a list of URLs of each job posting from every page
* Create a list of every job description gathered from each posting

#### Generate Keywords/Key terms Key verbs, etc
* Data pre-processing:
  * Tokenization: split the long paragraphs of job descriptions into single words
  * Data cleaning: 
    * Convert all words to lowercase
    * Get rid of punctuation
    * Delete stopwords and noise words
  * Generating n-grams:
  generate multiple dictionaries of bigrams, trigrams, fourgrams, etc until the largest generated n-gram have occured only once in all job descriptions making it irrelevant and then pass them through a filter to get rid of ngrams that have weak frequency scores
  * Lemmatization:
    find the most used verbs in job descriptions and present them in their infinitive form
      * Get a list of all available turkish verbs from the TDK dictionary
      * Convert the verbs to their root form by removing the ‘mek’ and ‘mak’
      * Get a list of all possible turkish verbal suffixes
      * Scan the list of tokenized words from job descriptions for verbal suffixes and collect them as potential verbs
      * Scan the list of potential verbs for each root of each verb and collect them as verbs alongside their frequency score
      
## References
* Özge Doğuç - Ömer Berkay Aytaç - Gökhan Silahtaroğlu. Lemmatizer: Akıllı Türkçe Kök Bulma Yöntemi 
(https://www.researchgate.net/publication/346227584_Lemmatizer_Akilli_Turkce_Kok_Bulma_Yontemi)
* Hatem Haddad - Chedi Bechikh Ali. Performance of Turkish Information Retrieval: Evaluating the Impact of Linguistic Parameters and Compound Nouns
(https://www.researchgate.net/publication/263465256_Performance_of_Turkish_Information_Retrieval_Evaluating_the_Impact_of_Linguistic_Parameters_and_Compound_Nouns)
* Murat KALENDER - Emin Erkan KORKMAZ. Turkish entity discovery with word embeddings
(https://www.researchgate.net/publication/317343390_Turkish_entity_discovery_with_word_embeddings)
* Muskan Garg. A survey on different dimensions for graphical keyword extraction techniques
(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8062621/)
* Ahmet Aksoy's trstop  
(https://github.com/ahmetax/trstop/blob/master/dosyalar/turkce-stop-words)
* Necmettin Çarkacı's TDKDictionaryCrawler 
(https://github.com/ncarkaci/TDKDictionaryCrawler)
