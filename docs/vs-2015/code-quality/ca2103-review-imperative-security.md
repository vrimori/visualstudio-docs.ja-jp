---
title: 'Ca 2103: 命令型のセキュリティの確認 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dd075c4c6edc84422c6c09846d23ef0049d55002
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886555"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: 命令型のセキュリティを確認します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドが強制セキュリティを使用しています。また、そのメソッドで、確認要求がアクティブな場合に変更できるステータス情報または戻り値を使用して、アクセス許可を構築している可能性があります。

## <a name="rule-description"></a>規則の説明
 強制セキュリティでは、管理対象のオブジェクトを使用して、メタデータにアクセス許可とアクションを格納する属性を使用して、宣言型のセキュリティと比較して、コードの実行中に、アクセス許可とセキュリティ アクションを指定します。 強制セキュリティは、アクセス許可オブジェクトの状態を設定し、実行時までが使用できない情報を使用してセキュリティ アクションを選択することができますので、非常に柔軟性があります。 あるは、柔軟性は、アクションが有効になっている限り、アクセス許可の状態を判断するために使用のランタイム情報が変更されるリスクをものです。

 できる限り、宣言セキュリティを使用します。 宣言型の要求が簡単に理解できます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 アクセス許可の状態は、アクセス許可が使用されている限り、変更できる情報を依存しないことを確認する命令型のセキュリティ確認要求を確認します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 アクセス許可は、データの変更に依存しない場合は、この規則による警告を抑制するのには安全です。 ただし、等価な宣言型に強制確認要求を変更することをお勧めします。

## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



