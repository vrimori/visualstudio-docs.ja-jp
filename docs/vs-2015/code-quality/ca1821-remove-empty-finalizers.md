---
title: 'Ca 1821: 空のファイナライザーを削除する |Microsoft Docs'
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
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f8aad4d616b3463afa44c8c776a06e6ca9159162
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222054"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: 空のファイナライザーを削除します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型が空か、基本型のファイナライザーを呼び出して、条件付きで出力されたメソッドのみを呼び出しているファイナライザーを実装します。

## <a name="rule-description"></a>規則の説明
 オブジェクトの有効期間の追跡に関連するパフォーマンス オーバーヘッドが増大するため、ファイナライザーは可能な限り使用しないでください。 オブジェクトは、収集する前に、ガベージ コレクターはファイナライザーを実行します。 これは、2 つのコレクションをオブジェクトを収集するために必要になることを意味します。 空のファイナライザーでは、この何の利点も追加のオーバーヘッドが発生します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 空のファイナライザーを削除します。 ファイナライザーがデバッグに必要な場合は、全体のファイナライザーを囲む`#if DEBUG / #endif`ディレクティブ。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールからのメッセージを抑制しないでください。 終了しないようにするには、パフォーマンスが低下し、メリットは提供されません。

## <a name="example"></a>例
 次の例は、空のファイナライザーを削除するか、不要なファイナライザーで囲む必要がありますが、`#if DEBUG / #endif`ディレクティブ、およびファイナライザーを使用して、`#if DEBUG / #endif`ディレクティブ正しくします。

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]



