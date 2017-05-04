---
title: "方法: プログラムによって Web ページを Outlook のフォルダーに関連付ける | Microsoft Docs"
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
  - "フォルダー [Visual Studio での Office 開発], Web ページおよび"
  - "Outlook [Visual Studio での Office 開発], Web ページ (フォルダーにアタッチされている)"
  - "Web ページ [Visual Studio での Office 開発], Outlook フォルダー"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 方法: プログラムによって Web ページを Outlook のフォルダーに関連付ける
  この例では、Microsoft Office Outlook で `HtmlView` という名前のフォルダーを確認します。  フォルダーが存在しない場合は、フォルダーが作成され、そのフォルダーに Web ページが割り当てられます。  フォルダーが存在する場合は、フォルダーの内容が表示されます。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## 参照  
 [フォルダーの操作](../vsto/working-with-folders.md)   
 [方法: プログラムによって名前を指定してフォルダーを取得する](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [方法: プログラムによってカスタム フォルダーのアイテムを作成する](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  