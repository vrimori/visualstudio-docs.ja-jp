---
title: '方法: プログラムによって Outlook でアイテムを移動'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257723"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>方法: プログラムによって Outlook でアイテムを移動
  この例から未読の電子メール メッセージの移動、**受信トレイ**という名前のフォルダーに**テスト**します。 例では、のみ、単語が含まれているメッセージを移動**テスト**で、`Subject`フィールド。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 この例で必要な要素は次のとおりです。  
  
-   という名前の Outlook メール フォルダー**テスト**します。  
  
-   電子メール メッセージが到着する単語**テスト**で、`Subject`フィールド。  
  
## <a name="see-also"></a>関連項目  
 [フォルダーを操作します。](../vsto/working-with-folders.md)   
 [方法: プログラムによって名前でフォルダーを取得します。](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって特定のフォルダー内を検索](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  