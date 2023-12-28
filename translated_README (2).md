<p align="center" width="100%">
<img src="assets/logo.png" alt="Owl" style="너비: 25%; 최소 너비: 150px; 표시: 블록; 여백: 자동;">
</p>

[![데이터 라이선스]](https://img.shields.io/badge/Data%20License-Apache_2.0-green.svg)](https://github.com/aidarmyrzakhan/Atlas-A-LLM-Inquiry-Principle-Benchmark/blob/main/LICENSE.md)
[![파이썬 3.10+]](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/release/python-390/)
[![코드 스타일: 검정](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

# ATLAS: LLM 조회 원리 벤치마크

이 리포지토리에는 대규모 언어 모델(LLM)을 위한 효과적인 쿼리 및 프롬프트 구성에 대한 리소스와 연구가 포함되어 있습니다. 주요 기여는 LLaMA-1/2, GPT-3.5, GPT-4 등 다양한 규모의 LLM과의 상호 작용을 최적화하기 위한 26가지 지침 원칙을 소개하는 것입니다.

[//]: # (![demo]&#40;assest/demo.png | width=100&#41;)
[<img src="assets/demo.png" width="750" />](./assets/demo.png)

## 개요

우리의 작업은 다양한 규모의 대규모 언어 모델에 대한 질문을 공식화하는 기본 개념을 단순화하는 것을 목표로 합니다. 사용자의 능력을 조사하고 사용자의 이해도를 향상시킴으로써 지침과 프롬프트의 디자인을 최적화하는 데 중점을 둡니다. LLaMA-1/2 및 GPT-3.5/4와 같은 모델에 대한 광범위한 실험을 통해 제안된 원칙의 효과를 검증했습니다.

[//]: # (![배포]&#40;assets/distribution.png | width=100&#41;)
[<img src="assets/distribution.png" width="750" />](./assets/distribution.png)

## 데이터 릴리스

12.5만 개의 데이터 포인트로 구성된 데이터 세트는 LLM 프롬프트 원리 연구를 지원합니다. 데이터는 [`26가지 원칙`](./data/README.md)의 이해와 적용을 용이하게 하기 위해 큐레이션되어 있습니다.
이 프로젝트에는 서로 다른 요구와 연구 초점을 충족하는 두 가지 유형의 데이터 세트가 포함되어 있습니다:

   1. **일반 데이터셋(`general_dataset.json`)**: 이 포괄적인 데이터 세트는 26가지 원칙 각각에 대한 모든 사례를 단일 파일로 결합하여 연구와 그 다양한 응용에 대한 전체적인 관점을 제공합니다.
   
      - 파일: [`general_dataset.json`](./data/general_dataset.json)
      - 구조:
        - 각 항목에는 작업을 설명하는 `instruction` 필드가 포함되어 있습니다.
        - output` 필드는 명령어에 대한 모델 생성 응답을 제공합니다.
   
      예시
      ```json
      {
       "instruction": "만약 당신이 전문 경제학자라면 어떻게 대답하겠습니까? 자본주의 경제 시스템과 사회주의 경제 시스템의 주요 차이점은 무엇인가요?",
       "output": "전문 경제학자로서 저는 자본주의 경제 시스템과 사회주의 경제 시스템의 주요 차이점을 몇 가지 차원에서 설명하겠습니다..."
      }
   
   2. **개별 원칙 데이터세트(`principle_{i}.json`)**: 보다 집중적인 연구를 위해 26가지 원칙 각각에 대해 별도의 데이터 세트를 제공합니다. 이러한 파일을 통해 연구자들은 특정 원칙의 데이터를 개별적으로 탐색하고 분석할 수 있습니다.
   
      - 파일 원리_1.json`, `원리_2.json`, ..., `원리_26.json`
      각 파일은 일반 데이터 세트와 동일한 구조를 따르지만 각 원리와 관련된 예제만 포함되어 있습니다.


## 데이터 생성
우리 프로젝트의 경우, 처음에는 강력한 기준선을 설정하기 위해 일련의 원칙적이고 기초적인 질문을 수작업으로 만들었습니다. 이러한 질문은 다양한 주제와 복잡성을 포괄할 수 있도록 세심하게 제작되어 지침 생성 프로세스의 포괄적인 출발점이 되었습니다. 그 다음에는 GPT-4 API를 사용하여 질문 리포지토리를 확장했습니다. 수동으로 만든 질문과 의미 및 주제적으로 관련된 새로운 질문을 생성하는 작업을 수행했습니다.

원칙에 따라 지침을 생성하려면
   ```
   python generate.py
   ```


## 원칙적인 명령어 미세 조정

저희 벤치마크는 [스탠포드 알파카](https://github.com/tatsu-lab/stanford_alpaca) 또는 [패스트챗](https://github.com/lm-sys/FastChat)과 호환됩니다. 미세 조정된 모델을 추가로 제공할 예정입니다.

## 인용

```
@article{bsharat2023principled,
  title={원칙에 입각한 지침만 있으면 LLaMA-1/2, GPT-3.5/4에 질문할 수 있다},
  저자={손도스 마흐무드 브샤라트, 아이다르 미르자칸, 지치앙 쉔},
  저널={arXiv preprint arXiv:2312.16171},
  year={2023},
}
```


## 기여하기
원칙을 개선하고 데이터 세트를 확장하기 위한 기여와 제안을 환영합니다.

## 감사

[스탠포드 알파카](https://github.com/tatsu-lab/stanford_alpaca)
