---
title: "スイムレーンのプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.swimlane"
helpviewer_keywords: 
  - "ドメイン固有言語, スイムレーン"
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# スイムレーンのプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

スイムレーンに図を追加できます。  スイムレーンを縦または横の領域に図を分割します。  スイムレーン内に表示する他の図形を定義できます。  詳細については、「[方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)」を参照してください。  これらのプロパティを使用する方法の詳細については[ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md) を参照してください。  
  
 スイムレーン次の表に示すプロパティがあります。  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|本体の塗りつぶしの色|スイムレーンの本体の塗りつぶしの色。|白|  
|ヘッダーの塗りつぶしの色|スイムレーンのヘッダーの塗りつぶしの色。|濃い灰色|  
|区分線の色|の区切り線の色。|明るい灰色|  
|の区切り線のスタイル|区分線の行 \(`Solid``Dash``Dot``DashDot``DashDotDot`または `Custom`\) のスタイル。|`Dash`|  
|区分線の太さ|インチの区切り線の太さ。|0.03125|  
|テキストの色|このスイムレーンに関連付けられたテキスト デコレータに使用される色。|黒|  
|Access 修飾子|クラスのアクセス レベル \(`public` または `internal`\)。|Public|  
|カスタム属性|このスイムレーンから生成されたコードに属性を追加するために使用されるクラスが含まれています。|なし|  
|派生型が生成されます。|`True` が基本クラスおよび部分クラスの両方 \(オーバーライドによってカスタマイズをサポートする\) 生成されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|カスタム コンストラクターがあります。|`True` がソース・コードでカスタム コンストラクター提供されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|継承の修飾子|スイムレーン \(`none``abstract` または `sealed`\) から生成されるソース・コードのクラスの継承について説明します。|\[none\]|  
|基本スイムレーン|このスイムレーンの基本クラス。|\(なし\)|  
|名前|このスイムレーンの名前。|現在の名前|  
|名前空間|このスイムレーンにサブスクライブする名前空間。|現在の名前空間|  
|ツールヒントの種類|ツールヒントの定義方法が `fixed``variable`\(または\) `none`。  `fixed` は`Fixed Tooltip Text` のプロパティの値は ; `variable` がカスタム コードでツールヒントに指定します。|なし|  
|説明|このスイムレーンに関連付けられている単純に注意してください。|なし|  
|\[配置\]|水平方向または垂直方向の配置。|\[垂直方向\]|  
|最初の高さ|このインチのスイムレーンの最初の高さ。  水平方向のスイムレーンにのみ適用されます。|0|  
|初期の幅|このインチのスイムレーンの初期の幅。  垂直方向のスイムレーンにのみ適用されます。|0|  
|発行のテキストの色|`True`ユーザーが生成したデザイナーのスイムレーンの色を設定できます。  これを設定するにはスイムレーンの図形を右クリックし\[ENT2ENT\] をクリックします。|False|  
|Description|生成されたデザイナーを作成するために使用します。|なし|  
|\[表示名\]|スイムレーンこのクラスによって生成されたデザイナーに表示される名前。|なし|  
|固定ツール ヒント テキスト|固定ツールヒントに使用されるテキスト。|なし|  
|ヘルプ キーワード|このスイムレーンのキー インデックスを付けるために使用されるヘルプ キーワードです。|なし|  
  
## 参照  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)