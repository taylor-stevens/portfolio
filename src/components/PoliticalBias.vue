<template>
    <v-container class="fill-height">
        <v-row>
            <v-col>
                <div class="text-h4" style="margin-top: 3%; margin-bottom: 3%;">
                    Addressing Political Bias in News Articles with Multinomial Regression
                </div>
                <div style="margin-bottom: 3%;">
                    All of the infomation found in this tab can be found in the 
                    <a href="https://docs.google.com/document/d/1Ikoay_N5WoR-IqjMdaVAHz-y5ivq-MUC452NJHw-rLk/edit#heading=h.xxfojxegu9p5" target="_blank">Final Report</a>  
                    for this project.
                    <br><br>
                    The objective of the project centers on the optimization of a multinomial regression model (MLRM) 
                    tailored for predicting bias in online articles. It is hypothesized that although political bias 
                    is a complex problem, a MLRM will be able to classify a satisfiable amount of articles that it is 
                    presented with. This model operates on a dataset consisting of crucial columns: topic, source, bias_score, 
                    and paragraph_vectors (reflecting article content), each numerically encoded and normalized. 
                    The optimization would include elevating the model's efficacy and ensuring dependable predictions 
                    when confronted with unseen articles. In general, the multinomial regression model is known for its 
                    ability to predict probabilities of group membership across multiple classes or categories. In the 
                    case of this project, it is tuned to recognize and predict the bias category of online articles, drawing 
                    insights from the features inherent in the dataset columns. Across multiple iterations, the model 
                    provides probability estimates to articles such that they are in various bias categories, with the goal 
                    of reducing error as it trains itself. The three categories that this project's model is training to 
                    predict includes both left, center, and right labels, translated into the numerical scores of 0, 1, and 2 
                    respectively. Each score showcases the dominant bias ingrained within the article based on the provided 
                    features. Aside from the goal of having a high accuracy rate in classifying articles, it is important to 
                    understand the model’s output and the sources of misclassification.
                    The current repository can be found
                    <a
                        key="Github"
                        href="https://github.com/anjali-tanna/cs4100_final_project"
                        title="Github"
                        class="d-inline-block mx-2 social-link"
                        rel="noopener noreferrer"
                        target="_blank"
                    >
                        <v-icon
                        :icon="'fa-brands fa-github'"
                        size="24"
                        style="color: white;"
                        />
                    </a>
                    <a href="https://github.com/anjali-tanna/cs4100_final_project" target="_blank">here</a>.
                </div>
            </v-col>
        </v-row>
        <v-row justify-self="center" justify="center" style="margin-bottom: 3%;">
            <v-col>
                <v-img src="./mlrm_overview.jpg"
                justify-self="center"
                >
                </v-img>
            </v-col>
            <v-col cols="1">
                <v-container class="grow d-flex flex-column flex-nowrap">
                    <v-row style="padding-bottom: 10%;">
                        <v-icon
                        :icon="'fa-brands fa-python'"
                        size="50"
                        style="color: white;"
                        />
                    </v-row>
                    <v-row style="margin-bottom: 5%;">
                        <v-img src="../assets/numpy.png"></v-img>
                    </v-row>
                    <v-row style="margin-bottom: 5%;">
                        <v-img src="../assets/pandas.png"></v-img>
                    </v-row>
                    <v-row style="margin-bottom: 5%;">
                        <v-img src="../assets/scikit-learn.png"></v-img>
                    </v-row>
                </v-container>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <div class="text-h5">
                    Database Selection and Cleaning
                </div>
                <br>
                The dataset utilized for training and testing the model is sourced from a publicly available repository on Google 
                Datasets, accessible through the Hugging Face platform. Composed of 13 comprehensive columns, including important 
                attributes such as topic, source, bias, url, title, date, authors, content, source_url, and bias_text, this dataset 
                stands as a foundation for the analysis to be undertaken post training. The project's success heavily relied upon 
                pre-labeled data, which this repository was able to provide. Without the availability of labeled data, the model would 
                have been performing unsupervised learning, which would have introduced ambiguity and complexity, potentially undermining 
                the analysis. The supervised learning approach that was taken ensured a more straightforward trajectory in discerning 
                bias classifications, particularly in the political spectrum. Furthermore, the existence of labeled data allowed for 
                rigorous testing, validating the accuracy and efficacy of the classification model. Nuance was imperative for training 
                a MLRM as generally these types of models are not the strongest available to classify complex ideas. 
                The dataset's bias distribution represents a broad spectrum of the ways in which bias can permeate articles. 
                Understanding the dataset’s distributions proved instrumental in understanding the model's sensitivity to different biases. 
                Additionally, examining bias splits by source shed light on the inherent biases affiliated with specific platforms or publishers, 
                crucial insights that guided the understanding of how biases manifest across diverse sources. 
                <br><br>
                Upon acquiring the dataset, a series of preprocessing measures were undertaken to ensure data coherence and relevance 
                to the classification objectives. The primary aim was to refine the dataset, making it more comprehensible for the model 
                while eliminating extraneous or potentially misleading attributes. Initially, columns prone to introducing noise or 
                misleading the model's learning process, such as author, date, time, etc. were removed. This curation process aided 
                in reducing the dataset down to attributes appropriate to the classification goals. As a result, topic, source, bias, 
                title, and content, stood as the remaining columns in the dataset for the model to train with. After column reduction 
                was complete, title and content were transformed by Doc2Vec, a powerful vectorization library. The utilization of Doc2Vec 
                allowed for the mapping of textual data to meaningful numerical representations. The two columns were merged before undergoing 
                the transformation by Doc2Vec, which empowered the model to capture not just word importance but the semantic meaning of 
                the entire article including its title. Further, from this merged column, prior to applying the library, filler words, 
                commonly known as stop words, were removed from the content. This extraction process aimed to reveal the essence of the 
                articles, eliminating linguistic clutter that might obscure the model's understanding. This nuanced representation 
                resulted in the creation of an output array comprising 100 feature values per data sample. The utilization of Doc2Vec, 
                which pivoted away from simple word importance, enabled the model to grasp the intricate nuances and contextual depth 
                embedded within each article. This was important as bias cannot simply be captured by which words an author may have chosen. 
                After the vectorization of the text was completed, the source and topic columns underwent separate preprocessing. Each 
                column was given its own manual vectorization, replacing word values with numerical values through mapping. Finally, 
                the 3 vectorized columns (source, topic, and the merged content/title) underwent normalization, ensuring uniformity and 
                consistency in scale across the feature space, a crucial step preceding model training. Prior to introducing this step, 
                the model had significant trouble with classifying the articles, likely due to the different scales between source/topic 
                and content/title. This sequence of preprocessing steps, ranging from column curation to semantic representation and 
                normalization, resulted in a refined dataset optimized for the model's comprehension. By leveraging these techniques to 
                consolidate information, the preprocessing allowed for the model training to result in significantly more accurate bias 
                classification than before.
            </v-col>
            <v-col>
                <div class="text-h5">
                    Analysis and Discussion
                </div>
                <br>
                The exploration of a multilogistic regression model (MLRM) surfaced considerable insights into the intricate nature of 
                identifying political bias within written articles. Despite considerable progress made through a significant learning 
                curve, it became evident that MLRM might possess inherent limitations in capturing the nuanced intricacies of this 
                classification process, a barrier not predicted with the hypothesis. Although there was much more success after a 
                significant learning curve, there are notable missing pieces in the project. One of the key limitations stemmed from 
                MLRM's assumption of linear decision boundaries between classes. Political bias, however, can manifest as a multifaceted 
                spectrum rather than adhering to distinctly separable linear boundaries. This complexity likely resulted in the model 
                creating oversimplified classifications that failed to encapsulate the nuanced positions and ranges of political bias 
                present in articles. Furthermore, MLRMs operate under the assumption of feature independence, a premise that might not 
                hold true for political bias, which was not considered prior to analysis. This lack of feature independence could stem 
                from not only language nuances and historical references but also contextual intricacies and rhetorical devices. Attempting 
                to encapsulate these multifaceted aspects within a linear model framework would therefore pose significant challenges. 
                Because MLRMs might struggle to contextualize these elements effectively, the training could result in a loss of crucial 
                information essential for comprehending political leanings within articles. Considering these factors, while MLRM served as 
                a valuable baseline model, achieving higher accuracies than found in this project would likely require more sophisticated 
                approaches. Some techniques rooted in natural language processing (NLP), including deep learning architectures or ensemble 
                methods, could likely better handle the complexity and non-linearity present in the data. Further NLP methods would likely 
                find more success in capturing the subtle contextual cues vital for accurately identifying and classifying political bias 
                within articles. Despite the model's inherent limitations, noteworthy insights emerged from the training. Notably, 
                the selection of features such as source and topics significantly influenced the model's success, resulting in almost 
                85% accuracy in the classification of test data with just a little over 1000 samples in the dataset. Additionally, the 
                utilization of the Doc2Vec library played a pivotal role in the model's ability to achieve satisfactory classification 
                accuracy. The transformation of text based data into semantic representations through this library greatly contributed 
                to the model's efficacy compared to other vectorization techniques that were tested. Without the DocToVec vectors as 
                features, the model failed to even hit 50% classification abilities. 
                <br><br>
                Alongside the difficulties with MLRM and complex classification, several challenges and unmet expectations hindered the 
                project's progression. The scarcity of data that precisely matched the desired criteria, specifically, the unavailability 
                of a dataset with five categories for classification, imposed limitations on the model's complexity and accuracy. It is 
                likely however, that although more complex data could not be found, that the MLRM would have struggled to classify a 5 
                category political bias, as the model's accuracy witnessed a slight decline from only 2 to 3 categories. Further, the 
                scale of the dataset, though larger than manually curated alternatives, remained insufficient for practical applications. 
                The limited volume of around 1,300 rows potentially impacted the model's accuracy due to inadequate instances for 
                comprehensive learning. The search for a larger dataset proved difficult, consuming significant time without yielding 
                the desired scale of data. When attempting to supplement the small dataset, it was quickly clear that it would not be 
                reasonable to continue in the timeframe provided as it was extremely difficult to get raw text of articles due to paywalls 
                and other cross origin resource policies (CORP) that blocked the use of libraries such as BeautifulSoup.
                <br><br>
                Along the way, some failed library usage atttempts, resulted in the discovery of Doc2Vec, which brought 
                forth the realization that political bias might not merely be linked to word repetitions within articles. 
                Rather, the identification of bias appears to be intricately linked to word relations, context, and broader 
                linguistic nuances. This observation underscores the crucial role of context and word relationships in bias 
                identification, deviating from a simplistic association with individual word occurrences.
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
//
</script>