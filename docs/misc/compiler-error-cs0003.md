---
title: "コンパイラ エラー CS0003 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0003"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0003"
ms.assetid: 6aee4b0e-e24f-47b5-8281-ca4c7ee8a3cf
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0003
メモリが不足しています  
  
 コンパイラでは、コンパイルを完了するために十分な仮想メモリを割り当てることができませんでした。 不要なアプリケーションをすべて閉じて、もう一度コンパイルします。  
  
 ページファイル サイズを増やすことが必要な場合もあるため、空きディスク領域があることを確認してください。  
  
 このエラーは、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] と C\# コンパイラのバージョンが一致しなかったり、C\# コンパイラをサポートする 1 つまたは複数のファイルが破損しているために発生する場合もあります。この場合には、Visual Studio を再インストールしてください。