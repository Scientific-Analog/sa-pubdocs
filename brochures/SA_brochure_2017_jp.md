---
Title: "Scientific Analog Product Brochure (2017 | Japanese)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL", "GLISTER", "MODELZEN"]
Year: 2017
Source: "XMODEL_brochure_201706_jp.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: Take Your Analog Models to the Next Level


<!-- Page 2 -->
## Our Products

* **XMODEL** を用いることで、SystemVerilog上でアナログ／ミックスド・シグナル システムの速度と精度が両立するシミュレーションができます。

* **GLISTER** は、Cadence® Virtuoso® Schematic Editor に組み込まれた XMODEL と MODELZEN の GUI です。

* **MODELZEN** を用いることで、回路図またはネットリストから自動的にモデルを生成できます。


<!-- Page 3 -->
# XMODEL is for Everyone!

## System Architects
**XMODELの高速イベントドリブンシミュレーションを使って、アナログ/ミックスド・シグナルシステムのアーキテクチャを探索。**

 * GLISTERを使って、回路図でシステムレベルモデルを構成。
 * 他のアナログ機能モデル（Verilog-A/MSやReal Number Verilog）より10〜100倍高速化。
 * 合成できるデジタルHDLモデルを含むシステムレベルの動作を検証。

*XMODEL as Top-Down Tool*

## Circuit Designers
**回路図ベースのアナログ設計環境で簡単に回路モデルを構成、または自動生成。**

 * GLISTERの豊富なプリミティブを使って、回路図でトップダウン機能モデルを構成。
 * 回路レベルモデリング（CLM）を使って、SystemVerilogでアナログ回路の動作を記述。
 * MODELZENを用いることで、回路から自動的にモデルを抽出可能。

*XMODEL as Bottom-Up Tool*

## Verification Engineers
**デジタルとアナログの両方のコンポーネントからなる大規模システムのチップレベル機能を検証。**

 * 例：デジタル較正機能搭載RFトランシーバ、高速I/O搭載プロセッサ、内部発電でのDRAM、…
 * SystemVerilogの単一シミュレーションプラットフォームで、超高速のイベントドリブンシミュレーションを利用。
 * 既存のデジタル検証フロー（例：UVM）やミックスド・シグナルシミュレーションフローとシームレスに統合。

*XMODEL as Sign-Off Tool*


<!-- Page 4 -->
# XMODEL: Empower SystemVerilog with Event-Driven Analog Models

XMODELはVCS、NC-Verilog、Questa/ModelSimなど、既存のSystemVerilogシミュレータの拡張パッケージであり、機能モデルまたは回路レベルモデルを使ってアナログ／ミックスド・シグナル システムを高速で正確にシミュレーションします。XMODELはSPICEを起動することなくSystemVerilog上でアナログシミュレーションの実行ができるため、SPICE、Verilog-AMS、Real-Number Verilogなど、既存のツールに課題をもたらすデジタル・アナログ混載の大規模で複雑なミックスド・シグナル・システムの検証に理想的です。

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

## XMODELの機能モデルによるイベントドリブン シミュレーション

XMODELは革新的なアルゴリズムを使ってアナログ波形を関数形式で表現し、イベントドリブン手法で効率的に計算します。その結果、XMODELプリミティブで構成された機能モデルは、正確な結果を得るため波形上のすべての値を計算する必要のあるVerilog-AMSやReal-Number Verilogに対して最大10-100倍の高速化を実現します。

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


## XMODELによるSystemVerilogでの回路レベルシミュレーション

XMODELは機能プリミティブに加えてレジスタ、キャパシタ、トランジスタ、伝送線路などの回路レベル プリミティブを提供します。この回路レベル プリミティブを使うことで、負荷効果、非線形性、スイッチング、複数のドライバ効果など、Real-Number Verilog(wrealモデル)が直接サポートしない様々なアナログエフェクトを持つモデルを簡単に構成できます。さらに、シミュレーションはSPICEを起動することなく、SystemVerilogだけで実行できます。
 

<!-- Page 5 -->
# GLISTER: Model Circuits in Schematics without Writing Codes

GLISTERは、Cadence® Virtuoso® 環境に組み込まれたXMODELとMODELZEN向けのGUIです。GLISTERを用いることで、コードを書かなくても簡単に回路図でアナログモデルを構成し、XMODELシミュレーションが実行できます。

## XMODELプリミティブ シンボルでモデルを構築

GLISTERは、豊富なXMODELプリミティブを回路図シンボルとして提供し、それをSystemVerilogモデルにネットリストすることができます。したがって、GLISTERを使ってモデルを作成することは、コーディングせずに単にプリミティブシンボルを回路図に配置し、ワイヤでそれらを接続することを意味します。GLISTERを使ったモデル構成は、Cadence® Design Environmentに組み込まれたオンラインドキュメントでより簡単にできます。

## ミックスドシグナルの階層的ネットリスト生成

