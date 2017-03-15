---
title: "例外のトラブルシューティング : System.AccessViolationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.AccessViolationException 例外"
  - "AccessViolationException クラス"
ms.assetid: 7f09315d-8aad-4ab1-8b5e-21a8c97f6c14
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.AccessViolationException
<xref:System.AccessViolationException> は、保護されたメモリに対して読み取りまたは書き込みを行おうとするとスローされます。  
  
## 関連するヒント  
 アクセスしようとしているメモリが割り当て済みであることを確認します。  
 自動メモリ管理は、共通言語ランタイムが提供するサービスの 1 つです。 このサービスを利用するために、マネージ コードに移行することもできます。 詳細については、「[自動メモリ管理](../Topic/Automatic%20Memory%20Management.md)」を参照してください。  
  
 アクセスしようとしているメモリが破損していないことを確認します。  
 無効なポインターによって複数の読み取り操作または書き込み操作が発生すると、メモリが破損する場合があります。  
  
### コメント  
 アンマネージ コードまたはアンセーフ コードでは、割り当て済みでないメモリ、またはアクセスできないメモリに対して読み取りまたは書き込みを行おうとするとアクセス違反が発生します。 無効なポインターによる読み取りまたは書き込みがすべてアクセス違反になるとは限らないため、通常、アクセス違反は、無効なポインターによって複数の読み取りまたは書き込みが発生したこと、およびメモリが破損している可能性があることを示します。  
  
 マネージ コードでは、すべての参照は有効であるか、null であるかのどちらかです。<xref:System.NullReferenceException> は、検証可能なコード内の null 参照を参照しようとするすべての操作に対してスローされます。  
  
 安全でないマネージ コードで発生したアクセス違反は、プラットフォームに応じて <xref:System.NullReferenceException> または <xref:System.AccessViolationException> として表現されます。  
  
 アンマネージ コードのアクセス違反は、そのままマネージ コードに返された場合、常に <xref:System.AccessViolationException> 内にラップされます。  
  
## 参照  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [メモリ管理 : 例](../Topic/Memory%20Management:%20Examples.md)   
 [自動メモリ管理](../Topic/Automatic%20Memory%20Management.md)