# Major changes

MWE = Multi Word Expression

1. Changed the file extension of all semantic lexicon files from `.usas` to `.txt` and added the relevant header names e.g. `lemma` and `semantic_tags` for single word lexicons and `mwe_template` and `semantic_tags` for MWE lexicons in accordance with the Lexicon File Format section within the [README.md](./README.md)
2. Added a [License file](./LICENSE) which contains the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. This file was added so that on GitHub under the About section in the right hand corner there is a link that says `View License` which will direct users to this [License file](./LICENSE).
3. Reformated the [README.md](./README.md) so that it contains more structure. New content is added around File formats of single and MWE lexicon files.
4. Within the [MWE lexicon for Chinese](./Chinese/mwe-chi.tsv). Line 119 was removed as it contained a MWE template but no USAS tags. The MWE template on line 119 was `平顶_noun 女帽_noun`.
5. For the [Malay single lexicon](./Malay/semantic_laexicon_ms.tsv), I tested to see if the first column was a repeat of the second column using the [test_token_is_equal_to_lemma.py python script](./test_token_is_equal_to_lemma.py) and it was. The first, `token`, and the second column, `lemma`, both represented the `lemma` field, therefore the `token` field/column has been removed. In addition the [Malay single lexicon](./Malay/semantic_laexicon_ms.tsv) also contained a `POS` column that only contained the word `POS` therefore this column was also removed.
6. Created a scripts section within the [README.md](./README.md), the scripts section contains explanations on what the new python scripts do and how to use them.
7. The [Russian MWE semantic lexicon file](./Russian/mwe-rus.tsv) contained many tab separation errors e.g. line 89 was `без_* {всякой/лишней/излишней/особой/особенной}	суеты_*	N3.8-` which contains an extra tab between `без_* {всякой/лишней/излишней/особой/особенной}` and `суеты_*` when it should have been a single whitespace like: `без_* {всякой/лишней/излишней/особой/особенной} суеты_*	N3.8-`. All of these tab separation errors have been corrected.
8. The [Russian single word semantic lexicon file](./Russian/semantic_lexicon_rus.tsv) both the `lemma` and `token` columns are identical, tested using [test_token_is_equal_to_lemma.py python script.](./test_token_is_equal_to_lemma.py). Therefore the `token` column has been removed leaving only the `lemma` column.
9. The [Portuguese single semantic lexicon file](./Portuguese/semantic_lexicon_pt.tsv) contained a few tab separation errors e.g. line 1070 was `ansiar		verb	X7+` and is now `ansiar	verb	X7+`, if this was left as was then it would suggest that the semantic tags are `verb` instead of `X7+`.
10. The `language_resources.json` file has been added, which is a JSON file that contains meta data on what each lexicon resource file contains in this repository per language. This file is explained in the `USAS Lexicon Meta Data` section of the `README.md`
11. Removed `ID` column in the [Urdu semantic lexicon file](./Urdu/Urdu_Semantic_Lexicon.tsv), as the ID only represented line number and nothing else.
12. Added [CONTRIBUTING guidelines](./CONTRIBUTING.md) for contributing a lexicon resource.
13. Added [GitHub action](./.github/workflows/ci.yml) which will convert the lexicon resources created in text file format, following [CONTRIBUTING guidelines](./CONTRIBUTING.md), to TSV format. After conversion it will check that TSV files are formatted correctly, and if so it will add and commit the TSV files into the repository.