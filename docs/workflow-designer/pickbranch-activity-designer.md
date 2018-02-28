---
title: "PickBranch アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: d583c662de31b990982b78d876bc0046e89089d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="pickbranch-activity-designer"></a>PickBranch アクティビティ デザイナー
<xref:System.Activities.Statements.PickBranch> は、受信イベントによってトリガー可能な、<xref:System.Activities.Statements.Pick> アクティビティ内のイベント ベースの実行パスを提供します。  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick.Branches%2A> アクティビティの <xref:System.Activities.Statements.Pick> コレクションに格納されます。 各 <xref:System.Activities.Statements.PickBranch> は <xref:System.Activities.Statements.Pick> アクティビティの分岐に格納され、トリガーの役割を果たす受信イベントに応答して実行できます。 このようにして、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]では、イベント ベースの制御フロー モデリングが提供されます。 各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> および <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Pick アクティビティ デザイナーの使用方法  
 **PickBranch**デザイナーは含まれて、**制御フロー**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブに[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 2 つの空<xref:System.Activities.Statements.PickBranch>を持つオブジェクトの名前を表示する**Branch1**と**Branch2**の要素として既定で作成される、<xref:System.Activities.Statements.Pick>アクティビティと、 **Pick**アクティビティ デザイナーをドロップ最初に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]です。 それぞれ<xref:System.Activities.Statements.PickBranch.DisplayName%2A>でプロパティの値を編集できる、 **PickBranch**デザイナーのヘッダー内、または、**プロパティ**各分岐のウィンドウ。  
  
 2 つの方法を追加する<xref:System.Activities.Statements.PickBranch>オブジェクトのコレクションを<xref:System.Activities.Statements.Pick>オブジェクト: ドラッグ アンド ドロップ、 **PickBranch**からデザイナー、**ツールボックス**からコンテキスト メニューを使用内で、 **Pick**デザイン画面。  
  
1.  **PickBranch**デザイナーを作成、<xref:System.Activities.Statements.PickBranch>からドラッグされたときに、**ツールボックス**の分岐のいずれかにドロップし、 **Pick** 上のアクティビティデザイナー[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面。 新しい <xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick> デザイナー内で、コレクションに含まれている既存の <xref:System.Activities.Statements.PickBranch> 要素の左側または右側に配置できます。 ドラッグしたときに、 **PickBranch**にデザイナー、 **Pick** 、マウスでデザイナー、 **Pick**デザイナーでは、青灰色の縦の帯を使用して、場所を示します、 <xref:System.Activities.Statements.PickBranch>マウスの指定した配置に追加されます。  
  
2.  右クリックして**Pick**アクティビティ デザイナー (内部ではない**PickBranch**デザイナー) を選択し、コンテキスト メニューを**分岐の作成**を追加、新しい<xref:System.Activities.Statements.PickBranch>です。 注意して、新しい<xref:System.Activities.Statements.PickBranch>、既存の右側に追加<xref:System.Activities.Statements.PickBranch>内のオブジェクト、 **Pick**デザイナー。  
  
 **PickBranch**デザイナーを展開すると、**トリガー**と**アクション**ボックスまたは折りたたむをヘッダーの右側にある二重のキャレットをクリックします。 編集、<xref:System.Activities.Statements.PickBranch.Trigger%2A>と<xref:System.Activities.Statements.PickBranch.Action%2A>それぞれの<xref:System.Activities.Statements.PickBranch>にアクティビティをドロップすることによって、**トリガー**と**アクション**そのデザイナーのボックスです。  
  
 <xref:System.Activities.Statements.PickBranch>内のオブジェクト、<xref:System.Activities.Statements.Pick.Branches%2A>のコレクション、<xref:System.Activities.Statements.Pick>オブジェクトをドラッグ アンド ドロップし、内の新しい場所にして並べ替えることができます、 **Pick**デザイナー。 **Pick**デザイナーが青灰色の縦の帯を使用して位置を示す、<xref:System.Activities.Statements.PickBranch>がマウスの指定した配置に追加します。  
  
 <xref:System.Activities.Statements.PickBranch> は 2 とおりの方法で削除できます。  
  
1.  選択、 **PickBranch**デザイナーおよびそれを削除します。  
  
2.  選択、 **PickBranch**デザイナーは、右クリックして、コンテキスト メニューを取得し、選択を**削除**です。  
  
 オンにしてください、 **PickBranch**デザイナー内のアクティビティのいずれかを選択すると、その**トリガー**または**アクション**ボックスが、誤ってこれらの活動の 1 つを削除していません。<xref:System.Activities.Statements.PickBranch>オブジェクト。  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの PickBranch のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.PickBranch> のプロパティと、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]でのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|列の見出しに表示されるフレンドリ名、 **PickBranch**デザイナー。 既定値は Branch です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> を呼び出すことのできる <xref:System.Activities.Statements.PickBranch.Action%2A> アクションが含まれます。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各 <xref:System.Activities.Statements.PickBranch> には、トリガーされたときに実行される <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。|  
  
## <a name="see-also"></a>参照  
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)   
 [Pick アクティビティ](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Pick アクティビティの使用](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)