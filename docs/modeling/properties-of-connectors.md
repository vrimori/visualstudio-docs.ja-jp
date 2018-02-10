---
title: "コネクタのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 858ce6fd3d53cd580a2aaac1b6b5c160dffac517
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-connectors"></a>コネクタのプロパティ
コネクタは、生成されたデザイナーでのドメインの関係を表します。  
  
 詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)です。  
  
 コネクタでは、次の表に記載されているプロパティがあります。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|色|このコネクタの色。|黒|  
|破線スタイル|(実線、破線、ドット、DashDot、DashDotDot、またはカスタム) は、このコネクタの線のダッシュのスタイル。|[実線]|  
|ソース終了スタイル|(HollowArrow、EmptyArrow、FilledArrow、EmptyDiamond、FilledDiamond、または None) は、このコネクタのソース エンドのスタイルです。|なし|  
|ターゲット エンドのスタイル|(HollowArrow、EmptyArrow、FilledArrow、EmptyDiamond、FilledDiamond、または None) は、このコネクタのターゲット エンドのスタイルです。|なし|  
|テキストの色|このコネクタに関連付けられているテキスト デコレーターのために使用される色。|黒|  
|太さ|このコネクタの線の太さは、インチ単位で測定されます。|0.03125|  
|アクセス修飾子|クラスのアクセスのレベル (`public`または`internal`)。|Public|  
|カスタム属性|このコネクタから生成されるソース コードのクラスに属性を追加するために使用します。|\<なし >|  
|二重の生成の派生|場合`True`、基底クラスと部分クラス (カスタマイズをサポートする上書きを使用) の両方が生成されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|False|  
|カスタム コンス トラクターを持つ|場合`True`、ソース コードでカスタム コンス トラクターが提供されます。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)です。|False|  
|継承修飾子|コネクタから生成されるソース コード クラスの継承の種類を記述します (`none`、`abstract`または`sealed`)。|none|  
|基本のコネクタ|このコネクタの基本クラス。|(なし)|  
|name|このコネクタの名前。|現在の名前|  
|名前空間|このコネクタに関連付けられた名前空間。|現在の名前空間|  
|ツールヒントの種類|(固定、変数、またはなし)、ツールヒントを定義する方法です。 固定されている場合、次の値、`Fixed Tooltip Text`プロパティは、ツールヒントとして使用以外の場合は、変数、ツール ヒントがカスタム コードで定義します。|\<なし >|  
|メモ|このコネクタに関連付けられている非公式なノートです。|\<なし >|  
|ルーティング スタイル|コネクタをルーティングに使用されるスタイルです。 A`Rectilinear`コネクタにより、要求された直角のターン、`Straight`コネクタはありません。|直角|  
|プロパティとして公開されている色<br /><br /> プロパティとして公開される破線スタイル<br /><br /> プロパティとして公開されている幅<br /><br /> テキストの色を公開します。|場合`True`図形の指定されたプロパティを設定できます。 この設定は、図形の定義を右クリックし、クリックして**公開追加**です。|False|  
|説明|生成された、デザイナーを文書化するために使用します。|\<なし >|  
|表示名|このコネクタについて生成されたデザイナーで表示される名前です。|\<なし >|  
|固定のツールヒント テキスト|固定のツールヒントに使用されるテキストです。|\<なし >|  
|ヘルプ キーワード|この要素の F1 ヘルプをインデックス化に使用されるキーワード。|\<なし >|  
  
## <a name="see-also"></a>参照  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)