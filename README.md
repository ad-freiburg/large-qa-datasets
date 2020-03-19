# Large Question Answering Datasets
A collection of large datasets containing questions and their answers for use in Natural Language Processing tasks like question answering (QA).
Datasets are sorted by year of publication.

## Question Datasets

#### WebQuestions
*Berant et al.* \
**PDF:** <https://www.aclweb.org/anthology/D13-1160.pdf> \
**Dataset:** <https://github.com/brmson/dataset-factoid-webquestions> \
**Year of Publication:** 2013 \
**Size:** 5,810\
**Data Collection:**
Berant et al. use the Google Suggest API as basis for generating questions.
They start with a single question (*"Where was Barack Obama born"*) and feed the Google Suggest API with three query fragments generated from the source question: the question without the phrase before the entity, the question without the entity and the question without the phrase after the entity. Each of these queries generates 5 candidate questions. The candidate questions are added to a queue of questions and the process is repeated for each of the questions in the queue. They stop after 1M questions are generated.
Due to the nature of the approach, the generated questions start with a wh-word and revolve around a single entity.
100K of these questions are given to crowdsourcing workers who select a Freebase entity, value or list of entities as answer. Questions that are answered identically by at least two workers are included in the dataset. \
**Examples:**

    {"qId": "wqr001696", "answers": ["Federal republic"], "qText": "what is the politicals system of nigeria?"}
    {"qId": "wqr001095", "answers": ["Italia Conti Academy of Theatre Arts"], "qText": "where did pixie lott go to school?"}
    {"qId": "wqr003126", "answers": ["Mwinilunga"], "qText": "where does the zambezi river begin?"}
    {"qId": "wqr003288", "answers": ["Westlake High School", "University of Florida", "Auburn University", "Blinn College"], "qText": "what school did cam newton go to before auburn?"}
    {"qId": "wqr001075", "answers": ["Dwayne Carter III"], "qText": "what is lil wayne real name?"}


#### SimpleQuestions
*Bordes et al.* \
**PDF:** <https://arxiv.org/pdf/1506.02075.pdf>\
**Dataset:** <https://research.fb.com/downloads/babi/> \
**Year of Publication:** 2015 \
**Size:** 108,442 \
**Data Collection:** Bordes et al. collect Freebase facts as subject - predicate - object triples. Human English-speaking annotators are then asked to form a question from the subject and predicate of the triple such that the object answers the question. \
**Examples:**

    www.freebase.com/m/0fll_lg  www.freebase.com/music/release/track    www.freebase.com/m/0dwkrfl  What's a song off of knuffelrock 6
    www.freebase.com/m/09nzdd   www.freebase.com/film/director/film www.freebase.com/m/0tm5mj7  which film was directed by joseph morgan (actor)
    www.freebase.com/m/02hlgmw  www.freebase.com/cvg/game_version/publisher www.freebase.com/m/020wds   Who published heart of the maelstrom
    www.freebase.com/m/03nq3v   www.freebase.com/people/deceased_person/place_of_death  www.freebase.com/m/09jp3    where did juan antonio lavalleja's life end?
    www.freebase.com/m/0299rn   www.freebase.com/people/deceased_person/place_of_death  www.freebase.com/m/04swd    where in russia did  agostinho neto pass


#### CNN/DailyMail Corpus
*Hermann et al.*\
**PDF:** <https://arxiv.org/pdf/1506.03340.pdf>\
**Dataset:** <https://github.com/deepmind/rc-data/> \
**Year of Publication:** 2015 \
**Size:** ca. 1M \
**Data Collection:** Hermann et al. construct a reading comprehension dataset by collecting articles from the CNN and DailyMail websites. They use the websites' summarization statements to create Cloze style questions by replacing single entities with placeholders. Entities are anonymized within articles to prevent systems from infering answers using general world knowledge.\
**Examples:**

    <news article> Costa Concordia ran aground off @placeholder in january 2012 , killing 32 people [Giglio]
    <news article> the attacks are in retaliation for the death of bin Laden , @placeholder Taliban say [Pakistani]
    <news article> Baker , a junior at @placeholder , describes night of homecoming dance [Richmond High]
    <news article> rural workers migrating to @placeholder cities for work have little access to social services [China]
    <news article> @placeholder and Instagram posts go viral [Facebook]


