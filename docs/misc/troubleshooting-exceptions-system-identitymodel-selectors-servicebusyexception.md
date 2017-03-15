---
title: "例外のトラブルシューティング : System.IdentityModel.Selectors.ServiceBusyException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ServiceBusyException 例外"
  - "System.IdentityModel.Selectors.ServiceBusyException 例外"
ms.assetid: 88acdc6b-45ad-40c6-aa5c-3b56244edcee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IdentityModel.Selectors.ServiceBusyException
<xref:System.IdentityModel.Selectors.ServiceBusyException> 例外は、CardSpace サービスが他の要求の処理でビジー状態であることを示すためにスローされます。 CardSpace は要求をキューに配置しないので、一度に処理できる要求は 1 つだけです。  
  
 CardSpace の別のインスタンスが実行されているかどうかを確認してください。 別のインスタンスが実行中の場合は、タスク マネージャーで icardagt.exe プロセスを終了することにより、実行を停止します。  
  
## 参照  
 <xref:System.IdentityModel.Selectors.ServiceBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)