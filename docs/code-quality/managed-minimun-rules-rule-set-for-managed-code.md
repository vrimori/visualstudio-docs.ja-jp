---
title: "マネージ コードのマネージ最小規則ルール設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 4bfbf600850119078d91a988eb1e621cec9346e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>マネージ最小規則に対して規則セット マネージ コード
マネージ最小規則は、潜在的なセキュリティ ホール、アプリケーションのクラッシュ、その他の重要な論理エラーやデザイン エラーなど、コードで最も重要な問題に注目します。 プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA 1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|  
|[CA 1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します。|  
|[CA 2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドは破棄されなければなりません|  
|[CA 2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバー ロードします。|
