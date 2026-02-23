---
Title: "Scientific Analog Product Brochure (2020 | Korean)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL", "GLISTER", "MODELZEN"]
Year: 2020
Source: "XMODEL_brochure_202007_ko.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: SystemVerilog에서 아날로그 회로를 검증하는 최선의 방법


<!-- Page 2 -->
# SystemVerilog에서 아날로그 회로를 검증하는 최선의 방법을 찾고 계신가요?

## 검증 엔지니어
SystemVerilog에서 아날로그 모델을 빠르게 시뮬레이션 하고 싶어요.

### XMODEL은 SystemVerilog에서 아날로그 시뮬레이션을 가장 빠르게 수행할 수 있는 방법입니다.
XMODEL만의 event-driven 알고리즘 방식과 풍부한 primitive로 Real-Number Verilog에 비해 10~100배 이상 빠른 실행속도를 낼 수 있습니다.

## 시스템 아키텍트
아날로그 모델을 작성해야 하는데 Verilog 코딩을 못해요. 

### GLISTER로 top-down 아날로그 모델을 schematic 형태로 작성할 수 있습니다.
GLISTER라면 Cadence Virtuoso에서 간단히 XMODEL primitive 심볼을 사용하여 다양한 아날로그 회로 모델을 코딩 없이 쉽게 작성할 수 있습니다.

## 회로 설계자
아날로그 회로에서 SystemVerilog 모델을 추출하고 싶어요.

### MODELZEN을 사용해 회로에서 아날로그 모델을 자동으로 추출할 수 있습니다.
MODELZEN은 항상 정합성이 보장되는 SystemVerilog 모델을 마우스 클릭 한 번만에 회로에서 생성해냅니다.


<!-- Page 3 -->
# XMODEL: SystemVerilog상에서 아날로그 모델을 빠르게 검증하세요!

XMODEL은 다양한 아날로그 회로들을 기존의 디지털 검증 환경인 SystemVerilog상에서 쉽게 모델링하고 시뮬레이션할 수 있게 해주는 확장패키지입니다. XMODEL은 현재 Synopsys의 VCS, Cadence의 Xcelium(구 NCVerilog), MentorGraphics사의 Questa(구 ModelSim)을 지원하고 있습니다.

## XMODEL Simulation Flow

```
      Analog/Mixed-Signal Models
                   │
                   ▼
 ┌────────────────────────────────────┐
 │               XMODEL               │
 │                                    │
 │     XMODEL Primitives Library      │
 │                  +                 │
 │      SystemVerilog Simulator       │
 │                  +                 │
 │      XMODEL Simulation Engine      │
 │                                    │
 └────────────────────────────────────┘
                   │
                   ▼
          Simulation Results
```

## SystemVerilog상에서 빠르고 정확한 아날로그 시뮬레이션

XMODEL은 단순 값이 아닌 함수식을 사용해 아날로그 파형을 표현하고, 이를 event-driven 방식으로 계산하는 혁신적인 알고리즘을 사용합니다. XMODEL에서 제공하는 primitive를 사용해서 구성한 동작모델(functional model)은 정확한 결과를 위해 파형 위의 많은 점을 계산해야 하는 Verilog-AMS 또는 Real-Number Verilog에 비해 최대 10~100배 이상의 빠른 실행속도를 낼 수 있습니다.

### XMODEL (Event-Driven)
Can be both fast and accurate thanks to fewer events

```
        □  ← events
       / \
      /   \
  □───     ───□
```

### Other Simulators  
*(SPICE, Verilog-AMS, Real-Number Verilog)*

Must trade speed for accuracy due to more events required

```
      ┌─┐
      │ └─┐
      │   └─┐
  ┌───┘      └───┐
```

## SystemVerilog에서 수행가능한 회로 시뮬레이션

XMODEL을 사용하면, 디지털 시뮬레이터인 SystemVerilog상에서도 저항, 커패시터, 다이오드, 트랜지스터 등의 소자를 직접 활용하여 아날로그 회로를 표현할 수 있고, 이를 XMODEL의 event-driven 방식으로 빠르게 시뮬레이션할 수 있습니다. 이 기능은 특히 아날로그 회로에 존재하는 비선형성, 로딩 효과, 스위칭 효과, 다중 드라이버 효과 등을 모델링하는 데 매우 유용합니다. 놀라운 점은 이러한 회로 시뮬레이션이 SPICE를 전혀 사용하지 않는 순수 SystemVerilog 환경에서 실행 가능하다는 것입니다.

