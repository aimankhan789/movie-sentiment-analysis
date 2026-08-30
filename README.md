# Movie Sentiment Analysis
# IMDB Movie Review Sentiment Analysis

## Project Description

This is an intermediate-level Natural Language Processing (NLP) project focused on sentiment analysis of movie reviews. It represents an escalation from basic spam classification to a more challenging real-world NLP task involving contextual language, sentiment, and negation.

The project classifies IMDB movie reviews as either **Positive** or **Negative** using text preprocessing, TF-IDF feature extraction, and multiple classical machine learning algorithms

## Objective

The main objective is to build a machine learning model that can automatically determine whether a movie review expresses a positive or negative sentiment.

## Dataset

The project uses the IMDB Dataset of 50K Movie Reviews.

- Total reviews: 50,000
- Positive reviews: 25,000
- Negative reviews: 25,000
- Classes: Positive and Negative
- Dataset is perfectly balanced
- Dataset Link: kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews
- ## Preprocessing

The reviews were cleaned and prepared using the following NLP preprocessing pipeline:

1. HTML tags were removed from the reviews.
2. Text was converted to lowercase.
3. Contractions were expanded.
4. Negation handling was applied to preserve sentiment-changing expressions.
5. Punctuation was removed.
6. Text was tokenized into individual words.
7. Stopwords were removed while preserving important negation words such as `not`.
8. Words were lemmatized using WordNetLemmatizer.
9. The cleaned tokens were rejoined into text.
10. ### Negation Handling Example

Negation handling was used to preserve the meaning of sentiment-changing phrases.

**Before preprocessing:**

> I don't like this movie. It is not good.

**After preprocessing:**

> `not_like` `movie` `not_good`


### Negation Handling

Negation handling was used because words such as "not" can completely change the sentiment of a phrase.

**Before preprocessing:**

> I don't like this movie. It is not good.

**After preprocessing:**

> i do_not like this movie it is not_good

This allows the model to treat expressions such as `not_good` as a sentiment-related feature instead of losing the effect of negation.
## Model Performance

Three machine learning algorithms were evaluated with different TF-IDF configurations:

- LinearSVC
- Logistic Regression
- Multinomial Naive Bayes

### Accuracy Comparison

| TF-IDF Configuration | LinearSVC | Logistic Regression | Multinomial Naive Bayes |
|---|---:|---:|---:|
| Unigram | 0.9014 | 0.9024 | 0.8683 |
| Unigram + Sublinear TF | 0.9006 | 0.9059 | 0.8706 |
| Unigram + Bigram + Sublinear TF | 0.9065 | 0.9092 | 0.8842 |
| Trigram + Sublinear TF | 0.9123 | 0.9103 | 0.8888 |

### Best Model

The best-performing model was **LinearSVC with Trigram + Sublinear TF**, achieving a test accuracy of **91.23%**.

### Cross-Validation

The final LinearSVC model achieved:

- Test Accuracy: **91.23%**
- Mean 5-Fold Cross-Validation Accuracy: **90.43%**
- Cross-Validation Standard Deviation: **0.16%**

The close cross-validation performance indicates that the model provides consistent results across different validation folds


## Comparison with Published Benchmarks

Our best model, TF-IDF Trigram + Sublinear TF with LinearSVC, achieved **91.23% test accuracy**.
## 📚 Comparison with Published Benchmarks

Our best result achieved an accuracy of approximately **91%**, which compares favorably with the original Stanford IMDB benchmark.

| Method | Accuracy |
|---|---:|
| Original Stanford paper | 88.89% |
| Our best result | ~91% |
| State-of-the-art classical ML | ~93% |

Our best model achieved **91.23% accuracy**, outperforming the original Stanford benchmark of **88.89%** while remaining close to the reported performance of state-of-the-art classical machine learning methods (~93%).

| Approach | Accuracy |
|---|---:|
| Original Stanford IMDB paper | 88.89% |
| Our best model — TF-IDF Trigram + Sublinear TF + LinearSVC | 91.23% |
| State-of-the-art classical ML | ~93% |

Our result is higher than the original Stanford benchmark and is competitive with classical machine learning approaches.

The use of TF-IDF trigrams helped capture short phrase-level context, while sublinear TF reduced the influence of very frequent terms.
## Limitations

Although the final model achieved strong performance, the project has some limitations:

- TF-IDF is mainly a bag-of-words representation and does not fully understand language context.
- Sarcasm and irony can be difficult to classify correctly.
- Mixed-sentiment reviews may contain both positive and negative expressions.
- Negation can still be challenging in complex sentences.
- Genre or writing-style differences may affect model performance.
- The model does not truly understand the meaning of a review like a human reader.
- Performance may change when the model is applied to a different dataset or domain.
- ## Conclusion

This project successfully demonstrates how Natural Language Processing can be used for movie review sentiment classification.

The best-performing configuration was **TF-IDF Trigram + Sublinear TF with LinearSVC**, which achieved **91.23% test accuracy**.

The experiments showed that:

- TF-IDF is an effective representation for movie-review text classification.
- Adding bigrams and trigrams can improve the model's ability to capture phrase-level information.
- Sublinear TF can improve the representation of frequently occurring terms.
- LinearSVC performed better than Logistic Regression and Multinomial Naive Bayes in our experiments.
- Negation handling is important because negation can change the sentiment of an expression.
- Error analysis showed that difficult cases can still arise from sarcasm, irony, mixed sentiment, and contextual language.

Overall, the project achieved strong performance while using classical NLP and machine learning techniques.
## Future Improvements

The project can be improved further in the following ways:

- Use transformer-based models such as **BERT** to capture contextual meaning.
- Experiment with other advanced NLP models.
- Perform more extensive hyperparameter tuning.
- Improve handling of sarcasm, irony, and mixed sentiment.
- Test the model on reviews from different datasets and domains.
- Explore word embeddings and contextual embeddings instead of relying only on TF-IDF.
- Use additional evaluation metrics and error analysis techniques.

BERT and other transformer-based models could address some of the contextual limitations of traditional bag-of-words approaches.
## Kaggle Notebook

[View the Kaggle Notebook](https://www.kaggle.com/code/aimanafzal123/movie-review-sentiment-analysis)
- Average review length: approximately 230 words
- ## Error Analysis

The final model was evaluated on the test set to understand its mistakes.

- Total test reviews: 10,000
- Incorrect predictions: 877
- Error rate: 8.77%

The misclassified reviews showed that errors can occur because of negation, sarcasm, mixed sentiment, and contextual language.

The model achieved strong performance on both short and long reviews:

- Short reviews (< 50 words): 92.21% accuracy
- Long reviews (> 200 words): 91.48% accuracy
- ## 📊 Results

The following table shows the accuracy of all 12 combinations of TF-IDF configurations and machine learning algorithms.

| TF-IDF Configuration | LinearSVC | Logistic Regression | Multinomial Naive Bayes |
|---|---:|---:|---:|
| Unigram | 90.14% | 90.24% | 86.83% |
| Unigram + Sublinear TF | 90.06% | 90.59% | 87.06% |
| Unigram + Bigram + Sublinear TF | 90.65% | 90.92% | 88.42% |
| Trigram + Sublinear TF | 91.23% | 91.03% | 88.84% |

**Best Accuracy:** 91.23% — Trigram + Sublinear TF with LinearSVC.
