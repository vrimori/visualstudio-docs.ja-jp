---
title: "方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: f87b05b45fafab3ad28a6da6a98391b8d121be7e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-attachments-from-outlook-e-mail-items"></a>方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存する
  この例では、メールを受信トレイで受け取ったときに、電子メールの添付ファイルを指定されたフォルダーに保存します。  
  
> [!IMPORTANT]  
>  この例は、という名前のフォルダーを追加する場合にのみ**TestFileSave** C ディレクトリのルートに位置します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>参照  
 [メール アイテムの操作](../vsto/working-with-mail-items.md)   
 [方法: プログラムによって名前のフォルダーを取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって電子メール メッセージが受信したときにアクションを実行](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [方法: プログラムによって特定のフォルダー内を検索する](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  