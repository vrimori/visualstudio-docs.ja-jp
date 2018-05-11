---
title: スイムレーンのプロパティ
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: b9ffdf12daa93da9a5f7190866682bc60401dbcc
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-swimlanes"></a>スイムレーンのプロパティ
スイムレーンは、ダイアグラムに追加できます。 スイムレーンはダイアグラムを垂直方向または水平方向の領域に分割します。 スイムレーン内に表示される他の図形を定義することができます。 詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)です。

 スイムレーンには、次の表に記載されているプロパティがあります。

|プロパティ|説明|既定値|
|--------------|-----------------|-------------|
|本文の塗りつぶしの色|スイムレーンの本文の塗りつぶしの色。|白|
|ヘッダーの塗りつぶしの色|ヘッダー、スイムレーンの塗りつぶしの色。|DarkGray|
|区切り記号の色|区切り線の色。|LightGray|
|区切り線のスタイル|区切り線のスタイル (`Solid`、 `Dash`、 `Dot`、 `DashDot`、 `DashDotDot`、または`Custom`)。|`Dash`|
|区切り記号の幅|インチ単位の区切り線の太さ。|0.03125|
|テキストの色|このレーンに関連付けられているテキスト デコレーターのために使用される色。|黒|
|アクセス修飾子|クラスのアクセスのレベル (`public`または`internal`)。|Public|
|カスタム属性|このレーンから生成されるコードのクラスに属性を追加するために使用します。|\<なし >|
|二重の生成の派生|場合`True`、基底クラスと部分クラス (カスタマイズをサポートする上書きを使用) の両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|False|
|カスタム コンス トラクターを持つ|場合`True`、ソース コードでカスタム コンス トラクターが提供されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|False|
|継承修飾子|レーンから生成されるソース コードのクラスの継承の種類を表します (`none`、`abstract`または`sealed`)。|none|
|基本のレーン|このレーンの基本クラス。|(なし)|
|名前|このレーンの名前。|現在の名前|
|名前空間|このレーンに関連付けられた名前空間。|現在の名前空間|
|ツールヒントの種類|ツールヒントを定義する方法 (`fixed`、 `variable`、または`none`)。 場合`fixed`、次の値、`Fixed Tooltip Text`プロパティを使用します。 場合`variable`、ツールヒントがカスタム コードで定義されます。|\<なし >|
|メモ|このレーンに関連付けられている非公式なノートです。|\<なし >|
|アラインメント|水平方向または垂直方向の配置です。|Vertical|
|初期の高さ|インチで、このレーンの初期の高さ。 水平のレーンにのみ適用されます。|0|
|初期の幅|インチで、このレーンの初期の幅。 垂直方向のレーンにのみ適用されます。|0|
|テキストの色を公開します。|場合`True`ユーザーは、生成されたデザイナーで、スイムレーンの色を設定することができます。 設定するこのレーン図形を右クリックし、をクリックして**公開追加**です。|False|
|説明|生成された、デザイナーを文書化するために使用します。|\<なし >|
|表示名|このレーン クラスを参照する、生成されたデザイナーで表示される名前です。|\<なし >|
|固定のツールヒント テキスト|固定のツールヒントに使用されるテキストです。|\<なし >|
|ヘルプ キーワード|このレーンの F1 ヘルプをインデックス化に使用されるキーワード。|\<なし >|

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)