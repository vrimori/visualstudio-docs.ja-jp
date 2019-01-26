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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 38bb141c6011739e56c5e7fee0fe77729f472232
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933363"
---
# <a name="properties-of-swimlanes"></a>スイムレーンのプロパティ
図にスイムレーンを追加できます。 スイムレーンは、ダイアグラムを垂直または水平方向の領域に分割します。 スイムレーン内に表示するには、他の図形を定義することができます。 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。

 スイムレーンの次の表に記載されているプロパティがあります。

|プロパティ|説明|既定値|
|-|-|-|
|本文の塗りつぶしの色|スイムレーンの本体の塗りつぶしの色。|白|
|ヘッダーの塗りつぶしの色|スイムレーンのヘッダーの塗りつぶしの色。|濃い灰色|
|区切り記号の色|区切り線の色。|LightGray|
|区切り線のスタイル|区切り線のスタイル (`Solid`、 `Dash`、 `Dot`、 `DashDot`、 `DashDotDot`、または`Custom`)。|`Dash`|
|区切り記号の太さ|インチ単位の区切り線の太さです。|0.03125|
|テキストの色|このスイムレーンに関連付けられているテキスト デコレーターに使用される色。|黒|
|アクセス修飾子|クラスのアクセスのレベル (`public`または`internal`)。|Public|
|カスタム属性|このスイムレーンから生成されるコード クラスに属性を追加するために使用します。|\<none>|
|Double 型を生成します派生。|場合`True`、基底クラスと (オーバーライドによってカスタマイズをサポート) する部分クラスの両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|False|
|カスタム コンス トラクターがあります。|場合`True`、カスタム コンス トラクターは、ソース コードで提供されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|False|
|継承修飾子|スイムレーンから生成されるソース コードのクラスの継承の種類について説明します (`none`、`abstract`または`sealed`)。|none|
|ベース スイムレーン|このスイムレーンの基本クラス。|(なし)|
|名前|このスイムレーンの名前。|現在の名前|
|名前空間|このスイムレーンに関連付けられた名前空間。|現在の名前空間|
|ツールヒントの種類|ツールヒントを定義する方法 (`fixed`、 `variable`、または`none`)。 場合`fixed`の値、`Fixed Tooltip Text`プロパティを使用します。 場合`variable`、ツールヒントはカスタム コードで定義されています。|\<none>|
|メモ|このスイムレーンに関連付けられている非公式のメモ。|\<none>|
|アラインメント|水平または垂直の配置。|Vertical|
|初期の高さ|インチ単位でこのスイムレーンの初期の高さ。 水平方向のスイムレーンにのみ適用されます。|0|
|初期の幅|インチ単位でこのスイムレーンの初期の幅。 縦方向のスイムレーンにのみ適用されます。|0|
|テキストの色を公開します。|場合`True`ユーザーは、生成されたデザイナーで、スイムレーンの色を設定することができます。 この設定は、スイムレーンのシェイプを右クリックし、クリックして**公開追加**します。|False|
|説明|生成されたデザイナーを文書化するために使用します。|\<none>|
|表示名|このスイムレーン クラスを参照する生成されたデザイナーに表示される名前です。|\<none>|
|固定のツールヒント テキスト|固定のツールヒントに使用されるテキスト。|\<none>|
|ヘルプ キーワード|このスイムレーンの F1 ヘルプのインデックスを作成するために使用するキーワードです。|\<none>|

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)