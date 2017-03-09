---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. | Microsoft Docs"
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
  - "vs.message.0x800A002A"
  - "vs.message.VB_E_IDWOLENOTRESPONDING"
ms.assetid: 0a4efbb7-72de-43a8-a51a-4a7a24ec743a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft.
サーバー アプリケーションが現在の要求を完了していません。  
  
 このエラーは、ウイルス対策ソフトウェアによって、devenv.exe の一部のプロセスがブロックされているために発生する場合もあります。  本製品では、複数の機能でスクリプトが使用されており、このスクリプトがウイルス対策ソフトウェアによってブロックされる場合があります。  関連情報については、[http:\/\/support.microsoft.com\/kb\/306905\/ja](http://support.microsoft.com/kb/306905/ja) の「起動時に Visual IDE を開けない、またはエラー メッセージ "アプリケーションを起動できません" が表示される」を参照してください。  
  
### このエラーを解決するには  
  
-   \[切り替え\] をクリックしてアプリケーションを開き、問題を調べます。  
  
     または  
  
     \[再試行\] をクリックして、サーバー アプリケーションが要求の処理を完了するまで待ちます。  
  
### ウイルス対策ソフトウェアに関連するエラーを解決するには  
  
-   使用しているウイルス対策ソフトウェアで、devenv.exe から起動されたスクリプトの実行を許可するように指定します。  詳細については、ウイルス対策ソフトウェア製品のドキュメントを参照してください。