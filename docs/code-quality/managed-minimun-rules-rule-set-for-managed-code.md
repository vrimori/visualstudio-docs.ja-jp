---
title: "マネージ コードの &quot;マネージ最小規則&quot; 規則セット | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
caps.handback.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# マネージ コードの &quot;マネージ最小規則&quot; 規則セット
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マネージ最小限の規則は、セキュリティ ホール、アプリケーション クラッシュ、そのほかの重要な論理エラーやデザイン エラーなど、コードに含まれる最も重要な問題に関するものです。  プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。  
  
|規則|説明|  
|--------|--------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドは破棄されなければなりません|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします。|