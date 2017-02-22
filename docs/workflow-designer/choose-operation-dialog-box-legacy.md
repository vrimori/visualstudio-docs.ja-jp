---
title: "[操作の選択] ダイアログ ボックス (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# [操作の選択] ダイアログ ボックス (レガシ)
このトピックでは、従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]の **\[操作の選択\]** ダイアログ ボックスの使用方法について説明します。[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用します。  
  
 <xref:System.Workflow.Activities.ReceiveActivity> アクティビティまたは <xref:System.Workflow.Activities.SendActivity> アクティビティと関連付ける操作を選択するには、**\[操作の選択\]** ダイアログ ボックスを使用します。このダイアログ ボックスの使用の詳細については、「[方法: WCF コントラクト操作を実装する \(レガシ\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)」および「[方法: WCF コントラクト操作を呼び出す \(レガシ\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)」を参照してください。  
  
 次の表は、**\[操作の選択\]** ダイアログ ボックスのユーザー インターフェイス \(UI\) 要素です。  
  
|UI 要素|説明|  
|-----------|--------|  
|**\[コントラクトの 追加\]**|新しいコントラクトを作成します。このコントラクトに対して新しい操作を定義できます \(この要素は <xref:System.Workflow.Activities.ReceiveActivity> でのみ使用されます\)。|  
|**\[操作の 追加\]**|**\[操作の選択\]** ダイアログ ボックスで作成した新しいコントラクトに新しい操作を追加します。 **Note:**  新しい操作は、**\[操作の選択\]** ダイアログ ボックスで作成したコントラクトに対してのみ追加できます。 <br /><br /> \(この要素は <xref:System.Workflow.Activities.ReceiveActivity> でのみ使用されます\)。|  
|**\[インポート...\]**|以前に定義されたコントラクトをインポートし、そのコントラクトから操作を選択できます。|  
|**\[操作 名\]**|現在選択されている操作の名前。このテキスト ボックスを編集できるのは、**\[操作の選択\]** ダイアログ ボックスで操作を作成した場合のみです。|  
|**\[パラメーター\]**|現在選択されている操作のパラメータ定義が表示されるタブ。 **Note:**  パラメータ定義を変更できるのは、**\[操作の選択\]** ダイアログ ボックスで操作を作成した場合のみです。|  
|**\[プロパティ\]**|クライアントとサービス間で送信されたメッセージの <xref:System.Net.Security.ProtectionLevel> 設定が表示されるタブ。 **Note:**  このタブが有効なのは、**\[操作の選択\]** ダイアログ ボックスで操作を作成した場合のみです。|  
|**\[アクセス許可\]**|その操作の呼び出しを許可されているユーザーの <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> プロパティおよび <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> プロパティが表示されるタブ。たとえば、Administrators グループのユーザーのみがその操作の呼び出しを許可されている場合は、**\[ロール\]** ボックスに「Administrators」と入力します。<br /><br /> このタブは、**\[操作の選択\]** ダイアログ ボックスで作成した操作と、**\[インポート\]** ボタンを使用してインポートした操作の両方に対して有効です。|  
  
> [!NOTE]
>  **\[操作の選択\]** ダイアログ ボックスには、ワークフロー内の他の <xref:System.Workflow.Activities.SendActivity> アクティビティで使用されるコントラクトまたは操作のみが表示されます。同様に、<xref:System.Workflow.Activities.ReceiveActivity> アクティビティの **\[操作の選択\]** ダイアログ ボックスには、ワークフロー内の他の **ReceiveActivity** アクティビティで使用されるコントラクトまたは操作のみが表示されます。  
  
## 参照  
 [方法: WCF コントラクト操作を実装する \(レガシ\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [方法: WCF コントラクト操作を呼び出す \(レガシ\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)