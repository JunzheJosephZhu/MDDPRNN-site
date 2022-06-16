## This is THE github project page for MultiDecoder-DPRNN(a source separation system that automatically adapts to an arbitrary number of speakers, and outputs the corresponding number of sources).
Code can be found here as a part of the Asteroid source separation library: https://github.com/asteroid-team/asteroid/tree/master/egs/wsj0-mix-var/Multi-Decoder-DPRNN\

To test the model on your own dataset, download the example model and configuration from HuggingFace https://huggingface.co/JunzheJosephZhu/MultiDecoderDPRNN, and run python eval.py --test_dir <format_string>. The format string should indicate folder name for the json files, and be formattable with a single number that indicates ground truth number of speakers. For example, you could have json files "2speakers/s2.json" and "3speakers/s3.json", and your format string would be "{}speakers", while your config file should have n_srcs: [2, 3].

## What is Multi-Decoder DPRNN? How does it work?
This work is a modification to common audio separation models, like DPRNN. I will briefly explain how DPRNN works, and then explain how our Multi-Decoder mechanism allows it to generalize to an arbitrary number of speakers.






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
