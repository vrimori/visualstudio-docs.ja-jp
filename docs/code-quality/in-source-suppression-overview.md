---
title: コード分析の警告を抑制します。
ms.date: 12/01/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: a377f08a8f0a3397aee778a71c74457420dec70f
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54835059"
---
# <a name="suppress-code-analysis-warnings"></a>コード分析の警告を抑制します。

警告が適用可能でないことを示すと便利です。 これは、チーム メンバーのコードをレビューしたこと、および警告を抑制することを示します。 ソース内抑制 (ISS) は、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>警告を抑制する属性。 属性は、警告を生成したコードのセグメントの近くに配置できます。 追加することができます、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>入力して、ソース ファイルに属性で警告のショートカット メニューを使用することも、**エラー一覧**に自動的に追加します。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性は、条件付き属性、コンパイル時に CODE_ANALYSIS コンパイルのシンボルが定義されている場合にのみ、マネージ コード アセンブリの IL メタデータに含まれています。

C++/cli CLI、マクロの CA を使用して\_抑制\_メッセージまたは CA\_GLOBAL\_属性を追加するヘッダー ファイルで SUPPRESS_MESSAGE。

> [!NOTE]
> ソース内抑制をソース内抑制のメタデータを誤って発送を防ぐために、リリース ビルドで使用しないでください。 さらに、ソース内抑制の処理コスト、ため、アプリケーションのパフォーマンスが低下することができます。

