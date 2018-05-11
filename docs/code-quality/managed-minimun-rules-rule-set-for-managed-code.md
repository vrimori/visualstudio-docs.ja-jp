---
title: マネージ最小規則に対して規則セット マネージ コード
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ec566fb45b68505849639af00f85bbe81aa6f16
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>マネージ最小規則に対して規則セット マネージ コード
マネージ最小規則は、潜在的なセキュリティ ホール、アプリケーションのクラッシュ、その他の重要な論理エラーやデザイン エラーなど、コードで最も重要な問題に注目します。 プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。

|ルール|説明|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します。|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドは破棄されなければなりません|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバー ロードします。|
