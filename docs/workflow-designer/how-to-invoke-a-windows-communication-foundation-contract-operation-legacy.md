---
title: "方法: Windows Communication Foundation コントラクト操作を呼び出す (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 方法: Windows Communication Foundation コントラクト操作を呼び出す (レガシ)
このトピックでは、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用して [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] コントラクト操作を呼び出す方法について説明します。  
  
 **SendActivity** アクティビティをツールボックスからワークフロー デザイン サーフェイスにドラッグした後、既存のコントラクトをインポートし、その **SendActivity** アクティビティから呼び出す操作を決定する必要があります。コントラクトとその操作は、[\[操作の選択\] ダイアログ ボックス \(レガシ\)](../Topic/Choose%20Operation%20Dialog%20Box%20\(Legacy\).md)で選択します。  
  
 さらに、サービスで構成ファイルを使用している場合は、<xref:System.Workflow.Activities.ChannelToken> を指定する必要があります。<xref:System.Workflow.Activities.ChannelToken> により、送信アクティビティでワークフロー サービスへの接続に使用するエンドポイント構成が特定されます。  
  
### SendActivity アクティビティから WCF コントラクト操作を呼び出すには  
  
1.  デザイナで **SendActivity** アクティビティをダブルクリックするか、**\[プロパティ\]** ペインの **ServiceOperationInfo** プロパティの横にある省略記号をクリックします。  
  
2.  **\[操作の選択\]** ダイアログ ボックスが開いたら、右上隅にある **\[インポート\]** をクリックします。  
  
     [\[.NET 型の参照と選択\] ダイアログ ボックス \(レガシ\)](../Topic/Browse%20and%20Select%20a%20.NET%20Type%20Dialog%20Box%20\(Legacy\).md)が開きます。  
  
3.  必要なコントラクトを含んでいるアセンブリまたはプロジェクトを検索します。  
  
4.  コントラクトを選択し、**\[OK\]** をクリックします。  
  
5.  **\[使用可能な操作\]** で、呼び出す操作を選択し、**\[OK\]** をクリックします。  
  
### チャネル トークンを指定するには  
  
1.  デザイナで <xref:System.Workflow.Activities.SendActivity> アクティビティを選択します。  
  
2.  **\[プロパティ\]** ペインで、<xref:System.Workflow.Activities.ChannelToken> の名前を指定します。この名前は、チャネル トークンを一意に識別します。  
  
3.  チャネル トークン ノードを展開し、<xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> フィールドで使用するクライアント エンドポイントの名前を指定します。構成ファイル内の同名のエンドポイント構成が、チャネルの構成に使用されます。  
  
4.  構成ファイル内にエンドポイント構成が存在しない場合は、エンドポイント構成を作成します。クライアントの構成の詳細については、「[WCF クライアントの概要](../Topic/WCF%20Client%20Overview.md)」を参照してください。  
  
## 参照  
 [\[操作の選択\] ダイアログ ボックス \(レガシ\)](../Topic/Choose%20Operation%20Dialog%20Box%20\(Legacy\).md)   
 [方法: WCF コントラクト操作を実装する \(レガシ\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)