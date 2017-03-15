---
title: "例外のトラブルシューティング : System.CannotUnloadAppDomainException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "CannotUnloadAppDomainException クラス"
ms.assetid: eeee07c3-fdbc-4c91-859b-a419d23be9ba
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.CannotUnloadAppDomainException
次のいずれかをアンロードしようとすると、<xref:System.CannotUnloadAppDomainException> 例外がスローされます。  
  
-   既定のアプリケーション ドメイン。これはアプリケーションの実行中は常に読み込んでおく必要があります。  
  
-   実行を即時に中断できない実行中のスレッドがあるアプリケーション ドメイン。  
  
-   既にアンロードされているアプリケーション ドメイン。  
  
## 関連するヒント  
 **既定のアプリケーション ドメイン、実行中のスレッドがあるアプリケーション ドメイン、または既にアンロードされているアプリケーション ドメインをアンロードしようとしていないことを確認します。**  
 これらの状態ではこの例外がスローされます。 詳細については、「<xref:System.AppDomain.Unload%2A>」を参照してください。  
  
## 参照  
 <xref:System.CannotUnloadAppDomainException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)