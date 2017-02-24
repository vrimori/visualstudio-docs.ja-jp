---
title: "Editorconfig の .NET コード スタイル設定 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 01
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
translationtype: Human Translation
ms.sourcegitcommit: 31f433b28b67dc6f3179be87cb5894b5b3f0aa4f
ms.openlocfilehash: e0fcd94f2e42f2ce8d454b9d754cfa4ad063d9e0

---

# <a name="net-code-style-settings-for-editorconfig"></a>Editorconfig の .NET コード スタイル設定

## <a name="possible-values"></a>使用可能な値 

`options_name = false|true : none|suggestion|warning|error`

コード スタイル オプションには、**true** (このオプションを使用する) または **false** (このオプションを使用しない)、コロン (`:`)、重要度 (`none`、`suggestion`、`warning`、または `error`) を指定する必要があります。 重要度は、コード ベースでそのスタイルに適用する強制レベルを意味します。

重要度 | 効果
------------ | -------------
none | このスタイルに準拠していないとき、ユーザーには何も表示されませんが、コード生成機能はこのスタイルで生成します。 
修正候補 | このスタイルに準拠していないとき、修正候補としてユーザーに表示されます (最初の&2; 文字の下に点線が付きます)。
警告 | このスタイルに準拠していないとき、コンパイラの警告が表示されます。
エラー | このスタイルに準拠していないとき、コンパイラ エラーが表示されます。

## <a name="net-code-style-options"></a>.NET コード スタイルのオプション

