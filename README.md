# Filling Query-Type Text Inputs for Android Applications via Inner-App Mining and GPT Recommendation
## 🔆 Introduction for MATI

We introduce a new GUI text input generation method named MATI(Mining App to generate TestInput) for query-type input items in Android applications with an intent to effectively activate query searches. The method is built on an idea that the data suitable to input to a query often already occur on the GUI.

## 🚀 Quick Start

Our method can be integrated into any testing tool or framework. As an example, we integrated MATI to a GUI testing tool named cvrip. 

In the project directory, we provide the following command to run the cvrip with MATI:
```shell
python visualripper.py -o output -device emulator-5554 -app airbnb -package com.airbnb.android -start_activity com.airbnb.android.main.feat.homescreen.HomeActivity -window "0,63,1080,1794" -recognition yolov5+ocr -input art -state_compare resnet50+ssim_orb:0.5:0.9 -max_action_times 500
```

## 💡 Tips<a name="tips"></a>

Here is the link of our method with cvrip: https://pan.nuaa.edu.cn/share/d21a17741135e06b7dc3c67839. (For the details of cvrip's usage, you can see the README.md in the project)
We also provide some experiental subjects in the apk directory in the project.

### Requirements
- Android Studio
    - API 30
    - Android 11
    - x86_64
    - 1080x1920

- OpenAI api key

- Python 3.8+

## Demo
We provide a workflow to show the MATI method in action.
![](./assets/workflow.png)

## MATI Structure

### ⚙️ Word Filter

We use the word_filter library to extract the words from the GUI page.

```python word_filter.py -o <output_dir> -i <image_file> -app <app_name>```

### ⚙️ Hint Text Extraction
We use the hint_text_extraction library to extract the hint text from the GUI page.

```python hint.py -tl <text_list> -ll <location_list>, '-t' <input_item_location>```

### ⚙️ LLM-Recommender

We use the LLM-Recommender library with GPT-3.5-turbo model to recommend the most relevant words for the input.
```python LLM_Recommender.py -wl <word_list> -ht <hint_text> -li <local_infomatio> <output_dir>```
