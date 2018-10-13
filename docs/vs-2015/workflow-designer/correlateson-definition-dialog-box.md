---
title: '[CorrelatesOn の定義] ダイアログ ボックス |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 3171efb985eec54d0e935d2e8499c69631c6dfc8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285819"
---
# <a name="correlateson-definition-dialog-box"></a>[CorrelatesOn の定義] ダイアログ ボックス
**CorrelatesOn**でダイアログ ボックスが使用される[!INCLUDE[wfd1](../includes/wfd1-md.md)]を編集する、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>のプロパティを<xref:System.ServiceModel.Activities.Receive>アクティビティ。 [!INCLUDE[crdefault](../includes/crdefault-md.md)] [受信](../workflow-designer/receive-activity-designer.md)トピック。  
  
 <xref:System.ServiceModel.Activities.Receive> アクティビティの間の相関関係によって、ワークフロー内でさまざまなサービス操作が相互に接続される方法が指定されます。  
  
 次の表に、ユーザー インターフェイス (UI) 要素の**CorrelatesOn**  ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**CorrelatesWith**|適切なワークフロー インスタンスにメッセージをルーティングするために使用される <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|**XPath クエリ**|受信メッセージから相関関係データを抽出するためのクエリを含む、キーと値のペア。 これは、<xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> プロパティに対応します。 XPath クエリは、<xref:System.ServiceModel.MessageQuerySet> オブジェクトに含まれます。|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>[CorrelatesOn] ダイアログ ボックスを起動するには  
 **受信**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所でアクティビティを通常配置しています。 この操作により、Receive という既定の <xref:System.ServiceModel.Activities.Receive> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 選択、**受信**アクティビティ デザイナーおよび (コレクション) のテキストを横にある省略記号のボタンをクリックし、 **CorrelatesOn**プロパティ グリッドでプロパティ、 **CorrelatesOn の定義**ダイアログ ボックスを表示します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Activities.Receive>   
 [関連付け初期化子のダイアログ ボックスを追加します。](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [[関連付け] ダイアログ ボックスを追加します。](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [[関連付け初期化] ダイアログ ボックス](../workflow-designer/initialize-correlation-dialog-box.md)