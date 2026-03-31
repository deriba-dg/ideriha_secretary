# 論文メモ #004: パーキンソン病における安静時EEGシータ波増加（多施設FDA研究）

登録日: 2026-03-31

## 論文情報

- **タイトル**: Spectral features of resting-state EEG in Parkinson's Disease: A multicenter study using functional data analysis
- **著者**: Alberto Jaramillo-Jimenez et al.
- **掲載**: Clinical Neurophysiology, Vol. 151, pp. 28–40 (July 2023)
- **DOI**: 10.1016/j.clinph.2023.03.363
- **PubMed**: [37146531](https://pubmed.ncbi.nlm.nih.gov/37146531/)
- **ScienceDirect**: [S1388245723005989](https://www.sciencedirect.com/science/article/pii/S1388245723005989)

## 概要

- パーキンソン病（PD）患者84名 vs 健常者85名（計169名）を4施設から収集
- Functional Data Analysis（FDA）を用いて安静時EEGのスペクトル特徴をエポックごとに分析
- **全データセットで共通してPD群のシータ波相対パワーが増加**していることを確認
- 後頭部のプレアルファ帯域の増加も再現性のある所見

## 開眼/閉眼条件 ← 重要

**閉眼と開眼の混在**。データセットごとに条件が異なる：

| データセット | 施設 | 記録条件 |
|-------------|------|---------|
| California | Scripps Clinic, La Jolla, USA | **閉眼** |
| Finland | University of Turku, Finland | **閉眼** |
| Medellín | Universidad de Antioquia, Colombia | **閉眼** |
| Iowa | University of Iowa (Narayanan Lab) | **開眼** |

- 4施設中3施設は**閉眼**、Iowa のみ**開眼**
- 重要な知見: **プレアルファの差異は閉眼条件に限定されず、開眼条件（Iowa）でもPDで頑健に観察された**
  - → シータ波の増加はアルファ波の低下（slowing）だけでは説明できず、シータリズム自体の寄与が大きいことを示唆

## 方法

- **EEG機器**: 施設ごとに異なる（BioSemi ActiveTwo / NeurOne Tesla / Brain Vision / Neuro Scan Labs Synamps2）
- **電極**: 国際10-20法に準拠、29〜64ch（wet electrode）
- **前処理**: Python実装の自動パイプライン
- **スペクトル解析**: MNEのpsd_multitaper → YASAライブラリのbandpowerで相対PSD算出
- **周波数帯域**: δ(1-4Hz), θ(4-8Hz), α(8-13Hz), β(13-30Hz)（IFCN推奨基準）
- **FDA**: エポックごと（5秒エポック）の時間変動をモデル化

## 主要な結果

1. **シータ波相対PSD**: 全4データセットの大部分のチャネルでPD群が有意に増加
2. **後頭部プレアルファ**: FDA解析でより顕著な差異。従来の平均化では消えてしまうエポックレベルの差異を検出
3. **アルファ/シータ比・主波数（DF）**: PD群で低下傾向だが、全データセットで一般化はできず
4. **FDAの優位性**: 平均化アプローチでは見逃される差異を検出でき、外れ値の影響も評価可能

## エビデンス調査への示唆

- **閉眼条件でのシータ波増加**はPDの一般化可能なバイオマーカー
- **開眼条件でもプレアルファ/シータの増加が確認**されたことは、条件によらない頑健な指標であることを支持
- 複数施設・複数機器のデータで再現性が確認されているため、エビデンスとしての信頼性は高い
- オープンデータ: Iowa（Narayanan Lab）、California（OpenNeuro）、Finland（OSF）で公開

## 関連論文

- 開眼/閉眼条件の影響を体系的に調べた論文: [Early detection of Parkinson's disease: Systematic analysis of the influence of the eyes on quantitative biomarkers in resting state electroencephalography (Heliyon, 2023)](https://www.sciencedirect.com/science/article/pii/S2405844023078337)
  - PD患者13名（認知正常・早期）で閉眼時にシータ過剰活動を確認
  - 臨床では開眼・閉眼の両条件で記録することを推奨
