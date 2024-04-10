## 🧠📖 The Principles of Deep Learning Theory

> Deep Analysis

**Deep learning** is an area of Artificial Intelligence that has been very successful recently. In simple words, it can be understood as a branch of AI where function models are created from a basic computational block called a **neuron**. These neurons are organized in sequential computational **layers**, and in the case of deep learning, there are multiple layers, allowing these units, forming the model, to learn representations of the world.

This chapter provides a more theoretical approach to neural networks in deep learning, presenting many important concepts and methods for addressing mathematical issues. Firstly, a mathematical structure is established to understand a neural network as a **parameterized function**, where there is an input to the function and a vector with a large number of parameters that control the shape of this function. For this function to be useful, it is necessary to initialize the **parameter vector** randomly and then adjust it so that the resulting network function is as close as possible to the target function. This concept is known as the **approximation function**, where data is trained in a learning algorithm to achieve the best possible result.

To better understand the possible technical problems that may arise from this mathematical representation of a neural network, **Taylor series expansion** is used. Thus, three problems are identified: the infinite number of terms in the function; randomness in sampling the parameter vector at each initialization, resulting in different functions in those initializations; and the complexity of training, where the learned parameter values are not unique, resulting from an iterative process with nonlinear dynamics.

One possible approach to solving these problems is to use the **principle of sparsity**, setting a limit to the width of the neural network, which would result in a trained distribution that approximates a **Gaussian distribution**, simplifying the analysis. However, this approach is not physically feasible, so the search is for a way to study the interactions between neurons in a finite-sized network. For this, the **perturbation theory** is used, with a 1/n expansion to calculate the distribution, resulting in a **nearly-Gaussian distribution** that resembles more closely a realistic neural network and can be used as a minimal theoretical model to understand deep learning.

Finally, the chapter introduces the concept of **depth-to-width aspect ratio**, which is a measure to divide the depth by the width of neurons in a layer, determining how deep these layers are.

In terms of theoretical implications, the application of mathematical concepts such as Taylor series and perturbation theory is fundamental to understanding neural networks in a simplified manner while still capturing essential aspects of their behavior, enabling the construction of more manageable theoretical models that can be utilized effectively. However, it is important to highlight the possibility of excessive simplification of models, which represents a limitation in analyzing neural network behavior.

In summary, all the theories and concepts discussed aim to contribute to the understanding of deep learning, simplifying the complexities associated with the subject and making them more accessible for deeper theoretical analysis. This is particularly important as often the focus is mainly on implementation and achieving satisfactory results without a full understanding of the underlying functioning of neural networks. However, it is crucial to recognize that these approaches may have limitations in simplifying complex models, potentially leading to the loss of possible insights.

Regarding alignment with other approaches, I believe these theories can be understood as complementary, as there are other approaches in the field of deep learning, such as data-driven learning and experimental exploration. Therefore, they blend well to offer both a conceptual and analytical framework and empirical validation and practical understanding.

## ✏️📘 Chapter 5: Feature Engineering

> Detailed summary

The chapter 5 of the book "Designing Machine Learning Systems," written by Chip Huyen, discusses the importance of selecting the right features for developing ML models and how to extract them in a suitable format, a field known as feature engineering. The author emphasizes that, although one of the promises of deep learning is to automatically extract features with its algorithms, many production applications are not based on deep learning, highlighting the importance of studying this area.

Following that, several common operations in the field of feature engineering are addressed, including:

- **Handling missing data:** it is emphasized that not all missing data in a database are of the same type and that missing data can often contain valuable information for the model. Two ways of dealing with missing data are discussed: filling in with a default value or removing them from the dataset. However, it is highlighted that removal can result in the loss of important information, while filling with default values can introduce different types of issues.

- **Scaling:** also known as feature scaling, aims to adjust the data so that they are in similar ranges, preventing an ML model from assigning excessive importance to larger values compared to smaller ones.

- **Discretization:** aims to transform continuous features into discrete ones by dividing the data into specific categories, which can be useful when there is a limitation in the amount of training data.

- **Encoding categorical features:** addresses effective ways of handling categorical features, highlighting the challenge of dealing with dynamic categories in production systems.

- **Feature crossing:** consists of combining two or more features to create new ones, useful for capturing nonlinear relationships between features.

Finally, the chapter addresses the problem of data leakage, which occurs when a label "leaks" into the set of features used for making predictions, and this same information is not available during inference. This problem can result in significant prediction errors and can be caused by various reasons, including how data is split, treated, and generated throughout the data pipeline.

Among the main causes of data leakage, the chapter highlights the random division of training and test data without considering time-based data; performing scaling before data splitting; filling missing data with test data statistics; not handling duplicate data properly; group leakage, when very similar information is found in different parts of training or test sets; and leakage originating from the data generation process (for example, two hospitals using different machines to obtain X-ray images, resulting in image variations).

In this sense, it is important to note that data leakage is a problem that can significantly affect the performance of ML models and can occur at any stage of the data pipeline. Therefore, there are several best practices that can be employed to avoid this problem, including:

- **Separating training/validation/test data according to time values, not randomly:** it's crucial to split time-series data into training, validation, and test sets based on chronological order. This ensures that the model is trained on past data, validated on recent data, and tested on the most recent data, preventing leakage from future information into the past.

- **Performing oversampling of data only after the split:** when dealing with imbalanced datasets, oversampling should be done only after splitting the data into training and testing sets. This prevents duplicated examples from appearing in both sets, which could lead to overly optimistic model performance.

- **Performing scaling and normalization only after data splitting:** scaling and normalization are essential preprocessing steps, but they should be performed after splitting the data. This prevents leakage of information from the test set into the training set, ensuring an unbiased evaluation of the model.

- **Using statistics only from training data to fill missing values and scale features:** when handling missing data, it's important to compute statistics (like mean or median) only from the training data to fill missing values and scale features. This prevents information leakage from the test set and maintains the integrity of the evaluation process.

- **Understanding the entire data generation and collection process to avoid data leakage:** understanding how data is generated and collected is crucial to prevent data leakage. Consulting domain experts can help verify the integrity of the data collection process and identify potential biases or leaks in the data.

- **Understanding feature importance, removing irrelevant features, and prioritizing generalizable ones:** feature selection plays a key role in model performance. It's important to identify and remove irrelevant features while prioritizing those that generalize well across different datasets. Techniques like feature importance analysis and selection can aid in this process.