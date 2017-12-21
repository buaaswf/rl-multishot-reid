* [Multi-shot Re-identification](#1)
* [Preparations](#1.1)
* [Usage](#1.2)

<h3 id="1">Multi-shot Re-identification</h3>

---

Training and testing codes for multi-shot Re-Identification. Currently, these codes are tested on the PRID-2011 dataset, iLiDS-VID dataset and MARS dataset.

<h3 id="1.1">Preparations</h3>

---

Before starting running this code, you should make the following preparations:

* Download the [MARS](http://www.liangzheng.com.cn/Project/project_mars.html)
, [iLIDS-VID](http://www.eecs.qmul.ac.uk/~xiatian/downloads_qmul_iLIDS-VID_ReID_dataset.html) and [PRID-2011](https://www.tugraz.at/institute/icg/research/team-bischof/lrs/downloads/PRID11/).
* Install MXNet following the [instructions](http://mxnet.io/get_started/index.html#setup-and-installation) and install the python interface. Currently the repo is tested on commit e06c55.

<h3 id="1.2">Usage</h3>

---

* Download the datasets and unzip.
* Prepare data file. Generate image list file according to the file `preprocess_ilds_image.py`
, `preprocess_prid_image.py` and `preprocess_mars_image.py` under `baseline` folder.
* The code is split to two stage, the first stage is a image based re-id task,
please refer the script `run.sh` in `baseline` folder. The usage is:
```shell
sh run.sh $gpu $dataset $network $recfloder
```
e.g. If you want to train MARS dataset on gpu 0 using inception-bn, please run:
```shell
sh run.sh 0 MARS inception-bn /data3/matt/MARS/recs
```
The codes for this stage is based on [this repo](https://github.com/TuSimple/re-identification).
* The second stage is a multi-shot re-id task based on reinforcement learning.
Please refer the script `run.sh` in `RL` folder. The usage is:
```shell
sh run.sh $gpu $unsure-penalty $dataset $network $recfloder
```
* For evaluation, please refer `baseline_test.py` and `find_eg.py`.

