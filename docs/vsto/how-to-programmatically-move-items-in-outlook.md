---
title: "方法: プログラムによって Outlook でアイテムを移動する | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook フォルダー [Visual Studio での Office 開発], 移動 (項目を)"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: プログラムによって Outlook でアイテムを移動する
  この例では、未読の電子メール メッセージを、**\[受信トレイ\]** から **Test** という名前のフォルダーに移動します。  この例では、`Subject` フィールドに **Test** という単語を含むメッセージのみ移動します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   **Test** という名前の Outlook のメール フォルダー  
  
-   `Subject` フィールドに **Test** という単語を含む、受信した電子メール メッセージ  
  
## 参照  
 [フォルダーの操作](../vsto/working-with-folders.md)   
 [方法: プログラムによって名前を指定してフォルダーを取得する](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって特定のフォルダー内を検索する](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行する](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  