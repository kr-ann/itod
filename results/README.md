This folder contains files with results of our algorithm. 

Files **kw_for_0_errors, kw_for_10_errors, kw_for_20_errors, kw_for_30_errors, kw_for_40_errors** contain keywords that we extract from contexts of word senses in the ideal dataset as well as those with the specified percent of errors.
Keywords are extracted as follows: 
all contexts for this sense, lemmatized -> frequency distribution of words -> remove stop-words -> take 30 most common -> find their cosine with the target word -> keep only those where its value > 0.3 -> sort them in the descending order.

**all_definitions** is a file in which there are all definitions for our target words from the dictionary. **all_definitions_convenient** is the same file but in a more readable form.

**RUSSE-Efremova_corresspondence** is a text file with manually matched clusters from RUSSE (our datasets) with definitions from the dictionary we use.

**0_errors_overlap_convenient** is an excel file whith the output of our baseline approach based on simple overlap of clusters' keywords and dictionary definitions. Even on the ideal dataset it performs very poorly so we don't even experiment with noised datasets with errors.

Two last files, **Ключевые слова** and **Статистика...** contain keywords for each cluster and statistics of senses and contexts of the final dataset we use, respectively. 

**evaluation_cosine_on_ideal, evaluation_cosine_on_10_errors, evaluation_cosine_on_20_errors, evaluation_cosine_on_30_errors, evaluation_cosine_on_40_errors** contain definitions chosen by our algorithm on datasets with different percent of noise and evaluation if they are right.

**ideal_test_df_with_definitions, errors_10_df_with_definitions, errors_20_df_with_definitions, errors_30_df_with_definitions, errors_40_df_with_definitions** are test sets (10% of the original dataset) where for each sense a definition is chosen basing on training sets with the specified percent of errors. There's also an evaluation whether the definition is right or wrong.
