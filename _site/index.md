
****

# <center>Multi-Decoder DPRNN: High Accuracy Source Counting and Separation</center>
*<center><font size="4">ICASSP 2021</font></center>*
<center><font size="4">Junzhe Zhu, Raymond Yeh, Mark Hasegawa-Johnson</font></center>
<center><font size="4">
<a href="https://github.com/JunzheJosephZhu/asteroid/tree/master/egs/wsj0-mix-var/Multi-Decoder-DPRNN">[code]</a>
<a href="http://www.isle.illinois.edu/speech_web_lg/pubs/2021/zhu2021multi.pdf">[paper]</a>
<a href="examples/citation.txt" target="_blank">[BibTeX]</a>
</font></center>
<br>
<img src="examples/pipeline.png">
**Abstract**: We propose an end-to-end trainable approach to single-channel speech separation with unknown number of speakers, **only training a single model for arbitrary number of speakers**. Our approach extends the MulCat source separation backbone with additional output heads: a count-head to infer the number of speakers, and decoder-heads for reconstructing the original signals. Beyond the model, we also propose a metric on how to evaluate source separation with variable number of speakers. Specifically, we cleared up the issue on how to evaluate the quality when the ground-truth hasmore or less speakers than the ones predicted by the model. We evaluate our approach on the WSJ0-mix datasets, with mixtures up to five speakers. **We demonstrate that our approach outperforms state-of-the-art in counting the number of speakers and remains competitive in quality of reconstructed signals.**
<br>
<br>

****
**<font size="5"> Example Input & Output </font>**
### <center>Input(Mixture, 2 sources):</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/2_mixture.wav" type="audio/wav"></audio></center>
### <center>Output(2 Estimated Sources)</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/2_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/2_source_1.wav" type="audio/wav"></audio></center>
****
### <center>Input(Mixture, 3 sources):</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_mixture.wav" type="audio/wav"></audio></center>
### <center>Output(3 Estimated Sources)</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_source_1.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/3_source_2.wav" type="audio/wav"></audio></center>
****
### <center>Input(Mixture, 4 sources):</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_mixture.wav" type="audio/wav"></audio></center>
### <center>Output(4 Estimated Sources)</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_1.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_2.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/4_source_3.wav" type="audio/wav"></audio></center>
****
### <center>Input(Mixture, 5 sources):</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_mixture.wav" type="audio/wav"></audio></center>
### <center>Output(5 Estimated Sources)</center>
<center><audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_0.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_1.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_2.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_3.wav" type="audio/wav"></audio>
<audio controls class="audio-player" preload="metadata" style="width: 180px;"> <source src="examples/5_source_4.wav" type="audio/wav"></audio></center>
****

## **Publications**
Zhu, J., Yeh, R. A., & Hasegawa-Johnson, M. (2021). Multi-Decoder Dprnn: Source Separation for Variable Number of Speakers. ICASSP 2021 - 2021 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), 3420–3424. doi:10.1109/ICASSP39728.2021.9414205 <a href="examples/citation.txt" target="_blank">[BibTeX]</a>

****

## **Contact**
<a href="mailto:josefzhu@stanford.edu"> Email the author</a> if you have any question