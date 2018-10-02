---
title: PickBranch アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9c4e8156fffa975a511d0e6bc54ac139b2e10d81
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546962"
---
# <a name="pickbranch-activity-designer"></a>PickBranch アクティビティ デザイナー
<xref:System.Activities.Statements.PickBranch> は、受信イベントによってトリガー可能な、<xref:System.Activities.Statements.Pick> アクティビティ内のイベント ベースの実行パスを提供します。  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick.Branches%2A> アクティビティの <xref:System.Activities.Statements.Pick> コレクションに格納されます。 各 <xref:System.Activities.Statements.PickBranch> は <xref:System.Activities.Statements.Pick> アクティビティの分岐に格納され、トリガーの役割を果たす受信イベントに応答して実行できます。 このようにして、[!INCLUDE[wfd1](../includes/wfd1-md.md)]では、イベント ベースの制御フロー モデリングが提供されます。 各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> および <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Pick アクティビティ デザイナーの使用方法  
 **PickBranch**で見つかるデザイナー、**制御フロー**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブを[!INCLUDE[wfd2](../includes/wfd2-md.md)](または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 2 つの空<xref:System.Activities.Statements.PickBranch>を持つオブジェクトの名前を表示する**Branch1**と**Branch2**の要素として、既定で作成された、<xref:System.Activities.Statements.Pick>アクティビティと、**選択**アクティビティ デザイナーは先にドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]します。 これらそれぞれ<xref:System.Activities.Statements.PickBranch.DisplayName%2A>でプロパティ値を編集できる、 **PickBranch**デザイナーのヘッダー内、または、**プロパティ**各分岐はウィンドウ。  
  
 追加する 2 つの方法はあります<xref:System.Activities.Statements.PickBranch>オブジェクトのコレクションを<xref:System.Activities.Statements.Pick>オブジェクト: ドラッグ アンド ドロップ、 **PickBranch**からデザイナー、**ツールボックス**からコンテキスト メニューを使用内で、**選択**デザイン画面。  
  
1.  **PickBranch**デザイナーを作成、<xref:System.Activities.Statements.PickBranch>からドラッグされるときに、**ツールボックス**の分岐の 1 つにドロップして、**選択**上のアクティビティデザイナー[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面。 新しい <xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick> デザイナー内で、コレクションに含まれている既存の <xref:System.Activities.Statements.PickBranch> 要素の左側または右側に配置できます。 ドラッグしたときに、 **PickBranch**デザイナー上に、**選択**マウス、デザイナー、**選択**デザイナーでは、青灰色の縦の帯を使用して、場所を示します、 <xref:System.Activities.Statements.PickBranch>位置に追加されます。  
  
2.  右クリックして**選択**アクティビティ デザイナー (内部ではない**PickBranch**デザイナー) を選択し、コンテキスト メニューを**分岐の作成**新しいを追加する<xref:System.Activities.Statements.PickBranch>します。 注意して、新しい<xref:System.Activities.Statements.PickBranch>が既存の右側に追加<xref:System.Activities.Statements.PickBranch>内のオブジェクト、**選択**デザイナー。  
  
 **PickBranch**デザイナーを展開すると、**トリガー**と**アクション**ボックスまたはクリックすると、ヘッダーの右側にある二重のキャレットで折りたたまれています。 編集、<xref:System.Activities.Statements.PickBranch.Trigger%2A>と<xref:System.Activities.Statements.PickBranch.Action%2A>それぞれの<xref:System.Activities.Statements.PickBranch>にアクティビティをドロップすることによって、**トリガー**と**アクション**そのデザイナーのボックスです。  
  
 <xref:System.Activities.Statements.PickBranch>内のオブジェクト、<xref:System.Activities.Statements.Pick.Branches%2A>のコレクションを<xref:System.Activities.Statements.Pick>オブジェクトをドラッグ アンド ドロップし、内の新しい場所にして並べ替えることができる、**選択**デザイナー。 **選択**デザイナーは青灰色の縦の帯で示されます使用して、<xref:System.Activities.Statements.PickBranch>位置が追加されます。  
  
 <xref:System.Activities.Statements.PickBranch> は 2 とおりの方法で削除できます。  
  
1.  選択、 **PickBranch**デザイナーして削除します。  
  
2.  選択、 **PickBranch**デザイナー、右クリックして選択し、コンテキスト メニューを**削除**します。  
  
 オンにしてください、 **PickBranch**デザイナー内のアクティビティのいずれかを選択すると、その**トリガー**または**アクション**ボックスが、誤ってこれらの活動の 1 つを削除および not<xref:System.Activities.Statements.PickBranch>オブジェクト。  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの PickBranch のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.PickBranch> のプロパティと、[!INCLUDE[wfd2](../includes/wfd2-md.md)]でのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|ヘッダーに表示されるフレンドリ名、 **PickBranch**デザイナー。 既定値は Branch です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> を呼び出すことのできる <xref:System.Activities.Statements.PickBranch.Action%2A> アクションが含まれます。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各 <xref:System.Activities.Statements.PickBranch> には、トリガーされたときに実行される <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。|  
  
## <a name="see-also"></a>関連項目  
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)   
 [Pick アクティビティ](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Pick アクティビティの使用](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)