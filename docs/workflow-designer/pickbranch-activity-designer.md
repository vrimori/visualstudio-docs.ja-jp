---
title: "PickBranch アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# PickBranch アクティビティ デザイナー
<xref:System.Activities.Statements.PickBranch> は、受信イベントによってトリガー可能な、<xref:System.Activities.Statements.Pick> アクティビティ内のイベント ベースの実行パスを提供します。  
  
## PickBranch  
 <xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick> アクティビティの <xref:System.Activities.Statements.Pick.Branches%2A> コレクションに格納されます。各 <xref:System.Activities.Statements.PickBranch> は <xref:System.Activities.Statements.Pick> アクティビティの分岐に格納され、トリガーの役割を果たす受信イベントに応答して実行できます。このようにして、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]では、イベント ベースの制御フロー モデリングが提供されます。各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> および <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。  
  
### Pick アクティビティ デザイナーの使用方法  
 **PickBranch** デザイナーは、**\[ツールボックス\]** の **\[制御フロー\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Pick** アクティビティ デザイナーを初めて[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]にドロップすると、既定では、2 つの空の <xref:System.Activities.Statements.PickBranch> オブジェクト \(それぞれの表示名は "**Branch1**" および "**Branch2**"\) が <xref:System.Activities.Statements.Pick> アクティビティの要素として作成されます。それぞれの <xref:System.Activities.Statements.PickBranch.DisplayName%2A> プロパティの値は、**PickBranch** デザイナーのヘッダー内、または各分岐の **\[プロパティ\]** ウィンドウ内で編集できます。  
  
 <xref:System.Activities.Statements.PickBranch> オブジェクトを <xref:System.Activities.Statements.Pick> オブジェクトのコレクションに追加する方法は 2 つあります。**\[ツールボックス\]** から **PickBranch** デザイナーをドラッグ アンド ドロップする方法と、**Pick** デザイン サーフェイス内からコンテキスト メニューを使用する方法です。  
  
1.  **PickBranch** デザイナーを**\[ツールボックス\]** からドラッグし、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の画面上にある **Pick** アクティビティ デザイナーの分岐のいずれかにドロップすると、<xref:System.Activities.Statements.PickBranch> が作成されます。新しい <xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick> デザイナー内で、コレクションに含まれている既存の <xref:System.Activities.Statements.PickBranch> 要素の左側または右側に配置できます。マウスを使用して **PickBranch** デザイナーを **Pick** デザイナー上にドラッグすると、**Pick** デザイナーには、マウス操作で追加された <xref:System.Activities.Statements.PickBranch> の位置が青灰色の縦の帯で示されます。  
  
2.  **Pick** アクティビティ デザイナー \(**PickBranch** デザイナーの内部ではない\) を右クリックし、コンテキスト メニューの **\[分岐の作成\]** をクリックして、新しい <xref:System.Activities.Statements.PickBranch> を追加します。**Pick** デザイナー内の既存の <xref:System.Activities.Statements.PickBranch> オブジェクトの右側に新しい <xref:System.Activities.Statements.PickBranch> が追加されます。  
  
 **PickBranch** デザイナーを展開すると、**\[トリガー\]** ボックスと **\[アクション\]** ボックスを表示できます。このデザイナーを折りたたむには、ヘッダーの右側にある二重のキャレットをクリックします。アクティビティを、そのデザイナーの **\[トリガー\]** ボックスと **\[アクション\]** ボックスにドロップして、各 <xref:System.Activities.Statements.PickBranch> の <xref:System.Activities.Statements.PickBranch.Trigger%2A> と <xref:System.Activities.Statements.PickBranch.Action%2A> を編集します。  
  
 <xref:System.Activities.Statements.Pick> オブジェクトの <xref:System.Activities.Statements.Pick.Branches%2A> コレクションに含まれる <xref:System.Activities.Statements.PickBranch> オブジェクトを並べ替えるには、**Pick** デザイナー内の新しい位置にドラッグ アンド ドロップします。**Pick** デザイナーには、マウス操作で追加された <xref:System.Activities.Statements.PickBranch> の位置が青灰色の縦の帯で示されます。  
  
 <xref:System.Activities.Statements.PickBranch> は 2 とおりの方法で削除できます。  
  
1.  **PickBranch** デザイナーを選択して削除します。  
  
2.  **PickBranch** デザイナーを選択して右クリックし、コンテキスト メニューの **\[削除\]** をクリックします。  
  
 **PickBranch** デザイナーは必ず選択してください。誤って、**\[トリガー\]** ボックスまたは **\[アクション\]** ボックス内のいずれかのアクティビティを選択すると、<xref:System.Activities.Statements.PickBranch> オブジェクトではなく、これらのボックス内のアクティビティのいずれかが削除されます。  
  
### ワークフロー デザイナーでの PickBranch のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.PickBranch> のプロパティと、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]でのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|------------|--------|----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|省略可|**PickBranch** デザイナーのヘッダーに表示される表示名。既定値は Branch です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Action%2A> を呼び出すことのできる <xref:System.Activities.Statements.PickBranch.Trigger%2A> アクションが含まれます。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各 <xref:System.Activities.Statements.PickBranch> には、トリガーされたときに実行される <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。|  
  
## 参照  
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)   
 [Pick アクティビティ](../Topic/Pick%20Activity.md)   
 [Pick アクティビティの使用](../Topic/Using%20the%20Pick%20Activity.md)