#### Children's Book Test (CBT)
*Hill et al.* \
**PDF:** <https://arxiv.org/pdf/1511.02301.pdf>\
**Dataset:** <https://research.fb.com/downloads/babi/>\
**Year of Publication:** 2016\
**Size:** 687,343\
**Data Collection:** Hill et al. construct a reading comprehension dataset from 108 children's books. An example consists of context, query, answer candidates and the actual answer. The context consists of 20 consecutive sentences. A single word is removed from the 21st sentence such that the sentence forms the query and the removed word forms the answer. The answer candidates consist of 9 words that appear within the 21 sentences and have the same type as the answer (named entity, common noun, verb, preposition) plus the actual answer.
**Examples:**

    1 With almost everything else to make them happy , they wanted one thing : they had no children .
    ...
    17 `` Everyone who should be asked , '' answered the queen .
    18 `` People are so touchy on these occasions , '' said his majesty .
    19 `` You have not forgotten any of our aunts ? ''
    20 `` No ; the old cats ! ''
    21 replied the XXXXX ; for the king 's aunts were old-fashioned , and did not approve of her , and she knew it .    queen       ancestors|baby|boy|everyone|fairies|mother|portrait|queen|time|walls


#### 30M Factoid Question-Answer Corpus
*Serban et al.* \
**PDF:** <https://www.aclweb.org/anthology/P16-1056.pdf> \
**Dataset:** <http://academictorrents.com/details/973fb709bdb9db6066213bbc5529482a190098ce> \
**Year of Publication:** 2016 \
**Size:** 30M \
**Data Collection:** Serban et al. use an encoder-decoder architecture to generate questions from Freebase facts (subject - predicate - object triples). Their system is trained on the SimpleQuestions dataset by Bordes et al. .\
**Examples:**

    <http://rdf.freebase.com/ns/m.04whkz5>    www.freebase.com/book/written_work/subjects    <http://rdf.freebase.com/ns/m.01cj3p>    what is the book e about ?
    <http://rdf.freebase.com/ns/m.0tp2p24>    www.freebase.com/music/release_track/release    <http://rdf.freebase.com/ns/m.0sjc7c1>    in what release does the release track cardiac arrest come from ?
    <http://rdf.freebase.com/ns/m.04j0t75>    www.freebase.com/film/film/country    <http://rdf.freebase.com/ns/m.07ssc>    what country is the debt from ?
    <http://rdf.freebase.com/ns/m.0ftqr>    www.freebase.com/music/producer/tracks_produced    <http://rdf.freebase.com/ns/m.0p600l>    what songs have nobuo uematsu produced ?
    <http://rdf.freebase.com/ns/m.036p007>    www.freebase.com/music/release/producers    <http://rdf.freebase.com/ns/m.0677ng>    who produced eve-olution ?


