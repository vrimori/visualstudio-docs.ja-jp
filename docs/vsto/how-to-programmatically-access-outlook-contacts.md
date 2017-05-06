---
title: "方法: プログラムによって Outlook の連絡先にアクセスする"
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
  - "連絡先 [Visual Studio での Office 開発], 検索"
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 方法: プログラムによって Outlook の連絡先にアクセスする
  この例では、指定された検索文字列が姓に含まれるすべての連絡先を検索します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/backup/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/VB/thisaddin.vb#1)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   **\[連絡先\]** フォルダー内にある、姓に "**Na"** という文字列が含まれる連絡先 \(Tzipi Butnaru など\)  
  
## 参照  
 [連絡先アイテムの操作](../vsto/working-with-contact-items.md)   
 [方法: プログラムによって Outlook の連絡先にエントリを追加する](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [方法: プログラムによって特定の連絡先を検索する](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [方法: プログラムによって連絡先から電子メール アドレスを検索する](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [方法: プログラムによって Outlook の連絡先を削除する](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  