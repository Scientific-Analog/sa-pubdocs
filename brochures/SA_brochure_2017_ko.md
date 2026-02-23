---
Title: "Scientific Analog Product Brochure (2017 | Korean)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL", "GLISTER", "MODELZEN"]
Year: 2017
Source: "XMODEL_brochure_201706_ko.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: Empower SystemVerilog with Event-Driven Analog Models

XMODEL은 다양한 아날로그 회로들을 기존의 디지털 검증 환경인 SystemVerilog상에서 쉽게 모델링하고 시뮬레이션할 수 있게 해주는 확장패키지입니다. XMODEL은 현재 Synopsys®의 VCS®, Cadence®의 INCISIVE® (NCVerilog®), MentorGraphics®의 Questa® (ModelSim®)을 지원하고 있습니다.

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
 │   (VCS®, NC-Verilog®, ModelSim®)   │
 │                  +                 │
 │      XMODEL Simulation Engine      │
 │                                    │
 └────────────────────────────────────┘
                   │
                   ▼
          Simulation Results
```

## Event-Driven 방식의, 빠른 Functional 모델 시뮬레이션

XMODEL은 단순 값이 아닌 함수식을 사용해 아날로그 파형을 표현하고, 이를 event-driven 방식으로 계산하는 혁신적인 알고리즘을 사용합니다. XMODEL에서 제공하는 primitives를 사용해서 구성한 동작모델 (functional model)은 정확한 결과를 위해 파형의 많은 점을 계산해야 하는 Verilog-AMS 또는 Real-Number Verilog에 비해 최대 10~100배 이상의 빠른 실행속도를 낼 수 있습니다.

### XMODEL (Event-Driven)

```
        □  ← events
       / \
      /   \
  □───     ───□
```

### Other Simulators  
*(SPICE, Verilog-AMS, Real-Number Verilog)*

```
      ┌─┐
      │ └─┐
      │   └─┐
  ┌───┘      └───┐
