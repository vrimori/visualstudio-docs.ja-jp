---
title: 'UML シーケンス図: リファレンス |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 94ae423e74e0d78389a196adf1185ebdfa062069
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548411"
---
# <a name="uml-sequence-diagrams-reference"></a>UML シーケンス図: リファレンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UML シーケンス図: リファレンス](https://docs.microsoft.com/visualstudio/modeling/uml-sequence-diagrams-reference)します。  
  
Visual Studio で、*シーケンス図*クラス、コンポーネント、サブシステム、またはアクターのインスタンス間でメッセージのシーケンスを表します相互作用を示しています。 この図は下へ行くほど時間が経過していることを示していて、1 つの参加要素から別の参加要素への制御フローを表しています。 シーケンス図を使用して、クラスとメソッドの代わりに、インスタンスとイベントを視覚化します。 この図では、同じ型の 1 つ以上のインスタンスを表示できます。 また、同じメッセージの 1 つ以上の出現も表示できます。  
  
 UML シーケンス図は UML モデルの一部で、UML モデリング プロジェクト内にのみ存在します。 UML シーケンス図を作成する、**アーキテクチャ** メニューのをクリックして**新しい UML またはレイヤー図**します。 作成および描画する方法について詳しく[UML シーケンス図](../modeling/uml-sequence-diagrams-guidelines.md)または[UML モデリング図](../modeling/edit-uml-models-and-diagrams.md)一般にします。  
  
 この機能をサポートする Visual Studio のバージョンを確認するには、「 [アーキテクチャ ツールとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
## <a name="reading-sequence-diagrams"></a>シーケンス図の読み取り  
 次の表では、シーケンス図に表示される要素について説明します。 詳細については、これらは[要素のプロパティ](../modeling/properties-of-elements-on-uml-sequence-diagrams.md)します。  
  
 ![シーケンス図のパーツ](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**図形**|**要素**|**説明**|  
|---------------|-----------------|---------------------|  
|1|**生存線**|垂直線は、相互作用の発生中に参加要素に発生するイベントのシーケンスを表し、下方向へ行くにつれて、時間が経過することを示します。 この参加要素になり得るのは、クラス、コンポーネント、またはアクターのインスタンスです。|  
|2|**アクター**|開発中のシステムに対して、外部となる参加要素。<br /><br /> アクター記号を設定して、生存線の上部にある表示を行うことができます、**アクター**プロパティ。|  
|3|**同期メッセージ**|送信側は動作を続行する前に、同期メッセージに対する応答を待機します。 この図には、呼び出しと戻り値の両方が表示されます。 同期メッセージは、プログラム内の通常の関数呼び出しと、同じように動作する他の種類のメッセージを表すために使われます。|  
|4|**非同期メッセージ**|送信側が動作を続行するために、応答を必要としないメッセージ。 非同期メッセージは、送信側からの呼び出しのみを示しています。 個別のスレッド間の通信、または新しいスレッドの作成を表すために使われます。|  
|5|**実行発生**|垂直方向に網かけされた四角形が参加要素の生存線に表示されます。これは、参加要素が操作を実行する期間を表します。<br /><br /> 参加要素がメッセージを受信した時点で、実行が開始されます。 開始メッセージが同期メッセージだった場合、実行は送信者に対する «戻り» 矢印で終了します。|  
|6|**コールバック メッセージ**|以前の呼び出しからの戻り値を待機している参加要素に返されるメッセージ。 既存の実行発生の上に、生成された実行発生が表示されます。|  
|7|**自己メッセージします。**|参加要素から自身へのメッセージ。 送信実行の上に、生成された実行発生が表示されます。|  
|8|**メッセージを作成します。**|参加要素を作成するメッセージ。 参加要素が作成メッセージを受信する場合、このメッセージはその要素が受信する最初のメッセージのはずです。|  
|9|**検出されたメッセージ**|不明または指定されていない参加要素からの非同期メッセージ。|  
|10|**消失メッセージ**|不明または指定されていない参加要素への非同期メッセージ。|  
|11|**コメント**|生存線の任意のポイントにコメントを付けることができます。|  
|12|**相互作用使用**|別の図で定義されているメッセージのシーケンスを囲みます。<br /><br /> 作成する、**相互作用使用**ツール をクリックしを含めたい生存線をまたぐからドラッグします。|  
|13|**結合フラグメント**|フラグメントのコレクション。 各フラグメントは、1 つ以上のメッセージを囲むことができます。 結合フラグメントには複数の種類があります。 詳細については、次を参照してください。 [UML シーケンス図のフラグメントを使用した制御フローの記述](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)します。<br /><br /> フラグメントを作成するには、メッセージを右クリックして**ブロックの挿入**フラグメントの種類を順にクリックします。|  
|14|**フラグメント ガード**|フラグメントが発生するかどうかに関連する条件を示すために使用できます。<br /><br /> ガードを設定するには、フラグメントを選択し、ガードを選択して、値を入力します。|  
|**X**|**破棄イベント**|オブジェクトが削除されるか、アクセス不可能になったポイントを表します。 すべての生存線の下部に表示されます。|  
||**相互作用**|シーケンス図に表示されるメッセージと生存線のコレクションです。 相互作用のプロパティを表示することで選択する必要があります**UML モデル エクスプ ローラー**します。|  
||**シーケンス図**|相互作用を表示する図。 相互作用のプロパティを表示するには、図の空白部分をクリックします。 **注:** 、表示、ダイアグラムを含むファイルが異なる場合が相互作用シーケンス図の名前。|  
  
## <a name="see-also"></a>関連項目  
 [UML シーケンス図: ガイドライン](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML モデルおよびダイアグラムを編集します。](../modeling/edit-uml-models-and-diagrams.md)   
 [UML ユース ケース図: リファレンス](../modeling/uml-use-case-diagrams-reference.md)   
 [UML クラス図: リファレンス](../modeling/uml-class-diagrams-reference.md)   
 [UML コンポーネント図: リファレンス](../modeling/uml-component-diagrams-reference.md)   
 [UML コンポーネント図: リファレンス](../modeling/uml-component-diagrams-reference.md)



