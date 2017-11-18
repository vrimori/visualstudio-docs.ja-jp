---
title: "方法: プログラムによって Outlook のアイテムを移動 |Microsoft ドキュメント"
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], moving items
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fc7afe28e435e0dcdd58c7403f6282ebf3609a23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>方法: プログラムによって Outlook でアイテムを移動する
  この例から未読メ ッ セージの移動、**受信トレイ**という名前のフォルダーに**テスト**です。 語を含んでいるメッセージを移動のみ**テスト**で、`Subject`フィールドです。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   名前付き Outlook メール フォルダー**テスト**です。  
  
-   電子メール メッセージが到着する単語**テスト**で、`Subject`フィールドです。  
  
## <a name="see-also"></a>関連項目  
 [フォルダーの操作](../vsto/working-with-folders.md)   
 [方法: プログラムによって名前のフォルダーを取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって特定のフォルダー内を検索](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行する](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  