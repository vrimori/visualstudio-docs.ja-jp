---
title: 'CA2149: 透過的メソッドは、ネイティブ コード内に呼び出しを行ってはならない'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: a30e3581101b1065f26d01e70657981a5220e56c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548745"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: 透過的メソッドは、ネイティブ コード内に呼び出しを行ってはならない
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドは、P/invoke などのメソッド スタブを使用してネイティブ関数を呼び出します。

## <a name="rule-description"></a>規則の説明
 このルールは、P/invoke 経由など、ネイティブ コードを直接呼び出すすべての透過的メソッドに対して適用されます。 この規則に違反が発生、<xref:System.MethodAccessException>レベル 2 の透過性モデルとの完全な要求で<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>レベル 1 の透過性モデルでします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、マークのメソッドを呼び出すネイティブ コードと、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]