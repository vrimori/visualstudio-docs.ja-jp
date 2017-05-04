---
title: "方法: プログラムによって連絡先から電子メール アドレスを検索する | Microsoft Docs"
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
  - "電子メール [Visual Studio での Office 開発]、検索"
  - "連絡先 [Visual Studio での Office 開発]、検索"
  - "検索 (連絡先を)"
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 方法: プログラムによって連絡先から電子メール アドレスを検索する
  この例では、連絡先フォルダーから、電子メール アドレスに **example.com** というドメイン名が含まれている連絡先を検索します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_OL_SearchEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchEmail/CS/thisaddin.cs#1)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   電子メール アドレスに **example.com** というドメイン名が含まれており \(たとえば、`somebody@example.com`\)、姓と名が設定されている連絡先。  
  
## 参照  
 [連絡先アイテムの操作](../vsto/working-with-contact-items.md)   
 [方法: プログラムによって電子メールを送信する](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [方法: プログラムによって Outlook の連絡先にアクセスする](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [方法: プログラムによって Outlook の連絡先にエントリを追加する](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  