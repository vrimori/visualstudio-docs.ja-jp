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
ms.openlocfilehash: 799b5d2feafbf4a0e7b6ff54673983a585b0d2fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876891"
---
# <a name="properties-of-domain-classes"></a>ドメイン クラスのプロパティ
ドメイン クラスでは、次の表に、プロパティがあります。 ドメイン クラスについては、次を参照してください。[理解のモデル、クラスとリレーションシップ](../modeling/understanding-models-classes-and-relationships.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。

|プロパティ|説明|既定値|
|-|-|-|
|アクセス修飾子|ドメイン クラスのアクセスのレベル (`public` または `internal`)。|`public`|
|カスタム属性|このドメイン クラスから生成されるソース コードのクラスに属性を追加するために使用します。|\<なし >|
|Double 型を生成します派生。|場合`True`、基底クラスと (オーバーライドによってカスタマイズをサポート) する部分クラスの両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|`False`|
|カスタム コンス トラクターがあります。|場合`True`、カスタム コンス トラクターは、ソース コードで提供されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|`False`|
|継承修飾子|ドメイン クラスから生成されるソース コードのクラスの継承の種類について説明します (`none`、`abstract`または`sealed`)。|`none`|
|基本クラス|このドメイン クラスが派生の場合、基底クラスの名前。|\<なし >|
|名前|このドメイン クラスの名前。|現在の名前|
|名前空間|このドメイン クラスの名前空間。|現在の名前空間|
|メモ|このドメイン クラスに関連付けられている非公式のメモ。|\<なし >|
|説明|生成されたデザイナーの UI を文書化するために使用する説明。|\<なし >|
|表示名|このドメイン クラスの生成されたデザイナーに表示される名前です。|\<なし >|
|ヘルプ キーワード|このドメイン クラスの F1 ヘルプのインデックスを作成するために使用する省略可能なキーワード。|\<なし >|

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)