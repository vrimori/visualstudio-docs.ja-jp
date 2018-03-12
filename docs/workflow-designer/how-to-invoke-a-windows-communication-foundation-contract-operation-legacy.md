---
title: "方法: Windows Communication Foundation コントラクト操作 (レガシ) を呼び出す |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 522db4f46486470333393ca99f384f258898e09a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>方法: Windows Communication Foundation コントラクト操作を呼び出す (レガシ)
このトピックを呼び出す方法について説明、[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]コントラクト操作を対象とする従来の Windows ワークフロー デザイナーを使用して、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]または[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]です。

 ドラッグした後、 **SendActivity**活動ツールボックスからワークフロー デザイン サーフェイスには、既存のコントラクトをインポートしを呼び出す操作を決定する必要があります**SendActivity**アクティビティ。 契約内容とを通じてその操作を選択する、[選択操作 ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)です。

 さらに、サービスで構成ファイルを使用している場合は、<xref:System.Workflow.Activities.ChannelToken> を指定する必要があります。 <xref:System.Workflow.Activities.ChannelToken> により、送信アクティビティでワークフロー サービスへの接続に使用するエンドポイント構成が特定されます。

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>SendActivity アクティビティから WCF コントラクト操作を呼び出すには

1.  ダブルクリックして、 **SendActivity**デザイナーのアクティビティ の横にある省略記号 をクリックして、 **ServiceOperationInfo**プロパティに、**プロパティ**ウィンドウです。

2.  ときに、**操作の選択** ダイアログ ボックスが開いたら、**インポート** ダイアログ ボックスの右上隅にします。

     [を参照して .NET の種類 ダイアログ ボックス (レガシ) を選択](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)が開きます。

3.  必要なコントラクトを含んでいるアセンブリまたはプロジェクトを検索します。

4.  コントラクトを選択し、クリックして**OK**です。

5.  **使用可能な操作**を起動し、をクリックする操作を選択して**OK**です。

### <a name="to-specify-a-channel-token"></a>チャネル トークンを指定するには

1.  デザイナで <xref:System.Workflow.Activities.SendActivity> アクティビティを選択します。

2.  **プロパティ** ウィンドウでの名前を指定、<xref:System.Workflow.Activities.ChannelToken>です。 この名前は、チャネル トークンを一意に識別します。

3.  チャネル トークン ノードを展開し、<xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> フィールドで使用するクライアント エンドポイントの名前を指定します。 構成ファイル内の同名のエンドポイント構成が、チャネルの構成に使用されます。

4.  構成ファイル内にエンドポイント構成が存在しない場合は、エンドポイント構成を作成します。 クライアントの構成の詳細については、次を参照してください。 [WCF クライアントの概要](/dotnet/framework/wcf/wcf-client-overview)です。

## <a name="see-also"></a>関連項目

- [[操作の選択] ダイアログ ボックス (レガシ)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [方法: WCF コントラクト操作 (レガシ) を実装します。](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)