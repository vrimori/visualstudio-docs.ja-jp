---
title: "ドメイン クラスのプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, ドメイン クラス"
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# ドメイン クラスのプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ドメイン クラスに次の表に示すプロパティがあります。  ドメイン クラスについては[モデル、クラス、およびリレーションシップについて](../modeling/understanding-models-classes-and-relationships.md) を参照してください。  これらのプロパティを使用する方法の詳細については[ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md) を参照してください。  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|Access 修飾子|ドメイン クラスのアクセス レベル \(`public` または `internal`\)。|`public`|  
|カスタム属性|このドメイン クラスから生成されるソース・コードに属性を追加するために使用されるクラスが含まれています。|なし|  
|派生型が生成されます。|`True` が基本クラスおよび部分クラスの両方 \(オーバーライドによってカスタマイズをサポートする\) 生成されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|`False`|  
|カスタム コンストラクターがあります。|`True` がソース・コードでカスタム コンストラクター提供されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|`False`|  
|継承の修飾子|ドメイン クラス \(`none``abstract` または `sealed`\) から生成されるソース・コードのクラスの継承について説明します。|`none`|  
|基本クラス|このドメイン クラスが派生している場合基本クラスの名前。|なし|  
|名前|このドメイン クラスの名前。|現在の名前|  
|名前空間|このドメイン クラスの名前空間。|現在の名前空間|  
|説明|このドメイン クラスに関連付けられている単純に注意してください。|なし|  
|Description|生成されるデザイナーの UI を説明する説明。|なし|  
|\[表示名\]|このドメイン クラスに対して生成されたデザイナーに表示される名前。|なし|  
|ヘルプ キーワード|このドメイン クラスはF1 ヘルプにインデックスを付けるために使用される省略可能なキーワード。|なし|  
  
## 参照  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)