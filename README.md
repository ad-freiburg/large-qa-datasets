# Large Question Answering Datasets
A collection of large datasets containing questions and their answers for use in Natural Language Processing tasks like question answering (QA).
Datasets are sorted by year of publication.

## Question Datasets

### Table of Contents
- [WebQuestions](#webquestions) (2013 | 5,810 questions collected via the Google Suggest API)
- [SimpleQuestions](#simplequestions) (2015 | 108,422 questions generated from Freebase triples)
- [CNN/DailyMail Corpus](#cnndailymail-corpus) (2015 | ~1M cloze-style questions generated from news articles)
- [Children's Book Test](#childrens-book-test-cbt) (2016 | 687,343 cloze-style questions generated from children's books)
- [30M Factoid Question-Answer Corpus](#30m-factoid-question-answer-corpus) (2016 | 30M automatically generated q's from Freebase triples)
- [GraphQuestions](#graphquestions) (2016 | 5,166 questions generated from Freebase subgraphs)
- [SearchQA](#searchqa) (2017 | 140,461 Jeopardy! questions with relevant web snippets)
- [TriviaQA](#triviaqa) (2017 | ~95,000 questions collected from trivia websites)
- [LC-QuAD](#lc-quad) (2017 | 5,000 questions semi-automatically generated from complex SPARQL queries)
- [SQuAD](#squad) (2016/2018 | 107,785/151,054 reading comprehension questions about Wikipedia articles)
- [ComplexWebQuestions](#complexwebquestions) (2018 | 34,689 q's semi-automatically generated from complex SPARQL queries)
- [HotpotQA](#hotpotqa) (2018 | 112,779 multi-hop reasoning questions from Wikipedia articles)
- [MS MARCO](#ms-marco) (2018 | 1,010,916 queries collected from Bing and Cortana)
- [QuAC](#quac) (2018 | 98,407 dialog-style questions about Wikipedia articles)
- [CoQA](#coqa) (2019 | ~127,000 dialog-style questions about text from 7 different domains)
- [FreebaseQA](#freebaseqa) (2019 | 28,348 questions collected from trivia websites and TriviaQA)
- [ComQA](#comqa) (2019 | 11,214 questions collected from WikiAnswers)
- [Natural Questions](#natural-questions) (2019 | 323,045 real queries to Google Search)
- [Compositional Freebase Questions](#compositional-freebase-questions-cfq) (2020 | 239,357 automatically generated compositional questions)
- [AdversarialQA](#adversarialqa) (2020 | 36,000 hard questions for QA models)


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
**Data Collection:** Hill et al. construct a reading comprehension dataset from 108 children's books. An example consists of context, query, answer candidates and the actual answer. The context consists of 20 consecutive sentences. A single word is removed from the 21st sentence such that the sentence forms the query and the removed word forms the answer. The answer candidates consist of 9 words that appear within the 21 sentences and have the same type as the answer (named entity, common noun, verb, preposition) plus the actual answer. \
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


#### SearchQA
*Dunn et al.* \
**PDF:** <https://arxiv.org/pdf/1704.05179.pdf>\
**Dataset:** <http://nlp.cs.washington.edu/triviaqa/>\
**Year of Publication:** 2017 \
**Size:** 140,461 \
**Data Collection:** Dunn et al. collect question and answer pairs from the TV show *Jeopardy!* from the *J! Archive*.
 They retrieve results for each question from Google in order to enhance each question with a set of relevant web
 page snippets. They clean the Google results by for example excluding results that contain the term "Jeopardy!" to
 prevent getting an answer trivially from the snippets via phrase-matching. \
**Examples:**

    "question": "While he was in Spain in 1959, he wrote \"The Dangerous Summer\", a story about rival bullfighters", "answer": "Hemingway", ...
    "question": "Like a door, a Broadway show does these 2 things", "answer": "open & close", ...
    "question": "A valley at 282 feet below sea level in this state is the lowest point in the Western Hemisphere", "answer": "California", ...
    "question": "Like banks, many grocery stores now have these for dispensing cash & taking deposits", "answer": "ATMs", ...
    "question": "He was the voice of Mickey Mouse in \"Steamboat Willie\"", "answer": "Walt Disney", ...

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

#### HotpotQA
*Yang et al.* \
**PDF:** <https://arxiv.org/pdf/1809.09600.pdf>\
**Dataset:** <https://hotpotqa.github.io/>\
**Year of Publication:** 2018\
**Size:** 112,779\
**Data Collection:** HotpotQA contains Wikipedia-based questions that require multi-hop reasoning. The questions were
 generated by crowd workers who were shown multiple texts from different Wikipedia articles and asked to generate a
 question that requires reasoning about all these texts. Each question answer pair comes with a set of supporting
 facts and multiple contexts.\
**Examples:**

    "question": "Were Scott Derrickson and Ed Wood of the same nationality?", "answer":"yes", ...
    "question": "What government position was held by the woman who portrayed Corliss Archer in the film Kiss and Tell?", "answer": "Chief of Protocol", ...
    "question": "What science fantasy young adult series, told in first person, has a set of companion books narrating the stories of enslaved worlds and alien species?", "answer": "Animorphs", ...
    "question": "Are the Laleli Mosque and Esma Sultan Mansion located in the same neighborhood?", "answer": "no", ...
    "question": 'The director of the romantic comedy "Big Stone Gap" is based in what New York city?', "answer": "Greenwich Village, New York City", ...


#### MS MARCO
*Nguyen et al.* \
**PDF:** <https://arxiv.org/pdf/1611.09268.pdf>\
**Dataset:** <https://microsoft.github.io/msmarco/>\
**Year of Publication:** 2018\
**Size:** 1,010,916\
**Data Collection:** The MS MARCO dataset contains search queries submitted via Bing or Cortana. For each query, the dataset contains text passages from documents that are provided by Bing as a result for the given query. 182,669 queries additionally come with answers generated by crowd workers.\
**Examples:**


#### QuAC
*Choi et al.* \
**PDF:** <https://arxiv.org/pdf/1808.07036.pdf>\
**Dataset:** <http://quac.ai/>\
**Year of Publication:** 2018\
**Size:** 98,407\
**Data Collection:** Choi et al. pair up two crowd workers where one of them acts as the teacher and the other one as
 the student. The teacher has access to a section of a Wikipedia article. The teacher only sees the section title and
 first paragrpah of the corresponding Wikipedia article. The student then asks questions about the article. The teacher
 answers with a contiguous span of the article text. In addition, the teacher can guide the questioning of the
 student by providing information e.g., on the answerability of the quesiton or whether the student should follow up
 on that question or not. The dialog ends after 12 questions have been answered or more than two questions were
 marked as unanswerable or if one of the partners ends the dialog.\
**Examples:**

    {"section_title": "1983-1989: Collaboration with Nikos Karvelas", "title": "Anna Vissi", ..., "qas": [
    {"question": "what happened in 1983?", ..., "orig_answer": {"text": "In May 1983, she married Nikos Karvelas, a composer,", ...}},
    {"question": "did they have any children?", ..., "orig_answer": {"text": "in November she gave birth to her daughter Sofia.", ...}},
    {"question": "did she have any other children?", ..., "orig_answer": {"text": "CANNOTANSWER", ...}},
    {"question": "what collaborations did she do with nikos?", ..., "orig_answer": {"text": "Since 1975, all her releases have become gold or platinum and have included songs by Karvelas.", ...}}, ...}


#### CoQA
*Reddy et al.* \
**PDF: <https://arxiv.org/pdf/1808.07042.pdf>** \
**Dataset:** <https://stanfordnlp.github.io/coqa/>\
**Year of Publication:** 2019\
**Size:** ca. 127,000\
**Data Collection:** Reddy et al. first select passages from seven domains, such as children’s stories from MCTest
 and literature from Project Gutenberg. Such passages are presented to pairs of crowd workers where one worker is the
 questioner and the other is the answerer. They are asked to have a conversation about the given passage in form of
 questions and answers.\
**Examples:**

    Once upon a time, in a barn near a farm house, there lived a little white kitten named Cotton. Cotton lived high
    up in a nice warm place above the barn where all of the farmer's horses slept. ...

    Q		What color was Cotton?
    A		white || a little white kitten named Cotton
    A		white || white kitten named Cotton
    A		white || white
    A		white || white kitten named Cotton.

    Q		Where did she live?
    A		in a barn || in a barn near a farm house, there lived a little white kitten
    ...


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


#### Natural Questions
*Kwiatkowski et al. (Google Research)* \
**PDF:** <https://www.aclweb.org/anthology/Q19-1026.pdf>\
**Dataset:** <https://ai.google.com/research/NaturalQuestions>\
**Year of Publication:** 2019\
**Size:** 307,373 training + 7,830 development + 7,842 test\
**Data Collection:** The questions come from real queries issued to the Google search engine. Human annotators were given the question together with a Wikipedia page from the top-5 search results, and marked a long answer (a paragraph) and a short answer (the target span) in the article, or *null* if the answer was not present in the article. Questions were excluded if the annotators classified them as ambigous, incomprehensible, dependent on clear false presuppositions, opinion-seeking, or not clearly a request for factual information.\
**Examples:** (see <https://ai.google.com/research/NaturalQuestions/databrowser> for more)

    URL: https://en.wikipedia.org//w/index.php?title=Five_Nights_at_Freddy%27s&oldid=827108665, question: "what is the story behind 5 nights at freddy's", short answer: none, long answer: "The series is centered on the story of a fictional restaurant named Freddy Fazbear's Pizza, a pastiche of restaurants like Chuck E. Cheese's and ShowBiz Pizza Place. The first three games involve the player working as a nighttime security guard, in which they must utilize several tools, most notably checking security cameras, to survive against animatronic characters, which become mobile and homicidal after-hours. The fourth game, which uses different gameplay mechanics from its predecessors, takes place in the house of a child who must defend against nightmarish versions of the animatronics by closing doors and fleeing on foot. The fifth game takes place in a maintenance facility owned by a sister company of Freddy Fazbear's Pizza. The player character is a technician instead of a night guard, who must do different tasks each night as told by an AI voice heard in the game. In the sixth game, the player acts as the owner of a pizzeria which they must decorate with payable items, and must also work the night shift for their pizzeria, which plays similarly to previous games."
    URL: https://en.wikipedia.org//w/index.php?title=Nick_Cannon&oldid=800876512, question: "who is the announcer on americas got talent", short answer: "Nicholas Scott "Nick" Cannon", long answer: "Nicholas Scott "Nick" Cannon (born October 8, 1980)[1] is an American rapper, actor, comedian, director, screenwriter, film producer, entrepreneur, record producer, radio and television personality. On television, Cannon began as a teenager on All That before going on to host The Nick Cannon Show, Wild 'N Out, and America's Got Talent. He acted in the films Drumline, Love Don't Cost a Thing, and Roll Bounce. As a rapper he released his debut self-titled album in 2003 with the hit single "Gigolo", a collaboration with singer R. Kelly. In 2007 he played the role of the fictional footballer TJ Harper in the film Goal II: Living the Dream. In 2006, Cannon recorded the singles "Dime Piece" and "My Wife" for the planned album Stages, which was never released. Cannon married American R&B/pop singer, Mariah Carey in 2008. He filed for divorce in December 2014, after six years of marriage. The divorce was finalized in 2016."
    URL: https://en.wikipedia.org//w/index.php?title=English_poetry&oldid=832934616, question: "two main styles of english poetry in the seventeenth century", short answer: none, long answer: none
    URL: https://en.wikipedia.org//w/index.php?title=Sri_Lankan_cricket_team_in_India_in_2017%E2%80%9318&oldid=840491900, question: "who won the match sri lanka or india", short answer: "India", long answer: "India won the Test series 1–0, after the first and third matches were drawn.[15] India won the ODI series 2–1, their eighth consecutive series win since beating Zimbabwe in June 2016.[16] India won the T20I series 3–0.[17]"
    URL: https://en.wikipedia.org//w/index.php?title=Na_Na_Hey_Hey_Kiss_Him_Goodbye&oldid=826421545, question: "who sang sha na na hey hey goodbye", short answer: none, long answer: none


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


#### AdversarialQA
*Bartolo et al.* \
**PDF:** <https://arxiv.org/pdf/2002.00293.pdf>\
**Dataset:** <https://adversarialqa.github.io/>\
**Year of Publication:** 2020\
**Size:** 36,000\
**Data Collection:** A crowd worker is given a text passage and asked to generate a question about the paragraph
 and to mark an answer within the paragraph. The paragraph and the question are then given to a model which predicts
 an answer to the question. A word-overlap score between the human answer and the model answer is computed to determine
 whether the model answered correctly. If the score is lower than a certain threshold, the question is kept. Bartolo et
 al. use three different models for this process (which get progressively stronger): BiDAF, BERT and RoBERTa, all of
 which are trained on SQuAD. Based on these three models, they create three different datasets with 12,000 questions
 each (10,000 training, 1,000 valudation and 1,000 test examples).\
**Examples:**

    [{"title": "Kenya", "paragraphs": [{"context": "The African Great Lakes region, which Kenya is a part of, has been inhabited by humans since the Lower Paleolithic period. By the first millennium AD, the Bantu expansion had reached the area from West-Central Africa. The borders of the modern state consequently comprise the crossroads of the Niger-Congo, Nilo-Saharan and Afroasiatic areas of the continent, representing most major ethnolinguistic groups found in Africa. Bantu and Nilotic populations together constitute around 97% of the nation's residents. European and Arab presence in coastal Mombasa dates to the Early Modern period; European exploration of the interior began in the 19th century. The British Empire established the East Africa Protectorate in 1895, which starting in 1920 gave way to the Kenya Colony. Kenya obtained independence in December 1963. Following a referendum in August 2010 and adoption of a new constitution, Kenya is now divided into 47 semi-autonomous counties, governed by elected governors.", "qas": [
    {"question": "when has people evidently existed in Kenya?", "answers": [{"answer_start": 87,"text": "since the Lower Paleolithic period"}], ...},
    {"question": "what happened 115 years prior to kenya having a ruling which allows splitting the land and electing leaders for the lands?", "answers": [{"answer_start": 656, "text": "The British Empire established the East Africa Protectorate"}], ...},
    {"question": "what happened 47 years before kenya created a ruling which allows splitting the land and electing leaders for the lands?", "answers": [{"answer_start": 778, "text": "Kenya obtained independence"}], ...},
    {"question": "what happened 68 years before Kenya achieved freedom from colonization?", "answers": [{"answer_start": 656,"text": "The British Empire established the East Africa Protectorate in 1895"}], ...}]}


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
*Heilman and Smith*\
**PDF:** <https://www.aclweb.org/anthology/N10-1086.pdf>\
**Code:** <http://www.cs.cmu.edu/~ark/mheilman/questions/>\
**Year of Publication:** 2010\
**Approach:** Heilman and Smith generate questions from sentences using a set of hand-crafted syntactic transformation rules. They use an *overgenerate and rank* approach where they first generate as many questions as possible and then rank them according to their quality using a logistic regression model.\
**Examples:**


#### Generating Natural Language Question-Answer Pairs from a KnowledgeGraph Using a RNN Based Question Generation Model
*Indurthi et al.*\
**PDF:** <https://www.aclweb.org/anthology/E17-1036.pdf>\
**Code:**\
**Year of Publication:** 2017\
**Approach:** Indurthi et al. create keyword sets from Freebase facts (subject - predicate - object triples) by enriching the triples with the types of subject and object (e.g. *"Barack Obama"*-> *"person"*, *"Google"*->*"organization"*) and the predicate parent (e.g. *"CEO"*->*"designation"*). They use an encoder-decoder architecture based on Recurrent Neural Networks with Long Short Term Memory units to generate questions from subsets of these keyword sets.\
**Examples:**

    Where is the birth place of alan turing ?   maida vale
    Who was the inventor of lu decomposition ?  alan turing
    tv episodes of alan turing ?    dangerous knowledge
    what is the author of the mathematical logic    alan turing
    what is the ioc code for france ?   fr


#### Learning to Ask: Neural Question Generation for Reading Comprehension
*Du et al.*\
**PDF:** <https://arxiv.org/pdf/1705.00106.pdf>\
**Code:** <https://github.com/xinyadu/nqg>\
**Year of Publication:** 2017\
**Approach:** Du et al. generate questions from given sentences (and in a second model for given paragraphs) using an RNN encoder-decoder architecture. Their encoder is based on a bidirectional LSTM which takes word embeddings (300 dimensional pre-trained GloVe embeddings) as input. The decoder is based on an LSTM network and an attention mechanism. They deal with OoV words in the output by inserting for a predicted token UNK at time step *t* the input token with the highest attention score. The system is evaluated over the SQuAD dataset and compared to several baselines as well as Heilman and Smith's system. Additionally, they conduct a human evaluation where 100 random questions are rated in terms of naturalness and difficulty. Their system significantly outperforms the state-of-the-art system by Heilman and Smith.\
**Examples:**

    "question": "what is one of the largest city centers in the uk ?", "sentence": "the largest of these is the eldon square shopping centre , one of the largest city centre shopping complexes in the uk ."
    "question": "how long ago did the paleoproterozoic exhibit ?", "sentence": "free oxygen first appeared in significant quantities during the paleoproterozoic eon -lrb- between 3.0 and 2.3 billion years ago -rrb- ."
    "question": "what is one of the first objections of the immune system to infection ?", "sentence": "inflammation is one of the first responses of the immune system to infection ."
    "question": "what are the most successful agricultural production regions in africa ?", "sentence": "tea , coffee , sisal , pyrethrum , corn , and wheat are grown in the fertile highlands , one of the most successful agricultural production regions in Africa ."
    "question": "when did income inequality fall in the us ?", "sentence": "as an example , income inequality did fall in the united states during its high school movement from 1910 to 1940 and thereafter ."


#### Neural Question Generation from Text: A Preliminary Study
*Zhou et al.*\
**PDF:** <https://arxiv.org/pdf/1704.01792.pdf>\
**Code:** <https://github.com/magic282/NQG>\
**Year of Publication:** 2017\
**Approach:** Zhou et al. present a neural encoder-decoder model to generate questions from sentences. They use a bidirectional-GRU-based encoder and an attention-based decoder. The encoder takes as input a concatenation of a token's word embedding, answer position information as BIO tag, word case, POS and NER tag. They use a copy mechanism to copy rare and unknown words from the input sentence to the output sequence. The proposed system is evaluated over the SQuAD dataset. Additionally, Zhou et al. perform a human evaluation over a subset of the generated questions.\
**Examples:**

    "question": "in what year did genghis khan begin a retaliatoryattack on the tanguts ?", "sentence": "in 1226, immediately after returning from the west, genghis khan began a retaliatory attack on the tanguts ."
    "question": "what did manning suffer in his left foot ?", "sentence": "in week 10 , manning suffered a partial tear of the plantar fasciitis in his left foot ."
    "question": "who designed the lombardi trophy ?", "sentence": "like the lombardi trophy , the “ 50 ” will be designed by tiffany & co. ."


#### Machine comprehension by text-to-text neural question generation
*Yuan et al.* \
**PDF:** <https://arxiv.org/pdf/1705.02012.pdf>\
**Code:** <https://github.com/bloomsburyai/question-generation> (unofficial TensorFlow implementation)\
**Year of Publication:** 2017\
**Approach:** Yuan et al. generate questions from documents using a combination of supervised and reinforcement learning. They use a standard LSTM/attention-based encoder-decoder architecture and enhance it with techniques from reinforcement learning. During training, they use policy gradient optimization to maximize 1) a language model based score for fluency and 2) the performance of a pre-trained QA system on the generated questions. The input to the encoder are word embeddings combined with a binary feature that indicates whether a token belongs to the answer phrase. They evaluate their system over the SQuAD dataset.\
**Examples:**

    "question": "what language did the grainger market architecture belong to?"
    "question": "what is southern california known for?"
    "question": "what did the confucian scholars believe were attracted to the medical schools?"
    "question": "what is an example of a theory that can cause polynomial-timesolutions to be useful?"


#### Paragraph-level Neural Question Generation with Maxout Pointer and Gated Self-attention Networks
*Zhao et al.* \
**PDF:** <https://www.aclweb.org/anthology/D18-1424.pdf>\
**Code:** <https://github.com/seanie12/neural-question-generation> (unofficial PyTorch implementation)\
**Year of Publication:** 2018\
**Approach:** Zhao et al. introduce an encoder-decoder architecture that effectively leverages paragraph-level inputs for generating questions from documents. The model uses a gated self-attention encoder and a Maxout Pointer mechanism in the decoder to copy words from the input to the output sequence. The encoder consists of a bidirectional LSTM with a self-attention mechanism. It takes word embeddings as input (pre-trained GloVe vectors) concatenated with a feature that indicates whether a token belongs to the answer phrase. The decoder consists of another LSTM over which an attention mechanism is applied. They propose the Maxout Pointer mechanism to copy words from the input to the generated output. Decoder output scores and copy scores from the Maxout Pointer mechanism are concatenated, softmax is applied over the vector and probabilities pointing to the same words are summed up to get the final token probability. Zhao et al. evaluate their system over SQuAD and the MS MARCO dataset. The reported scores beat the scores reported by Du et al., Zhou et al. and Song et al. and makes their system state of the art.\
**Examples:**

    "question": "what competition did thomas davis think he would play in ?", "paragraph": "carolina suffered a major setback when thomas davis , an 11-year veteran who had already overcome three acl tears in his career , went down with a broken arm in the nfc championship game .despite this , he insisted he would still find a way to play in the super bowl. [...]"
    "quesiton": "how much money did walt wanted to invest in 1953?", "paragraph": "walt disney and his brother roy contacted goldenson at the end of 1953 for abc to agree to finance part of the disneyland project in exchange for producing a television program for the network .walt wanted abc to invest $500,000 and accrued a guarantee of $4.5 million in additional loans , a third of the budget intended for the park . [...]"
    "question": "what type of protest did percy shelley write ?", "paragraph": "following the peterloo massacre of 1819 , poet percy shelley wrote the political poem the mask of anarchy later that year , that begins with the images of what he thought to be the unjust forms of authority of his time and then imagines the stirrings of a new form of social action . it is perhaps the first modern [ vague ] statement of the principle of nonviolent protest . [...]"
    "question": "when was the victoria and albert museum founded ?", "paragraph": "the victoria and albert museum ( often abbreviated as the v & a ) , london , is the world ’s largest museum of decorative arts and design , housing a permanent collection of over 4.5 million objects. it was founded in 1852 and named after queen victoria and prince albert. [...]"


#### Capturing Greater Context for Question Generation
*Tuan et al.*\
**PDF:** <https://arxiv.org/pdf/1910.10274.pdf>\
**Code:** -\
**Year of Publication:** 2019\
**Approach:** Tuan et al. propose an encoder-decoder architecture that uses a multi-stage attention mechanism to identify tokens at document-level that are closely related to the answer. Their encoder takes two inputs: the document word embeddings and the answer word embeddings (using 300 dimensional pre-trained GloVe embeddings). Both are fed to a bidirectional LSTM layer. The output is passed through 2 stages of attention. In the resulting context representation, the word representation at the position of the answer is masked with a masking vector. This ensures that the system knows the position of the answer and generates questions that are coherent with the answer without including parts of the answer in the question. Tuan et al. evaluate their system on three datasets (SQuAD, MS MARCO, NewsQA) and additionally conduct a human evaluation using the same settings as Du et al.. They achieve results that beat previous state-of-the-art systems over all three datasets and achieve higher results than Du et al. in the human evaluation.\
**Examples:**

    "question": "when was the abc motion pictures dissolved?", "document": "In 1968, abc took advantage of new fcc ownership regulations that allowed broadcasting companies to own a maximum of seven radio stations nationwide in order to purchase houston radio stations kxyz and kxyz-fm for $1 million in shares and $1.5 million in bonds. that year, roone arledge was named president of abc sports; the company also founded abc pictures, a film production company which released its first picture that year, the ralph nelson-directed charly. it was renamed abc motion pictures in 1979. this unit was dissolved in 1985. [...]"
    "question": "what does lack of education lead directly to?", "document": "an important factor in the creation of inequality is variation in individuals' access to education. education, especially in an area where there is a high demand for workers, creates high wages for those with this education, however, increases in education first increase and then decrease growth as well as income inequality. as a result, those who are unable to afford an education, or choose not to pursue optional education, generally receive much lower wages. the justification for this is that a lack of education leads directly to lower incomes, and thus lower aggregate savings and investment. [...]"
    "question": "when was the appearance of the bible in french language?", "document": "the appearance of the bible in french language was important to the spread of the protestant movement and development of the reformed church in france. the country had a long history of struggles with the papacy by the time the protestant reformation finally arrived. around 1294, a french version of the scriptures was prepared by the roman catholic priest, guyard de moulin."


#### Asking Questions the Human Way: Scalable Question-Answer Generation from Text Corpus
*Liu et al.*\
**PDF:** <https://arxiv.org/pdf/2002.00748.pdf>\
**Code:** <https://github.com/bangliu/ACS-QG>\
**Year of Publication:** 2020\
**Approach:** Liu et al. propose a 3-step question generation system to generate questions given a plain input document. In a first step, an answer, a clue (contained in the question to constrain the question context) and a question style ("*which*", "*why*", "*yes/no*", ...) is extracted from a text passage using syntactic parsing and chunking. In a second step, they train two models on the extracted information. The first model is a GRU-based encoder-decoder model with an attention and a copy mechanism. The second model is a fine-tuned version of the GPT2-small model. The input to both models is a concatenation of the word embeddings of the input sentence (300 dimensional pre-trained GloVe embeddings, trainable) and their NER and POS tag embeddings, a binary indicator whether the word is a content word and binary features to indicate whether it is part of the answer or the clue. In a third step, they use a BERT-based QA model to filter out low-quality question-answer pairs. They evaluate their system over SQuAD where they drastically outperform state-of-the-art approaches. They also conduct a human evaluation over their two models and additionally evaluate them by training a BERT-based QA model on the generated questions where both models perform acceptably but worse than a system trained purely on SQuAD.\
**Examples:**

    "question": "What is the New York Amsterdam News known for?", "answer": "one of the leading African American weekly newspapers in the United States", "sentence": "The New York Amsterdam News, based in Harlem, is one of the leading African American weekly newspapers in the United States."
    "question": "What is one of the leading African American weekly newspapers in the US?", "answer": "The New York Amsterdam News", "sentence": "The New York Amsterdam News, based in Harlem, is one of the leading African American weekly newspapers in the United States."
    "question": "What area of medicine is Manhattan known for training?", "answer": "the life sciences", "sentence": "Manhattan is a world center for training and education in medicine and the life sciences."
    "question": "Which city is a world center for education and training in medicine?", "answer": "Manhattan", "sentence": "Manhattan is a world center for training and education in medicine and the life sciences."
