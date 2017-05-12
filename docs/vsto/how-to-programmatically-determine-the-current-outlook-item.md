---
title: "方法: プログラムによって現在の Outlook のアイテムを確認する"
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
  - "電子メール [Visual Studio での Office 開発], 現在のアイテム"
  - "メール アイテム [Visual Studio での Office 開発], 現在の"
  - "Outlook [Visual Studio での Office 開発], 現在のアイテム"
  - "SelectionChanged イベント"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 方法: プログラムによって現在の Outlook のアイテムを確認する
  この例では、Explorer.SelectionChange イベントを使用して、現在のフォルダーの名前、および選択されたアイテムに関する一部の情報を表示します。  その後、選択されたアイテムを表示します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Microsoft Office Outlook 内の予定、連絡先、および電子メールの各アイテム。  
  
## 参照  
 [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)   
 [方法: プログラムによって名前を指定してフォルダーを取得する](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによって特定の連絡先を検索する](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  