---
title: 'Ca 1806: メソッドの結果を無視しない |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 90908bb85d88d939e2886f60083c0499cde2823c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: メソッドの結果を無視しない
|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 この警告のいくつかの理由があります。  
  
-   新しいオブジェクトを作成しても使用されていません。  
  
-   作成して新しい文字列を返すメソッドが呼び出され、新しい文字列は使用されません。  
  
-   HRESULT またはエラー コードを返す COM または P/invoke メソッドは使用されません。 規則の説明  
  
 不要なオブジェクトの作成と使用されていないオブジェクトの関連付けられているガベージ コレクションは、パフォーマンスを低下します。  
  
 文字列は不変であり String.ToUpper などのメソッド呼び出し元のメソッド内の文字列のインスタンスを変更する代わりに、文字列の新しいインスタンスを返します。  
  
 HRESULT またはエラー コードを無視する、またはリソース不足状態に予期しないエラー状態で動作する可能性があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 メソッド A は、使用されていません。 B オブジェクトの新しいインスタンスを作成する場合は、インスタンスを別のメソッドに引数として渡すまたは変数に代入します。 オブジェクトの作成が必要でない場合は、それを除去- または -  
  
 メソッド A が B のメソッドを呼び出しますが、メソッド B で返される新しい文字列インスタンスを使用しないかどうか。 インスタンスを引数として別のメソッドに渡して、変数に代入します。 または、必要がない場合は、呼び出しを削除します。  
  
 - または -  
  
 またはエラー コードをメソッド A が B のメソッドを呼び出しますが、HRESULT を使用しない場合、メソッドを返します。 条件付きステートメントの結果を使用、結果を変数に代入または別のメソッドに引数として渡します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 オブジェクトを作成する操作に何らかの目的に限り、この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、呼び出し元の String.Trim の結果を無視するクラスを示します。  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## <a name="example"></a>例  
 次の例では、以前の違反を修正するために String.Trim の結果を元に呼び出された変数に代入します。  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## <a name="example"></a>例  
 次の例では、作成したオブジェクトを使用しないメソッドを示します。  
  
> [!NOTE]
>  Visual Basic では、この違反を再現することはできません。  

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]   
  
## <a name="example"></a>例  
 次の例では、不要なオブジェクトの作成を削除することで上記の違反を修正します。  

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)] 

<!-- Examples don't exist for the below... -->
<!--
## Example  
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.  
  
## Example  
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.  
-->