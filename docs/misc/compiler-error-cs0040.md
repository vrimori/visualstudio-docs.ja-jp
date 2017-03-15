---
title: "コンパイラ エラー CS0040 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0040"
ms.assetid: 6a600166-0335-4b6d-b050-6821b4624c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0040
デバッグ情報ファイルを作成中に予期しないエラーが発生しました \-\- 'reason'  
  
 このエラーは、[\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) コンパイラ オプションを使用する場合に発生する可能性があり、コンパイラが .pdb ファイルに書き込むことができないことを示します。 このエラーの解決策としては、Visual Studio を再インストールする、コンパイラにファイルまたはディレクトリへの書き込みアクセスが許可されていることを確認する、\/debug を使用してコンパイルしないなどが考えられます。