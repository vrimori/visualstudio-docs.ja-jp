---
title: "例外のトラブルシューティング : System.Net.Sockets.SocketException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SocketException クラス"
ms.assetid: 89e8194d-83b0-450f-91f5-548e5c13944d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Net.Sockets.SocketException
ネットワークでエラーが発生すると、<xref:System.Net.Sockets.SocketException> クラスと <xref:System.Net.Sockets.Socket> クラスによって <xref:System.Net.Dns> 例外がスローされます。  
  
## 関連するヒント  
 **Errorcode プロパティを調べ、ソケット エラーの原因を判断します。**  
 <xref:System.Net.Sockets.SocketException> クラスの既定のコンストラクターは、最後に発生したオペレーティング システムのソケット エラーを <xref:System.Net.Sockets.SocketException.ErrorCode%2A> プロパティに設定します。  
  
## 参照  
 <xref:System.Net.Sockets.SocketException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Secure Sockets Layerの使用](../Topic/Using%20Secure%20Sockets%20Layer.md)