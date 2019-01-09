---
title: EditorConfig ファイルでの .NET の名前付け規則
ms.date: 11/20/2017
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: 60bffcf458e96a5e224493ac9a33b8fa9fb72541
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898662"
---
# <a name="net-naming-conventions-for-editorconfig"></a>EditorConfig での .NET の名前付け規則

名前付け規則は、クラス、プロパティ、およびメソッドなどのコード要素の名前付けに関するものです。 たとえば、パブリック メンバーは大文字表記とする必要があること、または非同期メソッドは "Async" で終わる必要があることを指定できます。 これらの規則を適用するには、[.editorconfig ファイル](../ide/create-portable-custom-editor-options.md)にそれらを含めます。 名前付け規則違反は、規則に対して選択した重大度に応じて、**エラー一覧**内に表示されるか、または名前の下に修正候補として表示されます。 違反を確認するためにプロジェクトをビルドする必要はありません。

名前付け規則は、*.editorconfig* ファイル内に固有度の高いものから低いものの順に並べる必要があります。 適用可能な最初に検出されたルールのみが適用されます。

それぞれの名前付け規則については、名前付け規則を適用するシンボル、名前付けのスタイル、および規則を適用する上での重大度を、以下に示すプロパティを使用して指定する必要があります。 プロパティの順序は重要ではありません。

まずは、名前付け規則を完全に記述するために必要なプロパティの各々で使用する名前付け規則のタイトルを選択します。 たとえば、`public_members_must_be_capitalized` は、名前付け規則の名前としてわかりやすく適切です。 以下のセクションでは、指定するタイトルを **<namingRuleTitle\>** として参照します。

## <a name="symbols"></a>シンボル

最初に、名前付けルールを適用するシンボルのグループを識別します。 このプロパティの形式は次のとおりです。

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

**<symbolTitle\>** の値を、`public_symbols` などのわかりやすいタイトルに置き換えて、シンボルのグループに名前を付けます。 規則が適用されるシンボルを記述する 3 つのプロパティ名 (シンボルの種類、アクセシビリティ レベル、修飾子) の中で **<symbolTitle\>** を使用します。

### <a name="kinds-of-symbols"></a>シンボルの種類

名前付け規則を適用するシンボルの種類を記述するには、次の形式でプロパティを指定します。

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

許容される値を次のリストに示します。個々の値をコンマで区切ることで複数の値を指定できます。

- \*(この値を使用すると、すべてのシンボルが指定されます)
- namespace
- class
- struct
- interface
- enum
- property
- メソッド
- フィールド
- event
- delegate
- パラメーター
- type_parameter
- local
- local_function

### <a name="accessibility-levels-of-symbols"></a>シンボルのアクセシビリティ レベル

名前付け規則を適用するシンボルのアクセシビリティ レベルを記述するには、次の形式でプロパティ名を指定します。

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

許容される値を次のリストに示します。個々の値をコンマで区切ることで複数の値を指定できます。

- \*(この値を使用すると、すべてのアクセシビリティ レベルが指定されます)
- public
- internal または friend
- private
- protected
- protected\_internal または protected_friend
- local

> [!NOTE]
> 対象とするシンボルの種類にアクセシビリティが適用されない場合は、アクセシビリティ レベルを名前付け規則の一部には指定しません。 たとえば、パラメーターにはアクセシビリティ レベルはありません。 パラメーターの名前付け規則にアクセシビリティ レベルを指定すると、名前付け規則は正しく機能しません。

### <a name="symbol-modifiers"></a>シンボルの修飾子

名前付け規則を適用するシンボルの修飾子を記述するには、次の形式でプロパティ名を指定します。

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

許容される値を次のリストに示します。個々の値をコンマで区切ることで複数の値を指定できます。

- `abstract` または `must_inherit`
- `async`
- `const`
- `readonly`
- `static` または `shared`

   > [!NOTE]
   > `static` または `shared` シンボルに対する名前付け規則がある場合、それは暗黙的に静的である `const` シンボルにも適用されます。 `static` 名前付け規則を `const` シンボルに適用しない場合は、`const` シンボルに対する別の名前付け規則を作成します。

