---
title: "例外のトラブルシューティング : Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
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
  - "CantStartSingleInstanceException 例外"
  - "Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException 例外"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
この例外は、単一インスタンスのアプリケーションの 2 つ目のインスタンスが、元のインスタンスに接続できない場合にスローされます。  
  
## コメント  
 この問題では以下の原因が考えられます。  
  
-   元のインスタンスが応答を停止した。  
  
-   カーネル オブジェクトを作成するためのアクセス許可がアプリケーションにない。  
  
     カーネル オブジェクトの基本名は、アセンブリの GUID、メジャー バージョン番号、およびマイナー バージョン番号を連結したものです。 たとえば、3639f15d\-9547\-43da\-8145\-60da347829915.1 という基本名になることがあります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)