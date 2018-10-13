---
title: '方法: Windows Communication Foundation コントラクト操作 (レガシ) を呼び出す |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5e59d5ed9617d4be71a0542e35dd509d9035ae33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181845"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>方法: Windows Communication Foundation コントラクト操作を呼び出す (レガシ)
このトピックでは、[!INCLUDE[indigo1](../includes/indigo1-md.md)] または [!INCLUDE[wfd1](../includes/wfd1-md.md)] を対象とする従来の [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]を使用して [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] コントラクト操作を呼び出す方法について説明します。  
  
 ドラッグした後、 **SendActivity**アクティビティ ワークフロー デザイン サーフェイスのツールボックスから、既存のコントラクトをインポートし、から呼び出される操作を決定する必要があります**SendActivity**アクティビティ。 コントラクトとその操作を選択する、[選択操作 ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)します。  
  
 さらに、サービスで構成ファイルを使用している場合は、<xref:System.Workflow.Activities.ChannelToken> を指定する必要があります。 <xref:System.Workflow.Activities.ChannelToken> により、送信アクティビティでワークフロー サービスへの接続に使用するエンドポイント構成が特定されます。  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>SendActivity アクティビティから WCF コントラクト操作を呼び出すには  
  
1.  ダブルクリック、 **SendActivity**アクティビティ デザイナーの横にある省略記号をクリックしてまたは、 **ServiceOperationInfo**プロパティ、**プロパティ**ウィンドウ。  
  
2.  ときに、**操作の選択**  ダイアログ ボックスが開いたら、**インポート** ダイアログ ボックスの右上隅にします。  
  
     [参照し、.NET の種類 ダイアログ ボックス (レガシ) を選択](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)が開きます。  
  
3.  必要なコントラクトを含んでいるアセンブリまたはプロジェクトを検索します。  
  
4.  コントラクトを選択し、をクリックして**OK**します。  
  
5.  **使用可能な操作**を起動し、をクリックする操作を選択します。 **OK**。  
  
### <a name="to-specify-a-channel-token"></a>チャネル トークンを指定するには  
  
1.  デザイナで <xref:System.Workflow.Activities.SendActivity> アクティビティを選択します。  
  
2.  **プロパティ**ウィンドウの名前を指定、<xref:System.Workflow.Activities.ChannelToken>します。 この名前は、チャネル トークンを一意に識別します。  
  
3.  チャネル トークン ノードを展開し、<xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> フィールドで使用するクライアント エンドポイントの名前を指定します。 構成ファイル内の同名のエンドポイント構成が、チャネルの構成に使用されます。  
  
4.  構成ファイル内にエンドポイント構成が存在しない場合は、エンドポイント構成を作成します。 クライアントの構成の詳細については、次を参照してください。 [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d)します。  
  
## <a name="see-also"></a>関連項目  
 [選択操作 ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [方法: WCF コントラクト操作 (レガシ) 実装](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)