## XMULAN으로 시뮬레이션 자동화

XMULAN은 XMODEL에 포함되어 있는 파이썬 라이브러리입니다. XMULAN을 활용하면, 파라미터 변화시키며 시뮬레이션을 실행하거나 그 결과를 수집하여 후처리하는 다양한 파이썬 스크립트를 작성할 수 있습니다.

## XMODEL-SPICE Co-simulation

XMODEL primitive로 작성한 SystemVerilog 모델은 호스트 시뮬레이터가 지원한다면, SPICE netlist, Verilog-AMS, 또는 Real-Number Verilog 모델과도 연동할 수 있습니다.


<!-- Page 4 -->
# GLISTER: Top-Down 아날로그 모델을 스키메틱 형태로 쉽게 그려서 작성하세요!

GLISTER는 Cadence®의 Virtuoso® 환경에서 아날로그 회로의 모델들을 한줄의 코드 작성 없이 schematic 형태로 쉽게 표현하고, 이로부터 SystemVerilog 모델을 추출하여 시뮬레이션 할 수 있게 해주는 GUI 환경입니다.

```
 ┌──────────────────────────────────────────────────────────┐
 |  Draw model schematics with XMODEL primitive symbols.    |
 |                           │                              |
 |                           ▼                              |
 |  And GLISTER can netlist them into SystemVerilog models. |
 └──────────────────────────────────────────────────────────┘
```

## XMODEL Primitive 심볼을 이용한 Schematic 형태의 모델 작성

GLISTER는 XMODEL의 다양한 primitive들을 schematic symbol의 형태로 제공합니다. 따라서 사용자는 다양한 아날로그 회로의 모델들을 코딩 작성없이 단순히 schematic 위에 그 symbol들을 배치하고 도선으로 연결하는 것으로 쉽게 표현할 수 있습니다. 특히, GLISTER 환경에서는 각 primitive에 대한 설명을 쉽게 얻을 수 있어 모델 작성을 더 용이하게 해줍니다.

## Hierarchical Netlisting을 통한 SystemVerilog 모델 생성

아날로그와 디지털 신호가 혼재하는 모델에서는 schematic 상의 각 도선이 wire, real, xbit 및 xreal 등의 다양한 signal type을 가질 수 있습니다. GLISTER는 이와 같은 signal type의 차이를 이해하는 유일한 netlister이며, 각 도선이 연결하는 primitive의 종류에 따라 적절한 signal type을 자동으로 인지할 수 있습니다.
게다가, 서로 다른 type의 신호들간에 연결이 필요할 때, 신호의 type을 변환해주는 connect primitive들도 자동으로 삽입할 수 있습니다.

## 통합된 Testbench 관리

GLISTER의 Testbench Editor를 사용하면, 대상 design의 hierarchy 구성, 시뮬레이션의 각종 옵션 등 시뮬레이션 테스트벤치에 해당되는 내용들을 GUI 환경을 통해 정의할 수 있고, 그 내용을 Cadence® 설계 database상의 cellview의 형태로 저장할 수 있습니다. 또한 GLISTER는 이 테스트벤치를 netlisting할 때, command-line 상에서 Makefile 스크립트를 통해 직접 실행할 수 있는 형태로 시뮬레이션 폴더를 구성하므로 일괄처리도 용이하게 수행할 수 있습니다.

## Cadence Analog Design Environment (ADE)와의 통합

GLISTER-ADE 통합환경을 통해, ADE세션에서 XMODEL을 시뮬레이터로 선택하여 테스트벤치 구성, netlist 생성, 시뮬레이션 실행, 파형 확인 등 주요 GLISTER 작업들을 익숙한 ADE 메뉴와 명령어로 수행할 수 있습니다.


<!-- Page 5 -->
# MODELZEN: 아날로그 회로로부터 Bottom-Up 모델을 자동 추출하세요!

MODELZEN과 함께라면 아날로그 모델 자동 생성은 꿈이 아닌 현실이 됩니다. MODELZEN은 bottom-up 모델 생성 툴로, 그 어떠한 아날로그 회로라도 XMODEL primitive를 사용한 동등한 SystemVerilog 모델로 변환할 수 있습니다.

