---
title: クラス ダイアグラムの uml 型のプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: de4bcd2779e448c48bd8ac6e66edf25ef4edddc5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193168"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>UML クラス ダイアグラムの型のプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML クラス図で、*型*がクラス、インターフェイス、または列挙体。  
  
> [!NOTE]
>  このトピックでは、UML クラス図における型のプロパティについて説明します。 詳細については、次のトピックを参照してください。  
  
-   [UML クラス図: リファレンス](../modeling/uml-class-diagrams-reference.md)  
  
-   [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)  
  
-   [UML クラス図の属性のプロパティ](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [UML クラス ダイアグラムの操作のプロパティ](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
-   [UML クラス ダイアグラムの関連のプロパティ](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>プロパティ  
 クラス、インターフェイス、または列挙のプロパティを次に示します。  
  
 型のプロパティを表示するには、ダイアグラムまたは型を右クリックして**UML モデル エクスプ ローラー**、 をクリックし、**プロパティ**します。 プロパティが表示されます、**プロパティ**ウィンドウ。  
  
|**Property**|**既定値**|表示の対象|説明|  
|------------------|-----------------|----------------|-----------------|  
|**Name**|既定名|すべての要素|要素を指定します。|  
|**修飾名**|格納元のパッケージ :: 型名|すべての要素|要素を一意に識別します。 要素を格納するパッケージの修飾名が先頭につきます。|  
|**色**|型の種類の既定値|すべての要素|この図形の色。 他のプロパティとは異なり、これは基になるモデル要素のプロパティではありません。 同じ型の異なるビューで異なる色を表示できます。|  
|**抽象型**|False|クラス|true の場合、クラスはインスタンス化できず、基本クラスとして使用されることになります。|  
|**リーフには**|False|クラス、インターフェイス|true の場合、型は派生型を持たないことになります。|  
|**アクティブ**|False|クラス|true の場合、この型の各インスタンスはコントロールのスレッドに関連付けられます。|  
|**可視性**|Public|クラス、インターフェイス、列挙|-Public-グローバルに参照できます。<br />-Private - このタイプは、それを所有するパッケージ内で参照できます。<br />-Package - パッケージ内で参照できます。|  
|**作業項目**|関連付けなし|すべての要素|この要素に関連付けられている作業項目の数。 作業項目に関連付けるを参照してください。[モデル要素をリンクし、作業項目](../modeling/link-model-elements-and-work-items.md)します。|  
|**説明**|(空白)|すべての要素|ここに、項目に関する一般的なメモを作成できます。|  
|**テンプレートのバインド**|(なし)|クラス、インターフェイス、列挙|空でない場合、この型はこのテンプレート クラスに対するバインディング パラメーター値によって定義されます。 プロパティを展開すると、テンプレート パラメーターのバインディングが表示されます。|  
|**テンプレート パラメーター**|(なし)|クラス、インターフェイス、列挙|空でない場合、これは、ここに一覧表示されているパラメーターを持つテンプレート クラスです。 クリックしてパラメーターを追加または個々 のパラメーターのプロパティを表示、 **[...]**.|  
  
## <a name="see-also"></a>関連項目  
 [UML クラス図の属性のプロパティ](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML クラス図の操作のプロパティ](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML クラス図の関連付けのプロパティ](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)



