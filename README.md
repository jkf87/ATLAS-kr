<p align="center" width="100%">
<img src="assets/logo.png" alt="Owl" style="width: 25%; min-width: 150px; display: block; margin: auto;">
</p>

[![Data License](https://img.shields.io/badge/Data%20License-Apache_2.0-green.svg)](https://github.com/aidarmyrzakhan/Atlas-A-LLM-Inquiry-Principle-Benchmark/blob/main/LICENSE.md)
[![Python 3.10+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/release/python-390/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

# ATLAS: An LLM Inquiry Principle Benchmark

This repository contains resources and research on formulating effective queries and prompts for large language models (LLMs). The primary contribution is the introduction of 26 guiding principles aimed at optimizing interactions with LLMs of various scales, such as LLaMA-1/2, GPT-3.5, and GPT-4.

이 리포지토리에는 대규모 언어 모델(LLM)을 위한 효과적인 쿼리와 프롬프트를 구성하는 데 관한 리소스와 연구가 포함되어 있습니다. 주요 내용은 LLaMA-1/2, GPT-3.5, GPT-4 등 다양한 규모의 LLM과의 상호 작용을 최적화하기 위한 26가지 지침 원칙을 소개하는 것입니다.

[//]: # (![demo]&#40;assest/demo.png | width=100&#41;)
[<img src="assets/demo.png" width="750" />](./assets/demo.png)

## Overview

Our work aims to simplify the underlying concepts of formulating questions for different scales of large language models. By examining their abilities and enhancing user comprehension, we focus on optimizing the design of instructions and prompts. Extensive experiments conducted on models like LLaMA-1/2 and GPT-3.5/4 have verified the effectiveness of the proposed principles. 

우리의 작업은 다양한 규모의 대규모 언어 모델에 대한 질문을 구성하는 기본 개념을 단순화하는 것을 목표로 합니다. 사용자의 능력을 조사하고 사용자의 이해도를 향상시킴으로써 지침과 프롬프트의 디자인을 최적화하는 데 중점을 둡니다. LLaMA-1/2 및 GPT-3.5/4와 같은 모델에 대한 광범위한 실험을 통해 제안된 원칙의 효과를 검증했습니다. 

[//]: # (![distribution]&#40;assets/distribution.png | width=100&#41;)
[<img src="assets/distribution.png" width="750" />](./assets/distribution.png)

## Data Release

Our dataset, comprising 12.5k data points, supports the study of LLM prompting principles. The data is curated to facilitate understanding and application of the [`26 principles`](./data/README.md). 
Our project includes two types of datasets, catering to different needs and research focuses:

12.5만 개의 데이터 포인트로 구성된 데이터 세트는 LLM 프롬프트 원칙에 대한 연구를 지원합니다. 데이터는 [`26가지 원칙`](./data/README.md)의 이해와 적용을 용이하게 하기 위해 큐레이션되었습니다. 
이 프로젝트에는 서로 다른 요구와 연구 초점을 충족하는 두 가지 유형의 데이터 세트가 포함되어 있습니다:

1. **일반 데이터 세트(`general_dataset.json`)**: 이 종합 데이터 세트는 26가지 원칙 각각에 대한 모든 사례를 하나의 파일로 결합하여 연구와 그 다양한 응용에 대한 전체적인 관점을 제공합니다.

- 파일: [`general_dataset.json`](./data/general_dataset.json)
- 구조:
- 각 항목에는 작업을 설명하는 `instruction` 필드가 포함되어 있습니다.
- output` 필드는 명령어에 대한 모델 생성 응답을 제공합니다.

예시

```
{
"instruction": "만약 당신이 전문 경제학자라면 어떻게 대답하겠습니까? 자본주의 경제 시스템과 사회주의 경제 시스템의 주요 차이점은 무엇인가요?",
"output": "전문 경제학자로서 저는 자본주의 경제 시스템과 사회주의 경제 시스템의 주요 차이점을 몇 가지 차원에서 설명하겠습니다..."
}
```     

2. **개별 원칙 데이터 세트(`principle_{i}.json`)**: 보다 집중적인 연구를 위해 26가지 원칙 각각에 대해 별도의 데이터 세트를 제공합니다. 이 파일을 통해 연구자들은 특정 원칙의 데이터를 개별적으로 탐색하고 분석할 수 있습니다.

- 파일 원리_1.json`, `원리_2.json`, ..., `원리_26.json`
각 파일은 일반 데이터 세트와 동일한 구조를 따르지만 각 원리와 관련된 예제만 포함되어 있습니다.


## 데이터 생성
이 프로젝트의 경우, 처음에는 강력한 기준선을 설정하기 위해 일련의 원칙적이고 기초적인 질문을 수작업으로 만들었습니다. 이러한 질문은 다양한 주제와 복잡성을 포괄할 수 있도록 세심하게 제작되어 지침 생성 프로세스의 포괄적인 출발점이 되었습니다. 그 다음에는 GPT-4 API를 사용하여 질문 리포지토리를 확장했습니다. 수동으로 만든 질문과 의미 및 주제적으로 연관성이 있는 새로운 질문을 생성하는 작업을 수행했습니다.

원칙에 따라 지침을 생성하려면: 
   ```
   python generate.py
   ```


## Pincipled Instruction Finetuning

저희 벤치마크는 [스탠포드 알파카](https://github.com/tatsu-lab/stanford_alpaca) 또는 [패스트챗](https://github.com/lm-sys/FastChat)과 호환됩니다. 세밀하게 조정된 모델을 추가로 제공할 예정입니다.

## Citation

```
@article{bsharat2023principled,
  title={Principled Instructions Are All You Need for Questioning LLaMA-1/2, GPT-3.5/4},
  author={Sondos Mahmoud Bsharat, Aidar Myrzakhan, Zhiqiang Shen},
  journal={arXiv preprint arXiv:2312.16171},
  year={2023},
}
```


## Contributing
We welcome contributions and suggestions to improve our principles and expand the dataset.

## Acknowledgements

[Stanford Alpaca](https://github.com/tatsu-lab/stanford_alpaca)
