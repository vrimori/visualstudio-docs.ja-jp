---
title: '方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd564b71622ad5f9ee6500ddc3864bad0b21686b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672407"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存
  この例では、メールを受信トレイで受け取ったときに、電子メールの添付ファイルを指定されたフォルダーに保存します。  
  
> [!IMPORTANT]  
>  この例の動作という名前のフォルダーを追加する場合にのみ**TestFileSave** C ディレクトリのルートにあります。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>関連項目  
 [メールの項目を操作します。](../vsto/working-with-mail-items.md)   
 [方法: プログラムによって名前でフォルダーを取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [方法: プログラムによって特定のフォルダー内を検索](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  