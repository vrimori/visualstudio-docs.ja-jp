---
title: アクティビティ デザイナーの移行 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 4f699cb378ceb8ee9b236c2d2e8b47b3d7f40944
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284519"
---
# <a name="transition-activity-designer"></a>Transition アクティビティ デザイナー
<xref:System.Activities.Statements.Transition> は、2 つの状態間の遷移を表します。  
  
## <a name="using-the-transition-activity-designer"></a>Transition アクティビティ デザイナーの使用  
 Transition アクティビティ デザイナーを使用すると、2 つの状態間の遷移を構成できます。  
  
### <a name="transition-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Transition のプロパティ  
 次の表に、ワークフロー デザイナーを使用して設定できる <xref:System.Activities.Statements.Transition> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|<xref:System.Activities.Statements.Transition> アクティビティ デザイナーの表示名を指定します。 既定値は**T1**します。 値は、プロパティ グリッド、展開された Transition デザイナーのヘッダー、および展開された Transition デザイナー内のアクション セクションのヘッダーで編集できます。 <xref:System.Activities.Activity.DisplayName%2A> は、ワークフロー デザイナーの上部に表示される階層リンク バーで使用されます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|存在する場合に評価される式を指定します。 **True**前に、先の状態に制御が渡されます。 この条件は、プロパティ グリッドおよび展開された Transition デザイナーで編集できます。 共有遷移に含まれる複数の条件は、Transition デザイナーに表示される順に評価されます。 **注:** されている場合、<xref:System.Activities.Statements.Transition.Condition%2A>に評価される、切り替え効果の**False** (に評価されるすべての共有トリガー遷移の条件または**False**)、移行は行われませんすべての遷移状態からのすべてのトリガーを再スケジュールされます。 このチュートリアルでは、条件の構成方法 (推定値が正しいか間違っているかを判断する特定のアクションが用意されています) により、この状況は発生しません。|  
|**ソース**|True|この遷移の発生元の状態を示します。 元の状態の名前をクリックすると、デザイナー ビューはその状態の展開ビューに切り替わります。 この値は、遷移が作成されていて、変更できない場合に設定されます。|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|完了時に遷移を開始するアクティビティを指定します。 このアクティビティを設定するからアクティビティをドラッグ、**ツールボックス**にドロップし、**トリガー**遷移のセクション。|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|トリガー アクティビティが完了したときに実行されるアクティビティを指定します、<xref:System.Activities.Statements.Transition.Condition%2A>がある場合に評価される**true**します。 このアクティビティは、元の状態の <xref:System.Activities.Statements.State.Exit%2A> アクティビティ (存在する場合) が実行された後、遷移先の状態に遷移するときに実行されます。 アクティビティをドラッグして、この値を設定することができます、transition デザイナーが展開されている場合、**ツールボックス**にドロップし、**アクション**遷移のセクション。 1 つの遷移に対して複数のアクションが存在する場合があります。 遷移内に複数のアクションがある場合は、アクションに表示される上向き矢印または下向き矢印をクリックすることで、個々のアクションの展開と折りたたみ、および並べ替えを実行できます。|  
|**変換先**|True|遷移の完了後にステート マシンが遷移した状態を示します。 これは、オブジェクト モデルにおける遷移の <xref:System.Activities.Statements.Transition.To%2A> プロパティに対応します。 遷移先の状態の名前をクリックすると、デザイナー ビューはその状態の展開ビューに切り替わります。 この値は、遷移が作成されたときに設定され、デザイナーで遷移を遷移先の状態に接続する矢印をドラッグすると変更できます。|  
  
### <a name="creating-transitions"></a>遷移の作成  
 遷移を作成するには、ある状態から別の状態へ線をドラッグするか、ある状態を別の状態の上にドラッグすると表示される三角形に状態をドロップします。 ドラッグによって遷移を作成するには、元の状態の端にマウス ポインターを置き、元の状態から遷移先の状態に線をドラッグします。 ドロップによって遷移を作成するには、遷移先の状態をドラッグして元の状態の上にマウス ポインターを置き、元の状態の周囲に表示される 4 つの三角形のうち 1 つにドロップします。 先の状態がからドラッグするか、新しい状態にすることができます、**ツールボックス**、または既存の状態がワークフロー デザイナーからドラッグします。  
  
> [!NOTE]
>  ステート マシンの 1 つの状態では、ワークフロー デザイナーを使用して作成された遷移を最大 76 個まで含めることができます。 デザイナー以外で作成されたワークフローの状態の遷移に関する制限は、システム リソースによってのみ制限されます。  
  
 トリガーを共有する遷移とは、同じトリガー イベントを共有する遷移のセットです。 共有されるトリガーにより、共通のトリガー イベントを共有する複数の遷移用に構成された式の評価に基づいて、条件に従って遷移先の状態に移行することができます。 遷移に追加のアクションを追加して共有遷移を作成するには、目的の遷移の始点を表す円をクリックし、目的の状態にドラッグします。 新しい遷移では最初の遷移と同じトリガーが共有されますが、その条件とアクションは一意になります。 共有遷移も作成できますから、遷移デザイナー内をクリックして**追加共有トリガー遷移**から目的のターゲットの状態を選択し、遷移デザイナーの下部にある、 **使用可能な状態の接続に**ドロップダウンします。  
  
## <a name="see-also"></a>関連項目  
 [ステート マシン](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [状態](../workflow-designer/state-activity-designer.md)