## MODELZEN Conversion Flow

```
      SPICE/Spectre Netlist
                │
                ▼
┌──────────────────────────────┐
│           MODELZEN           │
│                              │
│  1. Input Netlist Parsing    │
│  2. Topology Analysis        │
│  3. Device Model Fitting     │
│  4. Output Model Generation  │
│                              │
└──────────────────────────────┘
                │
                ▼
         XMODEL Netlist
```

## 항상 옳게 동작하는 아날로그 모델의 자동 생성

기본적으로 MODELZEN은 XMODEL의 회로 시뮬레이션 기능을 활용하여 주어진 회로의 구조적 모델(structural model)을 생성합니다. 즉, MODELZEN은 회로를 구성하는 개별 소자들의 특성을 파악하여 그에 해당하는 모델을 생성한 후, 그 소자단위의 모델들을 기존 회로의 연결상태로 연결한 회로 모델을 생성합니다. 이러한 방법의 장점은 대상 회로에 대한 전문적인 지식이 없어도 항상 정확하게 동작하는 모델을 쉽게 생성할 수 있다는 것입니다. 또한 생성된 모델은 XMODEL의 event-driven 시뮬레이션 방식에 의해 SystemVerilog상에서 빠르게 실행됩니다.

## User-Defined Models (UDM)을 이용한 Functional 모델 생성

MODELZEN은 회로 수준의 모델 뿐만 아니라, 보다 빠른 시뮬레이션이 가능한 상위모델도 생성할 수 있습니다. MODELZEN의 새로운 user-defined model(UDM) 인터페이스를 통해 회로의 일부 블록을 선택하여 그에 맞춤형 functional 모델을 생성할 수 있으며, 이 모델에 필요한 파라미터 값들은 SPICE 시뮬레이션으로 자동 추출할 수 있습니다. 지금까지 수작업으로 bottom-up 모델을 생성해왔다면, UDM 인터페이스는 전문지식의 문맥화를 통해 모델 생성을 자동화할 수 있는 아주 좋은 방법이 될 것입니다.

## 마우스 클릭 한번으로 생성되는 모델!

GLISTER와 함께 MODELZEN을 사용하면 Cadence® Virtuoso® Schematic Editor상에서 마우스를 단 한 번 클릭하는 것만으로 모델을 자동 생성할 수 있어 더욱 편리합니다. GLISTER는 모델 생성을 위해 netlist 생성 및 속성 추출 등의 준비단계를 자동으로 수행하고, MODELZEN이 생성한 모델을 다시 Cadence® database로 import하는 역할을 수행합니다.


<!-- Page 6 -->
# About Scientific Analog, Inc.

사이언티픽아날로그는 2015년에 아날로그 IC도 디지털 IC처럼 쉽고 체계적인 방법으로 설계할 수 있다는 신념을 가지고 설립한 미국 실리콘밸리에 본사를 둔 신흥벤처기업입니다.

현재 컴퓨터, 스마트폰, 가전기기 등에 탑재되는 대부분의 시스템-온-칩(SoC)들은 주로 디지털 회로로 이루어져 있지만, 일부 포함되는 아날로그 회로들 때문에 전체적인 동작 검증이 매우 어렵고, 뒤늦게 발견한 오류 때문에 개발한 제품의 시장 진입이 지연되는 경우가 많습니다.

사이언티픽아날로그는 바로 이러한 문제를 해결하기 위해서 XMODEL이란 아날로그 설계자동화 및 검증 소프트웨어를 개발하였고, 삼성전자, SK하이닉스와 같은 국내의 다수의 반도체설계 회사들의 관심과 수요가 크게 증가하고 있습니다.

## Contact Us
사이언티픽아날로그 또는 라이선싱에 대한 자세한 문의는 공식 이메일 (info@scianalog.com) 로 연락주시거나 공식 웹사이트 (www.scianalog.com) 에 방문해 주세요.
* Email: info@scianalog.com
* Website: https://www.scianalog.com

## Disclaimers
XMODEL, GLISTER, MODELZEN, XWAVE, XMULAN은 사이언티픽아날로그의 상표입니다.
이 브로슈어에 쓰인 모든 상표들은 그 해당하는 권리권자의 고유재산입니다.