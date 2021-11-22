# url-classifier-thesis
The data, models, methods and finding of Bogdan Covrig's thesis titled _"URL Product Web Page Classifier"_.

## Data
- `product_links_annotated.csv`: the product pages URLs _(n=2522)_ manually annotated into the two categories (`0: non-shopping webpage` and `1: shopping webpage`). The annotation was performed as described in [Mathur _et al._](https://webtransparency.cs.princeton.edu/dark-patterns/) (section 4.2.1). The set contains URLs from:
    - `0-714`: A. Mathur, G. Acar, M. J. Friedman, E. Lucherini, J. Mayer, M. Chetty, and A. Narayanan, [“Dark patterns at scale: Findings from a crawl of 11k shopping websites,”](https://webtransparency.cs.princeton.edu/dark-patterns/) _Proceedings of the ACM on Human- Computer Interaction_, vol. 3, no. CSCW, pp. 1–32, 2019.
    - `714-2521`: B. Covrig, C. Rosca, C. Goanta _TBD_
- `product_links_features_labels.csv`: all the features extracted from the product pages URLs. The set contains the following information:
    - `url`: The full product URL. *Example: https://harrypottershop.com/products/hogwarts-express-ticket-ornament?pr_prod_strat=copurchase&pr_rec_pid=5843216793758&pr_ref_pid=5843215679646&pr_seq=uniform*
    - `schema`: The schema of the URL. _Example: https://_
    - `domain`: The domain name of the URL. _Example: harrypottershop.com_
    - `path`: The path of the URL. *Example: /products/hogwarts-express-ticket-ornamentpr_prod_strat=copurchase&pr_rec_pid=5843216793758&pr_ref_pid=5843215679646&pr_seq=uniform*
    - `path_len`: Total length of the path. _Example: 131_
    - `num_dot`: Number of dots _(.)_ or extension in the path. _Example: 0_
    - `num_hyphen`: Number of hyphens _(–)_ or segments in the sections of the path. _Example: 3_
    - `num_slash`: Number of slashes _(/)_ or sections of the path. _Example: 2_
    - `num_hash`: Number of hashes _(#)_ or anchors in the path. _Example: 0_
    - `num_param`: Number of equals _(=)_ or URL parameters in the path. _Example: 4_
    - `contains_product`: Boolean if there are present one (or more) _product_-related keywords _(e.g. product, item)_ in the path. _Example: 1_
    - `contains_category`: Boolean if there are present one (or more) _category_-related words _(e.g. category, collection)_. _Example: 0_
    - `longest_num`: Length of the longest numerical feature (usually IDs) found in the path. _Example: 13_
    - `label`: The non-product/product label of the URL. _Example: 1_

## Models
- `log-reg-mod.pkl`: Logistic Regression classifier model trained on the URLs dumped in the `product_links_annotated.csv` dataset. The classification report of the model tested with _n=247_ entries of the set below:
    ```
                precision    recall  f1-score   support

            0       0.91      0.89      0.90       128
            1       0.89      0.91      0.90       119

    accuracy                            0.90       247
    macro avg       0.90      0.90      0.90       247
    weighted avg    0.90      0.90      0.90       247
    ```

Use [pickle](https://docs.python.org/3/library/pickle.html) to import the model and [sklearn](https://scikit-learn.org/stable/install.html) to use it accordingly.

```python
import pickle
clf = pickle.load(open('log-reg-mod.pkl', 'rb'))
```

## Notebooks
_tbd_

## More information
The notebooks and publications will follow soon.
