---
title: "例外のトラブルシューティング : System.Security.VerificationException | Microsoft Docs"
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
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "VerificationException クラス"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Security.VerificationException
セキュリティ ポリシーによってコードがタイプ セーフでなければならず、検査プロセスでそのコードがタイプ セーフかどうかを確認できない場合、<xref:System.Security.VerificationException> 例外がスローされます。  
  
## 関連するヒント  
 アプリケーションがクラス ライブラリの競合するバージョンを 2 つ読み込んでいないことを確認します。  
 検査プロセスの一部として、Microsoft Intermediate Language \(MSIL\) がタイプ セーフかどうかがチェックされます。これによって各オブジェクトを安全に分離し、偶発的または意図的な破壊から保護できます。 詳細については、「[タイプ セーフとセキュリティ](http://msdn.microsoft.com/ja-jp/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)」をご覧ください。  
  
## 参照  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)