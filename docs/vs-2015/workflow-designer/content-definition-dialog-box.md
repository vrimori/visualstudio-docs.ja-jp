---
title: コンテンツの定義 ダイアログ ボックス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0c0fffed6bbb8d9690f96679d910d5ac4a3b631e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176124"
---
# <a name="content-definition-dialog-box"></a>[コンテンツ定義] ダイアログ ボックス
**コンテンツ定義**でダイアログ ボックスが使用される[!INCLUDE[wfd1](../includes/wfd1-md.md)]を構成する、**コンテンツ**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、 <xref:System.ServiceModel.Activities.SendReply>、および<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 [!INCLUDE[crabout](../includes/crabout-md.md)] このボックスを使用するアクティビティ デザイナーを参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)トピック。  
  
 次の表に、ユーザー インターフェイス (UI) 要素の**関連付けの初期化** ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**メッセージ**|メッセージの内容を指定します、**メッセージ データ**式テキスト ボックスと、型を使用して、**メッセージの種類**ドロップダウン リスト ボックス。 既定では、**コンテンツ定義**を使用して、 <xref:System.ServiceModel.Activities.ReceiveMessageContent>、要求、<xref:System.ServiceModel.Channels.Message>またはメッセージ コントラクト、ワークフロー サービス定義内の型。|  
|**パラメーター**|をクリックして、**パラメーター**ラジオ ボタンを使用する<xref:System.ServiceModel.Activities.ReceiveParametersContent>、データ コントラクトを受け取る。 <xref:System.Activities.OutArgument> キーおよび値のペアのジェネリック コレクションを設定するには、データ グリッドを使用します。これらの値は、現在のワークフローの変数パラメーターに割り当てられます。|  
  
 **コンテンツ定義**ダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 デザイナーへのアクセス方法は、どの場合も同様です。ここでは、Receive デザイナーを使用する例で手順を説明します。  
  
 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所でアクティビティを通常配置しています。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**アクティビティ デザイナーおよび (コンテンツ) のテキストの横にある省略記号のボタンをクリックし、**コンテンツ**プロパティ グリッドでプロパティ、**コンテンツ定義**ダイアログ ボックスを表示します。  
  
 内でコンテンツを指定することができます、**メッセージ**のセクションを<xref:System.ServiceModel.Activities.ReceiveMessageContent>アクティビティ内、または、**パラメーター**のセクションを<xref:System.ServiceModel.Activities.ReceiveParametersContent>アクティビティ。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー デザイナーの UI ヘルプ](../workflow-designer/workflow-designer-ui-help.md)