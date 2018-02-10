---
title: "Visual Studio でコード分析の警告を抑制する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 5862b164c72c8f07c78db8948face95edfde357c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="suppressing-code-analysis-warnings"></a>コード分析警告の抑制

警告が適用可能でないことを示すために便利です。 これは、チーム メンバーのコードをレビューしたこと、および警告を抑制することを示します。 ソース内抑制 (ISS) 使用して、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>警告を抑制する属性。 属性は、警告を生成したコード セグメントの近くに配置できます。 追加することができます、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>入力して、その属性をソース ファイルで警告のショートカット メニューを使用することも、**エラー一覧**に自動的に追加します。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> CODE_ANALYSIS コンパイル シンボルがコンパイル時に定義されている場合にのみ、属性は、条件付き属性、マネージ コード アセンブリの IL メタデータに含まれています。

C + + CLI、CA のマクロを使用\_抑制\_メッセージまたは CA\_グローバル\_属性を追加するヘッダー ファイルで SUPPRESS_MESSAGE です。

> [!NOTE]
> ソース内抑制メタデータを誤って配布を防ぐために、リリース ビルドのソース内抑制を使用する必要がありますできません。 さらに、ソース内抑制の処理コストのため、アプリケーションのパフォーマンスが低下することができます。

> [!NOTE]
> Visual Studio 2017 にプロジェクトを移行する場合に、コード分析の警告の手に負えないものの数が直面突然可能性があります。 警告を修正し、コード分析を一時的にオフにする準備ができていない場合は、プロジェクトのプロパティ ページを開きます (**プロジェクト** > ***プロジェクト*プロパティ...**) に移動し、**コード分析**タブです。選択を解除**ビルドに対するコード分析を有効にする**、プロジェクトをリビルドします。 または、設定をコードに対して実行する別、小規模なルールを選択することができます。 警告を解決する準備ができたらにコード分析を有効にしてください。

## <a name="suppressmessage-attribute"></a>SuppressMessage 属性

選択すると**抑制**でコード分析警告のコンテキストかを右クリック メニューから、**エラー一覧**、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>コード内、またはプロジェクトのグローバル抑制に属性が追加ファイルです。

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

- **規則のカテゴリ**-ルールが定義されているカテゴリです。 コード分析規則のカテゴリの詳細については、次を参照してください。[マネージ コードの警告](../code-quality/code-analysis-for-managed-code-warnings.md)です。

- **Rule Id** -ルールの識別子。 サポートには、短期および長期のルールの識別子名の両方が含まれます。 短い名前が CAXXXX です。長い名前は、CAXXXX:FriendlyTypeName です。

- **位置揃え**-テキスト メッセージの抑制の理由を文書化するために使用します。

- **メッセージ Id** -各メッセージの問題の一意の識別子。

- **スコープ**-警告を抑制するターゲット。 ターゲットが指定されていない場合は、属性のターゲットに設定されます。 サポートされているスコープ、次のとおりです。

    - Module

    - 名前空間

    - リソース

    - 型

    - メンバー

- **ターゲット**- 警告を抑制するターゲットを指定するために使用する識別子。 アイテムの完全修飾名でなければなりません。

## <a name="suppressmessage-usage"></a>SuppressMessage 使用状況

レベルでコード分析の警告が抑制されている、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性を適用します。 たとえば、属性は、アセンブリ、モジュール、型、メンバー、またはパラメーターのレベルで適用できます。 これの目的は、違反が発生するコードに抑制情報を密に結合します。

抑制の一般的な形式には、規則のカテゴリと、ルール名の省略可能な人間が判読できる形式を含む、ルールの識別子が含まれています。 例:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

ソース内抑制のメタデータを最小限に抑えるための厳密なパフォーマンス上の理由がある場合は、ルール名を省略できます。 規則のカテゴリとそのルール ID 一緒に規則を十分に一意の識別子を構成します。 例:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

保守容易性の理由から、ルール名を省略することは推奨されません。

## <a name="suppressing-selective-violations-within-a-method-body"></a>メソッド本体内の選択的な違反を抑制します。

抑制属性は、メソッドに適用できますが、メソッド本体に埋め込むことはできません。 これを追加する場合に特定のルールのすべての違反を抑制することを意味、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性をメソッドにします。

場合によっては、将来のコードが自動的にコード分析規則から除外されていないように例については、違反の特定のインスタンスを抑制する場合があります。 これは、使用することは特定のコード分析規則、`MessageId`のプロパティ、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性。 一般に、従来の規則の違反 (ローカル変数またはパラメーター) の特定のシンボル敬意を`MessageId`プロパティです。 [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) is an example of such a rule. ただし、実行可能コード (非シンボル) に違反のレガシ規則を使用しない、`MessageId`プロパティです。 さらに、.NET コンパイラ プラットフォーム ("Roslyn") アナライザーを使用しない、`MessageId`プロパティです。

規則の特定のシンボルの違反を抑制するのにはシンボルの名前を指定、`MessageId`のプロパティ、<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性。 次の例では、コードの 2 つの違反を[CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;のいずれか、`name`変数と 1 つずつ、`age`変数。 違反のみ、`age`シンボルを非表示にします。

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

マネージ コード コンパイラ、および一部のサード パーティ製ツールは、迅速なコードの開発を促進するためのコードを生成します。 ソース ファイルに表示されるコンパイラによって生成されたコードが通常でマークされている、`GeneratedCodeAttribute`属性。

コード分析の警告と生成されたコードのエラーを抑制するかどうかを選択できます。 このような警告とエラーを抑制する方法については、次を参照してください。[する方法: 生成されたコードの警告を抑制する状況](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)です。

> [!NOTE]
> コード分析を無視`GeneratedCodeAttribute`アセンブリ全体または 1 つのパラメーターのいずれかに適用されたとき。

## <a name="global-level-suppressions"></a>グローバル レベルの抑制

マネージ コード分析ツールを調べ`SuppressMessage`アセンブリ、モジュール、型、メンバー、またはパラメーターのレベルで適用される属性です。 違反のリソースと名前空間に対しても適用されます。 これらの違反はグローバル レベルで適用する必要がスコープ設定し、は対象とします。 たとえば、次のメッセージには、名前空間の違反が抑制されます。

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 名前空間スコープで警告を抑制した場合は、それ自体の名前空間に対する警告を抑制します。 名前空間内の型に対する警告は抑制されません。

任意の抑制は、明示的なスコープを指定することで表現できます。 このような抑制は、グローバル レベルでライブする必要があります。 型を修飾することによって、メンバー レベルの抑制を指定できません。

グローバル レベルの抑制は、明示的に指定されたユーザーのソースにマップされないコンパイラによって生成されたコードを参照するメッセージを抑制する唯一の方法です。 たとえば、次のコードでは、コンパイラによって生成されたコンス トラクターに対する違反が抑制されます。

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`アイテムの完全修飾名を常に含まれています。

## <a name="global-suppression-file"></a>グローバル抑制ファイル

グローバル抑制ファイルでは、グローバル レベルの抑制か、ターゲットが指定されていない抑制の抑制を保持します。 たとえば、アセンブリ レベルの違反に対する抑制は、このファイルに格納されます。 また、ASP.NET 抑制は、プロジェクト レベルの設定は、フォームのコードを利用できないために、このファイルに格納されます。 グローバル抑制ファイルが作成され、選択した初めてのプロジェクトに追加、**プロジェクト抑制ファイル内**のオプション、**抑制**コマンドを**エラー一覧**ウィンドウです。

## <a name="see-also"></a>関連項目

<xref:System.Diagnostics.CodeAnalysis>