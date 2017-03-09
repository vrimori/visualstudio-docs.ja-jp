---
title: "エラー報告を自動的に送信できません | Microsoft Docs"
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
  - "bc2027"
  - "vbc2027"
helpviewer_keywords: 
  - "BC2027"
ms.assetid: 84ba8580-2234-46d1-b4a5-94b03f64c0c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# エラー報告を自動的に送信できません
エラー報告を自動的に送信できません。 エラー報告の送信設定を構成するには、'http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039' を参照してください。  
  
 `/errorreport:send` コンパイラ オプションを指定しましたが、コンピューターはエラー レポートを自動的に送信するよう構成されていません。 Visual Basic コンパイラの内部エラーについての情報は、一切送信されません。  
  
 **エラー ID:** BC2027  
  
### このエラーを解決するには  
  
-   `/errorreport:send` コンパイラ オプションを削除するか、`/errorreport:queue`、`/errorreport:prompt`、または `/errorreport:none` で置き換えます。  
  
     または  
  
-   [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039) の手順に従って、エラーの自動報告を有効にします。  
  
## 参照  
 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)   
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039)