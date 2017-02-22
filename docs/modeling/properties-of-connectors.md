---
title: "コネクタのプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, コネクタ"
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# コネクタのプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コネクタは生成されるデザイナーのドメイン リレーションシップを表します。  
  
 詳細については、「[方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)」を参照してください。  これらのプロパティを使用する方法の詳細については[ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md) を参照してください。  
  
 コネクタは次の表に示すプロパティがあります。  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|色|このコネクタの色。|黒|  
|スタイルを紛砕します。|このコネクタ \(実線ダッシュドットDashDotDashDotDotカスタム\) の行の破線スタイル。|\[実線\]|  
|ソースの最後のスタイル|このコネクタ \(HollowArrowEmptyArrowFilledArrowEmptyDiamondFilledDiamondまたはなし\) のソース・の最後のスタイル。|なし|  
|最後のスタイルを対象とします。|このコネクタ \(HollowArrowEmptyArrowFilledArrowEmptyDiamondFilledDiamondまたはなし\) のターゲットの最後のスタイル。|なし|  
|テキストの色|この接続に関連付けられたテキスト デコレータに使用される色。|黒|  
|Thickness|インチ単位のこのコネクタの行の太さ。|0.03125|  
|Access 修飾子|クラスのアクセス レベル \(`public` または `internal`\)。|Public|  
|カスタム属性|この形式から生成されるソース・コードに属性を追加するために使用されるクラスが含まれています。|なし|  
|派生型が生成されます。|`True` が基本クラスおよび部分クラスの両方 \(オーバーライドによってカスタマイズをサポートする\) 生成されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|カスタム コンストラクターがあります。|`True` がソース・コードでカスタム コンストラクター提供されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|継承の修飾子|コネクタ \(`none``abstract` または `sealed`\) から生成されるソース・コードのクラスの継承について説明します。|\[none\]|  
|コネクタを適用します|このコネクタの基本クラス。|\(なし\)|  
|名前|このコネクタの名前。|現在の名前|  
|名前空間|このコネクタによってサブスクライブする名前空間。|現在の名前空間|  
|ツールヒントの種類|ツールヒントの定義方法の \(修正変数または None。\)   修正ツールヒントとして `Fixed Tooltip Text` のプロパティの値が使用されています ; 変数がカスタム コードでツールヒントに指定します。|なし|  
|説明|この接続に関連付けられている単純に注意してください。|なし|  
|スタイルのルーティング|コネクタのパスを指定するために使用されるスタイル。  `Rectilinear` のコネクタは必要に応じて正を回転します ; `Straight` のコネクタは。|直線|  
|プロパティとして公開される色<br /><br /> プロパティとして公開される破線スタイル<br /><br /> プロパティとして公開される太さ<br /><br /> 発行のテキストの色|`True`ユーザーが指定した図形のプロパティを設定できます。  これを設定するには図形定義を右クリックし\[ENT0ENT\] をクリックします。|False|  
|Description|生成されたデザイナーを作成するために使用します。|なし|  
|\[表示名\]|このコネクタの生成されたデザイナーに表示される名前。|なし|  
|固定ツール ヒント テキスト|固定ツールヒントに使用されるテキスト。|なし|  
|ヘルプ キーワード|この要素のキー インデックスを付けるために使用されるヘルプ キーワードです。|なし|  
  
## 参照  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)