To test the model on your own dataset, download the example model and configuration from HuggingFace https://huggingface.co/JunzheJosephZhu/MultiDecoderDPRNN, and run python eval.py --test_dir <format_string>. The format string should indicate folder names for the json files that contain the filenames of the .wav files you want to test, and should be formattable with a single number that indicates the ground truth number of speakers. For example, you could have json files "2speakers/s2.json" and "3speakers/s3.json", and your format string would be "{}speakers", while your config file should have n_srcs: [2, 3].


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
