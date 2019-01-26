---
title: マネージド コードの "マネージ最小規則" 規則セット
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c929abe75a22e705cc86f256dbbf7942280149d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013289"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>マネージド コードの "マネージ最小規則" 規則セット

マネージ最小規則は、潜在的なセキュリティ ホール、アプリケーションのクラッシュ、およびその他の重要なロジックとデザイン エラーなど、コードの最も重大な問題に集中します。 この規則セットを含める任意のカスタム規則セットで、プロジェクトを作成します。

|ルール|説明|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドは破棄されなければなりません|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします|
