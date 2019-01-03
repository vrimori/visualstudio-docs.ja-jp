---
title: デコレーターのプロパティ
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: fc0f6e3fe8078675792109c41ee75272b44ca714
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865363"
---
# <a name="properties-of-decorators"></a>デコレーターのプロパティ
デコレーターは、アイコン、テキスト、または図形またはコネクタを図に表示される展開/折りたたみの山かっこです。 デコレーターの 3 種類のプロパティを次の表に示します。 一部のプロパティには、シェイプのデコレータでのみ、またはコネクタのデコレーターでのみが表示されます。

 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。

## <a name="expandcollapse-decorator"></a>デコレータの展開/折りたたみ

|プロパティ|説明|既定値|
|-|-|-|
|DisplayName|生成されたデザイナーに表示されるデコレータの名前。|折りたたみデコレータを展開します。|
|名前|デコレータの名前。|ExpandCollapseDecorator|
|メモ|このデコレータに関連付けられている非公式のメモ。|\<なし >|
|HorizontalOffset|(インチ単位)、デコレーターの既定の位置を基準とした水平オフセット。 (図形にのみ。)|0|
|Verticaloffset があります。|(インチ単位)、デコレーターの既定の位置を基準とした垂直オフセット。 (図形にのみ。)|0|
|OffsetFromLine|インチ単位で、既定位置を基準として、コマンドラインからのデコレーターのオフセット。 (コネクタでのみ。)|0|
|OffsetFromShape|インチ単位で、既定位置を基準として、図形からのデコレーターのオフセット。 (コネクタでのみ。)|0|
|位置|デコレーターの既定の位置。|SourceTop|

## <a name="icon-decorator"></a>デコレーターのアイコン

|プロパティ|説明|既定値|
|-|-|-|
|DefaultIcon|表示されるアイコンまたはイメージ ファイルのパス。|\<なし >|
|DisplayName|生成されたデザイナーに表示されるデコレータの名前。|デコレーターのアイコン|
|名前|デコレータの名前。|IconDecorator|
|メモ|デコレータに関連付けられている非公式のメモ。|\<なし >|
|HorizontalOffset|(インチ単位)、デコレーターの既定の位置を基準とした水平オフセット。 (図形にのみ。)|0|
|Verticaloffset があります。|(インチ単位)、デコレーターの既定の位置を基準とした垂直オフセット。 (図形にのみ。)|0|
|OffsetFromLine|インチ単位で、既定位置を基準として、コマンドラインからのデコレーターのオフセット。 (コネクタでのみ。)|0|
|OffsetFromShape|インチ単位で、既定位置を基準として、図形からのデコレーターのオフセット。 (コネクタでのみ。)|0|
|位置|デコレーターの既定の位置。|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|プロパティ|説明|既定値|
|-|-|-|
|DefaultText|表示される既定のテキスト。|group1|
|DisplayName|生成されたデザイナーに表示されるデコレータの名前。|group1|
|FontSize|デコレーターに表示されるテキストのフォント サイズ。|8|
|FontStyle|デコレーターに表示されるテキストのフォント スタイル。|Regular|
|名前|デコレータの名前。|group1|
|メモ|デコレータに関連付けられている非公式のメモ。|\<なし >|
|HorizontalOffset|(インチ単位)、デコレーターの既定の位置を基準とした水平オフセット。 (図形にのみ。)|0|
|Verticaloffset があります。|(インチ単位)、デコレーターの既定の位置を基準とした垂直オフセット。 (図形にのみ。)|0|
|OffsetFromLine|インチ単位で、既定位置を基準として、コマンドラインからのデコレーターのオフセット。 (コネクタでのみ。)|0|
|OffsetFromShape|インチ単位で、既定位置を基準として、図形からのデコレーターのオフセット。 (コネクタでのみ。)|0|
|位置|デコレーターの既定の位置。|TargetBottom|

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)