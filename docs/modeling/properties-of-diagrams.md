---
title: "ダイアグラムのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c00ec651510da84594c370e312112c50bc545606
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-diagrams"></a>図のプロパティ
生成されたデザイナーのダイアグラムがどのように表示されるかを指定するプロパティを設定することができます。 たとえば、ダイアグラムのテキストの既定の色を指定できます。  
  
 詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)です。  
  
 次の表は、ダイアグラムのプロパティを一覧表示します。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|[塗りつぶしの色]|ダイアグラムの塗りつぶしの色。|白|  
|テキストの色|ダイアグラムで表示されるテキストの色。|黒|  
|アクセス修飾子|クラス (パブリックまたは内部) のアクセス修飾子。|Public|  
|カスタム属性|生成されたコードのクラスに属性を追加するために使用します。|\<なし >|  
|二重の生成の派生|場合`True`、基底クラスと部分クラス (カスタマイズをサポートする上書きを使用) の両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|False|  
|カスタム コンス トラクターを持つ|場合`True`、ソース コードでカスタム コンス トラクターが提供されます。 詳細については、次を参照してください[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md).。|False|  
|継承修飾子|ダイアグラムから生成されるソース コード クラスの継承の種類を記述します (`none`、`abstract`または`sealed`)。|なし|  
|基本のダイアグラム|この図の基本クラス。|(なし)|  
|name|このダイアグラムの名前。|現在の名前|  
|名前空間|このダイアグラムに関連付けられた名前空間。|現在の名前空間|  
|表されるクラス|このダイアグラムを表すルート ドメイン クラスです。|該当する場合、現在のルート クラス|  
|メモ|この要素に関連付けられている非公式なノートです。|\<なし >|  
|プロパティとして公開塗りつぶしの色|場合`True`ユーザーは、生成されたデザイナーのダイアグラムの塗りつぶしの色を設定できます。 これを設定するダイアグラムの図形を右クリックし、をクリックして**追加 Explosed**です。|False|  
|テキストの色をプロパティとして公開します。|場合`True`ユーザーは、生成されたデザイナーで、ダイアグラムのテキストの色を設定することができます。 これを設定するダイアグラムの図形を右クリックし、をクリックして**追加 Explosed**です。|False|  
|説明|生成された、デザイナーを文書化に使用される説明です。|\<なし >|  
|表示名|このダイアグラムの生成されたデザイナーで表示される名前です。|\<なし >|  
|ヘルプ キーワード|このダイアグラムの F1 ヘルプをインデックス化に使用されるキーワード。|\<なし >|  
  
## <a name="see-also"></a>参照  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)