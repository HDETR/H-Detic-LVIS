# Prepare datasets for H-Detic-LVIS

Only COCO+LVIS is supported by **H-Detic-LVIS** now, please follow the instructions below.

Download COCO and LVIS data place them in the following way:

```
<datasets_path>/
    lvis/
        lvis_v1_train.json
        lvis_v1_val.json
    coco/
        train2017/
        val2017/
        annotations/
            captions_train2017.json
            instances_train2017.json 
            instances_val2017.json
```

For more datasets, please see [data preparation in Detic](https://github.com/facebookresearch/Detic/blob/main/datasets/README.md).
