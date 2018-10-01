---
title: ドメイン リレーションシップのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ff37703643dc9d1c795fe10b5f24154ee46174af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534352"
---
# <a name="properties-of-domain-relationships"></a>ドメイン リレーションシップのプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ドメイン リレーションシップのプロパティの](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-relationships)します。  
  
次の表に、プロパティは、ドメイン リレーションシップに関連付けられます。 ドメイン リレーションシップについては、次を参照してください。[理解のモデル、クラスとリレーションシップ](../modeling/understanding-models-classes-and-relationships.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|アクセス修飾子|ドメイン リレーションシップのアクセスのレベル (`public`または`internal`)。|`public`|  
|カスタム属性|ドメイン リレーションシップから生成されるソース コードのクラスに属性を追加するために使用します。|\<なし >|  
|Double 型を生成します派生。|場合`True`、基底クラスと (オーバーライドによってカスタマイズをサポート) する部分クラスの両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|`False`|  
|カスタム コンス トラクターがあります。|場合`True`、カスタム コンス トラクターがソース コードで提供されることを示します。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。|`False`|  
|継承修飾子|ドメイン リレーションシップから生成されるソース コードのクラスの継承の種類について説明します (`none`、`abstract`または`sealed`)。|\<なし >|  
|重複を許可します。|場合`True`、同じ 2 つの要素間、ドメイン リレーションシップの重複リンクが作成されます。|`False`|  
|基本リレーションシップ|ドメイン リレーションシップを派生の場合、ドメイン リレーションシップのベース リレーションシップ。|\<なし >|  
|埋め込みは|場合`True`、ドメイン リレーションシップが埋め込みリレーションシップ。 場合`False`リレーションシップの参照リレーションシップです。|\<both>|  
|名前|ドメイン リレーションシップの名前。|現在の名前|  
|名前空間|ドメイン リレーションシップに関連付けられた名前空間。|現在の名前空間|  
|メモ|ドメイン リレーションシップに関連付けられている非公式のメモ。|\<なし >|  
|説明|コードを文書化するために使用しては、生成されたデザイナーの UI で使用する説明。|\<なし >|  
|表示名|ドメイン リレーションシップに対して生成されたデザイナーに表示される名前です。|\<なし >|  
|ヘルプ キーワード|ドメイン リレーションシップの F1 ヘルプのインデックスを作成するために使用する省略可能なキーワード。|\<なし >|  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