- [Dotnet コード スタイルの設定](#this_and_me)
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
- [CSharp コード スタイルの設定](#csharp_codestyle)
    - ["var"](#var)
        - [組み込み型の "var"](#var_built_in)
        - [型が明らかな場合の "var"](#var_apparent)
        - [それ以外の場所の "var"](#var_elsewhere)
    - [式形式のメンバー](#expression_bodied_members)
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
    - ["Null" 検査設定](#null_checking)
        - [スロー式](#null_checking_throw_expressions)
        - [条件付き代理呼び出し](#null_checking_conditional_delegate_calls)

## <a name="a-namethisandmethis-and-me-qualificationa"></a><a name="this_and_me">"This." と "Me."修飾</a>

### <a name="a-namethisandmefieldsfieldsa"></a><a name="this_and_me_fields">フィールド</a>

|  オプション名 | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッドで使用されるすべての非静的フィールドに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として付けます。 | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** `Me.capacity = 0`
| False | 非静的メソッドで使用されるすべての非静的フィールドに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として付けません。 | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** `capacity = 0`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="a-namethisandmepropertiespropertiesa"></a><a name="this_and_me_properties">プロパティ</a>

|  オプション名 | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッドで使用されるすべての非静的プロパティに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として付けます。| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** `Me.ID = 0`
| False | 非静的メソッドで使用されるすべての非静的プロパティに C# の場合に `this.` を、Visual Basic の場合に `Me.` を接頭辞として*付けません*。 | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** `ID = 0`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="a-namethisandmemethodsmethodsa"></a><a name="this_and_me_methods">メソッド</a>
|  オプション名 | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッド内から呼び出されるすべての非静的フィールドに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として付けます。| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** `Me.Display()`
| False | 非静的メソッド内から呼び出されるすべての非静的フィールドに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として*付けません*。 | **C#:** <br>`Display();` <br><br> **Visual Basic:** `Display()`


#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="a-namethisandmeeventseventsa"></a><a name="this_and_me_events">イベント</a>
|  オプション名 | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 非静的メソッド内から参照されるすべての非静的イベントに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として付けます。| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Me.Elapsed, AddressOf Handler`
| False | 非静的メソッド内から参照されるすべての非静的イベントに C# の場合に `this.` を、VB の場合に `Me.` を接頭辞として*付けません*。 | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">型参照のための言語キーワードの型名 (int や string など) とフレームワークの型名</a>
### <a name="a-namelanguagekeywordsvariableslocals-parameters-and-membersa"></a><a name="language_keywords_variables">ローカル、パラメーター、メンバー</a>
|  オプション名 | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | ローカル、パラメーター、型メンバーの場合、型を表す言語キーワードを持つ型を使用し (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)、型名 (`Int32` や `Int64` など) の代わりにキーワードを使用します。| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | ローカル、パラメーター、型メンバーの場合、型を表す言語キーワードを持つ型を使用し (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)、キーワードの代わりに型名 (`Int32` や `Int64` など) を使用します。  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="a-namelanguagekeywordsmemberaccessmember-access-expressionsa"></a><a name="language_keywords_member_access">メンバー アクセス式</a>
|  オプション名 | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | キーワード表現 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) のある型でメンバー アクセス式が使用されるとき、キーワードを使用します。| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** `Dim local = Integer.MaxValue`
| False | キーワード表現 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) のある型でメンバー アクセス式が使用されるとき、型名を使用します。 | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="a-nameexpressionlevelexpression-level-preferencesa"></a><a name="expression_level">式レベル基本設定</a>
### <a name="a-nameexpressionlevelobjectinitializersobject-initializersa"></a><a name="expression_level_object_initializers">オブジェクト初期化子</a>
|  オプション名 | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 可能であれば、オブジェクト初期化子を使用し、オブジェクトを初期化します。| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** `Dim c = New Customer() With { .Age = 21 }`
| False | オブジェクト初期化子でオブジェクトを初期化*しません*。 | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="a-nameexpressionlevelcollectioninitializerscollection-initializersa"></a><a name="expression_level_collection_initializers">コレクション初期化子</a>
|  オプション名 | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

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

### <a name="a-nameexpressionleveltuplenamesexplicit-tuple-namesa"></a><a name="expression_level_tuple_names">明示的なタプル名</a>
|  オプション名 | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

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

### <a name="a-nameexpressionlevelnullcheckingcoalescing-expressions-in-null-checkinga"></a><a name="expression_level_null_checking">"null" 検査の結合式</a>
|  オプション名 | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

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

### <a name="a-nameexpressionlevelnullpropogationnull-propagation-in-null-checkinga"></a><a name="expression_level_null_propogation">"null" 検査の Null 値反映</a>
|  オプション名 | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **該当言語** | C# および Visual Basic

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

# <a name="a-namecsharpcodestylecsharp-code-style-settingsa"></a><a name="csharp_codestyle">CSharp コード スタイルの設定</a>
## <a name="a-namevarvara"></a><a name="var">"var"</a>
### <a name="a-namevarbuiltinvar-for-built-in-typesa"></a><a name="var_built_in">組み込み型の "var"</a>
|  オプション名 | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-namevarapparentvar-when-type-is-apparenta"></a><a name="var_apparent">型が明らかな場合の "var"</a>
|  オプション名 | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-namevarelsewherevar-elsewherea"></a><a name="var_elsewhere">それ以外の場所の "var"</a>
|  オプション名 | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-nameexpressionbodiedmembersmethodsa"></a><a name="expression_bodied_members">メソッド</a>
|  オプション名 | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-nameexpressionbodiedmembersconstructorsconstructorsa"></a><a name="expression_bodied_members_constructors">コンストラクター</a>
|  オプション名 | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-nameexpressionbodiedmembersoperatorsoperatorsa"></a><a name="expression_bodied_members_operators">演算子</a>
|  オプション名 | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-nameexpressionbodiedmemberspropertiespropertiesa"></a><a name="expression_bodied_members_properties">プロパティ</a>
|  オプション名 | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **該当言語** | C#

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | プロパティに式形式メンバーを使用します。| **C#:** <br>`public int Age => _age;`
| False | プロパティに式形式メンバーを使用しません。| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="a-nameexpressionbodiedmembersindexersindexersa"></a><a name="expression_bodied_members_indexers">インデクサー</a>
|  オプション名 | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-nameexpressionbodiedmembersaccessorsaccessorsa"></a><a name="expression_bodied_members_accessors">アクセサー</a>
|  オプション名 | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **該当言語** | C#

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

## <a name="a-namepatternmatchingpattern-matchinga"></a><a name="pattern_matching">パターン マッチング</a>
### <a name="a-namepatternmatchingiscastis-with-cast-checkinga"></a><a name="pattern_matching_is_cast">"cast" 検査の "is"</a>
|  オプション名 | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-namepatternmatchingasnullas-with-null-checkinga"></a><a name="pattern_matching_as_null">"null" 検査の "as"</a>
|  オプション名 | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **該当言語** | C#

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

### <a name="a-nameinlinedvariabledeclarationsinlined-variable-declarationsa"></a><a name="inlined_variable_declarations">インライン変数宣言</a>
|  オプション名 | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **該当言語** | C#

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | 可能であれば、`out` 変数をインラインで宣言します。 | **C#:** <br>`if (int.TryParse(value out int i) {...}`
| False | `out` 変数を明示的に宣言します。| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

## <a name="a-namenullcheckingnull-checking-preferencesa"></a><a name="null_checking">"Null" 検査設定</a>
### <a name="a-namenullcheckingthrowexpressionsthrow-expressionsa"></a><a name="null_checking_throw_expressions">スロー式</a>
|  オプション名 | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **該当言語** | C#

| 値 | 説明 | 適用済み 
| ------------- |:-------------|:-------------|
| True | スロー ステートメントの代わりにスロー式を使用します。 | **C#:** <br>`this.s = ss ?? throw new ArguementNullException(nameof(s));`
| False | スロー式の代わりにスロー ステートメントを使用します。| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>EditorConfig ファイルの例:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="a-namenullcheckingconditionaldelegatecallsprefer-conditional-delegate-callsa"></a><a name="null_checking_conditional_delegate_calls">条件付き代理呼び出しを使用する</a>
|  オプション名 | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **該当言語** | C#

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


<!--HONumber=Feb17_HO4-->


