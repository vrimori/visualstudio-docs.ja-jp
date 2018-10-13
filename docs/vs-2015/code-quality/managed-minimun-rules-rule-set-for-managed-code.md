---
title: マネージ コードの"マネージ最小規則"規則の設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f67b9e28069a1717ad500b7e8895a363db715fda
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251065"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>マネージド コードの "マネージ最小規則" 規則セット
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

最小の管理規則は、潜在的なセキュリティ ホール、アプリケーションのクラッシュ、およびその他の重要なロジックとデザイン エラーなど、コードの最も重大な問題に集中します。 プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します。|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドを破棄する必要があります。|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバー ロードします。|



