---
title: "Transition アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/20/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Transition.UI"
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "sdanie"
manager: "erikre"
---
# Transition アクティビティ デザイナー
<xref:System.Activities.Statements.Transition> は、2 つの状態間の遷移を表します。  
  
## Transition アクティビティ デザイナーの使用  
 Transition アクティビティ デザイナーは 2 つの状態間の遷移を構成できるようにします。  
  
### ワークフロー デザイナーでの Transition のプロパティ  
 次の表に、ワークフロー デザイナーを使用して設定できる <xref:System.Activities.Statements.Transition> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|省略可|<xref:System.Activities.Statements.Transition> アクティビティ デザイナーの表示名を指定します。既定値は **T1** です。値は、プロパティ グリッド、展開された Transition デザイナーのヘッダー、および展開された Transition デザイナー内のアクション セクションのヘッダーで編集できます。<xref:System.Activities.Activity.DisplayName%2A> はワーク フロー デザイナーの上部に表示される階層リンク バーで使用されます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|存在する場合、コントロールが対象の状態に渡される前に **True** と評価される必要がある式を指定します。この条件は、プロパティ グリッドおよび展開された Transition デザイナーで編集できます。共有される遷移の複数の条件は Transition デザイナーに表示される順に評価されます。 **Note:**  遷移の <xref:System.Activities.Statements.Transition.Condition%2A> が **False** と評価された場合 \(または共有トリガー遷移のすべての状態が **False** と評価された場合\)、遷移は発生せず、その状態からのすべての遷移のすべてのトリガーは再スケジュールされます。このチュートリアルでは、要件を構成する方法が原因でこの状況は発生しません \(推測値が正しいか間違っているかを判断する特定のアクションがあります\)。|  
|**ソース**|True|この遷移の発生元の状態を示しています。ソースの状態の名前をクリックすると、その状態の展開されたビューにデザイナー ビューを切り替えます。遷移が作成され、変更できない場合、この値が設定されます。|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|完了時に遷移を開始するアクティビティを指定します。このアクティビティを設定するには、**\[ツールボックス\]** からアクティビティをドラッグし、遷移の **\[トリガー\]** セクションにドロップします。|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|トリガー アクティビティが完了し、<xref:System.Activities.Statements.Transition.Condition%2A> \(存在する場合\) が **true** と評価された場合に、実行されるアクティビティを指定します。このアクティビティは、ソース状態の <xref:System.Activities.Statements.State.Exit%2A> アクティビティ \(存在する場合\) が実行された後、対象の状態に遷移するときに実行されます。Transition デザイナーが展開されているとき、この値は **\[ツールボックス\]** からアクティビティをドラッグし、遷移の **\[アクション\]** セクションにドロップして設定できます。1 つの遷移に複数のアクションが存在する場合があります。遷移内に複数のアクションがある場合に表示される上向きの矢印および下向きの矢印をクリックすることで、個々のアクションの展開や折りたたみ、および並べ替えを実行できます。|  
|**Destination**|True|遷移の完了後にステート マシンが遷移する状態を示します。これはオブジェクト モデルの遷移の <xref:System.Activities.Statements.Transition.To%2A> プロパティに対応します。対象の状態の名前をクリックすると、その状態の展開されたビューにデザイナー ビューを切り替えます。この値は遷移が作成されたときに設定され、デザイナーの対象の状態に遷移を接続する矢印をドラッグして、変更できます。|  
  
### 遷移の作成  
 遷移は、ある状態から別の状態へと行をドラッグするか、またはある状態を別の状態にドラッグすると表示される三角形へと状態をドロップすることで作成されます。ドラッグによって遷移を作成するには、ソースの状態の端にマウス ポインターを置き、元の状態から遷移先の状態に行をドラッグします。移行をドロップによって作成するには、遷移先の状態をドラッグし、ソースの状態にマウス ポインターを置き、ソースの状態の周囲に表示される 4 つの三角形の 1 つにドロップします。遷移先の状態は、**ツールボックス**からドラッグされた新しい条件と、ワーク フロー デザイナーからドラッグされている既存の状態のどちらでもかまいません。  
  
> [!NOTE]
>  ステート マシンの単一の状態はワーク フロー デザイナーを使用して作成された最大 76 の遷移を持つことができます。デザイナーを使用せずに作成されるワーク フローの状態の遷移制限は、システム リソースによってのみ制限されます。  
  
 共有されるトリガーの遷移は、同じトリガー イベントを共有する遷移のセットです。共有トリガーは、共通のトリガー イベントを共有する複数の遷移のために構成された式の評価に基づいて、遷移先の状態に条件付き実行ができます。遷移に追加のアクションを追加して共有遷移を作成するには、目的の遷移の開始点を表す円をクリックし、目的の状態にドラッグします。新しい遷移は最初の遷移と同じトリガーを共有しますが、一意の条件とアクションがあります。共有遷移は、Transition デザイナー内から Transition デザイナーの下部にある **\[共有されるトリガーの遷移の追加\]** をクリックし、**\[接続の使用可能な状態\]** ボックスから目的のターゲットの状態を選択することでも作成できます。  
  
## 参照  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [State](../workflow-designer/state-activity-designer.md)