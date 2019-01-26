---
title: 図のプロパティ
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: cf3405d74a1545bb86b1297b766faf46e68223a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942049"
---
# <a name="properties-of-diagrams"></a>図のプロパティ
生成されたデザイナーでのダイアグラムの表示方法を指定するプロパティを設定することができます。 たとえば、図でテキストの既定の色を指定できます。

 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[カスタマイズし、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)します。

 次の表は、図のプロパティを一覧表示します。

|プロパティ|説明|既定値|
|-|-|-|
|[塗りつぶしの色]|ダイアグラムの塗りつぶしの色。|白|
|テキストの色|ダイアグラムで表示されるテキストの色。|黒|
|アクセス修飾子|(パブリックまたは内部) クラスのアクセス修飾子。|Public|
|カスタム属性|生成されたコード クラスに属性を追加するために使用します。|\<none>|
|Double 型を生成します派生。|場合`True`、基底クラスと (オーバーライドによってカスタマイズをサポート) する部分クラスの両方が生成されます。 詳細については、次を参照してください。[をオーバーライドし、生成されたクラスを拡張](../modeling/overriding-and-extending-the-generated-classes.md)します。|False|
|カスタム コンス トラクターがあります。|場合`True`、カスタム コンス トラクターは、ソース コードで提供されます。 詳細については、次を参照してください[をオーバーライドし、生成されたクラスを拡張](../modeling/overriding-and-extending-the-generated-classes.md).。|False|
|継承修飾子|ダイアグラムから生成されるソース コードのクラスの継承の種類について説明します (`none`、 `abstract`、または`sealed`)。|なし|
|基本ダイアグラム|この図の基本クラス。|(なし)|
|名前|このダイアグラムの名前。|現在の名前|
|名前空間|この図に関連付けられた名前空間。|現在の名前空間|
|表されるクラス|この図を表すルート ドメイン クラス。|該当する場合、現在のルート クラス|
|メモ|この要素に関連付けられている非公式のメモ。|\<none>|
|プロパティとして公開塗りつぶしの色|場合`True`ユーザーは、生成されたデザイナーのダイアグラムの塗りつぶしの色を設定できます。 このプロパティを設定するには、ダイアグラムの図形を右クリックし、クリックして**公開追加**します。|False|
|テキストの色をプロパティとして公開します|場合`True`ユーザーは、生成されたデザイナーで、ダイアグラムのテキストの色を設定することができます。 このプロパティを設定するには、ダイアグラムの図形を右クリックし、クリックして**公開追加**します。|False|
|説明|生成されたデザイナーのドキュメントに使用される説明です。|\<none>|
|表示名|このダイアグラムの生成されたデザイナーに表示される名前です。|\<none>|
|ヘルプ キーワード|このダイアグラムの F1 ヘルプのインデックスを作成するために使用するキーワードです。|\<none>|

## <a name="see-also"></a>関連項目

[ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
