---
title: "例外のトラブルシューティング : System.Net.WebException | Microsoft Docs"
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
  - "WebException クラス"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Net.WebException
プラグ可能なプロトコルでネットワークにアクセスしているときにエラーが発生すると、<xref:System.Net.WebException> 例外がスローされます。  
  
## 関連するヒント  
 **例外の Response プロパティを調べて、要求に失敗した原因を判断します。**  
 <xref:System.Net.WebException> 例外が <xref:System.Net.WebRequest> クラスの派生クラスによってスローされた場合、<xref:System.Net.WebException.Response%2A> プロパティにはアプリケーションへのインターネット応答が示されます。  
  
 **例外の Status プロパティを調べて、要求に失敗した原因を判断します。**  
 例外の <xref:System.Net.WebException.Status%2A> プロパティには、このエラーのステータス情報が示されます。 詳細については、「<xref:System.Net.WebExceptionStatus>」を参照してください。  
  
 **XML Web サービスにステップ インしているときにタイムアウトになった場合は、XML Web サービス呼び出しのタイムアウト値を無制限に設定します。**  
 詳細については、「[エラー ： Web サービスのデバッグ中にタイムアウトになりました。](../debugger/error-timeout-while-debugging-web-services.md)」を参照してください。  
  
## 参照  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [方法: WebRequest クラスを使用してデータを送信する](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [方法: WebRequest クラスを使用してデータを要求する](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [方法: WebRequest に一致するプロトコル固有の WebResponse を取得する](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)