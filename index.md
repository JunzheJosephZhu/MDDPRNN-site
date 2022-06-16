## This is the github project page for MultiDecoder-DPRNN(a source separation system that automatically adapts to an arbitrary number of speakers, and outputs the corresponding number of sources).
Code can be found here as a part of the Asteroid source separation library: https://github.com/asteroid-team/asteroid/tree/master/egs/wsj0-mix-var/Multi-Decoder-DPRNN\

To test the model on your own dataset, download the example model and configuration from HuggingFace https://huggingface.co/JunzheJosephZhu/MultiDecoderDPRNN, and run python eval.py --test_dir <format_string>. The format string should indicate folder names for the json files that contain the filenames of the .wav files you want to test, and should be formattable with a single number that indicates the ground truth number of speakers. For example, you could have json files "2speakers/s2.json" and "3speakers/s3.json", and your format string would be "{}speakers", while your config file should have n_srcs: [2, 3].

## What is Multi-Decoder DPRNN? How does it work?
This work is a modification to common audio separation models, like DPRNN, or Conv-TasNet. I will briefly explain how these models work, and then explain how our Multi-Decoder mechanism allows them to generalize to an arbitrary number of speakers.
### How does DPRNN work?
First, given a mixture signal of T samples, we want to train a neural network to output S tracks of T samples, each representing a source in the mixture. In common models like DPRNN or Conv-TasNet, we assume S is known beforehand, which is usually untrue in real world applications.\
The common models first fold the signal into the subframes shape of [L, T/skip_size]. L here is called the _number of frames_.
<br><br>
Next up, the models use a linear layer to project the encoding into _encoding space_, resulting in an _encoding_ of shape [L, D], where D is the dimension of the _encoding space_. Then comes the part with the most computation, called the _separator_, which is usually some architecture based on LSTM or 1-D convolution, which spits out an output of shape [L, D], same as before. Finally, here comes the part that we want to fix: usually, a _projection layer_ would project the output into [L, D * S], and separate that into S separate tensors, each with shape [L, D]. Then each tensor is multiplied with the initial _encoding_, and projected back into [L, T/skip_size], finally being folded into some signal of length T. Therefore, we wind up with S tracks of signal, each containing T samples.
<br><br>
This approach works pretty well when S is fixed beforehand. However, it becomes annoying when there are multiple different values of S in the dataset. For example, some mixtures can have 2 sources, while others have 3. Facebook had a paper called "Voice Separation with an Unknown Number of Multiple Speakers", that basically trains a separate model for each value of S. However, this is inefficient, because 1. many models need to be trained. 2. We wouldn't know which model to use at test time, so we would have to run all of them and then decide which one to use.
<br><br>
So what do we do if we don't know S? Here comes our approach! If you look up two paragraphs, you can see that the _projection layer_ is the only part of the model whose parameter changes when S changes. So our solution is to train a different _projection layer_ for each value of S, and re-use the rest of the model! However, there remains one problem - we still need to be able to tell what S is, and decided on which _projection layer_ we select during test time. We do that by pooling the output of _separator_, and training a neural network classifier which tells us how many speakers there are.
<br><br>
I hope that clears things up! Here are some examples below. The sources are all separated from the mixture by our model, without knowing beforehand how many speakers there are. To see more numbers in our results, check out the paper here: https://arxiv.org/abs/2011.12022   Our model is very good at telling how many speakers there are, and reaches >98% accuracy when deciding whether there are 2, 3, 4, or 5 speakers, while the method by facebook only has <60% accuracy!

## Input(Mixture):
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/2_mixture.wav" type="audio/wav"></audio>
## Output(2 Estimated Sources)
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/2_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/2_source_1.wav" type="audio/wav"></audio>
<br>
## Input(Mixture):
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_mixture.wav" type="audio/wav"></audio>
## Output(3 Estimated Sources)
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_source_1.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_source_2.wav" type="audio/wav"></audio>
<br>
## Input(Mixture):
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_mixture.wav" type="audio/wav"></audio>
## Output(4 Estimated Sources)
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_1.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_2.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_3.wav" type="audio/wav"></audio>
<br>
## Input(Mixture):
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_mixture.wav" type="audio/wav"></audio>
## Output(5 Estimated Sources)
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_1.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_2.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_3.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_4.wav" type="audio/wav"></audio>
