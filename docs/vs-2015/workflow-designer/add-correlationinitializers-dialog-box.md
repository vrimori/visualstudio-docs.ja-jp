---
title: 関連付け初期化子のダイアログ ボックスの追加 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8543ebd784af13251663155327c2bfb9097b4904
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544652"
---
# <a name="add-correlationinitializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックス
**関連付け初期化子**でダイアログ ボックスが使用される[!INCLUDE[wfd1](../includes/wfd1-md.md)]を構成する、 **CorrelationInitializers**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>と<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 [!INCLUDE[crabout](../includes/crabout-md.md)] このボックスを使用するアクティビティ デザイナーを参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)トピック。  
  
 このダイアログ ボックスで指定したコレクションの関連付け初期化子では、メッセージング アクティビティ間の相関関係 (クエリベース、コンテキスト、コールバック コンテキスト、または要求/応答の相関関係) を初期化できます。  
  
 次の表に、ユーザー インターフェイス (UI) 要素の **[関連付け初期化子**] ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**初期化子を追加します。**|をクリックして、**追加初期化**ボックス、コレクションに追加の初期化子を追加します。|  
|**関連付けの種類**|関連付け初期化子の種類を指定します。 次の 4 種類から選択できます。<br /><br /> 1.<xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> を指定するためのコールバック関連付け初期化子。<br />2.<xref:System.ServiceModel.Activities.CorrelationInitializer> を指定するためのコンテキスト関連付け初期化子。<br />3.<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> を指定するための要求/応答関連付け初期化子。<br />4.<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> を指定するためのクエリ関連付け初期化子。<br /><br /> 編集する、 **CorrelationType**<br /><br /> 1.特定の行にタブ、**初期化子の追加**DataGrid します。<br />2.フォーカスを設定するには、Ctrl + Tab キーを押します**CorrelationTypeComboBox**<br />3.ポップアップ表示するには、Alt + Down キーを押して、 **ComboBox**して編集できます。|  
|**XPath クエリ**|送受信メッセージから相関関係データを抽出するためのクエリを含む、キーと値のペア。 このリストは、<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型を使用している場合にのみ有効です。|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックスを開くには  
 **関連付け初期化子**ダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 各ケースとを含むケースと似ていますそれらにアクセスする、**受信**デザイナーは、ここでの使用手順を説明します。  
  
 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所でアクティビティを通常配置しています。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**アクティビティ デザイナーおよび (コレクション) のテキストを横にある省略記号のボタンをクリックし、 **CorrelationInitializers**プロパティ グリッドでプロパティ、**追加関連付け初期化子の**ダイアログ ボックスを表示します。  
  
## <a name="see-also"></a>関連項目  
 [[関連付け] ダイアログ ボックスを追加します。](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [[関連付け初期化] ダイアログ ボックス](../workflow-designer/initialize-correlation-dialog-box.md)