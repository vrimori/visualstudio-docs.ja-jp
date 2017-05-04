---
title: "方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存する | Microsoft Docs"
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
  - "Outlook [Visual Studio での Office 開発]、添付ファイル"
  - "電子メール [Visual Studio での Office 開発]、添付ファイル"
  - "保存 (電子メールの添付ファイルを)"
  - "メール アイテム [Visual Studio での Office 開発]、添付ファイル"
  - "添付ファイル [Visual Studio での Office 開発]"
ms.assetid: 2f05e2bb-ae4f-407c-a6da-a3b1a4c31ab3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 方法: プログラムによって Outlook の電子メール アイテムから添付ファイルを保存する
  この例では、メールを受信トレイで受け取ったときに、電子メールの添付ファイルを指定されたフォルダーに保存します。  
  
> [!IMPORTANT]  
>  この例が機能するのは、C ディレクトリのルートに **TestFileSave** という名前のフォルダーを追加する場合だけです。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_OL_SaveAttachments#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SaveAttachments/CS/thisaddin.cs#1)]  
  
## 参照  
 [メール アイテムの操作](../vsto/working-with-mail-items.md)   
 [方法: プログラムによって名前を指定してフォルダーを取得する](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行する](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [方法: プログラムによって特定のフォルダー内を検索する](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  