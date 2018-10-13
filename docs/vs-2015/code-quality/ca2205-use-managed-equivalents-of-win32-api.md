---
title: 'CA2205: 管理と同等の Win32 API の使用 |Microsoft Docs'
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
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf944335259568e77c5470c53db511c5d15bdf1e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240254"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Win32 API に相当するマネージド API を使用します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメソッドが定義されているし、に、同等の機能を持つメソッドが存在する、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]クラス ライブラリ。

## <a name="rule-description"></a>規則の説明
 プラットフォーム呼び出しメソッドをアンマネージ DLL 関数の呼び出しに使用されを使用して定義、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性、または`Declare`Visual basic のキーワード。 定義済みの正しくない、プラットフォーム呼び出しメソッド パラメーターと戻り値のデータ型、および呼び出し規約、および文字など、不適切なフィールドの仕様のマッピングの問題のある不適切な名前の関数などの問題のためのランタイム例外につながる設定します。 、使用可能な場合は、一般に簡素化され、以下のエラーを定義し、非管理対象のメソッドを直接呼び出すよりも同等のマネージ メソッドを呼び出すが生じやすい。 プラットフォーム呼び出しメソッド対処する必要がある追加のセキュリティ問題につながることもできます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、アンマネージ関数の呼び出しを同等のマネージの呼び出しで置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 推奨される代替メソッドが必要な機能を提供しない場合は、この規則による警告を抑制します。

## <a name="example"></a>例
 プラットフォームは、次の例は、規則に違反するメソッドの定義を呼び出します。 さらに、プラットフォーム呼び出しメソッドの呼び出しし、同等のマネージ メソッドが表示されます。

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1404: P/Invoke の直後に GetLastError を呼び出します](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: P/Invoke を NativeMethods クラスに移動します](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke エントリ ポイントは存在しなければなりません](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke は参照可能になりません](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



