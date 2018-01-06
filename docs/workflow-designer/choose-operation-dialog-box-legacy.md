---
title: "選択操作 ダイアログ ボックス (レガシ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 2db745d34c86e4b0aa5639872106096421044bce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="choose-operation-dialog-box-legacy"></a>[操作の選択] ダイアログ ボックス (レガシ)
このトピックについて説明する方法を使用して、**操作の選択** ダイアログ ボックスでは、従来の[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]します。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
 **操作の選択**に関連付ける操作を選択 ダイアログ ボックスを使用して、<xref:System.Workflow.Activities.ReceiveActivity>アクティビティまたは<xref:System.Workflow.Activities.SendActivity>アクティビティ。 これらのアクティビティでこのダイアログ ボックスを使用する方法の詳細については、次を参照してください。[する方法: WCF コントラクト操作 (レガシ) を実装する](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)と[する方法: WCF コントラクト操作 (レガシ) を呼び出す](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)です。  
  
 次の表は、ユーザー インターフェイス (UI) 要素の**操作の選択** ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**契約を追加します。**|新しいコントラクトを作成します。 このコントラクトに対して新しい操作を定義できます  (この要素は <xref:System.Workflow.Activities.ReceiveActivity> でのみ使用されます)。|  
|**追加操作**|作成した新しいコントラクトに新しい操作が追加されて、**操作の選択** ダイアログ ボックス。 **注:**のみで作成したコントラクトに新しい操作を追加することができます、**操作の選択** ダイアログ ボックス。 <br /><br /> (この要素は <xref:System.Workflow.Activities.ReceiveActivity> でのみ使用されます)。|  
|**インポートしています.**|以前に定義されたコントラクトをインポートし、そのコントラクトから操作を選択できます。|  
|**操作名**|現在選択されている操作の名前。 このテキスト ボックスは、操作を作成した場合にのみ編集に使用できる、**操作の選択** ダイアログ ボックス。|  
|**パラメーター**|現在選択されている操作のパラメータ定義が表示されるタブ。 **注:**で操作を作成する場合にのみ、パラメーター定義を変更することができます、**操作の選択** ダイアログ ボックス。|  
|**プロパティ**|クライアントとサービス間で送信されたメッセージの <xref:System.Net.Security.ProtectionLevel> 設定が表示されるタブ。 **注:**で操作を作成する場合にのみ、このタブが有効になっている、**操作の選択** ダイアログ ボックス。|  
|**アクセス許可**|その操作の呼び出しを許可されているユーザーの <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> プロパティおよび <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> プロパティが表示されるタブ。 たとえば、Administrators グループからユーザーは、その操作の呼び出しをできませんでした、だけの場合はで記述する"Administrators"、**ロール**テキスト ボックス。<br /><br /> このタブで作成した両方の操作が有効になって、 **ChooseOperation**  ダイアログ ボックスおよび使用してインポートした操作、**インポート**ボタンをクリックします。|  
  
> [!NOTE]
>  **操作の選択** ダイアログ ボックスでは、コントラクトまたはその他によって使用されている操作のみを示しています。<xref:System.Workflow.Activities.SendActivity>ワークフロー内のアクティビティ。 同様に、**操作の選択** ダイアログ ボックスを<xref:System.Workflow.Activities.ReceiveActivity>アクティビティは、コントラクトまたはその他によって使用されている操作のみを示しています。 **ReceiveActivity**ワークフロー内のアクティビティ。  
  
## <a name="see-also"></a>参照  
 [方法: WCF コントラクト操作 (レガシ) を実装します。](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [方法: WCF コントラクト操作 (レガシ) を呼び出す](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)