---
title: "方法: プログラムによって Outlook のアイテムを移動 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 72b35bde8775a859ef15c5e18b381615974bccd7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
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
  
## <a name="see-also"></a>参照  
 [フォルダーの操作](../vsto/working-with-folders.md)   
 [方法: プログラムによって名前のフォルダーを取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって特定のフォルダー内を検索](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行する](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  