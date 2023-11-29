# ASR-(Automatic Speech Recognition)
Development of an Automatic Speech Recognition (ASR) system based on Sri Lankan Speaking accent 

## Main Objective

Development of an Automatic Speech Recognition system for feeding quires to Chatbot

![image](https://github.com/Wishwa98/ASR-AutomaticSpeechRecognition-/assets/86372219/f92915f3-8601-4b42-ac1a-56a9595e2235)

***

## Based Approach - 

### CTC Approach(Based on Deep Speech 2)
- Connectionist temporal classification used where it’s a model with RNN and CNN and trained on LJ speech dataset Downsides of this model was it requires high computational power and less accurate even after running 20 epochs
  - Disadvantages – Spelling errors
  - Mostly popular ASR models like Wav2Vec2 ,HuBERT are based on CTC architecture






### Seq2Seq Approach
- Sequence to Sequence model architecture which uses both encoder and decoder which is linked via cross attention mechanism.Where Encoder computes hidden-state representations of audio inputs and decoder plays the role as language model
  - Disadvantages – Slower Decoding :decoder steps happen one step at a time, More data hungry : requires significantly more training data to reach convergence

Used Whisper model which was released in end of September 2022 where it has been trained for 680,000 hours of audio data and fined tuned this whisper model for my requirements with “Commen Accent” dataset.
![image](https://github.com/Wishwa98/ASR-AutomaticSpeechRecognition-/assets/86372219/d22aae9a-7d3b-4eac-9282-fa1797cc12b0)


***

## Dataset Used
For this research purpose, we are going to target the Sri Lankan audience which means most of our English accent is a bit different when compared to the other countries' English accent, Sri Lanka India Bangladesh Pakistan are categorized into South Asian countries so that for in Sri Lankan basically we are using that speaking accent of English. So, we got a dataset named Common Accent which consists of South Asian voice clips.

***

## Best approach 
| CTC Approach| Seq2Seq Approach|
| ------ | ----------- |
| High usage of computational power   | Comparatively low usage of computational power |
| High rate of spelling errors| Low rate of Spelling errors|
| Only use Encoder    | Use both decoder and encoder ( Can enhance the ASR for multiple languages)|
| Word Accuracy is Low | Word Accuracy is High |
| Difficult to handle High robustness, Noise inputs | High robustness, Noise inputs can be handled |

Due to the above comparison, I had selected the seq2seq architecture model to fit for the chatbot

***

## Model Results
| CTC – Model based on Deep Speech2| Seq2Seq Whisper finetuned model|
| ------ | ----------- |
| WER = 0.26 (26%) | WER = 0.13 (13%) |
| WAcc = 1- 0.26 =  0.74 (74 %) | WAcc = 1 – 0.13 = 0.87 (87 %)|


***
## Evaluation Metrices used
There are different word error categories as Substitution, Insertion Deletion in both word level and character level Here we used the Word level, which calculates the substitutions insertions, and deletions on a word level These errors are annotated on a word-by-word basis,
+S=substitute
+D=Delete
+I=Insertion 
+N= Total number of words

𝑊𝐸𝑅=(𝑆+𝐼+𝐷)/𝑁

Word Error Rate is an error matrix that can be convert into accuracy matrix 

𝑊_𝐴𝑐𝑐=1−𝑊𝐸𝑅

