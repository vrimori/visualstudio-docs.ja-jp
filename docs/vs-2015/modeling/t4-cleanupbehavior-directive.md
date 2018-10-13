---
title: T4 CleanUpBehavior ディレクティブ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ee1882b6b63dbb2729070d32fcee7c1e58d280c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263403"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior ディレクティブ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

テキスト テンプレートを処理した後、appDomain を削除するには、次の行を含めます。  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 テキスト テンプレートは、ホスト プロセスから分離した appDomain で処理されます。 ほとんどの場合、1 つのテキスト テンプレートが処理されると、次のテンプレートを処理するために appdomain が再度使用されます。 ただし、CleanupBehavior を指定した場合、appDomain は削除され、新しい appDomain で次のテンプレートが処理されます。  
  
 これによってテキスト処理は遅くなりますが、リソースが破棄されたことを確認するうえで役立ちます。  
  
 このディレクティブは、Visual Studio ホストでのみ動作します。



