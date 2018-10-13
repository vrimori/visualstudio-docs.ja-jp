---
title: 'Ca 1504: 紛らわしいフィールド名の確認 |Microsoft Docs'
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
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 40a97c8e0a00537c8e44bb756c9ef56a00992ca6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293489"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: 紛らわしいフィールド名を確認します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 インスタンス フィールドの名前の名前または「s _」で始まり、 `static` (`Shared`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) フィールドが「m _」で開始します。

## <a name="rule-description"></a>規則の説明
 「S _」で始まるフィールド名は、多くのユーザーによって静的データに関連付けられます。 同様に、「m _」で始まるフィールド名は、インスタンス (メンバー) のデータに関連付けられます。 保守が簡単なコードは、名は、一般的に使用される規則に従う必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、適切なプレフィックスを使用して、フィールド名を変更します。 または、追加または削除して、現在のサフィックスと一致するフィールドを変更、`static`修飾子。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。



