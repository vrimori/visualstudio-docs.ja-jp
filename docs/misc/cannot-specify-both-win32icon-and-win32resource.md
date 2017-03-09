---
title: "/win32icon と /win32resource を両方指定することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc2023"
  - "bc2023"
helpviewer_keywords: 
  - "BC2023"
ms.assetid: 60914807-1fde-4fef-9c6f-6f4a62527eed
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32icon と /win32resource を両方指定することはできません
`/win32resource` オプションと `/win32icon` オプションは、どちらもアイコンの情報を出力ファイルに挿入するので、相互に排他的です。  
  
 **エラー ID:** BC2023  
  
### このエラーを解決するには  
  
-   `/win32icon` オプションのみを使用して .ico ファイルを出力ファイルに挿入します。 この .ico ファイルは、Windows エクスプローラーでは出力ファイルを表します。  
  
     — または —  
  
-   `/win32resource` オプションのみを使用して Win32 リソース ファイルを出力ファイルに挿入します。 Win32 リソースは、バージョンまたはビットマップ \(アイコン\) 情報を格納することができ、Windows エクスプローラーでアプリケーションを識別するのに役立ちます。  
  
## 参照  
 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)   
 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)