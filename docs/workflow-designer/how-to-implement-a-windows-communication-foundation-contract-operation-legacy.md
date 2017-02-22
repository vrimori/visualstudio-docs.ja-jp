---
title: "方法: Windows Communication Foundation コントラクト操作を実装する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 方法: Windows Communication Foundation コントラクト操作を実装する (レガシ)
このトピックでは、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用して [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] コントラクト操作を実装する方法について説明します。  
  
 **ReceiveActivity** アクティビティをツールボックスからワークフロー デザイン サーフェイスにドラッグした後、新しい [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] コントラクトを作成するか、既存のコントラクトをインポートして操作を実装します。コントラクトとその操作は、[\[操作の選択\] ダイアログ ボックス \(レガシ\)](../Topic/Choose%20Operation%20Dialog%20Box%20\(Legacy\).md)で選択または作成します。  
  
### WCF コントラクト操作を実装するには  
  
1.  デザイナで **ReceiveActivity** アクティビティをダブルクリックするか、**\[プロパティ\]** ペインの **ServiceOperationInfo** プロパティの横にある省略記号をクリックします。  
  
2.  以下のいずれかの操作を行います。  
  
    -   ダイアログ ボックスの右上隅にある **\[コントラクトの追加\]** をクリックします。新しい [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] コントラクトおよび操作が作成されます。  
  
         または  
  
    -   ダイアログ ボックスの右上隅にある **\[インポート\]** をクリックします。[\[.NET 型の参照と選択\] ダイアログ ボックス \(レガシ\)](../Topic/Browse%20and%20Select%20a%20.NET%20Type%20Dialog%20Box%20\(Legacy\).md)が開きます。必要なコントラクトを含んでいるアセンブリまたはプロジェクトを検索します。コントラクトを選択し、**\[OK\]** をクリックします。  
  
     コントラクトを作成またはインポートしたら、そのコントラクトに新しい操作を追加できます。新しい操作を追加するには、コントラクトを選択し、ダイアログ ボックスの右上隅にある **\[操作の追加\]** をクリックします。操作の追加が終了したら、手順 3. に進みます。  
  
3.  **ReceiveActivity** アクティビティに関連付ける操作を選択します。操作の定義は、操作の名前、パラメータ、プロパティ、アクセス許可の設定を変更することにより、操作できます。  
  
     名前を変更するには、**\[操作名\]** ボックスに新しい名前を入力します。  
  
     操作のパラメータを表示するには、**\[パラメータ\]** タブをクリックします。パラメータの名前、型、方向の変更のほか、操作のパラメータの追加または削除を行うことができます。  
  
     操作の保護レベルやサポートされるメッセージ交換機能を表示するには、**\[プロパティ\]** タブをクリックします。  
  
     操作の実装を許可するグループを指定するには、**\[アクセス許可\]** タブをクリックします。  
  
4.  **\[OK\]** をクリックすると、**ReceiveActivity** アクティビティにより、実装する操作の名前が表示されます。  
  
5.  その操作の実装に使用するワークフロー アクティビティを **ReceiveActivity** アクティビティ内に配置します。  
  
## 参照  
 [\[操作の選択\] ダイアログ ボックス \(レガシ\)](../Topic/Choose%20Operation%20Dialog%20Box%20\(Legacy\).md)   
 [方法: WCF コントラクト操作を呼び出す \(レガシ\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)