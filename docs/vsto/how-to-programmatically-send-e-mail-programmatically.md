---
title: "方法: プログラムによって電子メールを送信する | Microsoft Docs"
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
  - "電子メール [Visual Studio での Office 開発], 送信"
  - "メール アイテム [Visual Studio での Office 開発], 送信 (電子メールを)"
  - "Outlook [Visual Studio での Office 開発], 作成 (電子メールを)"
  - "Outlook [Visual Studio での Office 開発], 送信 (電子メールを)"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: プログラムによって電子メールを送信する
  この例では、電子メール アドレスに **example.com** というドメイン名を含む連絡先に電子メール メッセージを送信します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   電子メール アドレスに **example.com** というドメイン名を含む連絡先。  
  
## 信頼性の高いプログラミング  
 **example.com** というドメイン名を検索するフィルター コードは削除しないでください。  このフィルターを削除すると、そのソリューションでは、すべての連絡先に電子メール メッセージが送信されてしまいます。  
  
## 参照  
 [メール アイテムの操作](../vsto/working-with-mail-items.md)   
 [方法: プログラムによって電子メール アイテムを作成する](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [方法: プログラムによって Outlook の連絡先にアクセスする](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [方法: プログラムによって電子メール メッセージを受信したときにアクションを実行する](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  