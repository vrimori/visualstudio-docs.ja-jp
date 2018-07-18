---
title: ドメイン クラスのプロパティ
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5d880ac873766c59adfa53e9e61a6ad13520c135
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949024"
---
# <a name="properties-of-domain-classes"></a>ドメイン クラスのプロパティ
ドメイン クラスでは、次の表に、プロパティがあります。 ドメイン クラスについては、次を参照してください。[についてモデル、クラスとリレーションシップ](../modeling/understanding-models-classes-and-relationships.md)です。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)です。

|プロパティ|説明|既定値|
|--------------|-----------------|-------------|
|アクセス修飾子|ドメイン クラスのアクセスのレベル (`public` または `internal`)。|`public`|
|カスタム属性|このドメイン クラスから生成されるソース コードのクラスに属性を追加するために使用します。|\<なし >|
|二重の生成の派生|場合`True`、基底クラスと部分クラス (カスタマイズをサポートする上書きを使用) の両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|`False`|
|カスタム コンス トラクターを持つ|場合`True`、ソース コードでカスタム コンス トラクターが提供されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|`False`|
|継承修飾子|ドメイン クラスから生成されるソース コード クラスの継承の種類を記述します (`none`、`abstract`または`sealed`)。|`none`|
|基本クラス|このドメイン クラスを派生している場合、基本クラスの名前。|\<なし >|
|名前|このドメイン クラスの名前。|現在の名前|
|名前空間|このドメイン クラスの名前空間。|現在の名前空間|
|メモ|このドメイン クラスに関連付けられている非公式なノートです。|\<なし >|
|説明|生成された、デザイナーの UI を文書化に使用される説明です。|\<なし >|
|表示名|このドメイン クラスの生成されたデザイナーで表示される名前です。|\<なし >|
|ヘルプ キーワード|このドメイン クラスの F1 ヘルプをインデックス化に使用される省略可能なキーワードです。|\<なし >|

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)