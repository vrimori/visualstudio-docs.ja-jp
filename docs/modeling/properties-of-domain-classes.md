---
title: "ドメイン クラスのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f6e7310f88b4c5f0855a6851219727ae0dc82d86
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
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
|name|このドメイン クラスの名前。|現在の名前|  
|名前空間|このドメイン クラスの名前空間。|現在の名前空間|  
|メモ|このドメイン クラスに関連付けられている非公式なノートです。|\<なし >|  
|説明|生成された、デザイナーの UI を文書化に使用される説明です。|\<なし >|  
|表示名|このドメイン クラスの生成されたデザイナーで表示される名前です。|\<なし >|  
|ヘルプ キーワード|このドメイン クラスの F1 ヘルプをインデックス化に使用される省略可能なキーワードです。|\<なし >|  
  
## <a name="see-also"></a>参照  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)