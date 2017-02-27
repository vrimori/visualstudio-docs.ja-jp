---
title: "移植性に関する警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.PortabilityRules"
helpviewer_keywords: 
  - "移植性に関する警告"
  - "マネージ コード分析の警告、移植性に関する警告"
  - "警告、移植性"
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# 移植性に関する警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

移植性に関する警告では、異なるオペレーティング システム間の移植性がサポートされます。  
  
## このセクションの内容  
  
|規則|説明|  
|--------|--------|  
|[CA1900: 値型フィールドはポータブルでなければなりません](../code-quality/ca1900-value-type-fields-should-be-portable.md)|この規則は、明示的なレイアウト属性によって宣言された構造体が、64 ビット オペレーティング システムでアンマネージ コードにマーシャリングされるときに、適切にアライメントされるかどうかを確認します。|  
|[CA1901: P\/Invoke 宣言はポータブルでなければなりません](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|この規則では、P\/Invoke の各パラメーターのサイズと戻り値が評価され、32 ビットおよび 64 ビット オペレーティング システムのアンマネージ コードにマーシャリングされたときのサイズが正しいことが検証されます。|  
|[CA1903: 対象のフレームワークから API のみを使用します](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|メンバーまたは型が、プロジェクトの対象のフレームワークに含まれていない Service Pack で導入されたメンバーまたは型を使用しています。|