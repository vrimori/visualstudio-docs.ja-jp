---
title: "図のプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "ドメイン固有言語, 図"
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# 図のプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

図が生成されたデザイナーでどのように表示するかを指定するプロパティを設定できます。  たとえば図のテキストに既定の色を指定できます。  
  
 詳細については、「[方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)」を参照してください。  これらのプロパティを使用する方法の詳細については[ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md) を参照してください。  
  
 次の表は図のプロパティの一覧を示します。  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|塗りつぶしの色|図の塗りつぶしの色。|白|  
|テキストの色|図に表示されるテキストの色。|黒|  
|Access 修飾子|クラスのアクセス修飾子 \(public または internal\)。|Public|  
|カスタム属性|生成されたコードに属性を追加するために使用されるクラスが含まれています。|なし|  
|派生型が生成されます。|`True` が基本クラスおよび部分クラスの両方 \(オーバーライドによってカスタマイズをサポートする\) 生成されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|カスタム コンストラクターがあります。|`True` がソース・コードでカスタム コンストラクター提供されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|継承の修飾子|図 \(`none``abstract` または `sealed`\) から生成されるソース・コードのクラスの継承について説明します。|なし|  
|基本図|この図の基本クラス。|\(なし\)|  
|名前|この図の名前。|現在の名前|  
|名前空間|この図で指定する名前空間。|現在の名前空間|  
|で表されるクラス|この図を表すルート ドメインのクラス。|現在のルートに該当する場合はクラス|  
|説明|この要素に関連付けられている単純に注意してください。|なし|  
|プロパティとして公開の塗りつぶしの色|`True`ユーザーが生成したデザイナーのダイアグラムの塗りつぶしの色を設定できます。  これを設定するには図の図形を右クリックし\[ENT5ENT\] をクリックします。|False|  
|プロパティとして公開のテキストの色|`True`ユーザーが生成したデザイナーのダイアグラムのテキストの色を設定できます。  これを設定するには図の図形を右クリックし\[ENT2ENT\] をクリックします。|False|  
|Description|生成されたデザイナーを説明する説明。|なし|  
|\[表示名\]|この図の生成されたデザイナーに表示される名前。|なし|  
|ヘルプ キーワード|この図ではF1 ヘルプにインデックスを付けるために使用されるキーワード。|なし|  
  
## 参照  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)