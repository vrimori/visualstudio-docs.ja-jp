---
title: "CorrelationInitializers ダイアログ ボックスを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: b83b7c44857ffbbcf9dda465bb3c1c578ed73d3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="add-correlationinitializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックス
**関連付け初期化子**では、ダイアログ ボックスを使用してください[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を構成するには**CorrelationInitializers**のプロパティ、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.Receive>、 <xref:System.ServiceModel.Activities.SendReply>、および。<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティ。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]このボックスを使用するアクティビティ デザイナーを参照してください、[送信](../workflow-designer/send-activity-designer.md)、[受信](../workflow-designer/receive-activity-designer.md)、 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)、および[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)トピックです。  
  
 このダイアログ ボックスで指定したコレクションの関連付け初期化子では、メッセージング アクティビティ間の相関関係 (クエリベース、コンテキスト、コールバック コンテキスト、または要求/応答の相関関係) を初期化できます。  
  
 次の表は、ユーザー インターフェイス (UI) 要素の**[関連付け初期化子**] ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**初期化子を追加します。**|をクリックして、**追加初期化**コレクションに追加の初期化子を追加するボックスです。|  
|**関連付けの種類**|関連付け初期化子の種類を指定します。 次の 4 種類から選択できます。<br /><br /> 1.<xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> を指定するためのコールバック関連付け初期化子。<br />2.<xref:System.ServiceModel.Activities.CorrelationInitializer> を指定するためのコンテキスト関連付け初期化子。<br />3.<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> を指定するための要求/応答関連付け初期化子。<br />4.<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> を指定するためのクエリ関連付け初期化子。<br /><br /> 編集する、 **CorrelationType**<br /><br /> 1.特定の行にタブ、**初期化子の追加**データ グリッドです。<br />2.フォーカスを設定するには、Ctrl + tab **CorrelationTypeComboBox**<br />3.ポップアップ表示して Alt + Down を押して、 **ComboBox**し編集することです。|  
|**XPath クエリ**|送受信メッセージから相関関係データを抽出するためのクエリを含む、キーと値のペア。 このリストは、<xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型を使用している場合にのみ有効です。|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>[関連付け初期化子の追加] ダイアログ ボックスを開くには  
 **関連付け初期化子**でダイアログ ボックスを使用して、**送信**、**受信**、 **ReceiveAndSendReply**、および**SendAndReceiveReply**デザイナー。 各ケースと関係する場合と似ていますそれらにアクセスする、**受信**デザイナーは、ここで使用する、手順を説明します。  
  
 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所のアクティビティを通常配置しています。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**、省略記号が (コレクション) テキストの横にあるボタンをクリックしてアクティビティ デザイナー、 **CorrelationInitializers**プロパティ、プロパティ グリッドで、**追加関連付け初期化子の**ダイアログ ボックスを表示します。  
  
## <a name="see-also"></a>関連項目  
 [追加の相関関係 ダイアログ ボックス](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [[関連付け初期化] ダイアログ ボックス](../workflow-designer/initialize-correlation-dialog-box.md)