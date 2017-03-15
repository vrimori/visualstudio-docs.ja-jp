---
title: "例外のトラブルシューティング : System.Net.HttpListenerException | Microsoft Docs"
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
  - "HttpListenerException クラス"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Net.HttpListenerException
HTTP 要求の処理中にエラーが発生すると、<xref:System.Net.HttpListenerException> がスローされます。  
  
## 関連するヒント  
 登録済みの URI プレフィックスを登録しようとしていないか確認します。  
 URI プレフィックスが既に登録されている場合、この例外が発生します。  
  
 HTTP 要求が有効であることを確認します。  
 <xref:System.Net.HttpListener> の初期化時や HTTP 要求に対する応答の作成時または送信時にエラーが発生すると、<xref:System.Net.HttpListener> クラスやその関連クラスによってこの例外がスローされます。  
  
 `HttpListenerPrefixCollection.Add` メソッドを使用している場合は、`uriPrefix` がまだ追加されていないことを確認します。  
 この例外は、別の <xref:System.Net.HttpListener> が既にプレフィックス `uriPrefix` を追加している場合にスローされます。  
  
## 参照  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)