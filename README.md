# A GUI Text Input Generation Method - MATI
## 🔆 Introduction for MATI

We introduce a new GUI text input generation method named MATI(Mining App to generate TestInput) for query-type input items in Android applications with an intent to effectively activate query searches. The method is built on an idea that the data suitable to input to a query often already occur on the GUI.

## 🚀 Quick Start

Our method can be integrated into any testing tool or framework. As an example, we integrated MATI to a GUI testing tool named cvrip. 

In the project directory, we provide the following command to run the cvrip with MATI:
```shell
python visualripper.py -o output -device emulator-5554 -app airbnb -package com.airbnb.android -start_activity com.airbnb.android.main.feat.homescreen.HomeActivity -window "0,63,1080,1794" -recognition yolov5+ocr -input art -state_compare resnet50+ssim_orb:0.5:0.9 -max_action_times 500
```

## 💡 Downloads<a name="tips"></a>

Here are links of data of MATI.
1. Our method MATI with cvrip: https://pan.nuaa.edu.cn/share/58c00d9db1fda815b91452d07e. (For the details of cvrip's usage, you can see the README.md in the project)
2. The actual input and output values for each query-type input item: https://pan.nuaa.edu.cn/share/d93d506d4a63827d79ed596ebb
3. Experimental raw coverage data of MATI: https://pan.nuaa.edu.cn/share/3ebda5f8405530ebaf0736ca61
4. Subject input item datasets from both AUT and RICO: https://pan.nuaa.edu.cn/share/19b9f9a38d3883ddecd1ab3091
5. Subject APK file: https://pan.nuaa.edu.cn/share/3cf98164c25b2f0d0a40069e03


### 📝 Requirements
- Android Studio
    - API 30
    - Android 11
    - x86_64
    - 1080x1920

- OpenAI api key

- Python 3.8+

## ✨ Demo
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
