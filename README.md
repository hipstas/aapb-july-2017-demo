# HiPSTAS / WGBH / AAPB Report, July 2017

[Forward to pg. 2 >>](https://github.com/hipstas/aapb-july-2017-demo/blob/master/02_Audio_Labeler.md)


### People for whom audio machine learning may be useful
- individual historians and humanists sorting through digital audio collections
- journalists and documentarians searching for relevant material
- archivists and librarians doing maintenance and preservation work

### Problem space

- Cultural media collections are different from the industry machine learning context.
    - relatively small and static (or slowly growing) collections
    - The precision-recall tradeoff tends to favor recall.
    - rigorous performance scores not so important


- In this context, state-of-the-art performance may be overkill, both in terms of compute time and training time.
    - Deep learning requires a large quantity of training data and runs prohibitively slowly on consumer PCs.
    - Rough guideline: A system that takes more than a week or two to classify your collection of interest may not not be the best approach.
    - For small audio collections (minutes up to hundreds of hours), slow ML algorithms (decision trees, e.g.) with no dimension reduction can work just fine. For larger collections, we need to use SVM or GMM classifiers and perhaps a dimension reduction step (PCA or LDA).



- Initial constraints
    - Storage and compute resources may be limited.
    - Labeling audio for training is time-consuming.
    - Workers may not be comfortable writing code or using the command line.


- Technical challenges

    - Most existing software for training audio classifiers has a high learning curve.

    - Training models using hours of training data can take a very long time, making iterative improvements difficult.

    - Overfitting: Models trained on audio from a small number of sources may perform poorly in the real world.

    - Batch processing scripts become verbose and hard to maintain as you translate between various data sources, read and write audio and classification data, and manipulate time range values.


- Industry norm for designing ML classifiers: 3 separate labeled datasets before a model sees real-world data.
    - training set
    - validation set
    - test set






### Outputs from this project

#### To date

- Audio Tagging Toolkit (attk) Python package ([GitHub](https://github.com/hipstas/audio-tagging-toolkit), [Python Package Index](https://pypi.python.org/pypi/attk/0.0.6))

    - A set of straightforward tools for audio ML data processing.

    - Includes functions for extracting audio clips and manipulating classifier output data.

    - Extracts MFCC+delta features and identifies vowel ranges for speaker classification tasks.

    - Accepts CSV training labels created in Sonic Visualiser and the HiPSTAS Audio Labeler app.

    - Built using FFmpeg, Librosa, scikit-learn, MoviePy, Aubio, pyAudioAnalysis, and the SciPy stack.


- Audio Labeler application ([GitHub](https://github.com/hipstas/audio-labeler), [DockerHub](https://hub.docker.com/r/hipstas/audio-labeler/))

    - using Flask and Docker

- Audio ML Lab research environment in Docker ([GitHub](https://github.com/hipstas/audio-ml-lab), [DockerHub](https://hub.docker.com/r/hipstas/audio-ml-lab/))


    - includes dozens of




#### Forthcoming

- Female and Male UBM training sets, each comprising around 3,000 short speech clips.

- Dockerized tool for loading PBCore metadata into MongoDB and running searches
    - A back end for model building tasks (e.g.,
            - excluding audio that includes a given speaker's name in the metadata
            - excerpting audio from a single broadcast series
    - Will include a minimal in-browser interface for locating metadata manually.









<!--
Projects mix and match pieces,


  - pain point for wav-only systems: code gets verbose as

- limited HD space
- limited CPU capacity

- ^^ not the case in the tech industry! Where they use neural nets


there's a common structure for ML research, but this is different

Becomes about heuristics -- writing scripts to smooth and infer things from classification output


Example: podcast ad remover





Attk
- the best way to do everything


Audio Labeler
- usable by non-technical workers
- fixes shortcomings of naive random tagging tools
- customizable




Pipeline
 Keep extractor




Idea of ranges






Results:
Tone classifier
Pesca scores








Needs:


Flexible metadata search (MongoDB)

-->


[Forward to pg. 2 >>](https://github.com/hipstas/aapb-july-2017-demo/blob/master/02_Audio_Labeler.md)
