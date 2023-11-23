<!-- <p align="justify">
In this post, we show the demo of ED-TTS: Multi-Scale Emotion Modeling using Cross-Domain Emotion Diarization for Emotional Speech Synthesis
</p> -->

## Abstract
<p align="justify">
Previous emotional speech synthesis methods use an utterance level style embedding extracted from reference audio, which ignores the multi-scale nature of speech prosody. In this paper, we propose ED-TTS, a multi-scale emotional speech synthesis framework based on Speech Emotion Diarization (SED) and Speech Emotion Recognition (SER) to model the emotion from different levels. Specifically, the proposed method combines utterance-level emotion embedding extracted by SER with fine-grained frame-level emotion embeddings extracted by a SED model to condition the reverse process of denoising diffusion probabilistic model (DDPM). Moreover, we employ cross-domain SED to predict accurate soft labels, solving the problem of lack of fine-grained emotion-annotated dataset for supervising emotional TTS training. ED-TTS significantly outperforms recent emotional TTS baselines in both objective and subjective evaluation.
</p>

## Model Architecture

![]({{ site.url }}/assets/image/ICASSP 2024.png) 
The overview of ED-TTS and cross-domain training for SED. The color in waveforms denotes the predicted frame-level emotion labels by SED (e.g. red for non-neutral and blue for neutral). Extracter denotes CNN-based feature encoder of SED 


### Non-Parallel Transfer
In non-parallel style transfer, the TTS system must transfer prosodic style when the source and target text are completely different.

<table>
    <tr>
	<th> Reference Text:</th>
	<th> Reference Audio</th>
    </tr>
    <tr>
       	<th> Clear than clear water? (sad) </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/ref_sad.wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
	<th> Target Text</th>
	<th> proposed</th>
    </tr>
    <tr>
	<th> We have been fine, haven't we? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/sad_1.wav" type="audio/mpeg"></audio> </th>
    </tr>
    <tr>
	<th> Do you know the lid opens? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/sad_2.wav" type="audio/mpeg"></audio> </th>
    </tr>
</table>	



<table>
    <tr>
	<th> Reference Text:</th>
	<th> Reference Audio</th>
    </tr>
    <tr>
       	<th> Clear than clear water? (sad) </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/ref_angry.wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
	<th> Target Text</th>
	<th> proposed</th>
    </tr>
    <tr>
	<th> We have been fine, haven't we? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/angry_1.wav" type="audio/mpeg"></audio> </th>
    </tr>
</table>

<table>
    <tr>
	<th> Reference Text:</th>
	<th> Reference Audio</th>
    </tr>
    <tr>
       	<th> Clear than clear water? (sad) </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/ref_neutral.wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
	<th> Target Text</th>
	<th> proposed</th>
    </tr>
    <tr>
	<th> We have been fine, haven't we? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/neutral_1.wav" type="audio/mpeg"></audio> </th>
    </tr>
</table>

### HAPPY
<table>
    <tr>
	<th> Reference Audio</th>
    </tr>
    <tr>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/ref_happy.wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
	<th> Target Text</th>
	<th> proposed</th>
    </tr>
    <tr>
	<th> I read a few lines, but I did not understand a word. </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/happy_1.wav" type="audio/mpeg"></audio> </th>
    </tr>
</table>