> [!NOTE]
> プロジェクトを Visual Studio 2017 に移行する場合にコード分析の警告の数が多いを突然直面する可能性があります。 これらの警告の発信元[Roslyn アナライザー](roslyn-analyzers-overview.md)します。 警告を解決する準備ができて場合、を選択して抑制するすべてのことができます**分析** > **コード分析を実行し、アクティブな懸案事項の抑制**します。
>
> ![コード分析を実行して、Visual Studio での問題を抑制します。](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage 属性

選択すると**抑制**でコード分析警告のコンテキストまたは右クリック メニューから、**エラー一覧**、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>コードまたはプロジェクトのグローバル抑制を属性が追加されますファイルです。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性は、次の形式。

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

属性のプロパティは次のとおりです。

- **カテゴリ**-ルールが定義されているカテゴリ。 コード分析ルールのカテゴリの詳細については、次を参照してください。[マネージ コードの警告](../code-quality/code-analysis-for-managed-code-warnings.md)します。

- **CheckId** -ルールの識別子。 サポートには、短期および長期のルールの識別子名の両方が含まれます。 短い名前が CAXXXX;長い名前は、CAXXXX:FriendlyTypeName です。

- **位置揃え**-メッセージの抑制の理由を文書化に使用されるテキスト。

- **MessageId** -各メッセージの問題の一意識別子。

- **スコープ**-警告を抑制するターゲット。 ターゲットが指定されていない場合は、属性のターゲットに設定されます。 サポートされている[スコープ](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope)次に示します。

   - `module`

   - `resource`

   - `type`

   - `member`

   - `namespace` -このスコープは、名前空間自体に対して警告を抑制します。 名前空間内の型に対して警告は抑制されません。

   - `namespaceanddescendants` -(New for Visual Studio 2019) は、このスコープは、名前空間とその子孫のすべてのシンボルでの警告を抑制します。 `namespaceanddescendants`値 Roslyn アナライザー、に対してのみ有効ですし、FxCop に基づくバイナリのスタティック分析では無視されます。

- **ターゲット**- 警告を抑制するターゲットを指定するために使用する識別子。 項目の完全修飾名を含める必要があります。

## <a name="suppressmessage-usage"></a>SuppressMessage 使用状況

レベルでコード分析の警告が抑制されます、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性を適用します。 たとえば、アセンブリ、モジュール、型、メンバー、またはパラメーターのレベルで属性を適用できます。 この目的は、違反が発生する抑制については、コードに密に結合します。

抑制の一般的な形式には、ルールのカテゴリと、ルール名の省略可能な人間が判読できる形式を格納して、ルールの識別子が含まれています。 例:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

ソース内抑制のメタデータを最小限に抑えるための厳密なパフォーマンス上の理由がある場合は、ルール名を省略できます。 ルール カテゴリとそのルールの ID 構成規則を十分に一意の識別子。 例:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

保守容易性の理由から、ルール名を省略することはお勧めしません。

## <a name="suppress-selective-violations-within-a-method-body"></a>メソッド本体の内部の選択的な違反を抑制します。

抑制の属性は、メソッドに適用できますが、メソッド本文内に埋め込むことはできません。 つまり、追加する場合、特定のルールのすべての違反が抑制されます、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性をメソッド。

場合によっては、将来のコードが自動的に、コード分析規則から除外されていないように例については、違反の特定のインスタンスを抑制する場合があります。 これは、使用することは特定のコード分析規則、`MessageId`のプロパティ、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性。 一般に、レガシ規則の違反を特定のシンボル (ローカル変数またはパラメーター) に関して、`MessageId`プロパティ。 [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)ようなルールの例を示します。 ただし、実行可能コード (非シンボル) の違反のレガシ規則を順守しない、`MessageId`プロパティ。 さらに、.NET コンパイラ プラットフォーム ("Roslyn") のアナライザーを使用しない、`MessageId`プロパティ。

規則の特定のシンボルの違反を抑制するは、シンボルの名前を指定します。、`MessageId`のプロパティ、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性。 次の例では、コードの 2 つの違反を[CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;に 1 つずつ、`name`変数とに 1 つずつ、`age`変数。 違反にのみ、`age`シンボルが抑制されます。

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>生成されたコード

マネージ コード コンパイラと一部のサード パーティ製ツールは、迅速なコードの開発を促進するためのコードを生成します。 ソース ファイルに表示されるコンパイラによって生成されたコードがでマークされたは、通常、`GeneratedCodeAttribute`属性。

コード分析の警告と生成されたコードのエラーを抑制するかどうかを選択できます。 このような警告とエラーを抑制する方法については、次を参照してください。[方法。生成されたコードの警告を抑制する](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)します。

> [!NOTE]
> コード分析を無視`GeneratedCodeAttribute`アセンブリ全体または 1 つのパラメーターのいずれかに適用されます。

## <a name="global-level-suppressions"></a>グローバル レベルの抑制

マネージ コード分析ツールを検査`SuppressMessage`アセンブリ、モジュール、型、メンバー、またはパラメーターのレベルで適用される属性。 リソースと名前空間に対する違反が発生します。 これらの違反、グローバル レベルで適用する必要がありますスコープし、は対象とします。 たとえば、次のメッセージには、名前空間の違反が抑制されます。

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 警告を抑制するときに`namespace`スコープ、名前空間自体に対して警告を抑制します。 名前空間内の型に対する警告は抑制されません。

任意の抑制は、明示的なスコープを指定することによって表現できます。 このような抑制は、グローバル レベルでライブする必要があります。 メンバー レベルの抑制は、型を修飾して指定できません。

グローバル レベルの抑制は、明示的に指定されたユーザーのソースにマップされていないコンパイラによって生成されたコードを参照するメッセージを抑制する唯一の方法です。 たとえば、次のコードでは、コンパイラによって生成されたコンス トラクターに対する違反が抑制されます。

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` 項目の完全修飾名を常に含まれています。

## <a name="global-suppression-file"></a>グローバル抑制ファイル

グローバル抑制はグローバル レベルの抑制またはターゲットが指定されていない抑制の抑制が保持されます。 たとえば、アセンブリ レベルの違反の抑制は、このファイルに格納されます。 さらに、いくつかの ASP.NET の抑制は、プロジェクト レベルの設定は、フォームのコードを利用できないために、このファイルに格納されます。 グローバル抑制ファイルが作成され、選択した初めてのプロジェクトに追加、**プロジェクト抑制ファイル内**のオプション、**抑制**コマンド、**エラー一覧**ウィンドウ。

## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Roslyn アナライザーを使用して、](../code-quality/use-roslyn-analyzers.md)