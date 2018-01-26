---
title: "プロパティ デコレーターの |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b3f1c171f86c9af82e532abf948ee6199a16d0e1
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-decorators"></a>デコレーターのプロパティ
デコレーターは、アイコン、テキスト、または図形またはコネクタ図上に表示される可能性が展開/折りたたみの山かっこです。 次の表は、デコレーターの 3 種類のプロパティを表示します。 一部のプロパティには、図形デコレーターでのみ、またはコネクタ デコレーターでのみが表示されます。  
  
 詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)です。  
  
## <a name="expandcollapse-decorator"></a>デコレーターの展開/折りたたみ  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|DisplayName|生成されたデザイナーで表示されるデコレーターの名前です。|折りたたみデコレーターを展開します。|  
|name|デコレータの名前。|ExpandCollapseDecorator|  
|メモ|このデコレータに関連付けられている非公式なノートです。|\<なし >|  
|HorizontalOffset|水平方向のオフセットをインチで、デコレーターの既定の位置に対して相対的です。 (図形上のみです。)|0|  
|VerticalOffset|垂直方向のオフセットをインチで、デコレーターの既定の位置に対して相対的です。 (図形上のみです。)|0|  
|OffsetFromLine|デコレータ インチで、既定の位置に対して、行からのオフセット。 (コネクタののみ。)|0|  
|OffsetFromShape|デコレータ インチで、既定の位置に対しての形状からのオフセット。 (コネクタののみ。)|0|  
|位置|デコレータの既定の位置。|SourceTop|  
  
## <a name="icon-decorator"></a>アイコンの Decorator  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|DefaultIcon|表示されるアイコンまたはイメージ ファイルのパス。|\<なし >|  
|DisplayName|生成された、デザイナーに表示されるデコレーターの名前です。|アイコンの Decorator|  
|name|デコレータの名前。|IconDecorator|  
|メモ|デコレータに関連付けられている非公式なノートです。|\<なし >|  
|HorizontalOffset|水平方向のオフセットをインチで、デコレーターの既定の位置に対して相対的です。 (図形上のみです。)|0|  
|VerticalOffset|垂直方向のオフセットをインチで、デコレーターの既定の位置に対して相対的です。 (図形上のみです。)|0|  
|OffsetFromLine|デコレータ インチで、既定の位置に対して、行からのオフセット。 (コネクタののみ。)|0|  
|OffsetFromShape|デコレータ インチで、既定の位置に対しての形状からのオフセット。 (コネクタののみ。)|0|  
|位置|デコレータの既定の位置。|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|DefaultText|表示される既定のテキスト。|group1|  
|DisplayName|生成された、デザイナーに表示されるデコレーターの名前です。|group1|  
|FontSize|デコレータに表示されるテキストのフォント サイズ。|8|  
|FontStyle|デコレータに表示されるテキストのフォント スタイル。|Regular|  
|name|デコレータの名前。|group1|  
|メモ|デコレータに関連付けられている非公式なノートです。|\<なし >|  
|HorizontalOffset|水平方向のオフセットをインチで、デコレーターの既定の位置に対して相対的です。 (図形上のみです。)|0|  
|VerticalOffset|垂直方向のオフセットをインチで、デコレーターの既定の位置に対して相対的です。 (図形上のみです。)|0|  
|OffsetFromLine|デコレータ インチで、既定の位置に対して、行からのオフセット。 (コネクタののみ。)|0|  
|OffsetFromShape|デコレータ インチで、既定の位置に対しての形状からのオフセット。 (コネクタののみ。)|0|  
|位置|デコレータの既定の位置。|TargetBottom|  
  
## <a name="see-also"></a>参照  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)