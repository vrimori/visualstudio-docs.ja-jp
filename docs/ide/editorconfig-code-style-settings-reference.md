---
title: "EditorConfig の .NET コーディング規則の設定 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kaseyu
ms.author: kaseyu
manager: davidcsa
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 223750aef8d997c6ae017f49ea0a9522bdba72bc
ms.openlocfilehash: c5687a3971d4b670e73e55294e6dfd0c7c3f91d0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/10/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig の .NET コーディング規則の設定
.NET コーディング規則は [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options) ファイルを使用して構成します。 EditorConfig ファイルでは、**個々の .NET コーディング規則を有効化/無効化**し、(重要度レベルで) **規則を適用する程度を構成**することができます。 EditorConfig を使用して、コードベースに整合性を適用する方法の詳細については、[こちらの記事](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options)を参照してください。

サポートされている .NET コーディング規則には次の 3 つのカテゴリがあります。
- **[言語規則](#language)**: C# または Visual Basic 言語に関する規則です。たとえば、`var`/明示型、式形式メンバーを使用するなどです。
- **[書式規則](#formatting)**: コードを読みやすくするためのレイアウトや構造に関する規則です。たとえば、制御ブロックの Allman スタイルの中かっこ、スペースなどです。
- **[名前付け規則](#naming)**: オブジェクトに名前を付ける方法に関する規則です (例えば、`async` メソッドは "Async" で終わる必要がある等)。 

# <a name="language"> 言語規則</a>
## <a name="overview"></a>概要
**規則形式:**
`options_name = false|true : none|suggestion|warning|error`

コード スタイル オプションには、**true** (このオプションを使用する) または **false** (このオプションを使用しない)、コロン (`:`)、重要度 (`none`、`silent`、`suggestion`、`warning`、または `error`) を指定する必要があります。 重要度は、コード ベースでそのスタイルに適用する強制レベルを意味します。

`none` および `silent` は同義であり、ユーザーには何も表示されないことを意味します。 この規則を無効化する効果があります。

重要度 | 効果
------------ | -------------
none/silent | このスタイルに準拠していないとき、ユーザーには何も表示されませんが、コード生成機能はこのスタイルで生成します。 
修正候補 | このスタイルに準拠していないとき、修正候補としてユーザーに表示されます (最初の 2 文字の下に点線が付きます)。
警告 | このスタイルに準拠していないとき、コンパイラの警告が表示されます。
エラー | このスタイルに準拠していないとき、コンパイラ エラーが表示されます。

## <a name="net-language-convention-options"></a>.NET 言語規則のオプション

- **[.NET コード スタイルの設定](#this_and_me)**
    - ["This." と "Me."修飾](#this_and_me)
        - [フィールド](#this_and_me_fields)
        - [プロパティ](#this_and_me_properties)
        - [メソッド](#this_and_me_methods)
        - [イベント](#this_and_me_events)
    - [型参照のための言語キーワードの型名 (int や string など) とフレームワークの型名](#language_keywords)
        - [ローカル、パラメーター、メンバー](#language_keywords_variables)
        - [メンバー アクセス式](#language_keywords_member_access)
    - [式レベル基本設定](#expression_level)
        - [オブジェクト初期化子](#expression_level_object_initializers)
        - [コレクション初期化子](#expression_level_collection_initializers)
        - [明示的なタプル名](#expression_level_tuple_names)
        - ["null" 検査の結合式](#expression_level_null_checking)
        - ["null" 検査の Null 値反映](#expression_level_null_propogation)
- **[CSharp コード スタイルの設定](#csharp_codestyle)**
    - ["var"](#var)
        - [組み込み型の "var"](#var_built_in)
        - [型が明らかな場合の "var"](#var_apparent)
        - [それ以外の場所の "var"](#var_elsewhere)
    - [式形式のメンバー](#expression_body)
        - [メソッド](#expression_bodied_members_methods)
        - [コンストラクター](#expression_bodied_members_constructors)
        - [演算子](#expression_bodied_members_operators)
        - [プロパティ](#expression_bodied_members_properties)
        - [インデクサー](#expression_bodied_members_indexers)
        - [アクセサー](#expression_bodied_members_accessors)
    - [パターン マッチング](#pattern_matching)
        - ["cast" 検査の "is"](#pattern_matching_is_cast)
        - ["null" 検査の "as"](#pattern_matching_as_null)
    - [インライン変数宣言](#inlined_variable_declarations)
    - [式レベルの基本設定](#expression_level_csharp) -[`default` 式の単純化](#expression_level_default)
    - ["Null" 検査設定](#null_checking)
        - [スロー式](#null_checking_throw_expressions)
        - [条件付き代理呼び出し](#null_checking_conditional_delegate_calls)
    - [コード ブロック基本設定](#code_block)
        - [かっこを優先する](#prefer_braces)

## <a name="this_and_me">"This." と "Me."修飾</a>
### <a name="this_and_me_fields">フィールド (IDE0003/IDE0009)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `dotnet_style_qualification_for_field` | C# および Visual Basic | false:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッドで使用されるすべての非静的フィールドに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として付けます。 | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** <br> `Me.capacity = 0`
| False | 非静的メソッドで使用されるすべての非静的フィールドに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として付けません。 | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">プロパティ (IDE0003/IDE0009)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_property`| C# および Visual Basic | false:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッドで使用されるすべての非静的プロパティに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として付けます。| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** <br>`Me.ID = 0`
| False | 非静的メソッドで使用されるすべての非静的プロパティに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として*付けません*。 | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">メソッド (IDE0003/IDE0009)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_method`| C# および Visual Basic | false:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッド内から呼び出されるすべての非静的フィールドに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として付けます。| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** <br> `Me.Display()`
| False | 非静的メソッド内から呼び出されるすべての非静的フィールドに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として*付けません*。 | **C#:** <br>`Display();` <br><br> **Visual Basic:** <br> `Display()`


#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">イベント (IDE0003/IDE0009)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_qualification_for_event`| C# および Visual Basic | false:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッド内から参照されるすべての非静的イベントに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として付けます。| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | 非静的メソッド内から参照されるすべての非静的イベントに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として*付けません*。 | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">型参照のための言語キーワードの型名 (int や string など) とフレームワークの型名</a>
### <a name="language_keywords_variables"> ローカル、パラメーター、メンバー (IDE0012/IDE0014)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_locals_parameters_members`| C# および Visual Basic | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | ローカル、パラメーター、型メンバーの場合、型を表す言語キーワードを持つ型を使用し (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)、型名 (`Int32` や `Int64` など) の代わりにキーワードを使用します。| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | ローカル、パラメーター、型メンバーの場合、型を表す言語キーワードを持つ型を使用し (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)、キーワードの代わりに型名 (`Int32` や `Int64` など) を使用します。  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">メンバー アクセス式 (IDE0013/IDE0015)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_predefined_type_for_member_access`| C# および Visual Basic | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | キーワード表現 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) のある型でメンバー アクセス式が使用されるとき、キーワードを使用します。| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Integer.MaxValue`
| False | キーワード表現 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) のある型でメンバー アクセス式が使用されるとき、型名を使用します。 | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">式レベル基本設定</a>
### <a name="expression_level_object_initializers">オブジェクト初期化子 (IDE0017)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_object_initializer`| C# および Visual Basic | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 可能であれば、オブジェクト初期化子を使用し、オブジェクトを初期化します。| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | オブジェクト初期化子でオブジェクトを初期化*しません*。 | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">コレクション初期化子 (IDE0028)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_collection_initializer`| C# および Visual Basic | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 可能であれば、コレクション初期化子を使用してコレクションを初期化します。| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | オブジェクト初期化子でコレクションを初期化*しません*。 | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">明示的なタプル名 (IDE0033)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_explicit_tuple_names`| C# 7.0+ および Visual Basic 15+ | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | ItemX プロパティではなくタプル名を使用します。| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | タプル名ではなく ItemX プロパティを使用します。 | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">"null" 検査の結合式 (IDE0029)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_coalesce_expression`| C# および Visual Basic | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 三項演算子検査ではなく null 結合式を使用します。| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | null 結合式ではなく三項演算子検査を使用します。 | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">"null" 検査の null 値反映 (IDE0031)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_style_null_propagation`| C# 6.0+ および Visual Basic 14+ | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 可能であれば、null 条件演算子を使用します。| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | 可能であれば、三項 null 検査を使用します。 | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">CSharp コード スタイルの設定</a>
## <a name="var">"var" と明示型</a>
### <a name="var_built_in">組み込み型の "var" (IDE0007、IDE0008)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_for_built_in_types`| C# | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | `int` などの組み込みシステム型に `var` を使用します。| **C#:** <br>`var x = 5;`
| False | `int` などの組み込みシステム型に `var` を使用しません。 | **C#:** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">型が明らかな場合の "var" (IDE0007、IDE0008)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_when_type_is_apparent`| C# | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 宣言式の右側で型が既に述べられているときに `var` を使用します。| **C#:** <br>`var obj = new C();`
| False | 宣言式の右側で型が既に述べられているときに `var` を使用しません。 | **C#:** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">それ以外の場所の "var" (IDE0007、IDE0008) </a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_var_elsewhere`| C# | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 別のコード スタイル ルールにより上書きされない限り、あらゆるケースで `var` を使用します。| **C#:** <br>`var f = this.Init();`
| False | 別のコード スタイル ルールにより上書きされない限りあらゆるケースで var を使用することは望みません。| **C#:** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">式形式のメンバー</a>
### <a name="expression_bodied_members_methods">メソッド (IDE0022)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_methods`| C# 6.0+ | false:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | メソッドに式形式メンバーを使用します。| **C#:** <br>`public int GetAge() => this.Age;`
| False | メソッドに式形式メンバーを使用しません。| **C#:** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">コンストラクター (IDE0021)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_constructors`| C# 7.0+ | false:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | コンストラクターに式形式メンバーを使用します。| **C#:** <br>`public Customer(int age) => Age = age;`
| False | コンストラクターに式形式メンバーを使用しません。| **C#:** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">演算子 (IDE0023、IDE0024)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_operators` | C# 7.0+ | false:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 演算子に式形式メンバーを使用します。| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | 演算子に式形式メンバーを使用しません。| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">プロパティ (IDE0025)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_properties` | C# 7.0+ | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | プロパティに式形式メンバーを使用します。| **C#:** <br>`public int Age => _age;`
| False | プロパティに式形式メンバーを使用しません。| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = true:none
``` 

### <a name="expression_bodied_members_indexers">インデクサー (IDE0026)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_indexers` | C# 7.0+ | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | インデクサーに式形式メンバーを使用します。| **C#:** <br>`public T this[int i] => _value[i];`
| False | インデクサーに式形式メンバーを使用しません。| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">アクセサー (IDE0027)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_expression_bodied_accessors` | C# 7.0+ | true:なし | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | アクセサーに式形式メンバーを使用します。| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | アクセサーに式形式メンバーを使用しません。| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">パターン マッチング</a>
### <a name="pattern_matching_is_cast">"cast" 検査の "is" (IDE0020)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_is_with_cast_check` | C# 7.0+ | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | `is` 式と型キャストの代わりにパターン マッチングを使用します。| **C#:** <br>`if (o is int i) {...}`
| False | パターン マッチングの代わりに `is` 式と型キャストを使用します。| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">"null" 検査の "as" (IDE0019)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_pattern_matching_over_as_with_null_check` | C# 7.0+ | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | `as` 式と null 検査の代わりにパターン マッチングを使用し、何かが特定の型であるか判断します。| **C#:** <br>`if (o is string s) {...}`
| False | パターン マッチングの代わりに `as` 式と null 検査を使用し、何かが特定の型であるか判断します。| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">インライン変数宣言 (IDE0018)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_inlined_variable_declaration` | C# 7.0+ | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 可能であれば、`out` 変数をインラインで宣言します。 | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | `out` 変数を明示的に宣言します。| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">式レベル基本設定</a>
### <a name="expression_level_default">`default` 式の簡略化 (IDE0034) </a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_simple_default_expression` | C# 7.1+ | true:提案 | Visual Studio 2017 v. 15.3 |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | `default(T)` より `default` を優先 | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | 優先。 | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">"Null" 検査設定</a>
### <a name="null_checking_throw_expressions">スロー式 (IDE0016)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_throw_expression`  | C# 7.0+ | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | スロー ステートメントの代わりにスロー式を使用します。 | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | スロー式の代わりにスロー ステートメントを使用します。| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">条件付き代理呼び出しを使用する (IDE0041)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_style_conditional_delegate_call`  | C# 6.0+ | true:提案 | Visual Studio 2017 RTW |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | null 検査を実行する代わりに lambda を呼び出すとき、条件付き結合演算 (`?.`) を使用します。 | **C#:** <br>`func?.Invoke(args);`
| False | 条件付き結合演算 (`?.`) を使用する代わりに lambda を呼び出す前に null 検査を実行します。| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

## <a name="code_block">"コード ブロック基本設定</a>
### <a name="prefer_braces">かっこを優先する (IDE0011)</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_prefer_braces`  | C#  | true:なし | Visual Studio 2017 v. 15.3 |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | かっこを優先する | **C#:** <br>`if (test) { this.Display(); }`
| False | 可能な場合は、かっこを使用しない | **C#:** <br>`if (test) this.Display();`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

# <a name="formatting"> 書式規則 </a>
## <a name="overview"></a>概要
**規則形式:**
`options_name = false|true`

書式オプションには、**true** (このオプションを使用する) または **false** (このオプションを使用しない) を指定する必要があります。ただし、規則を適用する条件を代わりに指定する必要があるいくつかのケースを除きます。

## <a name="net-formatting-options"></a>.NET 書式のオプション

- **[.NET 書式設定](#usings)**
    - [using の整理](#usings)
        - [最初にシステム ディレクティブを並べ替える](#usings_sort_system_first)
- **[C# 書式設定](#newline)**
    - [改行オプション](#newline)
        - [左中かっこ (`{`) の前の改行](#newline_before_brace)
        - [`else` の前の改行](#newline_before_else)
        - [`catch` の前の改行](#newline_before_catch)
        - [`finally` の前の改行](#newline_before_finally)
        - [オブジェクト初期化子のメンバーの前の改行](#newline_before_object)
        - [匿名型のメンバーの前の改行](#newline_before_anonymous)
        - [クエリ式の句のメンバーの前の改行](#newline_before_query)
    - [インデント オプション](#indent)
        - [`switch` ケース コンテンツにインデントを付ける](#indent_switch)
        - [インデント`switch`ラベル](#indent_switch_labels)
        - [ラベルの位置付け](#label)
    - [スペース オプション](#spacing)
        - [キャストの後のスペース](#space_after_cast)
        - [制御フロー ステートメント内のキーワードの後のスペース](#space_control_flow)
        - [メソッド宣言パラメーター リストのかっこの間のスペース](#space_parameter_list)
        - [メソッド呼び出し引数リストのかっこ内のスペース](#space_method_call)
        - [その他のオプションのかっこ内のスペース](#space_other)
    - [折り返しオプション](#wrapping)
        - [1 行に複数のステートメントとメンバー宣言を表示する](#wrapping_statement)
        - [ブロックを単一行に配置する](#wrapping_block)

## <a name="usings">using の整理</a>
### <a name="usings_sort_system_first">最初にシステム ディレクティブを並べ替える</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`dotnet_sort_system_directives_first`  |  C# および Visual Basic | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | System.* using をアルファベット順に並べ替え、他の using の前に配置します。| **C#:** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | using の順序に関する要件はありません | **C#:** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">C# 書式設定</a>
## <a name="newline">改行オプション</a>
### <a name="newline_before_brace"> 左中かっこ (`{`) の前の改行</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_open_brace`  |  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| accessors、anonymous_methods、anonymous_types、control_blocks、events、indexers、lambdas、local_functions、methods、object_collection、properties、types  (複数の場合は、"," で区切ります)。 | 中かっこは指定された式の新しい行に配置する必要があります (Allman スタイル)。 |
| すべて | 中かっこはすべての式の新しい行に配置する必要があります (Allman)。 |
| none | 中かっこはすべての式の同じ行に配置する必要があります (K&R)。 |

#### <a name="applied"></a>以下のように適用されます。
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> `else` の前の改行</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_before_else` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| True | 新しい行に `else` ステートメントを配置します。  |
| False | 同じ行に `else` ステートメントを配置します。  |

#### <a name="applied"></a>以下のように適用されます。
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> `catch` の前の改行</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_catch`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| True | 新しい行に `catch` ステートメントを配置します。  |
| False | 同じ行に `catch` ステートメントを配置します。 |

#### <a name="applied"></a>以下のように適用されます。
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> `finally` の前の改行</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_finally`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| True | `finally` ステートメントを右中かっこの後の新しい行に配置する必要があります。  |
| False | `finally` ステートメントを右中かっこと同じ行に配置する必要があります。  |

#### <a name="applied"></a>以下のように適用されます。
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
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> オブジェクト初期化子のメンバーの前の改行</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_object_initializers`|  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| True | オブジェクト初期化子のメンバーを別の行に配置する必要があります。  |
| False | オブジェクト初期化子のメンバーを同じ行に配置する必要があります。  |

#### <a name="applied"></a>以下のように適用されます。
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> 匿名型のメンバーの前の改行</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_new_line_before_members_in_anonymous_types` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| True | 匿名型のメンバーを別の行に配置する必要があります。  |
| False | 匿名型のメンバーを同じ行に配置する必要があります。  |

#### <a name="applied"></a>以下のように適用されます。
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query"> クエリ式の句のメンバーの前の改行</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_new_line_within_query_expression_clauses`  |  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| True | クエリ式の句の要素を別の行に配置する必要があります。  |
| False | クエリ式の句の要素を同じ行に配置する必要があります。  |

#### <a name="applied"></a>以下のように適用されます。
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">インデント オプション</a>
### <a name="indent_switch"> `switch` ケース コンテンツにインデントを付ける </a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_case_contents`  |  C#  | true | Visual Studio 2017 v. 15.3  |

| 値 | 説明 
| ------------- |:-------------|
| True | `switch` ケース コンテンツにインデントを付けます  |
| False | `switch` ケース コンテンツにインデントを付けません |

#### <a name="applied"></a>以下のように適用されます。
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
```

```csharp
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

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="indent_switch_labels">インデント`switch`ラベル</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_indent_switch_labels`  |  C#  | true | Visual Studio 2017 v. 15.3  |

| 値 | 説明 
| ------------- |:-------------|
| True | インデント`switch`ラベル  |
| False | インデントされません`switch`ラベル |

#### <a name="applied"></a>以下のように適用されます。
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
```

```csharp
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

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_switch_labels = true
``` 

### <a name="label">ラベルの位置付け</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|`csharp_indent_labels`  |  C#  | one_less | Visual Studio 2017 v. 15.3  |


| 値 | 説明 
| ------------- |:-------------|
| one_less | ラベルは、現在のコンテキストのインデントを 1 つ減らした位置に配置されます |
| no_change | ラベルは、現在のコンテキストと同じインデントで配置されます |

#### <a name="applied"></a>以下のように適用されます。
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">スペース オプション</a>
### <a name="space_after_cast"> キャストの後のスペース</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_cast` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 値 | 説明 | 適用済み |
| ------------- |:-------------|:-------------|
| True | キャストと値の間にスペースが必要です  | **C#:** <br>`int y = (int) x;`
| False | キャストと値の間にスペースは必要ありません | **C#:** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> 制御フロー ステートメント内のキーワードの後のスペース </a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_after_keywords_in_control_flow_statements` |  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 | 適用済み |
| ------------- |:-------------|:-------------|
| True | キーワードの後にスペースが必要です | **C#:** <br>`for (int i;i<x;i++) { ... }`
| False | キーワードの後にスペースは必要ありません | **C#:** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> メソッド宣言引数リストのかっこの間のスペース </a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
| `csharp_space_between_method_declaration_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 値 | 説明 | 適用済み |
| ------------- |:-------------|:-------------|
| True | キーワードの後にスペースが必要です | **C#:** <br>`void Bark( int x ) { ... }`
| False | キーワードの後にスペースは必要ありません | **C#:** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> メソッド呼び出し引数リストのかっこ内のスペース</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_method_call_parameter_list_parentheses` |  C#  | false | Visual Studio 2017 v. 15.3  |


| 値 | 説明 | 適用済み |
| ------------- |:-------------|:-------------|
| TRUE | 制御フロー ステートメントのかっこの間にスペースを配置します。 | **C#:** <br>`MyMethod( argument );`
| false | 式のかっこの間にスペースを配置します。 | **C#:** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> その他のオプションのかっこ内のスペース </a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_space_between_parentheses`  |  C#  | false | Visual Studio 2017 v. 15.3  |


| 値 | 説明 | 適用済み |
| ------------- |:-------------|:-------------|
| control_flow_statements | 制御フロー ステートメントのかっこの間にスペースを配置します。 | **C#:** <br>`for( int i;i<x;i++ ) { ... }`
| 式 | 式のかっこの間にスペースを配置します。 | **C#:** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | 型キャストのかっこの間にスペースを配置します。 | **C#:**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">折り返しオプション</a>
### <a name="wrapping_statement">1 行に複数のステートメントとメンバー宣言を表示する</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|  `csharp_preserve_single_line_statements`   |  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 |
| ------------- |:-------------|
| True | 1 行に複数のステートメントとメンバー宣言を表示する  | 
| False | 別の行にステートメントとメンバー宣言を表示します。 | 

#### <a name="applied"></a>適用済み
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">ブロックを単一行に配置する</a>
| **オプション名** | **該当言語** | **Visual Studio の既定値** | **サポートされているバージョン** |
| ----------- | -------------------- | ----------------------| ----------------  |
|   `csharp_preserve_single_line_blocks`    |  C#  | true | Visual Studio 2017 v. 15.3  |


| 値 | 説明 |
| ------------- |:-------------|
| True | ブロックを単一行に配置します。 | 
| False | ブロックを別の行に配置します。 | 

#### <a name="applied"></a>適用済み
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming"> 名前付け規則 </a>
## <a name="overview"></a>概要
**規則形式:**<br>
namingRuleTitle:<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle:<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle:<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>名前付け規則の作成
名前付け規則には、**シンボル**、**スタイル**、および**重要度**を指定する必要があります。 名前付け規則は、固有度の高いものから低いものの順に並べる必要があります。 適用可能な最初に検出された規則のみが適用されます。 

### <a name="severity"></a>重要度
名前付けスタイル規則の重要度の有効なオプションは、`none`、`silent`、`suggestion`、`warning`、`error` です。

 `none` および `silent` は同義であり、ユーザーには何も表示されないことを意味します。 この規則を無効化する効果があります。

 `suggestion` は、IDE のエラー一覧でユーザーに以下が表示されることを意味します。 重要度が `suggestion` の場合、名前付け規則は実行されますが、ビルドは中断されません。

重要度 | 効果
------------ | -------------
none/silent | このスタイルに準拠していないとき、ユーザーには何も表示されませんが、コード生成機能はこのスタイルで生成します。 
修正候補 | このスタイルに準拠していないとき、修正候補としてユーザーに表示されます (最初の 2 文字の下に点線が付きます)。
警告 | このスタイルに準拠していないとき、コンパイラの警告が表示されます。
エラー | このスタイルに準拠していないとき、コンパイラ エラーが表示されます。

### <a name="symbol-specification"></a>シンボル指定
名前付け規則を適用する必要がある場合に、_どの_シンボルで_どの_修飾子と_どの_アクセシビリティ レベルを使用するかを指定します。

|  オプション名 | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| シンボル | ユーザー補助 | 修飾子
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |


### <a name="style-specification"></a>スタイル指定
シンボルに適用する名前付けスタイルを指定します。

|  オプション名 | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| スタイル | 説明 |
| ------------- |:-------------:|
| プレフィックス | 識別子の前に配置する必要がある文字。 |
| サフィックス | 識別子の後に配置する必要がある文字。 |
| 単語の区切り記号 | 識別子の単語の間に必要な区切り記号。 |
| [大文字/小文字の設定] |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 


### <a name="example-naming-convention"></a>名前付け規則の例
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

