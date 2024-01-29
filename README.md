# Nah-norm

Nahuatl Automatic Orthographic Normalization Research Project

This research project focuses on the development of an automatic orthographic normalization tool for the Nahuatl language, based on the Florentine Codex. Nahuatl has experienced orthographic instability due to factors such as joint authorship and the absence of a standardized writing system. The aim of this project is to create a tool that can normalize Nahuatl orthography, enabling the creation of literacy resources and stable data for corpus development.

To achieve efficient annotation and normalization processes, complex Neural Networks provided by OpenNMT are employed. The study compares various neural methods offered by OpenNMT to identify the most effective approach for Nahuatl Orthographic Normalization. This includes comparing different combinations of rnn, bidirectional encoder, and a widely prevalent but unlisted transformer model often used in OpenNMT literature.

The corpus utilized in this study draws from the Florentine Codex, a collection of cultural and linguistic studies of Central America, specifically focusing on the Aztec people who spoke Nahuatl. The chosen normalization standard aims to replicate the pre-colonial era and the immediate aftermath, as outlined by Campbell and Kattunen in the first volume of the Foundation Course in Nahuatl Grammar (1989).

One example of orthographic dissonance, as highlighted by Canger (2011), is the introduction of the /w/ sound, which led to variations in the orthography. Two representations emerged: 'hu' or 'u/v'. Another inconsistency lies in the representation of the /k/ sound, which can be found as 'k', 'c', or 'q' depending on the context. The normalization orthography in this study operates at the character level, as orthography refers to the spelling conventions within a writing system.

Due to limited computational power and resources, the architecture of each trained model may vary beyond the chosen encoder and decoder. The batch size and number of training steps were adjusted for efficiency and computational feasibility. The default settings in the OpenNMT introduction were initially adopted as the baseline but were later modified. The number of training steps was increased to 15,000 to allow training on the entire dataset, while the batch size was lowered to 60 to avoid runtime and memory errors.

The training process involves three corpora: source data (pre-normalized orthography) and target data (normalized orthography). Professional linguist annotators with knowledge of Nahuatl completed the normalizations. After training, the model files are tested on a separate set, and the predicted normalization output is evaluated, rather than relying on the scores provided by OpenNMT. The available data was split, with 80% designated for training and 20% for testing.

In terms of evaluation metrics, the study found that the metrics provided by OpenNMT were not suitable for assessing the efficiency and accuracy of the models. Instead, the study utilized the Character Error Rate (CER), which compares the predicted output to the target file at a character-by-character level, providing a percent-wrong score. Additionally, the BLEU score, commonly used in OpenNMT for evaluating results, did not adequately represent the efforts of the models.

The results of the experiments are summarized in the following table:

Experiment	Parameters (Enc., Dec., Training Steps, Batch Size)	CER Results

|Title|Encoder|Decoder|Training Steps|Batch Size| CER Score |
---- | ----- | ----- | ------ | ------ | ------- | 
| Baseline 1 | RNN, | Def., | 10,000,  | 60	| 17.63 |
| Baseline 2 | RNN, | Def., | 12,000, | 60	| 12.56 |
| Baseline 3 |	RNN, | Def., | 15,000, | 60	| 14.63 |
| Model 3 | BiRNN, | Trans., | 10,000, | 56	| 2.2 |
| Model 4	| BiRNN, | Trans., | 12,500, | 56	| 1.2 |
| Model 5	| BiRNN, | Trans., | 10,000, | 60	| 0.703 |
| Model 6	| BiRNN, | Trans., | 14,000, | 60	| 0.685 |
| Model 7	| BiRNN, | Trans., | 12,000, | 60	| 0.703 |
| Model 8	| BiRNN, | Trans., | 16,000, | 60 |	0.703 |

These results demonstrate the effectiveness of the neural models in achieving low character error rates, with the best-performing model achieving a CER of 0.685. The experimentation with different parameters and architectures highlights the importance of fine-tuning these elements for optimal results in Nahuatl orthographic normalization.
