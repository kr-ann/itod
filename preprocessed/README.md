This folder contains files from different steps of data preprocessing.

Firstly, there are files named like original datasets (**active-dict, active-rnc, active-rutenten, bts-rnc, bts-rutenten, wiki-wiki**) - they contain only those columns from original datasets that we'll use in our research, plus lemmatized contexts.

**all_senses, all_senses_2, all_senses_3** are dataframes with target words with all their senses. We take not all words from original datasets but apply some restrictions: 
1) we don't include words for which division into senses is different in different datasets (first file);
2) words for which one sense has five or more times more contexts than all other its senses together (second file);
3) words for whose senses there are significant difficulties when matching them with dictionary definitions from the dict we use (third file). 
The final file contains 36 words.

**df_to_work_with** contains the same 26 words but we further clean it in that it now contains only senses for which there are at least 20 contexts.

**10_errors, 20_errors, 30_errors, 40_errors** are made on the basis of df_to_work_with: if the latter is an 'ideal' dataset, these new datasets contain a specific percent of errors: for each cluster of context there's a number of wrongly annotated contexts from different senses.

**df_with_2_and_more, df_with_2_and_more_10_errors, df_with_2_and_more_20_errors,df_with_2_and_more_30_errors, df_with_2_and_more_40_errors** are datasets similar to the ones mentioned above except that they contain only words for which there are at least two senses.

**errors_10_train_df, errors_20_train_df, errors_30_train_df, errors_40_train_df** are train datasets (90% of the original dataset) with the specified percent of errors.
