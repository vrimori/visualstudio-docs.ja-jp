---
title: EditorConfig の .NET コーディング規則の設定
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8d7d07efa862e619961c21962dca20303efed97e
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742522"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig の .NET コーディング規則の設定

Visual Studio 2017 [EditorConfig](../ide/create-portable-custom-editor-options.md) ファイルを使用すれば、コードベースで一貫性のあるコード スタイルを定義および維持できます。 EditorConfig には、`indent_style` や `indent_size` などのいくつかの主要な書式設定プロパティが含まれています。 Visual Studio では、EditorConfig ファイルを使用して .NET コーディング規則の設定を構成することもできます。 EditorConfig ファイルでは、個々の .NET コーディング規則を有効化または無効化し、重要度レベルで規則を適用する程度を構成することができます。 EditorConfig を使用して、コードベースで整合性を適用する方法の詳細については、「[EditorConfig で移植可能なカスタム エディター設定を作成する](../ide/create-portable-custom-editor-options.md)」を参照してください。

[.editorconfig ファイルの例](#example-editorconfig-file)については、この記事の末尾をご覧ください。

## <a name="convention-categories"></a>規則のカテゴリ

サポートされている .NET コーディング規則には次の 3 つのカテゴリがあります。

- [言語コード スタイル](#language-code-styles)

   C# または Visual Basic 言語に関するルール。 たとえば、変数の定義時の `var` または明示的な型の使用や、式形式メンバーの優先に関するルールを指定できます。

- [書式規則](#formatting-conventions)

   コードを読みやすくするためのレイアウトや構造に関するルール。 たとえば、Allman 中かっこや、制御ブロックでのスペースの優先に関するルールを指定できます。

- [名前付け規則](../ide/editorconfig-naming-conventions.md)

   コード要素の名前付けに関するルール。 たとえば、`async` メソッドは "Async" で終わる必要があるなどと指定できます。

## <a name="language-code-styles"></a>言語コード スタイル

言語コード スタイルのルールには次の形式があります。

`options_name = false|true : none|silent|suggestion|warning|error`

各言語コード スタイルのルールでは、**true** (このスタイルを優先する) または **false** (このスタイルを優先しない)、および**重要度**を指定する必要があります。 重要度は、そのスタイルの適用レベルを指定します。

次の表に、指定できる重要度の値とその効果をリストします。

重要度 | 効果
:------- | ------
`none` | このルールに違反した場合、ユーザーには何も表示されません。 しかし、コード生成機能により、このスタイルでコードが生成されます。 重大度が `none` のルールが、**[クイック アクションとリファクタリング]** メニューに表示されることはありません。 ほとんどの場合、これは "無効" または "無視" と見なされます。
`silent` (Visual Studio 2017 バージョン 15.8 の `refactoring` も同様) | このルールに違反した場合、ユーザーには何も表示されません。 しかし、コード生成機能により、このスタイルでコードが生成されます。 重大度が `silent` のルールはクリーンアップに関するものであり、また **[クイック アクションとリファクタリング]** メニューに表示されます。
`suggestion` | このスタイル ルールに違反した場合、修正候補としてユーザーに表示されます。 修正候補は、最初の 2 文字の下に 3 つの灰色のドットとして表示されます。
`warning` | このスタイル ルールに違反した場合、コンパイラの警告が表示されます。
`error` | このスタイル ルールに違反した場合、コンパイラ エラーが表示されます。

次のリストに、使用できる言語コード スタイル設定を示します。

- .NET コード スタイルの設定
    - ["This."と "Me." 修飾子](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [型参照のためのフレームワーク型名の代わりの言語キーワード](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [修飾子の基本設定](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - dotnet\_style\_readonly\_field
    - [かっこの基本設定](#parentheses)
        - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_operators
        - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
    - [式レベル基本設定](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_prefer\_inferred\_tuple_names
        - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
        - dotnet\_style\_prefer\_auto\_properties
        - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
        - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
        - dotnet\_style\_prefer\_conditional\_expression\_over\_return
    - ["null" チェック設定](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- C# コード スタイルの設定
    - [暗黙的な型と明示的な型](#implicit-and-explicit-types)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [式形式のメンバー](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [パターン マッチング](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [インライン変数宣言](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [式レベル基本設定](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - ["null" チェック設定](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [コード ブロック基本設定](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>.NET コード スタイルの設定

このセクションのスタイル ルールは、C# および Visual Basic の両方に適用されます。 優先するプログラミング言語のコード例を表示するには、ブラウザー ウィンドウの右上隅にあるドロップダウンの **[言語]** メニューでそれを選択します。

#### <a name="this_and_me"></a>"This." 修飾子 と "Me." 修飾子

このスタイル ルール (ルール ID IDE0003 および IDE0009) は、フィールド、プロパティ、メソッド、またはイベントに適用できます。 **true** の値は、C# では `this.`、Visual Basic では `Me.` をコード記号の前に付けることを意味します。 **false** の値は、`this.` や `Me.` をコード要素の前に_付けない_ ことを意味します。

次の表に、ルール名、適用可能なプログラミング言語、および既定値を示します。

| 規則名 | 適用可能な言語 | Visual Studio の既定値 |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# および Visual Basic | false:none |
| dotnet_style_qualification_for_property | C# および Visual Basic | false:none |
| dotnet_style_qualification_for_method | C# および Visual Basic | false:none |
| dotnet_style_qualification_for_event | C# および Visual Basic | false:none |

**dotnet\_style\_qualification\_for_field**

- このルールが **true** に設定されている場合、C# では `this.`、Visual Basic では `Me.` をフィールドの前に付けます。
- このルールが **false** に設定されている場合、`this.` や `Me.` をフィールドの前に_付けません_。

コード例:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- このルールが **true** に設定されている場合、C# では `this.`、Visual Basic では `Me.` をプロパティの前に付けます。
- このルールが **false** に設定されている場合、`this.` や `Me.` をプロパティの前に_付けません_。

コード例:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**dotnet\_style\_qualification\_for_method**

- このルールが **true** に設定されている場合、C# では `this.`、Visual Basic では `Me.` をメソッドの前に付けます。
- このルールが **false** に設定されている場合、`this.` や `Me.` をメソッドの前に_付けません_。

コード例:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**dotnet\_style\_qualification\_for_event**

- このルールが **true** に設定されている場合、C# では `this.`、Visual Basic では `Me.` をイベントの前に付けます。
- このルールが **false** に設定されている場合、`this.` や `Me.` をイベントの前に_付けません_。

コード例:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

これらのルールは、次のように *.editorconfig* ファイルに表示されます。

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>型参照のためのフレームワーク型名の代わりの言語キーワード

このスタイル ルールは、ローカル変数、メソッド パラメーター、およびクラス メンバーに適用できます。また、型メンバー アクセス式に別個のルールとして適用できます。 **true** の値は、型を表すキーワードを持つ型に対して、型名 (`Int32` など) の代わりに言語キーワード (`int` や `Integer` など) を使用することを意味します。 **false** の値は、言語キーワードの代わりに型名を使用することを意味します。

次の表に、ルール名、ルール ID、適用可能なプログラミング言語、および既定値を示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 と IDE0014 | C# および Visual Basic | true:none |
| dotnet_style_predefined_type_for_member_access | IDE0013 と IDE0015 | C# および Visual Basic | true:none |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- このルールが **true** に設定されている場合は、型を表すキーワードを持つ型に対して、型名の代わりに、ローカル変数、メソッド パラメーター、およびクラス メンバーの言語キーワードを使用します。
- このルールが **false** に設定されている場合は、言語キーワードの代わりに、ローカル変数、メソッド パラメーター、およびクラス メンバーの型名を使用します。

コード例:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**dotnet\_style\_predefined\_type\_for\_member_access**

- このルールが **true** に設定されている場合は、型を表すキーワードを持つ型に対して、型名の代わりに、メンバー アクセス式の言語キーワードを使用します。
- このルールが **false** に設定されている場合は、言語キーワードの代わりに、メンバー アクセス式の型名を使用します。

コード例:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

これらのルールは、次のように *.editorconfig* ファイルに表示されます。

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>修飾子の基本設定

このセクションのスタイル ルールは、アクセシビリティ修飾子を必要にする、必要な修飾子の並べ替え順序を指定する、読み取り専用修飾子を必要にするなど、修飾子の基本設定に関するものです。

次の表には、ルール名、ルール ID、適用可能なプログラミング言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# および Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:none | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:none | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# および Visual Basic | true:suggestion | 15.7 |

**dotnet\_style\_require\_accessibility_modifiers**

このルールでは **true** や **false** の値は受け入れません。代わりに、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| always | アクセシビリティ修飾子を指定します。 |
| for\_non\_interface_members | パブリック インターフェイス メンバーの場合を除き、アクセシビリティ修飾子を宣言します。 これは、**always** と同じであり、C# が既定のインターフェイス メソッドを追加する場合の将来の対策のために追加されています。 |
| never | アクセシビリティ修飾子を指定しません。 |

コード例:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- このルールが修飾子のリストに設定されている場合は、指定された順序を優先します。
- ファイルでこのルールが省略されている場合は、修飾子の順序を優先しません。

コード例:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- このルールが修飾子のリストに設定されている場合は、指定された順序を優先します。
- ファイルでこのルールが省略されている場合は、修飾子の順序を優先しません。

コード例:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- このルールが **true** に設定されている場合は、フィールドがインラインまたはコンストラクターの内部でのみ割り当てられている場合は、フィールドを `readonly` (C#) または `ReadOnly` (Visual Basic) でマークする必要があります。
- このルールが **false** に設定されている場合は、フィールドを `readonly` (C#) または `ReadOnly` (Visual Basic) でマークする必要があるかどうかに関して特に規定がないことを指定します。

コード例:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

これらのルールは、次のように *.editorconfig* ファイルに表示されます。

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="parentheses"></a>かっこの基本設定

このセクションのスタイル ルールは、算術演算子、関係演算子、およびその他の 2 項演算子でのかっこの使用を含む、かっこの基本設定に関するものです。

次の表には、ルール名、ルール ID、適用可能なプログラミング言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# および Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# および Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# および Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# および Visual Basic | never_if_unnecessary:none | 15.8 |

**dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators**

- このルールが **always_for_clarity** に設定されている場合は、算術演算子 (`*`、`/`、`%`、`+`、`-`、`<<`、`>>`、`&`、`^`、`|`) の基本設定を明確にするためにかっこを使用します。
- このルールが **never_if_unnecessary** に設定されており、算術演算子 (`*`、`/`、`%`、`+`、`-`、`<<`、`>>`、`&`、`^`、`|`) の基本設定が明確な場合はかっこを使用しません。

コード例:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

**dotnet\_style\_parentheses\_in\_relational\_binary_operators**

- このルールが **always_for_clarity** に設定されている場合は、関係演算子 (`>`、`<`、`<=`、`>=`、`is`、`as`、`==`、`!=`) の基本設定を明確にするためにかっこを使用します。
- このルールが **never_if_unnecessary** に設定されており、関係演算子 (`>`、`<`、`<=`、`>=`、`is`、`as`、`==`、`!=`) の基本設定が明確な場合はかっこを使用しません。

コード例:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

**dotnet\_style\_parentheses\_in\_other\_binary_operators**

- このルールが **always_for_clarity** に設定されている場合は、他の 2 項演算子 (`&&`、`||`、`??`) の基本設定を明確にするためにかっこを使用します。
- このルールが **never_if_unnecessary** に設定されており、他の 2 項演算子 (`&&`、`||`、`??`) の基本設定が明確な場合はかっこを使用しません。

コード例:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

**dotnet\_style\_parentheses\_in\_other_operators**

- このルールが **always_for_clarity** に設定されている場合は、演算子の基本設定を明確にするためにかっこを使用します。
- このルールが **never_if_unnecessary** に設定されており、演算子の基本設定が明確な場合はかっこを使用しません。

コード例:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

これらのルールは、次のように *.editorconfig* ファイルに表示されます。

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:none
```

#### <a name="expression_level"></a>式レベル基本設定

このセクションのスタイル ルールは式レベル基本設定に関するものです。これには、オブジェクト初期化子、コレクション初期化子、明示的または推論されたタプル名、推定された匿名型が含まれます。

次の表には、ルール名、ルール ID、適用可能なプログラミング言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# および Visual Basic | true:suggestion | 最初のリリース |
| dotnet_style_collection_initializer | IDE0028 | C# および Visual Basic | true:suggestion | 最初のリリース |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ および Visual Basic 15+ | true:suggestion | 最初のリリース |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1+ および Visual Basic 15+ | true:suggestion | 15.6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# および Visual Basic | true:suggestion | 15.6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# および Visual Basic | true:none | 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# および Visual Basic | true:suggestion | 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# および Visual Basic | true:none | 15.8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# および Visual Basic | true:none | 15.8 |

**dotnet\_style\_object_initializer**

- このルールが **true** に設定されている場合、可能であれば、オブジェクト初期化子を使用してオブジェクトを初期化します。
- このルールが **false** に設定されている場合は、オブジェクト初期化子を使用してオブジェクトを初期化*しません*。

コード例:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**

- このルールが **true** に設定されている場合、可能であれば、コレクション初期化子を使用してコレクションを初期化します。
- このルールが **false** に設定されている場合は、コレクション初期化子を使用してコレクションを初期化*しません*。

コード例:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**dotnet\_style\_explicit\_tuple_names**

- このルールが **true** に設定されている場合は、ItemX プロパティではなくタプル名を使用します。
- このルールが **false** に設定されている場合は、タプル名ではなく ItemX プロパティを使用します。

コード例:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_prefer\_inferred\_tuple_names**

- このルールが **true** に設定されている場合、推論されたタプル要素名が優先されます。
- このルールが **false** に設定されている場合、明示的なタプル要素名が優先されます。

コード例:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- このルールが **true** に設定されている場合、推論された匿名型のメンバー名が優先されます。
- このルールが **false** に設定されている場合、明示的な匿名型のメンバー名が優先されます。

コード例:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

**dotnet\_style\_prefer\_auto\_properties**

- このルールが **true** に設定されている場合は、プライベート バッキング フィールドを持つプロパティよりも、自動プロパティが優先されます。
- このルールが **false** に設定されている場合、自動プロパティよりも、プライベート バッキング フィールドを持つプロパティが優先されます。

コード例:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

**dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method**

- このルールが **true** に設定されている場合、object.ReferenceEquals よりも、パターン一致の NULL 検査の使用が優先されます。
- このルールが **false** に設定されている場合、パターン一致の NULL 検査よりも、object.ReferenceEquals が優先されます。

コード例:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```



**dotnet\_style\_prefer\_conditional\_expression\_over_assignment**

- このルールが **true** に設定されている場合は、if-else ステートメントよりも三項条件を使用する割り当てを優先します。
- このルールが **false** に設定されている場合は、三項条件よりも if-else ステートメントを使用する割り当てを優先します。

コード例:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

**dotnet\_style\_prefer\_conditional\_expression\_over_return**

- このルールが **true** に設定されている場合は、if-else ステートメントよりも三項条件を使用する return ステートメントを優先します。
- このルールが **false** に設定されている場合は、三項条件よりも if-else ステートメントを使用する return ステートメントを優先します。

コード例:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

これらのルールは、次のように *.editorconfig* ファイルに表示されます。

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:none
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="null_checking"></a>"Null" 検査設定

このセクションのスタイル ルールは、null 検査設定が関係します。

次の表には、ルール名、ルール ID、適用可能なプログラミング言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# および Visual Basic | true:suggestion | 最初のリリース |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ および Visual Basic 14+ | true:suggestion | 最初のリリース |

**dotnet\_style\_coalesce_expression**

- このルールが **true** に設定されている場合は、三項演算子チェックではなく null 結合式を使用します。
- このルールが **false** に設定されている場合は、null 結合式ではなく三項演算子チェックを使用します。

コード例:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- このルールが **true** に設定されている場合、可能であれば、null 条件演算子を使用します。
- このルールが **false** に設定されている場合、可能であれば、三項 null チェックを使用します。

コード例:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

これらのルールは、次のように *.editorconfig* ファイルに表示されます。

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>C# コード スタイルの設定

このセクションのスタイル ルールは、C# のみに適用されます。

#### <a name="implicit-and-explicit-types"></a>暗黙的な型と明示的な型

このセクションのスタイル ルール (ルール ID IDE0007 および IDE0008) は、変数宣言での [var](/dotnet/csharp/language-reference/keywords/var) キーワードと明示的な型の使用に関するものです。 このルールは、ビルトイン型、型が明らかな場合、および他の場所に個別に適用できます。

次の表に、ルール名、適用可能なプログラミング言語、および既定値を示します。

| 規則名 | 適用可能な言語 | Visual Studio の既定値 |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:none |
| csharp_style_var_when_type_is_apparent | C# | true:none |
| csharp_style_var_elsewhere | C# | true:none |

**csharp\_style\_var\_for\_built\_in_types**

- このルールが **true** に設定されている場合は、`int` などのビルトイン システム型で変数を宣言する場合に `var` を使用します。
- このルールが **false** に設定されている場合は、`int` などのビルトイン システム型で変数を宣言する場合に `var` ではなく明示的な型を使用します。

コード例:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- このルールが **true** に設定されている場合、宣言式の右側で型が既に示されているときに `var` を使用します。
- このルールが **false** に設定されている場合、宣言式の右側で型が既に示されているときに `var` ではなく明示的な型を使用します。

コード例:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- このルールが **true** に設定されている場合は、別のコード スタイル ルールでオーバーライドされない限り、すべての場合に明示的な型ではなく `var` を使用します。
- このルールが **false** に設定されている場合は、別のコード スタイル ルールでオーバーライドされない限り、すべての場合に `var` ではなく明示的な型を使用します。

コード例:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>式形式のメンバー

このセクションのスタイル ルールは、ロジックが単一の式で構成される場合の[式形式のメンバー](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members)の使用に関するものです。 このルールは、メソッド、コンストラクター、演算子、プロパティ、インデクサー、およびアクセサーに適用できます。

次の表には、ルール名、ルール ID、適用可能な言語バージョン、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 と IDE0024 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:none | 15.3 |

**csharp\_style\_expression\_bodied_methods**

このルールでは、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| true | メソッドに式形式メンバーを使用します。 |
| when_on_single_line | 単一行になる場合は、メソッドに式形式メンバーを使用します。 |
| false | メソッドにブロック本体を使用します。 |

コード例:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

このルールでは、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| true | コンストラクターに式形式メンバーを使用します。 |
| when_on_single_line | 単一行になる場合は、コンストラクターに式形式メンバーを使用します。 |
| false | コンストラクターにブロック本体を使用します。 |

コード例:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

このルールでは、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| true | 演算子に式形式メンバーを使用します。 |
| when_on_single_line | 単一行になる場合は、演算子に式形式メンバーを使用します。 |
| false | 演算子にブロック本体を使用します。 |

コード例:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

このルールでは、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| true | プロパティに式形式メンバーを使用します。 |
| when_on_single_line | 単一行になる場合は、プロパティに式形式メンバーを使用します。 |
| false | プロパティにブロック本体を使用します。 |

コード例:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

このルールでは、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| true | インデクサーに式形式メンバーを使用します。 |
| when_on_single_line | 単一行になる場合は、インデクサーに式形式メンバーを使用します。 |
| false | インデクサーにブロック本体を使用します。 |

コード例:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

このルールでは、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| true | アクセサーに式形式メンバーを使用します。 |
| when_on_single_line | 単一行になる場合は、アクセサーに式形式メンバーを使用します。 |
| false | アクセサーにブロック本体を使用します。 |

コード例:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>パターン マッチング

このセクションのスタイル ルールは、C# での[パターン マッチング](/dotnet/csharp/pattern-matching)の使用に関するものです。

次の表に、ルール名、ルール ID、適用可能な言語バージョン、および既定値を示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- このルールが **true** に設定されている場合、`is` 式と型キャストの代わりにパターン マッチングを使用します。
- このルールが **false** に設定されている場合、パターン マッチングの代わりに `is` 式と型キャストを使用します。

コード例:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- このルールが **true** に設定されている場合、`as` 式と null チェックの代わりにパターン マッチングを使用し、何かが特定の型であるか判断します。
- このルールが **false** に設定されている場合、パターン マッチングの代わりに `as` 式と null チェックを使用し、何かが特定の型であるか判断します。

コード例:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>インライン変数宣言

このスタイル ルールは、`out` 変数がインラインで宣言されるかどうかに関するものです。 C# 7 以降では、別の変数宣言内ではなく、[メソッド呼び出しの引数リスト内で out 変数を宣言](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument)できます。

次の表に、ルール名、ルール ID、適用可能な言語バージョン、および既定値を示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- このルールが **true** に設定されている場合、可能であれば、メソッド呼び出しの引数リスト内で `out` 変数をインラインで宣言します。
- このルールが **false** に設定されている場合は、メソッド呼び出しの前に `out` 変数を宣言します。

コード例:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>式レベル基本設定

このセクションのスタイル ルールは、[既定の式](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference)、分解された変数、匿名関数よりローカル関数を使用するなど、式レベル基本設定に関するものです。

次の表には、ルール名、ルール ID、適用可能な言語バージョン、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0+ | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0+ | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

このスタイル ルールは、コンパイラが式の型を推定できる場合の、[既定の値式での `default` リテラル](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference)の使用に関するものです。

- このルールが **true** に設定されている場合は、`default(T)` より `default` を優先します。
- このルールが **false** に設定されている場合は、`default` より `default(T)` を優先します。

コード例:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- このルールが **true** に設定されている場合は、分解された変数宣言を優先します。
- このルールが **false** に設定されている場合、変数宣言では分解を優先しません。

コード例:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- このルールが **true** に設定されている場合は、匿名関数よりローカル関数を優先します。
- このルールが **false** に設定されている場合は、ローカル関数より匿名関数を優先します。

コード例:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>"Null" 検査設定

これらのスタイル ルールは、`throw` 式または `throw` ステートメントの使用や、null チェックを実行するか、[ラムダ式](/dotnet/csharp/lambda-expressions)の呼び出し時に条件付き合体演算子 (`?.`) を使用するかなどの、`null` チェックの構文に関するものです。

次の表に、ルール名、ルール ID、適用可能な言語バージョン、および既定値を示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion |

**csharp\_style\_throw_expression**

- このルールが **true** に設定されている場合は、`throw` ステートメントの代わりに `throw` 式を使用します。
- このルールが **false** に設定されている場合は、`throw` 式の代わりに `throw` ステートメントを使用します。

コード例:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- このルールが **true** に設定されている場合は、null チェックを実行する代わりに、ラムダ式の呼び出し時に条件付き合体演算子 (`?.`) を使用します。
- このルールが **false** に設定されている場合は、条件付き合体演算子 (`?.`) を使用する代わりに、ラムダ式を呼び出す前に null チェックを実行します。

コード例:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>コード ブロック基本設定

このスタイル ルールは、コード ブロックを囲む中かっこ `{ }` の使用に関するものです。

次の表には、ルール名、ルール ID、適用可能な言語バージョン、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | ルール ID | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | true:none | 15.3 |

**csharp\_prefer\_braces**

- このルールが **true** に設定されている場合は、コードが 1 行であっても中かっこを使用します。
- このルールが **false** に設定されている場合、中かっこは使用しません (許可されている場合)。

コード例:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>書式規則

書式規則のほとんどのルールには次の形式があります。

`rule_name = false|true`

**true** (このスタイルを優先する) または **false** (このスタイルを優先しない) を指定します。 重要度は指定しません。 いくつかのルールでは、true や false の代わりに、他の値を指定して、ルールを適用するタイミングと場所を示します。

Visual Studio で使用可能な書式規則のルールを以下にリストします。

- .NET 書式設定
    - [using の整理](#usings)
        - dotnet_sort_system_directives_first
        - dotnet_separate_import_directive_groups
- C# 書式設定
    - [改行オプション](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [インデント オプション](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [スペース オプション](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [折り返しオプション](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>.NET 書式設定

このセクションの書式ルールは、C# および Visual Basic に適用されます。

#### <a name="usings"></a>using の整理

この書式ルールは、他の using ディレクティブに対する System.* using ディレクティブの配置に関するものです。

次の表には、ルール名、適用可能な言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# および Visual Basic | true | 15.3 |
| dotnet_separate_import_directive_groups | C# および Visual Basic | true | 15.5 |

**dotnet\_sort\_system\_directives_first**

- このルールが **true** に設定されている場合、System.* using ディレクティブをアルファベット順に並べ替え、他の using の前に配置します。
- このルールが **false** に設定されている場合は、System.* using ディレクティブを他の using ディレクティブの前に配置しません。

コード例:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

*.editorconfig* ファイルの例:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

**dotnet\_separate\_import\_directive\_groups**

- このルールが **true** に設定されている場合、using ディレクティブ グループの間に空の行を置きます。
- このルールが **false** に設定されている場合、using ディレクティブ グループの間に空の行を置かないでください。

コード例:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

*.editorconfig* ファイルの例:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_separate_import_directive_groups = true
```

### <a name="c-formatting-settings"></a>C# 書式設定

このセクションの書式ルールは、C# コードにのみ適用されます。

#### <a name="newline"></a>改行オプション

これらの書式ルールは、コードの書式を設定する場合の改行の使用に関するものです。

次の表には、"改行" のルール名、適用可能な言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | all | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**csharp\_new\_line\_before\_open_brace**

このルールは、左中かっこ (`{`) を前のコードと同じ行に配置するか、新しい行に配置するかに関するものです。 このルールの場合、**true** や **false** は指定しません。 代わりに、**all**、**none**、または **methods** や **properties** などの 1 つ以上のコード要素を指定して、このルールを適用する必要があるタイミングを定義します。 使用可能な値の完全なリストを以下の表に示します。

| [値] | 説明
| ------------- |:-------------|
| accessors、anonymous_methods、anonymous_types、control_blocks、events、indexers、lambdas、local_functions、methods、object_collection_array_initializers、properties、types。<br>(種類が複数ある場合は、"," で区切ります)。 | 中かっこは指定されたコード要素の新しい行に配置する必要があります ("Allman" スタイルともいう)。 |
| all | 中かっこはすべての式の新しい行に配置する必要があります ("Allman" スタイル)。 |
| none | 中かっこはすべての式の同じ行に配置する必要があります ("K&R")。 |

コード例:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- このルールが **true** に設定されている場合は、`else` ステートメントを新しい行に配置します。
- このルールが **false** に設定されている場合は、`else` ステートメントを同じ行に配置します。

コード例:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- このルールが **true** に設定されている場合は、`catch` ステートメントを新しい行に配置します。
- このルールが **false** に設定されている場合は、`catch` ステートメントを同じ行に配置します。

コード例:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- このルールが **true** に設定されている場合は、`finally` ステートメントを右中かっこの後の新しい行に配置する必要があります。
- このルールが **false** に設定されている場合は、`finally` ステートメントを右中かっこと同じ行に配置する必要があります。

コード例:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- このルールが **true** に設定されている場合は、オブジェクト初期化子のメンバーを別の行に配置する必要があります。
- このルールが **false** に設定されている場合は、オブジェクト初期化子のメンバーを同じ行に配置する必要があります。

コード例:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- このルールが **true** に設定されている場合は、匿名型のメンバーを別の行に配置する必要があります。
- このルールが **false** に設定されている場合は、匿名型のメンバーを同じ行に配置する必要があります。

コード例:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- このルールが **true** に設定されている場合は、クエリ式の句の要素を別の行に配置する必要があります。
- このルールが **false** に設定されている場合は、クエリ式の句の要素を同じ行に配置する必要があります。

コード例:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>インデント オプション

これらの書式ルールは、コードの書式を設定する場合のインデントの使用に関するものです。

次の表には、ルール名、適用可能な言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**csharp\_indent\_case_contents**

- このルールが **true** に設定されている場合は、`switch` case の内容をインデントします。
- このルールが **false** に設定されている場合は、`switch` case の内容をインデントしません。

コード例:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- このルールが **true** に設定されている場合は、`switch` ラベルをインデントします。
- このルールが **false** に設定されている場合は、`switch` ラベルをインデントしません。

コード例:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

このルールでは **true** や **false** の値は受け入れません。代わりに、以下の表の値を受け入れます。

| [値] | 説明 |
| ----- |:----------- |
| flush_left | ラベルは左端の列に配置されます |
| one_less_than_current | ラベルは、現在のコンテキストのインデントを 1 つ減らした位置に配置されます |
| no_change | ラベルは、現在のコンテキストと同じインデントで配置されます |

コード例:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>スペース オプション

これらの書式ルールは、コードの書式を設定する場合の空白文字の使用に関するものです。

次の表には、ルール名、適用可能な言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | False | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_parentheses | C# | False | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | False | 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | False | 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | False | 15.7 |

**csharp\_space\_after_cast**

- このルールが **true** に設定されている場合は、キャストと値の間にスペースが必要です。
- このルールが **false** に設定されている場合は、キャストと値の間にスペースは必要_ありません_。

コード例:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- このルールが **true** に設定されている場合は、`for` ループなど、制御フロー ステートメントのキーワードの後にスペースが必要です。
- このルールが **false** に設定されている場合は、`for` ループなど、制御フロー ステートメントのキーワードの後にスペースは必要_ありません_。

コード例:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- このルールが **true** に設定されている場合は、メソッド宣言パラメーター リストの始めかっこの後と終わりかっこの前に空白文字を配置します。
- このルールが **false** に設定されている場合は、メソッド宣言パラメーター リストの始めかっこの後と終わりかっこの前に空白文字を配置しません。

コード例:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- このルールが **true** に設定されている場合は、メソッド呼び出しの始めかっこの後と終わりかっこの前に空白文字を配置します。
- このルールが **false** に設定されている場合は、メソッド呼び出しの始めかっこの後と終わりかっこの前に空白文字を配置しません。

コード例:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

このルールでは、以下の表の 1 つ以上の値を受け入れます。

| [値] | 説明 |
| ----- |:------------|
| control_flow_statements | 制御フロー ステートメントのかっこの間にスペースを配置します。 |
| 式 | 式のかっこの間にスペースを配置します。 |
| type_casts | 型キャストのかっこの間にスペースを配置します。 |

このルールを省略するか、`control_flow_statements`、`expressions`、または `type_casts` 以外の値を使用する場合、設定は適用されません。

コード例:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**csharp\_space\_before\_colon\_in\_inheritance_clause**

- このルールが **true** に設定されている場合、型宣言ではベースまたはインターフェイスのコロンの前にスペースが必要です。
- このルールが **false** に設定されている場合、型宣言ではベースまたはインターフェイスのコロンの前にスペースは必要_ありません_。

コード例:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**csharp\_space\_after\_colon\_in\_inheritance_clause**

- このルールが **true** に設定されている場合、型宣言ではベースまたはインターフェイスのコロンの後にスペースが必要です。
- このルールが **false** に設定されている場合、型宣言ではベースまたはインターフェイスのコロンの後にスペースは必要_ありません_。

コード例:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**csharp\_space\_around\_binary_operators**

このルールでは、以下の表のいずれかの値を受け入れます。

| [値] | 説明 |
| ----- |:------------|
| before_and_after | バイナリ演算子の前後にスペースを挿入する |
| none | バイナリ演算子の前後のスペースを削除する |
| ignore | バイナリ演算子の前後のスペースを無視する |

このルールを省略するか、`before_and_after`、`none`、または `ignore` 以外の値を使用する場合、設定は適用されません。

コード例:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- このルールが **true** に設定されている場合、メソッド宣言の空のパラメーター リストのかっこ内にスペースを挿入します。
- このルールが **false** に設定されている場合、メソッド宣言の空のパラメーター リストのかっこ内のスペースを削除します。

コード例:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- このルールが **true** に設定されている場合、メソッド呼び出し名と左かっこの間にスペースを挿入します。
- このルールが **false** に設定されている場合、メソッド呼び出し名と左かっこの間のスペースを削除します。

コード例:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- このルールが **true** に設定されている場合、空の引数リストのかっこ内にスペースを挿入します。
- このルールが **false** に設定されている場合、空の引数リストのかっこ内のスペースを削除します。

コード例:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>折り返しオプション

これらの書式ルールは、ステートメントとコード ブロックでの 1 行と別の行の使用に関するものです。

次の表には、ルール名、適用可能な言語、Visual Studio の既定値、および最初のサポート対象バージョンを示します。

| 規則名 | 適用可能な言語 | Visual Studio の既定値 | Visual Studio 2017 バージョン |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- このルールが **true** に設定されている場合は、1 行に複数のステートメントとメンバー宣言を表示します。
- このルールが **false** に設定されている場合は、別の行にステートメントとメンバー宣言を表示します。

コード例:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- このルールが **true** に設定されている場合は、1 行にコード ブロックを表示します。
- このルールが **false** に設定されている場合は、別の行にコード ブロックを表示します。

コード例:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

*.editorconfig* ファイルの例:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>EditorConfig ファイルの例

作業の開始に役立つように、ここでは既定のオプションを使用する *.editorconfig* ファイルの例を示します。

```EditorConfig
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:none
dotnet_style_qualification_for_property = false:none
dotnet_style_qualification_for_method = false:none
dotnet_style_qualification_for_event = false:none

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:none
dotnet_style_predefined_type_for_member_access = true:none

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:none
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:none
csharp_style_var_when_type_is_apparent = true:none
csharp_style_var_elsewhere = true:none

# Expression-bodied members
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = true:none
csharp_style_expression_bodied_accessors = true:none

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:none
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>関連項目

- [クイック アクション](../ide/quick-actions.md)
- [EditorConfig での .NET の名前付け規則](../ide/editorconfig-naming-conventions.md)
- [移植可能なカスタム エディター オプションを作成する](../ide/create-portable-custom-editor-options.md)
- [.NET コンパイラ プラットフォームの .editorconfig ファイル](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