#### GraphQuestions
*Su et al.* \
**PDF:** <https://www.aclweb.org/anthology/D16-1054.pdf>\
**Dataset:** <https://github.com/ysu1989/GraphQuestions>\
**Year of Publication:** 2016\
**Size:** 5,166\
**Data Collection:** Su et al. present a semi-automated approach to generate questions that exhibit a set of given characteristics (structure complexity, function, commonness, answer cardinality and paraphrasing). They generate graph query templates over a knowledge base (Su et al. use Freebase but argue that their approach is universally applicable) given a desired number of edges. The templates consist of nodes that correspond to entity classes (e.g. `DeceasedPerson` and `CauseOfDeath`) connected by edges that correspond to relations (e.g. `causeOfDeath`). They also include at most one function per template (e.g. `max`, `>`, `count`) to generate questions that include phrases like *"the most recent"*, *"people older than"*, *"how many"*. Templates are grounded by inserting entities and literals for some nodes (e.g. `Lung Cancer`) while leaving other nodes ungrounded such as the node corresponding to the answer. The resulting graph query is translated to a SPARQL query to retrieve the corresponding answer. Graduate students are employed to convert graph queries to natural language questions. Questions are paraphrased by having each graph converted by several editors as well as by inserting aliases for entity names.\
**Examples:**

    "question": "which venues can seat at least 1417 people?", "answer": ["Reno Events Center", "United Spirit Arena", "Deltaplex Arena & Conference Center", ...
    "question": "which legal cases are handled by justice scalia?", "answer": ["Dolan v. United States Postal Service"], ...
    "question": "find rockets made by chrysler llc that support low earth orbit.", "answer": ["Saturn I", "Saturn IB"], ...
    "question": "the ws07 runner-up was managed by who?", "answer": ["Don Baylor", "Clint Hurdle", "Jim Leyland"], ...
    "question": "can you list for me all of tourist attractions available in the united states?", "answer": ["Chinatown", "American Swedish Institute", "Marine Corps War Memorial", ...


#### TriviaQA
*Joshi et al.* \
**PDF:** <https://www.aclweb.org/anthology/P17-1147.pdf>\
**Dataset:** <http://nlp.cs.washington.edu/triviaqa/>\
**Year of Publication:** 2017 \
**Size:** ca. 95,000 \
**Data Collection:** Joshi et al. collect question-answer pairs from 14 trivia websites. Additionally, they gather textual evidence for the given answer from Web Search results and Wikipedia articles.\
**Examples:**

    "Question": "Bill Berry retired through ill health as a drummer in which band?", "Answer": "REM", ...
    "Question": "Which James Bond film features a song by Louis Armstrong?", "On Her Majesty's Secret Service", ...
    "Question": "Which country became the first in the world to issue the dreaded parking ticket?", "Answer": "France", ...
    "Question": "Who had a 70s No 1 hit with Billy, Don't Be A Hero?", "Answer": "Bo Donaldson and the Heywoods", ...
    "Question": "Sarah FitzGerald has been a 90s world champion in which sport?", "Answer": "Squash", ...


#### LC-QuAD
*Trivedi et al.* \
**PDF:** <https://iswc2017.ai.wu.ac.at/wp-content/uploads/papers/MainProceedings/152.pdf>\
**Dataset:** <http://lc-quad.sda.tech/>\
**Year of Publication:** 2017\
**Size:** 5,000\
**Data Collection:** Trivedi et al. use a list of seed entities, a predicate whitelist and SPARQL query templates to generate (complex) SPARQL queries. They then use what they call Normalized Natural Question Templates (NNQT) associated with each SPARQL template to create natural language questions. Since these questions are often ungrammatical, human editors are asked to manually correct and paraphrase the automatically generated questions. Along with the generated questions, the dataset also contains the corresponding SPARQL queries and NNQTs.\
**Examples:**

    "question": "when did Daniel Dennett receive the Erasmus Prize?", ...
    "question": "What is 365chess id of Alexander Alekhine?", ...
    "question": "Who is the follower of Charles the Fat who has a noble title as king of Franks?", ...
    "question": "Who was the sibling of Silvio Berlusconi?", ...
    "question": "What is on the bay of Praia that has a tributary called the Amazon basin?", ...


#### SQuAD
*Rajpurkar et al.* \
**PDF:** <https://arxiv.org/pdf/1606.05250.pdf>, <https://arxiv.org/pdf/1806.03822.pdf>\
**Dataset:** <https://rajpurkar.github.io/SQuAD-explorer/>\
**Year of Publication:** 2016/2018\
**Size:** 107,785/151,054\
**Data Collection:** The Stanford Question Answering Dataset (SQuAD) is a dataset designed for reading comprehension tasks. Crowd workers are employed to ask questions over a set of Wikipedia articles. They are then asked to annotate the questions with the text segment from the article that forms the answer. In a second version, they add ca. 50,000 unanswerable questions to the dataset. These questions, too, are generated by crowd workers over Wikipedia articles.\
**Examples:**

    "question": How many industry models are followed for the production process of poultry?", "answers": [{"text": "There are two distinct models of production;" ,...
    "question": "How much did Dell spend on acquiring different divisions?", "answers": [{"text": "$13 billion", ...
    "question": "What country found bank accounts and real estate owned by the Sassou regime?", "answers": [{"text": "France", ...
    "question": "How many hours did it take to force the Russians away during the attack?", "answers": [{"text": "three hours", ...
    "question": "The older version of Wayback Machine did not have much new data past what year?", "answers": [{"text": "2008", ...


#### ComplexWebQuestions
*Talmor & Berant* \
**PDF:** <https://arxiv.org/pdf/1803.06643.pdf>\
**Dataset:** <https://www.tau-nlp.org/compwebq>\
**Year of Publication:** 2018\
**Size:** 34,689\
**Data Collection:** The dataset is based on the WebQuestionsSP dataset by Yih et al. which in turn is a version of the WebQuestions dataset by Berant et al. in which questions are annotated with corresponding SPARQL queries. Talmor and Berant combine such SPARQL queries to form more complex queries. Four types of more complex queries are generated: conjunctions, superlatives, comparatives, and compositions. These queries are automatically translated to questions that can be understood by crowdsourcing workers who then rephrase the questions as natural language questions.\
**Examples:**

    "question": "Which films featuring Taylor Lautner were released after November 17, 2008?", "answers": [{answer": "The Twilight Saga: New Moon", ...
    "question": "Which language is utilized ,where the currency Brazilian cruzado novo, is used?", "answers": [{"answer": "Italian Language", ...
    "question": "What are the three countries that border the country where Cambodian French is spoken?", "answers": [{"answer": "Vietnam", ...
    "question": "Where is the birthplace of the politician who held the governmental position Undersecretary?", "answers": [{"answer": "Honolulu", ...
    "question": "Of the countries that Germany share borders with, which country has a nominal GDP of 279500000000.0?", "answers": [{"answer": "Austria", ...


#### MS MARCO
*Nguyen et al.* \
**PDF:** <https://arxiv.org/pdf/1611.09268.pdf>\
**Dataset:** <https://microsoft.github.io/msmarco/>\
**Year of Publication:** 2018\
**Size:** 1,010,916\
**Data Collection:** The MS MARCO dataset contains search queries submitted via Bing or Cortana. For each query, the dataset contains text passages from documents that are provided by Bing as a result for the given query. 182,669 queries additionally come with answers generated by crowd workers.\
**Examples:**


#### FreebaseQA
*Jiang et al.* \
**PDF:** <https://www.aclweb.org/anthology/N19-1028.pdf> \
**Dataset:** <https://github.com/kelvin-jiang/FreebaseQA>\
**Year of Publication:** 2019\
**Size:** 28,348 \
**Data Collection:** Jiang et al. collect questions from trivia websites and combine them with questions from the TriviaQA dataset by Joshi et al.. They perform entity recognition and entity matching on the collected questions over Freebase to annotate the question's subject and answer with Freebase IDs. The entity matching is verified by human annotators.\
**Examples:**

    "ProcessedQuestion": "the us ramstein air base is in which european country", "AnswersMid": "m.0345h", "AnswersName": "germany", ...
    "ProcessedQuestion": "who was the tallest president of the usa in the 20th century", "AnswersMid": "m.0f7fy", "AnswersName": "lyndon b. johnson", ...
    "ProcessedQuestion": "where are the luxemburg gardens", "AnswersMid": "m.05qtj", "AnswersName": "paris", ...
    "ProcessedQuestion": "nuuk, population about 15,000, is the capital city of which country", "AnswersMid": "m.035v3", "AnswersName": "greenland", ...
    "ProcessedQuestion": "who featured on the 2002 eve hit gangsta lovin", "AnswersMid": "m.0g824", "AnswersName": "alicia keys", ...


#### ComQA
*Abujabal et al.* \
**PDF:** <https://www.aclweb.org/anthology/N19-1027.pdf>\
**Dataset:** <http://qa.mpi-inf.mpg.de/comqa/>\
**Year of Publication:** 2019\
**Size:** 11,214\
**Data Collection:** Abujabal et al. extract questions from the [WikiAnswers](https://www.answers.com/) website. The questions are grouped into paraphrase clusters using crowd-sourcing.\
**Examples:**

    {"cluster_id": "cluster-1301", "questions": ["what two large countries border nepal?", "what two major countries are adjacent to nepal?", "what two large countries touch nepal?", "what two countries are on the border with nepal?"], "answers": ["https://en.wikipedia.org/wiki/india", "https://en.wikipedia.org/wiki/china"]}
    {"cluster_id": "cluster-2203", "questions": ["who was the wife of the second president of the us?", "wife of second us president?", "who is the wife of 2nd us president?"], "answers": ["https://en.wikipedia.org/wiki/abigail_adams"]}
    {"cluster_id": "cluster-2216", "questions": ["when did francis bellamy write the pledge of allegiance?"], "answers": ["1892-08"]}
    {"cluster_id": "cluster-286", "questions": ["what number of terms did andrew johnson do?"], "answers": ["1"]}
    {"cluster_id": "cluster-2282", "questions": ["who was the us president after andrew johnson?", "who won the position of president following andrew johnson?"], "answers": ["https://en.wikipedia.org/wiki/ulysses_s._grant"]}


#### Compositional Freebase Questions (CFQ)
*Keysers et al.* \
**PDF:** <https://arxiv.org/pdf/1912.09713.pdf>\
**Dataset:** <https://github.com/google-research/google-research/tree/master/cfq>\
**Year of Publication:** 2020\
**Size:** 239,357\
**Data Collection:** Keysers et al. generate questions by applying a set of grammatical rules. Along with natural language questions, they construct corresponding SPARQL queries using a rule-based approach as well as natural language answers.\
**Examples:**

    "question": "Was Burr Ridge Bank & Trust founded by Sid Grauman, founded by Gary Trepina and Bob Para, founded by an actor, and founded by Wayne J. Miller", "expectedResponse": "No", ...
    "question": "Which film directed by, written by, edited by, and produced by Michael P. Nash did a film producer's child edit", "expectedResponse": "Climate Refugees", ...
    "question": "Were O Brother, Where Art Thou? and A Day's Pleasure written by, produced by, directed by, and edited by a film director's sibling", "expectedResponse": "No", ...
    "question": "Did Traitor's executive producer influence Patton Oswalt and Patrice O'Neal, influence Funny or Die's founder and employee, and marry Bernadette Peters", "expectedResponse": "No", ...
    "question": "What German founder of Institute for Social Research was influenced by Bertolt Brecht and influenced by Immanuel Kant", "expectedResponse": "Theodor W. Adorno", ...


## Smaller QA datasets

#### Free917
*Cai & Yates* \
**PDF:** <https://www.aclweb.org/anthology/P13-1042.pdf>\
**Dataset:** <https://nlp.stanford.edu/software/sempre/>\
**Year of Publication:** 2013\
**Size:** 917 \
**Data Collection:** Cai and Yates construct a question dataset by asking two native English speakers to formulate questions about a range of given Freebase domains.


#### WikiQA
*Yang et al.* \
**PDF:** <https://www.aclweb.org/anthology/D15-1237.pdf>\
**Dataset:** <http://aka.ms/WikiQA>\
**Year of Publication:** 2015\
**Size:** 3,047 \
**Data Collection:** The questions originally stem from Bing query logs.


## QA datasets without corresponding publication

#### Yahoo! Answers Comprehensive Questions and Answers
**Dataset:** <https://webscope.sandbox.yahoo.com/catalog.php?datatype=l> \
**Size:** 4,483,032 \
**Data Collection:** Questions and answers in this dataset are extracted from the Yahoo! Answers website as of October 2007.


#### Jeopardy! Questions
**Dataset:** <https://www.reddit.com/r/datasets/comments/1uyd0t/200000_jeopardy_questions_in_a_json_file/> \
**Year of Publication:** 2014\
**Size:** ca. 200K \
**Data Collection:** Questions and answers in this dataset stem from the American Quiz Show Jeopardy!.


## Question Generation Systems

#### Good Question! Statistical Ranking for Question Generation
*Heilman and Smith* \
**PDF:** <https://www.aclweb.org/anthology/N10-1086.pdf> \
**Code:** <http://www.cs.cmu.edu/~ark/mheilman/questions/> \
**Year of Publication:** 2010 \
**Approach:** Heilman and Smith generate questions from sentences using a set of hand-crafted syntactic transformation rules. They use an *overgenerate and rank* approach where they first generate as many questions as possible and then rank them according to their quality using a logistic regression model. \
**Examples:**


#### Generating Natural Language Question-Answer Pairs from a KnowledgeGraph Using a RNN Based Question Generation Model
*Indurthi et al.* \
**PDF:** <https://www.aclweb.org/anthology/E17-1036.pdf> \
**Code:** \
**Year of Publication:** 2017\
**Approach:** Indurthi et al. create keyword sets from Freebase facts (subject - predicate - object triples) by enriching the triples with the types of subject and object (e.g. *"Barack Obama"*-> *"person"*, *"Google"*->*"organization"*) and the predicate parent (e.g. *"CEO"*->*"designation"*). They use an encoder-decoder architecture based on Recurrent Neural Networks with Long Short Term Memory units to generate questions from subsets of these keyword sets.\
**Examples:**

    Where is the birth place of alan turing ?   maida vale
    Who was the inventor of lu decomposition ?  alan turing
    tv episodes of alan turing ?    dangerous knowledge
    what is the author of the mathematical logic    alan turing
    what is the ioc code for france ?   fr


#### Neural Question Generation from Text: A Preliminary Study 
*Zhou et al.* \
**PDF:** <https://arxiv.org/pdf/1704.01792.pdf>\
**Code:** <https://github.com/magic282/NQG> \
**Year of Publication:** 2017\
**Approach:** Zhou et al. present a neural encoder-decoder model to generate questions from sentences. They use a bidirectional-GRU-based encoder and an attention-based decoder.\
**Examples:**

    "question": "in what year did genghis khan begin a retaliatoryattack on the tanguts ?", "sentence": "n 1226, immediately after returning from the west,  genghis  khan  began  a  retaliatory  attack  on  thetanguts ."
    "question": "what did manning suffer in his left foot ?", "sentence": "n week 10 , manning suffered a partial tear of theplantar fasciitisin his left foot ."
    "question": "who designed the lombardi trophy ?", "sentence": "like  the  lombardi  trophy  ,  the  “  50  ”  will  be  de-signed by tiffany & co. ."
