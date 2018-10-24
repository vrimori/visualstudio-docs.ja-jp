---
title: 'UML クラス図: リファレンス |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: cad1f9d5e0e4cefe6e0fba6ec4e919e78f00dd4e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855860"
---
# <a name="uml-class-diagrams-reference"></a>UML クラス図: リファレンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML クラス図は、アプリケーションが内部的に使用したり、ユーザーとのやり取りにおいて使用したりするオブジェクトおよび情報の構造を記述するものです。 そこで情報を記述する際に、詳細な実装は考慮されません。 クラスおよび関係は、データベース テーブル、XML ノード、ソフトウェア オブジェクトの組み合わせ、といったさまざまな方法で実装できます。  
  
> [!NOTE]
>  このトピックでは、UML クラス図について説明します。 .NET クラス図と呼ばれる別の種類のクラス図もあります。これは、プログラム コードを視覚化するために使用します。 詳細については、次を参照してください。[を表示するクラスと型のデザインおよび](http://go.microsoft.com/fwlink/?LinkId=142231)します。  
  
 UML クラス図を作成する、**アーキテクチャ**] メニューの [選択**新しい UML またはレイヤー図**します。 UML クラス図を描画する方法の詳細については、次を参照してください。 [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)します。 作成し、モデリング図を描画する方法の詳細については、次を参照してください。[編集 UML モデルと図](../modeling/edit-uml-models-and-diagrams.md)します。  
  
 この機能をサポートする Visual Studio のバージョンを確認するには、「 [アーキテクチャ ツールとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
## <a name="reading-class-diagrams"></a>クラス図の見方  
 このセクションでは、UML クラス図に表示される要素について表で説明します。 これらの要素のプロパティについては、次のトピックを参照してください。  
  
- [UML クラス ダイアグラムの型のプロパティ](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
- [UML クラス図の属性のプロパティ](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [UML クラス ダイアグラムの操作のプロパティ](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [UML クラス ダイアグラムの関連のプロパティ](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
  ![3 つのクラスの関係を示すとプロパティ](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
| **図形** |       **要素**        |                                                                                                                                                             **説明**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **クラス**         |                                                           特定の構造上または動作上の特性を共有するオブジェクトの定義。 詳細については、次を参照してください。[クラス ダイアグラムのプロパティの uml 型](../modeling/properties-of-types-on-uml-class-diagrams.md)します。                                                            |
|     1     |        分類子        |                                                                                                             クラス、インターフェイス、または列挙の総称。 コンポーネント、ユース ケース、およびアクターも分類子です。                                                                                                             |
|     2     | 折りたたみ/展開コントロール |                                                                                         分類子の詳細が表示されていない場合は、分類子の左上にあるエキスパンダーをクリックします。 場合によっては、各セグメントの [+] をクリックする必要もあります。                                                                                         |
|     3     |      **属性**       |   分類子の各インスタンスにアタッチされている、型指定された値。<br /><br /> 属性を追加する をクリックして、**属性**セクションし、キーを押します**ENTER**します。 属性のシグネチャを入力します。 詳細については、次を参照してください。 [uml の属性のプロパティにクラス ダイアグラム](../modeling/properties-of-attributes-on-uml-class-diagrams.md)します。   |
|     4     |      **操作**       | 分類子のインスタンスが実行できるメソッドまたは関数。 操作を追加する をクリックして、**操作**セクションし、キーを押します**ENTER**します。 操作のシグネチャを入力します。 詳細については、次を参照してください。 [UML での操作のプロパティにクラス ダイアグラム](../modeling/properties-of-operations-on-uml-class-diagrams.md)します。 |
|     5     |     **関連付け**      |                                                                  2 つの分類子のメンバー間の関係。 詳細については、次を参照してください。 [uml の関連付けのプロパティにクラス ダイアグラム](../modeling/properties-of-associations-on-uml-class-diagrams.md)します。                                                                   |
|    5a     |     **集計**      |                                                                                                    所有権を共有する関係を表す関連付け。 **集計**所有者ロールのプロパティに設定されて**Shared**します。                                                                                                     |
|    5b     |     **コンポジション**      |                                                                                                      「全体 - 部分」の関係を表す関連付け。 **集計**所有者ロールのプロパティに設定されて**複合**します。                                                                                                      |
|     6     |   **関連付けの名前**   |                                                                                                                                         関連付けの名前。 名前は空白にすることができます。                                                                                                                                          |
|     7     |      **ロール名**       |                       ロールの名前。つまり、関連付けの一方の端部の名前。 関連付けられているオブジェクトを参照するために使用できます。 前の図の Order `O` にとっては、`O.ChosenMenu` が、関連付けられている Menu です。<br /><br /> ロールごとに独自のプロパティを持ち、これらは関連付けのプロパティの下に表示されます。                       |
|     8     |     **多重度**     |                                         もう一方の端部の各オブジェクトに対してリンクできる、この端部のオブジェクトの数を示します。 この例では、各 Order を正確に 1 つの Menu にリンクする必要があります。<br /><br /> **\\**\* 可能なリンクの数に上限がないことを意味します。                                         |
|     9     |    **汎化**    |  *特定*分類子から定義の一部の継承、*全般*分類子。 コネクタの矢じり付きの端部にある方が、一般的な分類子です。 属性、関連付け、および操作が、特定の分類子に継承されます。<br /><br /> 使用して、**継承**2 つの分類子間の汎化を作成するためのツール。   |
  
 ![インターフェイスと列挙型を含むパッケージ](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|形式|要素|説明|  
|-----------|-------------|-----------------|  
|10|**Interface**|外部から認識できるオブジェクトの動作の一部の定義。 詳細については、次を参照してください。[クラス ダイアグラムのプロパティの uml 型](../modeling/properties-of-types-on-uml-class-diagrams.md)します。|  
|11|**列挙型**|リテラル値のセットで構成される分類子。|  
|12|**パッケージ**|分類子、関連付け、アクション、生存線、コンポーネント、およびパッケージのグループ。 論理クラス図は、メンバー分類子およびパッケージがパッケージ内に含まれているようすを示します。<br /><br /> 名前はパッケージ内でスコープように**Class1**内**Package1**とは異なる**Class1**パッケージの外部でします。 パッケージの名前の一部として表示されます、**修飾名**プロパティの内容。<br /><br /> 設定することができます、**リンクされたパッケージ**パッケージを参照する任意の UML 図のプロパティ。 この図に作成した要素はすべて、そのパッケージの一部となります。 パッケージの下に表示されるが**UML モデル エクスプ ローラー**します。|  
|13|**Import**|あるパッケージが別のパッケージのすべての定義を含むことを示す、パッケージ間の関係。|  
|14|**依存関係**|矢じり付きの端部側の分類子が変更された場合、これに依存する分類子の定義または実装が変更される可能性があります。|  
  
 ![コネクタとロリポップで示された実現](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|形式|**要素**|説明|  
|-----------|-----------------|-----------------|  
|16|**実現**|クラスは、インターフェイスによって定義される操作および属性を実装します。<br /><br /> 使用して、**継承**クラスとインターフェイスの実現関係を作成するためのツール。|  
|16|**実現**|同じ関係を示す別の表現形式。 ロリポップ シンボルのラベルによってインターフェイスを識別します。<br /><br /> この形式で表現するには、既存の実現関係を選択します。 関連付けの近くにアクション タグが表示されます。 アクション タグをクリックし、クリックして**ロリポップとして表示**します。|  
  
## <a name="see-also"></a>関連項目  
 [UML モデルおよびダイアグラムを編集します。](../modeling/edit-uml-models-and-diagrams.md)   
 [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)   
 [UML クラス ダイアグラムで型のプロパティ](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML クラス図の属性のプロパティ](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML クラス図の操作のプロパティ](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML クラス ダイアグラムの関連のプロパティ](../modeling/properties-of-associations-on-uml-class-diagrams.md)