```


## SystemVerilog에서 수행가능한 회로 시뮬레이션

XMODEL을 사용하면, 회로 시뮬레이션이 불가능한 디지털 시뮬레이터인 SystemVerilog 상에서도 저항, 커패시터, 인덕터, 다이오드, 트랜지스터 등의 소자들을 직접 조합하여 아날로그 회로를 표현할 수 있고, 이 회로를 XMODEL의 event-driven 방식으로 매우 빠르게 시뮬레이션할 수 있습니다. 이 기능은 특히 아날로그 회로에 있는 여러가지 비선형성, 로딩효과, 스위칭 동작, 다중 드라이버 효과 등을 모델링하는데 매우 유용합니다. 놀라운 점은, 이러한 회로 시뮬레이션이 SPICE를 전혀 사용하지 않는 순수 SystemVerilog 환경에서 실행 가능하다는 것입니다.


<!-- Page 2 -->
# GLISTER: Model Circuits in Schematics without Writing Codes

GLISTER는 Cadence®의 Virtuoso® 환경에서 아날로그 회로의 모델들을 한줄의 코드 작성 없이 schematic 형태로 쉽게 표현하고, 이로부터 SystemVerilog 모델을 추출하여 시뮬레이션할 수 있게 해주는 GUI 환경입니다.

## XMODEL Primitive 심볼을 이용한 Schematic 형태의 모델 작성

GLISTER는 XMODEL의 다양한 primitive들을 schematic symbol의 형태로 제공합니다. 따라서 사용자는 다양한 아날로그 회로의 모델들을 코딩 작성이 단순히 schematic 위에 그리는 것처럼 심볼들을 배치하고 도선을 연결하는 것으로 쉽게 표현할 수 있습니다. 특히, GLISTER 환경에서는 각 primitive에 대한 설명을 쉽게 얻을 수 있어 모델 작성이 더 용이하게 해줍니다.

## Hierarchical Netlisting을 통한 SystemVerilog 모델 생성

아날로그와 디지털 신호가 혼재하는 모델에서는 schematic 상의 각 도선이 wire, real, xbit 및 xreal 등 다양한 signal type을 가질 수 있습니다. GLISTER는 이와 같은 signal type의 차이를 이해하는 유연한 netlister이며, 각 도선이 연결하는 primitive의 종류에 따라 적절한 signal type을 자동으로 인지할 수 있습니다. 게다가, 서로 다른 type의 신호들간에 연결이 필요할 때 그 신호의 type을 변환해주는 connect primitive들도 자동으로 삽입할 수 있습니다.

## 통합된 Testbench 관리

GLISTER의 Testbench Editor를 사용하면, 대상 design의 hierarchy 구성, 시뮬레이션의 각종 옵션 등 시뮬레이션 테스>트 벤치에 해당되는 내용을 GUI 환경을 통해 정의할 수 있고, 그 내용을 Cadence® 설계 database상의 cellview의 형태>로 저장할 수 있습니다. 또한 GLISTER는 이 테스트벤치를 netlisting할 때, command-line 상에 Makefile 스크립트를 통
해 직접 실행할 수 있는 형태로 시뮬레이션 폴더를 구성하므로 일괄처리도 용이하게 수행할 수 있습니다.

## XMODEL-SPICE Co-simulation 지원

대상 design의 hierarchy에 회로 schematic view와 모델 schematic view들이 함께 있는 경우, GLISTER는 사용자가 XMODEL-SPICE co-simulation을 수행하고자 한다고 판단하고, 그에 알맞은 SystemVerilog 모델 파일, SPICE 또는 Spectre netlist 파일 및 co-simulation에 필요한 추가 파일들을 자동으로 준비해줍니다. 이러한 대상 design hierarchy는 Cadence® Hierarchy Editor를 사용하여 선택할 수 있습니다. GLISTER의 Testbench Editor는 Synopsys®의 VCS®와 XA, Cadence®의 NCVerilog®와 APS 등 다양한 시뮬레이터에 대해서 일관된 사용자 인터페이스를 제공합니다.


<!-- Page 3 -->
# MODELZEN: Create Analog Models with Peace of Mind

MODELZEN은 임의의 아날로그 회로로부터 SystemVerilog 모델을 자동으로 생성해주는 툴입니다.

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

기본적으로 MODELZEN은 XMODEL의 회로 시뮬레이션 기능을 활용하여 주어진 회로의 구조적 모델(structural model)을 생성합니다. 즉, MODELZEN은 회로를 구성하는 개별 소자들의 특성을 파악하여 그에 해당하는 모델을 생성한 후, 그 소자단위의 모델들을 기존 회로의 연결상태대로 연결한 회로 모델을 생성합니다. 이러한 방법의 장점은 대상 회로에 대한 전문적인 지식이 없어도 항상 정확히 동작하는 모델을 쉽게 생성할 수 있다는 것입니다. 또한 생성된 모델은 XMODEL의 event-driven 시뮬레이션 방식에 의해 SystemVerilog 상에서 빠르게 실행됩니다.

## 아날로그 전문지식이 없어도 가능한 모델 생성

MODELZEN을 사용하면 아날로그 전문가가 아니더라도 정확도 높은 SystemVerilog 모델을 쉽게 생성할 수 있습니다. MODELZEN의 구조적 모델링 방법은 주로 디지털 배경지식이 풍부한 검증 엔지니어들이 아날로그 회로 설계자에게 도움을 청하지 않고도 system-level 검증을 위한 아날로그 회로 모델을 직접 생성할 수 있게 해줍니다. 또한, 회로 설계자가 회로가 변경될 때마다 그에 맞게 모델을 자동 업데이트 할 수 있어 편리합니다.

## 마우스 클릭 한번으로 생성되는 모델!

GLISTER와 함께 MODELZEN을 사용하면 Cadence® Virtuoso® Schematic Editor상에서 마우스를 단 한번 클릭하는 것만으로도 모델을 자동 생성할 수 있어 더욱 편리합니다. GLISTER는 모델 생성을 위해 netlist 생성 및 속성 추출 등의 준비단계를 자동으로 수행하고, MODELZEN이 생성한 모델을 다시 Cadence® database로 import하는 역할을 수행합니다.

