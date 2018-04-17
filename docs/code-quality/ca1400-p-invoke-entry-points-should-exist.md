---
title: '1400: ca プラットフォーム呼び出しのエントリ ポイントは存在 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53e677308d5dcb5e89b410e4ab06a33a6c0caab4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: P/Invoke エントリ ポイントは存在しなければなりません
|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|CheckId|CA1400|  
|カテゴリ|Microsoft.Interoperability|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト メソッドが付いて、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>です。 アンマネージ ライブラリの位置を特定できないか、メソッドがライブラリ内の関数と一致しません。 ルールは、指定されているとおり、メソッドの名前を見つけることができません、アスタリスク、メソッド名では、'A' または 'W' ANSI またはメソッドのワイド文字バージョンで検索します。 ルールが持つ _ _stdcall 名の形式を使用して関数を特定しようとした一致が見つからない場合 (_MyMethod@1212 が引数の長さを表します)。 一致するものが見つからない、メソッド名が '#' で始まる場合は、ルールは、名前の参照ではなく序数参照として関数を検索します。  
  
## <a name="rule-description"></a>規則の説明  
 確認するコンパイル時のチェックがありませんでマークされたメソッド<xref:System.Runtime.InteropServices.DllImportAttribute>が参照されているアンマネージ DLL に配置されています。 指定した名前を持つ関数は、ライブラリではありませんか、メソッドへの引数では、関数の引数が一致しない、共通言語ランタイムは例外をスローします。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反の修正、修正を持つメソッドを<xref:System.Runtime.InteropServices.DllImportAttribute>属性。 アンマネージ ライブラリが存在し、メソッドを含むアセンブリと同じディレクトリにあることを確認してください。 ライブラリが存在し、正しく参照されている場合は、メソッド名、戻り値の型、および引数のシグネチャが、ライブラリ関数を一致することを確認します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 アンマネージ ライブラリが、それを参照するマネージ アセンブリと同じディレクトリにこの規則による警告は抑制しないでください。 アンマネージ ライブラリの場所を特定できない場合、この規則による警告を抑制して安全な場合があります。  
  
## <a name="example"></a>例  
 次の例は、規則に違反する型を示しています。 という名前の関数`DoSomethingUnmanaged`kernel32.dll で発生します。  
  
 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>