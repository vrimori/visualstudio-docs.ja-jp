---
title: '方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存 |Microsoft ドキュメント'
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
ms.openlocfilehash: b3ca0f8c86b31576fd5ce219a536725431b27007
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-attachments-from-outlook-e-mail-items"></a>方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存する
  この例では、メールを受信トレイで受け取ったときに、電子メールの添付ファイルを指定されたフォルダーに保存します。  
  
> [!IMPORTANT]  
>  この例は、という名前のフォルダーを追加する場合にのみ**TestFileSave** C ディレクトリのルートに位置します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>関連項目  
 [メール アイテムの操作](../vsto/working-with-mail-items.md)   
 [方法: プログラムによって名前のフォルダーを取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって電子メール メッセージが受信したときにアクションを実行](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [方法: プログラムによって特定のフォルダー内を検索する](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  