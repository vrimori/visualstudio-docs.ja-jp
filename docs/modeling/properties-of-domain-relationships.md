---
title: "ドメイン リレーションシップのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f81f4bca6d268cd9fd32a6edf44cbde40d7c357
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-domain-relationships"></a>ドメイン リレーションシップのプロパティ
次の表に、プロパティは、ドメイン リレーションシップに関連付けられます。 ドメイン リレーションシップについては、次を参照してください。[についてモデル、クラスとリレーションシップ](../modeling/understanding-models-classes-and-relationships.md)です。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)です。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|アクセス修飾子|ドメイン リレーションシップのアクセスのレベル (`public`または`internal`)。|`public`|  
|カスタム属性|ドメイン リレーションシップから生成されるソース コードのクラスに属性を追加するために使用します。|\<なし >|  
|二重の生成の派生|場合`True`、基底クラスと部分クラス (カスタマイズをサポートする上書きを使用) の両方を生成します。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|`False`|  
|カスタム コンス トラクターを持つ|場合`True`、ソース コードでカスタム コンス トラクターが指定されていることを示します。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|`False`|  
|継承修飾子|ドメイン リレーションシップから生成されるソース コード クラスの継承の種類を記述します (`none`、`abstract`または`sealed`)。|\<なし >|  
|重複を許可します。|場合`True`、ドメイン リレーションシップの重複したリンクは、同じ 2 つの要素の間で作成可能性があります。|`False`|  
|基本リレーションシップ|ドメインの関係を派生している場合、ドメイン リレーションシップの関係の基本。|\<なし >|  
|埋め込みは|場合`True`ドメインは、埋め込みの関係。 場合`False`リレーションシップが参照関係です。|\<両方 >|  
|name|ドメイン リレーションシップの名前です。|現在の名前|  
|名前空間|ドメインの関係に関連付けられた名前空間。|現在の名前空間|  
|メモ|ドメインの関係に関連付けられている非公式なノートです。|\<なし >|  
|説明|コードを文書化するために使用され、生成されたデザイナーの UI で使用される、説明します。|\<なし >|  
|表示名|ドメインの関係の生成されたデザイナーで表示される名前です。|\<なし >|  
|ヘルプ キーワード|ドメインの関係の F1 ヘルプをインデックス化に使用される省略可能なキーワードです。|\<なし >|  
  
## <a name="see-also"></a>参照  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)