---
title: 選択操作 ダイアログ ボックス (レガシ) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 717fb2918c0532d85985a7b63f03a2e8bb397355
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534185"
---
# <a name="choose-operation-dialog-box-legacy"></a>[操作の選択] ダイアログ ボックス (レガシ)
このトピックで説明する方法を使用して、**操作の選択**  ダイアログ ボックスで、従来の[!INCLUDE[wfd1](../includes/wfd1-md.md)]します。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用します。  
  
 **操作の選択**に関連付ける操作を選択 ダイアログ ボックスを使用する<xref:System.Workflow.Activities.ReceiveActivity>アクティビティまたは<xref:System.Workflow.Activities.SendActivity>アクティビティ。 これらのアクティビティでこのダイアログ ボックスの使用に関する詳細については、次を参照してください。[方法: WCF コントラクト操作 (レガシ) 実装](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)と[方法: WCF コントラクト操作 (レガシ) を呼び出す](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)します。  
  
 次の表に、ユーザー インターフェイス (UI) 要素の**選択操作** ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**契約を追加します。**|新しいコントラクトを作成します。 このコントラクトに対して新しい操作を定義できます  (この要素は <xref:System.Workflow.Activities.ReceiveActivity> でのみ使用されます)。|  
|**操作を追加します。**|作成した新しいコントラクトを新しい操作が追加されて、**選択操作** ダイアログ ボックス。 **注:** のみで作成したコントラクトに新しい操作を追加することができます、**選択操作** ダイアログ ボックス。 <br /><br /> (この要素は <xref:System.Workflow.Activities.ReceiveActivity> でのみ使用されます)。|  
|**インポートしています.**|以前に定義されたコントラクトをインポートし、そのコントラクトから操作を選択できます。|  
|**操作名**|現在選択されている操作の名前。 このテキスト ボックスは編集で操作を作成した場合にのみ使用可能な**選択操作** ダイアログ ボックス。|  
|**パラメーター**|現在選択されている操作のパラメータ定義が表示されるタブ。 **注:** で操作を作成した場合にのみ、パラメーターの定義を変更できる、**選択操作** ダイアログ ボックス。|  
|**Properties**|クライアントとサービス間で送信されたメッセージの <xref:System.Net.Security.ProtectionLevel> 設定が表示されるタブ。 **注:** で操作を作成した場合にのみ、このタブが有効になっている、**選択操作** ダイアログ ボックス。|  
|**アクセス許可**|その操作の呼び出しを許可されているユーザーの <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> プロパティおよび <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> プロパティが表示されるタブ。 たとえば、Administrators グループからユーザーがその操作の呼び出しが許可された場合のみはで記述する"Administrators"、**ロール**テキスト ボックス。<br /><br /> このタブで作成した両方の操作が有効になって、 **ChooseOperation**  ダイアログ ボックスと使用してインポートした操作、**インポート**ボタンをクリックします。|  
  
> [!NOTE]
>  **選択操作** ダイアログ ボックスには、コントラクトまたはその他によって使用されている操作のみが表示されます。<xref:System.Workflow.Activities.SendActivity>ワークフロー内のアクティビティ。 同様に、**選択操作** ダイアログ ボックスの<xref:System.Workflow.Activities.ReceiveActivity>アクティビティは、コントラクトまたはその他によって使用されている操作のみを示しています。 **ReceiveActivity**ワークフロー内のアクティビティ。  
  
## <a name="see-also"></a>関連項目  
 [方法: WCF コントラクト操作 (レガシ) 実装](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [方法: WCF コントラクト操作 (レガシ) を呼び出す](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)