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
       	<th> Clear than clear water? (female) </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/female/16-1405/ref.wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
	<th> Target Text</th>
	<th> proposed</th>
    </tr>
    <tr>
	<th> We have been fine, haven't we? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/female/16-1405/0018_001234-Sad.wav" type="audio/mpeg"></audio> </th>
    </tr>
    <tr>
	<th> Do you know the lid opens? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/female/16-1405/0018_001274-Sad.wav" type="audio/mpeg"></audio> </th>
    </tr>
    <tr>
	<th> Our King George is labourers? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/female/16-1405/0020_000120-Neutral.wav" type="audio/mpeg"></audio> </th>
    </tr>
    <tr>
	<th> Can your name be more hilarious? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/female/16-1405/0020_000276-Neutral.wav" type="audio/mpeg"></audio> </th>
    </tr>
</table>	



<table>
    <tr>
	<th> Reference Text:</th>
	<th> Reference Audio</th>
    </tr>
    <tr>
       	<th> Andy what's the gyre and to gimble? (male) </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/male/13-1406/ref.wav" type="audio/mpeg"></audio> </th>
    </tr>
	
    <tr>
	<th> Target Text</th>
	<th> proposed</th>
    </tr>
    <tr>
	<th> We have been fine, haven't we? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/male/13-1406/0018_001234-Sad.wav" type="audio/mpeg"></audio> </th>
    </tr>
    <tr>
	<th> Do you know the lid opens? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/male/13-1406/0018_001274-Sad.wav" type="audio/mpeg"></audio> </th>
    </tr>
    <tr>
	<th> Our King George is labourers? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/male/13-1406/0020_000120-Neutral.wav" type="audio/mpeg"></audio> </th>
    </tr>
    <tr>
	<th> Can your name be more hilarious? </th>
       	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/unpara/male/13-1406/0020_000276-Neutral.wav" type="audio/mpeg"></audio> </th>
    </tr>
</table>



### Questioning Intonation Intensity Control

<table>
    <tr> 
        <th> Text </th>
	<th style="5px;word-wrap;word-break"> Intensity = 0.3 (Most Weak)</th>
        <th style="5px;word-wrap;word-break"> Intensity = 0.6 (Medium) </th>
        <th style="5px;word-wrap;word-break"> Intensity = 0.9 (Most Strong) </th>
    </tr>

	<tr>
        <th> A nauseous draught? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001410-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001410-Surprise-MG.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001410-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	<tr>
        <th> On the twenty second of last march? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001409-Surprise-MG.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001409-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0019_001409-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
        </tr>

   	<tr>
        <th> Andy what's the gyre and to gimble? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0011_001406-Surprise-G.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0011_001406-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0011_001406-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	<tr>
        <th> At the end of four? </th>
	<th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0017_001419-Surprise-MG1.5.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0017_001419-Surprise-MG.wav" type="audio/mpeg"></audio> </th>
        <th> <audio controls id="player" onplay="pauseOthers(this);"><source src="assets/Demo/intensity/0017_001419-Surprise-MG2.wav" type="audio/mpeg"></audio> </th>
        </tr>
	
	

</table>
