---
title: "例外のトラブルシューティング : System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DeploymentDownloadException クラス"
  - "アプリケーションの配置 [C#]、DeploymentDownloadException クラス"
  - "アプリケーションの配置 [C#]、DeploymentDownloadException クラス"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.DeploymentFramework.DeploymentDownloadException
アプリケーションの更新プログラムをダウンロードしているときに、何らかのネットワーク例外が発生すると、`T:System.DeploymentFramework.DeploymentDownloadException` が発生します。  
  
## 関連するヒント  
 **InnerException を調べて、基になる System.Net または System.IO の例外を確認します。**  
 この例外は、アプリケーションの更新プログラムのダウンロード中にネットワーク例外が発生した場合に発生します。 例外の <xref:System.Exception.InnerException%2A> プロパティを調べて、基になっている例外を確認します。  
  
## 参照  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)