---
title: "ConnectionTimeout は 0 より大きくなければなりません。 | Microsoft Docs"
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
  - "vbrNetwork_BadConnectionTimeout"
ms.assetid: 15ac09a7-47f0-44f3-9e84-5bd10bd07450
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ConnectionTimeout は 0 より大きくなければなりません。
[My.Computer.Network Object](/dotnet/visual-basic/language-reference/objects/my-computer-network-object) を使用してファイルをアップロードとダウンロードする場合、`0` より大きい `connectionTimeout` を指定する必要があります。  
  
### このエラーを解決するには  
  
-   `0` より大きい `connectionTimeout` をご指定ください。  
  
## 参照  
 [My.Computer.Network.UploadFile メソッド](http://msdn.microsoft.com/ja-jp/5505ea3e-3dbd-460b-9f8f-62c84c0a4de6)   
 [My.Computer.Network.DownloadFile メソッド](http://msdn.microsoft.com/ja-jp/aeb7ed8f-1ac9-4242-ae57-9f35914eb329)   
 [How to: Upload a File](../Topic/How%20to:%20Upload%20a%20File%20in%20Visual%20Basic.md)   
 [How to: Download a File](../Topic/How%20to:%20Download%20a%20File%20in%20Visual%20Basic.md)   
 [Visual Basic による .NET Framework でのネットワーク操作](http://msdn.microsoft.com/ja-jp/c5379021-44ef-4d6a-acf5-e951fdcab6b2)