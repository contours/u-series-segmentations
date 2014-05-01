# Oral history interview segmentation data

This repository contains topic segmentations of transcripts of the following interviews from the [Oral Histories of the American South](http://docsouth.unc.edu/sohp/) project:

* [U-0005](http://docsouth.unc.edu/sohp/U-0005/U-0005.html)
* [U-0007](http://docsouth.unc.edu/sohp/U-0007/U-0007.html)
* [U-0008](http://docsouth.unc.edu/sohp/U-0008/U-0008.html)
* [U-0011](http://docsouth.unc.edu/sohp/U-0011/U-0011.html)
* [U-0012](http://docsouth.unc.edu/sohp/U-0012/U-0012.html)
* [U-0014](http://docsouth.unc.edu/sohp/U-0014/U-0014.html)
* [U-0017](http://docsouth.unc.edu/sohp/U-0017/U-0017.html)
* [U-0019](http://docsouth.unc.edu/sohp/U-0019/U-0019.html)
* [U-0020](http://docsouth.unc.edu/sohp/U-0020/U-0020.html)
* [U-0023](http://docsouth.unc.edu/sohp/U-0023/U-0023.html)
* [U-0098](http://docsouth.unc.edu/sohp/U-0098/U-0098.html)
* [U-0178](http://docsouth.unc.edu/sohp/U-0178/U-0178.html)
* [U-0180](http://docsouth.unc.edu/sohp/U-0180/U-0180.html)
* [U-0181](http://docsouth.unc.edu/sohp/U-0181/U-0181.html)
* [U-0183](http://docsouth.unc.edu/sohp/U-0183/U-0183.html)
* [U-0184](http://docsouth.unc.edu/sohp/U-0184/U-0184.html)
* [U-0185](http://docsouth.unc.edu/sohp/U-0185/U-0185.html)
* [U-0186](http://docsouth.unc.edu/sohp/U-0186/U-0186.html)
* [U-0193](http://docsouth.unc.edu/sohp/U-0193/U-0193.html)

The sentence-tokenized text of the transcripts can be found in the [`interview-sentences`](interview-sentences) directory.

All the following files contain linear segmentations serialized as [JSON in the Segeval format](http://segeval.readthedocs.org/en/latest/user/quickstart/#loading-data).

---

[**`segmentations.json`**](segmentations.json)<a name="segmentations"></a>

All human-created segmentations. Each segmentation is sentence-based, i.e. the segment masses are number of sentences per segment.

---

[**`segmentations-by-speaker-turns.json`**](segmentations-by-speaker-turns.json)

All human-created segmentations, each segmentation is *speaker-turn-based*, i.e. the segment masses are number of *speaker turns* per segment. This was generated using the script [`project.py`](https://github.com/contours/evaluation/project.py) and the data files [`segmentations.json`](#segmentations) (see above) and [`speakers.json`](#speakers) (see below).

    project.py segmentations.json speakers.json 

---

[**`speakers.json`**](speakers.json)<a name="speakers"></a>

Segmentations with boundaries placed at each point there is a speaker change.

---

[**`speechblocks.json`**](speechblocks.json)

Segmentations with boundaries placed at each point there is a speaker change *or paragraph break* in the original interview transcript.

---

**`segmentations-`coder name`.json`**<br>
**`segmentations-`coder name`-by-speaker-turns.json`**

These are simply subdivisions of [`segmentations.json`](#segmentations) into files that only contain segmentations from a single coder, and their speaker-turn-based variations.

---

[**`segmentations-null.json`**](segmentations-null.json)<br>
[**`segmentations-null-by-speaker-turns.json`**](segmentations-null-by-speaker-turns.json)

A null (no boundaries) segmentation generated using [`nullseg.py`](https://github.com/contours/evaluation/nullseg.py) and [`segmentations.json`](#segmentations), and it's speaker-turn-based version.

    nullseg.py segmentations.json

---

[**`segmentations-random.json`**](segmentations-random.json)<br>
[**`segmentations-random-by-speaker-turns.json`**](segmentations-random-by-speaker-turns.json)

A random segmentation generated using [`randomseg.py`](https://github.com/contours/evaluation/randomseg.py) and [`segmentations.json`](#segmentations), and it's speaker-turn-based version.

    randomseg.py segmentations.json

---

[**`texttiling-parameter-sweep`**](texttiling-parameter-sweep)

Directory with a large number of segmentations generated by [running TextTiling ](https://github.com/contours/textseg/blob/master/run-texttiling.hs) with various different parameter settings. The filenames reflect the values assigned to the following parameters: 

* `w` : pseudosentence (token sequence) size
* `k` : block size
* `m` : depth score cutoff is `(mean(depth) - m*(stddev(depth))`
* `n` : number of rounds of smoothing
* `s` : smoothing width
