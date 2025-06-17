# The Segmented Lakh MIDI Subset

This dataset was introduced in the 2025 ISMIR paper "Barwise Section Boundary Detection in Symbolic Music Using Convolutional Neural Networks"
- Paper
- Code and models

In the v1.0.0 folder you will find the SLMS, which consists of human section-level annotations of 6134 songs found in the metadata of files within the [Lakh MIDI dataset](https://colinraffel.com/projects/lmd/). The MIDI files themselves are available in the Lakh MIDI dataset.

The train/val/test split in the "SLMS loose" file was used to train the models in the paper above. "Loose" filtering means that in some cases, we accepted MIDI files into our _train_ (but not val or test) sets whose annotations were self-inconsistent (for instance, the boundary between a verse and a chorus might be marked twice within a file, but not the third time), but still likely to be useful for training. If you are interested in making your own data splits, then you will probably be interested in the "SMLS strict" file instead, which applies the same filtering standards to all files. 

We note that v1.0.0 of the SLMS is a _record_ of information found within the Lakh MIDI dataset, with no corrections. In future work, we plan to address the known issues below and build a larger and more consistent dataset of MIDI annotations by applying our own corrections to these files.

# Known issues/limitations

- We ignored all annotations within 8 bars of the first and last note onsets when filtering songs to build this dataset. As a result, some songs in SLMS v1.0.0 have annotations near the beginning or end of the song that don't make sense. Also, important measures near the beginning (such as the measure following a count-in) and ending (such as the measure containing the final note on or note off message) of a song are sometimes marked and sometimes not. Future work will clean up annotations within the first and last 8 bars of each song.

- A small percentage of the songs in the SLMS v.1.0.0 have annotations that are at least somewhat inconsistent with the [SALAMI](https://github.com/DDMAL/salami-data-public) guidelines for uppercase (section-level) annotations, and are more similar to the SALAMI guidelines for lowercase (phrase-level) annotations. Future work will involve creating two sets of annotations (coarse and fine) for each such file.

- The SLMS is a collection of markers which indicate boundaries between sections - nothing more. In some cases, these markers have associated text fields indicating function (e.g., "verse", "chorus", etc). We have not examined the correctness of these text fields.