GLISTERはwire、real、xbit、およびxrealなどのデジタルとアナログのコンポーネントを接続する種々の信号タイプが回路図モデルに含まれることを理解しています。GLISTERは回路図をSystemVerilogモデルにネットリストするとき、設計階層を横断することで自動的に適切な信号タイプを決定し、一貫した信号タイプと必要なコネクタを備えたモデルを生成します。

## 統合されたテストベンチ管理

GLISTERのTestbench Editorを用いることで、シミュレーションオプション、階層構成、ソースファイルなどをGUIを使ってCadence® デザインデータベースのセルビューとしてXMODELテストベンチを定義できます。また、各テストベンチセルビューはMakefileとソースファイルを含むシミュレーションディレクトリとしてエクスポートでき、コマンドラインからのバッチ処理を可
能にします。

## XMODEL-SPICE Co-simulationサポート

回路とモデルの両方のビューが設計階層に共存するとき、GLISTERはSystemVerilogモデルファイル、SPICE/Spectreネットリスト、ミックスドシグナルシミュレーション制御ファイルなど、XMODEL-SPICE co-simulationに必要なファイルを準備します。Cadence® Hierarchy Editorを使って、各セルまたはインスタンスに使えるセルビューを選択できます。GLISTERのTestbench Editorは、Synopsys®のVCS®やXA、Cadence®のNCVerilog®やAPSなど、様々なシミュレータと統一されたインターフェイスを提供します。


<!-- Page 6 -->
# MODELZEN: Create Analog Models with Peace of Mind

MODELZENは、XMODELプリミティブを使って回路をSystemVerilogモデルに変換させるアナログ回路用自動モデル生成ツールです。

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

## Quick and Correct-by-Constructionによるアナログモデルの生成

基本的に、MODELZENはXMODELの回路レベル シミュレーション機能を活用して、与えられた回路の構造モデルを生成します。つまり、MODELZENは回路を構成する個々の素子を特性付けることでモデルを構築し、結果としてのデバイスモデルを元の回路のトポロジどおりに接続します。この手法は、回路の機能を理解する必要がなく、correct-by-constructionモデルを保証します。さらに、生成されたモデルはXMODELのイベントドリブン シミュレーションによって高速で実行されます。MODELZENを用いることで、わずか数時間でフル・チップ・モデルが得られます。

## アナログの専門知識がなくてもモデルを生成可能

MODELZENを用いることで、アナログの専門家でなくてもアナログ回路の高精度モデルを作成できます。MODELZENの構造的モデリング手法のおかげで、テストエンジニアは回路設計者の助けなしでもシステムレベル検証用モデルを生成できます。また、回路設計者も回路が更新されるたびに楽にモデルの再構築ができます。


## クリック1回でモデルを生成

GLISTERと共にMODELZENを用いることで、クリック1回でCadence® Virtuoso®の回路図からモデルを自動的に生成できます。GLISTERはネットリスト生成や属性抽出などのモデル生成の準備段階を合理化し、生成されたモデルをデザインデータベースにインポートして最新の状態に保ちます。


<!-- Page 7 -->
# Take Your Analog Models to the Next Level

## XMODELプリミティブを使ったトップダウン モデリング

豊富なXMODELプリミティブを用いることで、回路設計を始める前にアイデアを機能モデルに記述し、その動作をテストすることが簡単にできます。

## MODELZEN / MODELFITによるボトムアップ モデリング

MODELZENやMODELFITを用いることで、回路設計が終わった後、回路から抽出したモデルでシステムレベルの検証を迅速に行うことができます。
 * **MODELZEN** 回路のネットリストを同等のXMODEL回路レベルモデルに変換します。
 * **MODELFIT** 機能モデルのパラメータをSPICEシミュレーションの結果と対照して校正します。

## XMODELによる高速システムレベル検証

トップダウンまたはボトムアップのどちらのモデルでも、XMODELはSPICEによるco-simulationサポートでSystemVerilogでの最も速いイベントドリブンシミュレーションを実現します。

## IC Design Flow with XMODEL

```
          1. Idea             ┐
              │               | Top-Down
              ▼               | Modeling
     2. Functional Model      ┘ 
              │
              ▼
 3. Circuit Implementation    ┐
              │               | Bottom-Up
              ▼               | Modeling
    4. Verification Model     ┘
              │
              ▼
       5. IC Product
```


<!-- Page 8 -->
# About Scientific Analog, Inc.

**Scientific Analog, Inc.**は、デジタル設計のように体系的で生産的なアナログIC設計を目指して2015年に設立されました。特に、確立されたデジタルフロー内のアナログモデルの効果的な利用は、成功したミックスド・シグナルICの設計と検証への鍵だと信じています。XMODEL、GLISTER、MODELZENは、この目標を達成するための最も重要な製品です。現在、アメリカ、韓国、中国、インドの25以上の企業や大学がXMODELを利用しています。

## Contact Us
Scientific Analog, Inc. または製品のライセンスやサポートの詳細については、下記のメールアドレスまでご連絡、またはウェブサイトをご覧ください。
* Email: info@scianalog.com
* Website: https://www.scianalog.com

## Disclaimers
本書に記載されているすべての商標は、それぞれの所有者に帰属します。
