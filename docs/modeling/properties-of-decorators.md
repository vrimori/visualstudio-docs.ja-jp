---
title: "デコレーターのプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, デコレーター"
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# デコレーターのプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

デコレータアイコンテキストまたは図のシェイプまたはコネクタに表示できる縮小シェブロン展開します。  次の表はデコレータの 3 種類のプロパティが表示されます。  プロパティの一部はシェイプまたはコネクタにデコレータ デコレータにのみ表示されます。  
  
 詳細については、「[方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)」を参照してください。  これらのプロパティを使用する方法の詳細については[ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md) を参照してください。  
  
## デコレータ折りたたみ \/ 展開します。  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|DisplayName|生成されたデザイナーに表示されるデコレータの名前。|折りたたみデコレータを展開します。|  
|名前|デコレータの名前。|ExpandCollapseDecorator|  
|説明|このデコレータに関連付けられている単純に注意してください。|なし|  
|HorizontalOffset|インチ デコレータの既定の場所に関連する水平オフセット。  図形 \(のみ\)|0|  
|VerticalOffset|インチ デコレータの既定の場所に関連する垂直オフセット。  図形 \(のみ\)|0|  
|OffsetFromLine|行からデコレータのオフセット \(インチの既定の位置を基準にします。  コネクタ \(のみ\)|0|  
|OffsetFromShape|図形からデコレータのオフセット \(インチの既定の位置を基準にします。  コネクタ \(のみ\)|0|  
|\[位置\]|デコレータの既定の場所です。|SourceTop|  
  
## デコレータ アイコン  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|DefaultIcon|表示されるアイコンまたはイメージ ファイルのパス。|なし|  
|DisplayName|生成されたデザイナーに表示するデコレータの名前。|デコレータ アイコン|  
|名前|デコレータの名前。|IconDecorator|  
|説明|デコレータに関連付けられている単純に注意してください。|なし|  
|HorizontalOffset|インチ デコレータの既定の場所に関連する水平オフセット。  図形 \(のみ\)|0|  
|VerticalOffset|インチ デコレータの既定の場所に関連する垂直オフセット。  図形 \(のみ\)|0|  
|OffsetFromLine|行からデコレータのオフセット \(インチの既定の位置を基準にします。  コネクタ \(のみ\)|0|  
|OffsetFromShape|図形からデコレータのオフセット \(インチの既定の位置を基準にします。  コネクタ \(のみ\)|0|  
|\[位置\]|デコレータの既定の場所です。|SourceTop|  
  
## TextDecorator  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|DefaultText|表示される既定のテキスト。|Label|  
|DisplayName|生成されたデザイナーに表示するデコレータの名前。|Label|  
|FontSize|デコレータに表示されるテキストのフォント サイズ。|8|  
|FontStyle|デコレータに表示されるテキストのフォント スタイル。|Regular|  
|名前|デコレータの名前。|Label|  
|説明|デコレータに関連付けられている単純に注意してください。|なし|  
|HorizontalOffset|インチ デコレータの既定の場所に関連する水平オフセット。  図形 \(のみ\)|0|  
|VerticalOffset|インチ デコレータの既定の場所に関連する垂直オフセット。  図形 \(のみ\)|0|  
|OffsetFromLine|行からデコレータのオフセット \(インチの既定の位置を基準にします。  コネクタ \(のみ\)|0|  
|OffsetFromShape|図形からデコレータのオフセット \(インチの既定の位置を基準にします。  コネクタ \(のみ\)|0|  
|\[位置\]|デコレータの既定の場所です。|TargetBottom|  
  
## 参照  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)