`required_modifiers` は省略可能なプロパティです。 このプロパティを省略した場合、名前付け規則はすべての修飾子に適用されます。

## <a name="style"></a>スタイル

名前付け規則を適用するシンボルのグループを識別したので、次に名前付けのスタイルを記述する必要があります。 名前が特定のプレフィックスまたは特定のサフィックスを持つスタイルを指定したり、名前に含まれている個々の単語が特定の文字で区切られるスタイルにしたりすることができます。 また、大文字/小文字のスタイルを指定することもできます。 スタイル プロパティの形式は次のようになります。

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

**<styleTitle\>** の値を、`first_word_upper_case_style` のようにわかりやすいタイトルに置き換えることで、スタイルに名前を付けます。 名前付けのスタイル (プレフィックス、サフィックス、単語区切り文字、大文字/小文字) を記述するプロパティ名の中で **<styleTitle\>** を使用します。 これらのプロパティを 1 つまたは複数使用して、目的のスタイルを記述します。

### <a name="require-a-prefix"></a>プレフィックスが必要

シンボル名が特定の文字で始まる必要があることを指定するには、次のプロパティを使用します。

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>サフィックスが必要

シンボル名が特定の文字で終わる必要があることを指定するには、次のプロパティを使用します。

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>特定の単語区切り記号が必要

シンボル名の中の個々の単語を特定の文字で区切る必要があることを指定するには、次のプロパティを使用します。

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>大文字/小文字のスタイルが必要

シンボル名に対して特定の大文字/小文字のスタイルを指定するには、次のプロパティを使用します。

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

このプロパティに設定できる値は次のとおりです。

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> 名前付けスタイルの一部として大文字/小文字スタイルを指定する必要があります。そうしないと、名前付けスタイルは無視される可能性があります。

## <a name="severity"></a>重要度

名前付け規則違反の重大度を記述するには、次の形式でプロパティを指定します。

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

次の表に、許容される重大度の値と、その意味を示します。

重要度 | 効果
------------ | -------------
none または silent | このスタイルに準拠していないときは、ユーザーには何も表示されません。ただし、自動生成コードは、このスタイルに従います。
修正候補 | このスタイルに準拠していないとき、修正候補としてユーザーに表示されます (最初の 2 文字の下に点線が付きます)。 コンパイル時には影響しません。
警告 | このスタイルに準拠していないとき、**エラー一覧**にコンパイラの警告が表示されます。
エラー | このスタイルに準拠していないとき、**エラー一覧**にコンパイラ エラーが表示されます。

> [!NOTE]
> 名前付け規則違反を確認するために、プロジェクトをビルドする必要はありません。 名前付け規則違反は、コードの編集時に、**エラー一覧**に表示されるか、または修正候補として表示されます。

## <a name="example"></a>例

次の *.editorconfig* ファイルには、パブリック プロパティ、メソッド、フィールド、イベント、デリゲートを大文字で入力する必要があることを指定した名前付け規則が含まれています。 この名前付け規則では、コンマを使用して個々のシンボル値を区切ることにより、規則を適用する複数の種類のシンボルを指定しています。

```EditorConfig
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

次のスクリーンショットでは、この名前付け規則の結果がエディターに表示されています。 2 つのパブリック変数に付けられた名前は、最初の文字が大文字になっていません。 1 つは `const`、もう 1 つは `readonly` です。 名前付け規則は `readonly` シンボルのみに適用されるので、`readonly` 変数のみに、名前付け規則の修正候補が表示されています。

![名前付け規則の修正候補](media/editorconfig-naming-rule-suggestion.png)

これで、違反の重大度を `warning` に変更してみましょう。

```EditorConfig
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

コード ファイルを閉じてから再度開いた場合、名前違反の下には修正候補が表示されるのではなく、緑色の波線が表示され、さらに**エラー一覧**に警告が表示されます。

![名前付け規則の警告](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>関連項目

- [.NET 言語と書式の規則](../ide/editorconfig-code-style-settings-reference.md)
- [移植可能なカスタム エディター オプションを作成する](../ide/create-portable-custom-editor-options.md)
- [.NET コンパイラ プラットフォームの .editorconfig ファイル](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
