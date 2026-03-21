# 論文メモ #001: 前頭葉アルファ波とFTD診断

登録日: 2026-03-21

## 論文情報

- **タイトル**: Quantitative Electroencephalography Markers for an Accurate Diagnosis of Frontotemporal Dementia: A Spectral Power Ratio Approach
- **PMC**: [PMC10744364](https://pmc.ncbi.nlm.nih.gov/articles/PMC10744364/)
- **掲載**: PMC (2023年12月頃)

## 概要

- FTD（前頭側頭型認知症）はプレセニル認知症で2番目に多いが、診断研究が不十分
- OpenNeuroのオープンデータを使用し、FTD患者23名 vs 健常者29名で前頭葉-側頭葉のパワー比を調査
- FFTでδ, θ, α, β, γ帯域のスペクトルパワーを抽出

## 主な結果

- FTD患者では**前頭葉のθ波・δ波が増加**、**側頭葉・頭頂葉のβ波が減少**
- グローバルなα波減弱がFTDで報告されているが、**領域別解析ではα波の有意差は見られなかった**
- 前頭葉-側頭葉のパワー比がFTD診断の指標として有望

## 重要ポイント（iderihaコメント）

> 前頭葉のアルファ波が減弱→認知症と関連。ただし開眼か閉眼か論文中に明記がない。要調査。

## 使用データセット

### 閉眼データ（本論文で使用）
- **OpenNeuro ds004504**: [A dataset of EEG recordings from: AD, FTD and Healthy subjects](https://openneuro.org/datasets/ds004504/versions/1.0.7)
- **条件: resting state, 閉眼 (eyes-closed)**
- 被験者: AD 36名, FTD 23名, 健常 29名（計88名）
- 装置: Nihon Kohden EEG 2100, 10/20システム, 500Hz
- 記録時間: 各10分以上
- MMSE: AD 17.75(sd=4.5), FTD 22.17(sd=8.22), CN 30

### 開眼データ（補完データセット）
- **OpenNeuro ds006036**: [Complementary open-eyes EEG recordings in photo-stimulation setting](https://openneuro.org/datasets/ds006036/versions/1.0.2)
- **条件: 開眼, 光刺激あり（5Hz, 10Hz, 15Hz, 最大30Hz）**
- 同一コホートからの補完データ
- ギリシャ・テッサロニキ大学AHEPA病院の臨床プロトコル

## 調査結果

検索の結果、**本論文(PMC10744364)で使用されたデータは閉眼(eyes-closed) resting state**であることが判明。
同一コホートの開眼データ(ds006036)も存在するが、こちらは光刺激条件のため単純な開眼安静時とは異なる。

## 残タスク

- [ ] ds004504のデータ記述を直接確認し、閉眼条件を最終確認する
- [ ] ds006036（開眼+光刺激）のデータを確認し、本論文の結果と比較可能かを調査する
