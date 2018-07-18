---
title: 'CA2221: ファイナライザーは保護されなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25d67c99a9c2b30461170b7e8b5090e0c08241ee
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917870"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: ファイナライザーは保護されなければなりません
|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリック型では、ファミリ (保護) アクセスが指定されていませんが、不要なファイナライザーを実装します。

## <a name="rule-description"></a>規則の説明
 ファイナライザーは、ファミリ アクセス修飾子を使用する必要があります。 このルールは、c#、Visual Basic および Visual C コンパイラによって強制されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、ファミリ アクセスできるように、ファイナライザーを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 高度な .NET 言語でこの規則に違反することはできません。Microsoft Intermediate Language を作成している場合は、違反することができます。

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>関連項目
 [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)