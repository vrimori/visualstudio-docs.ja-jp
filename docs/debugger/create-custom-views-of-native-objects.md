---
title: ネイティブ オブジェクトのカスタム ビューの作成
description: Natvis フレームワークを使用して、Visual Studio がデバッガーでネイティブ型を表示する方法をカスタマイズするには
ms.date: 10/31/2018
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ca1cf68af84556a76c29417c9bd56894a70f12ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997326"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>デバッガーでのネイティブ オブジェクトのカスタム ビューの作成

Visual Studio *Natvis* framework ネイティブ型をなどのデバッガー変数ウィンドウに表示する方法をカスタマイズする、**ローカル**と**ウォッチ**windows、および**データヒント**します。 Natvis 視覚化は、デバッグ中に表示を作成する種類を作成できます。 

Natvis 置換、 *autoexp.dat* XML 構文より適切に診断、バージョン管理、Visual Studio の以前のバージョンと複数のファイルをサポートします。  


## <a name="BKMK_Why_create_visualizations_"></a>Natvis 視覚化

Natvis フレームワークを使用すると、開発者が確認できるようにしてより簡単にデバッグ中を作成する型の視覚化ルールを作成できます。  

たとえば、次の図には、型の変数は示しています。 [::textbox](http://go.microsoft.com/fwlink/?LinkId=258422) 、カスタム視覚化が適用されず、デバッガー ウィンドウでします。  

![テキスト ボックスに既定のビジュアル化](../debugger/media/dbg_natvis_textbox_default.png "テキスト ボックスの既定の視覚化")  

強調表示された行には `Text` クラスの `TextBox` プロパティが示されています。 複雑なクラス階層によって、このプロパティを検索する困難になります。 デバッガーでは、テキスト ボックス内の文字列が表示されないように、カスタム文字列型を解釈する方法がわからない。  

同じ`TextBox`Natvis ビジュアライザーのカスタム ルールが適用されるときの変数ウィンドウではるかに簡単表示します。 クラスの重要なメンバーが同時に、表示され、デバッガーには、カスタム文字列型の基になる文字列値が表示されます。  

![ビジュアライザーを使用してデータをテキスト ボックス](../debugger/media/dbg_natvis_textbox_visualizer.png "ビジュアライザーを使用してデータをテキスト ボックス")  

##  <a name="BKMK_Using_Natvis_files"></a>C++ プロジェクトで .natvis ファイルの使用  

Natvis は *.natvis*視覚化ルールを指定するファイル。 A *.natvis*ファイルは XML ファイルは、 *.natvis*拡張機能。 Natvis スキーマが定義されている *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*します。  

基本的な構造を *.natvis*ファイルが 1 つまたは複数`Type`視覚化エントリを表す要素。 それぞれの完全修飾名`Type`要素が指定されてその`Name`属性。  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  

  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  

Visual Studio では、いくつか用意されています *.natvis*内のファイル、 *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*フォルダー。 これらのファイルは、多くの一般的な種類の視覚化ルールがあるし、新しい型の視覚化を記述するための例として使用できます。  

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ プロジェクトに .natvis ファイルを追加します。  

追加することができます、 *.natvis*にすべての C++ プロジェクト ファイル。  

**新しい追加 *.natvis*ファイル。**

1. C++ プロジェクト ノードを選択**ソリューション エクスプ ローラー**、選択および**プロジェクト** > **新しい項目の追加**、またはプロジェクトを右クリックし、選択**追加**  > **新しい項目の**します。
   
1. **新しい項目の追加**ダイアログ ボックスで、 **Visual C** > **ユーティリティ** > **デバッガー視覚化ファイル (.natvis)**. 
   
1. ファイルの名前を指定し、選択**追加**します。
   
   新しいファイルに追加されます**ソリューション エクスプ ローラー**、し、Visual Studio のドキュメント ウィンドウで開きます。 

Visual Studio デバッガーが読み込む *.natvis* C++ プロジェクト内のファイル、既定では、自動的にも含まれていますで、 *.pdb*ファイル、プロジェクトをビルドするとき。 ビルドのアプリケーションをデバッグする場合、デバッガーが読み込まれます、 *.natvis*ファイルから、 *.pdb*ファイルを開き、プロジェクトがあるない場合でもです。 たくない場合、 *.natvis*ファイルに含まれる、 *.pdb*、ビルドから除外することができます *.pdb*ファイル。

**除外する、 *.natvis*からファイルを *.pdb*:**

1. 選択、 *.natvis*ファイル**ソリューション エクスプ ローラー**を選択し、**プロパティ**アイコン、またはファイルを右クリックし、選択**プロパティ**.
   
1. 矢印の横にドロップダウン**ビルドから除外**を選択し、**はい**、し、 **ok**します。  

>[!NOTE]
>実行可能プロジェクトをデバッグするには、追加するのには、ソリューション項目を使用して、 *.natvis*でないファイルを *.pdb*、使用可能な C++ プロジェクトがないためです。  

>[!NOTE]
>読み込まれる Natvis 規則、 *.pdb* 、モジュール内の型にのみ適用されますが、 *.pdb*を参照します。 たとえば場合、 *Module1.pdb*という名前の型の Natvis エントリは`Test`にのみ適用されます、`Test`クラス*Module1.dll*します。 別のモジュールでは、という名前のクラスも定義されている場合`Test`、 *Module1.pdb* Natvis エントリは、これには適用されません。  

### <a name="BKMK_natvis_location"></a> Natvis ファイルの場所  

追加することができます *.natvis*をユーザー ディレクトリまたはシステム ディレクトリにファイルが複数のプロジェクトに適用したい場合。  

*.Natvis*ファイルは、次の順序で評価されます。  

1. すべて *.natvis*に埋め込まれているファイル、 *.pdb*読み込まれているプロジェクトで同じ名前のファイルが存在しない場合、デバッグしています。  

1. すべて *.natvis*読み込まれた C++ プロジェクトまたは最上位のソリューションに含まれるファイル。 このグループには、他の言語で、クラス ライブラリ プロジェクトではなくなど、読み込まれたすべての C++ プロジェクトが含まれています。 

1.  ユーザー固有の Natvis ディレクトリ (たとえば、 *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*)。  

1.  システム全体の Natvis ディレクトリ (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*)。 このディレクトリに、 *.natvis* Visual Studio と共にインストールされるファイル。 管理者のアクセス許可があれば、このディレクトリにファイルを追加することができます。  

## <a name="modify-natvis-files-while-debugging"></a>デバッグ中に .natvis ファイルを変更します。  

変更することができます、 *.natvis*そのプロジェクトのデバッグ中には、IDE でファイル。 Visual Studio を使用したデバッグの同じインスタンスでファイルを開く、それを変更し、保存します。 ファイルを保存するとすぐに、**ウォッチ**と**ローカル**変更を反映するように windows を更新します。 

追加または削除することができますも *.natvis*ファイルでソリューションをデバッグして、Visual Studio が追加または関連する視覚エフェクトを削除します。  

更新することはできません *.natvis*ファイルに埋め込まれている *.pdb*デバッグ中のファイルします。  

変更する場合、 *.natvis*ファイル、Visual Studio の外部で変更が反映されない自動的にします。 デバッガー ウィンドウを更新するを再評価することができます、 **.natvisreload**コマンド、**ウォッチ**ウィンドウ。 変更、デバッグ セッションを再起動しなくても有効になります。  

使用しても、 **.natvisreload**をアップグレードするコマンド、 *.natvis*ファイルより新しいバージョンにします。 たとえば、 *.natvis*その人がそれ以外の場合に加えた最近の変更を取得して、ソース管理にファイルをチェックすることがあります。 

##  <a name="BKMK_Expressions_and_formatting"></a> 式と書式  
Natvis 視覚化では、C++ 式を使用して、表示するデータ項目を指定します。 説明されるだけでなく、拡張機能と、デバッガーでの C++ 式の制限事項、 [Context operator (C++)](../debugger/context-operator-cpp.md)次に注意してください。  

- Natvis 式は、現在のスタック フレームではなく視覚化されるオブジェクトのコンテキストで評価されます。 たとえば、`x`という名前のフィールドに、Natvis 式で参照されて**x**という名前のローカル変数が、視覚化されるオブジェクトで**x**で現在の関数。 グローバル変数にアクセスすることができますが、Natvis 式内のローカル変数にアクセスできません。  

- Natvis 式には、関数の評価や副作用を許可しません。 関数呼び出しと代入演算子は無視されます。 [デバッガーの組み込み関数](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) は、他の関数とは異なり副作用がないため、Natvis 式からは自由に呼び出すことができます。  

- 式を表示する方法を制御するためで説明されている書式指定子のいずれかを使用できます[書式指定子で C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)します。 エントリがなど使用 Natvis によって内部的にした場合、書式指定子は無視されます、`Size`で式を[ArrayItems の展開](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)します。  

## <a name="natvis-views"></a>Natvis ビュー  

さまざまな方法で型を表示する別の Natvis ビューを定義することができます。 たとえば、次の視覚エフェクトに示します`std::vector`という名前の簡略化されたビューを定義する`simple`します。 `DisplayString`と`ArrayItems`要素を既定のビューに表示して、`simple`ビュー、中に、`[size]`と`[capacity]`に項目を表示しない、`simple`ビュー。 

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  


**ウォッチ**ウィンドウで、使用、 **、ビュー**書式指定子を別のビューを指定します。 単純なビューとして表示**vec,view(simple)**:  

![単純なビューとウォッチ ウィンドウ](../debugger/media/watch-simpleview.png "単純なビューとウォッチ ウィンドウ")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis エラー  

デバッガーには、視覚化エントリのエラーが発生すると、それらを無視します。 未加工の形式で型を表示、または、別の適切な視覚化を選択します。 Natvis 診断は、デバッガーで、視覚化エントリが無視される理由を理解して基になる構文を確認し、解析エラーを使用できます。 

**Natvis 診断を有効にします。**

- **ツール** > **オプション**(または**デバッグ** > **オプション**) > **のデバッグ** > **出力ウィンドウ**設定**Natvis 診断メッセージ (C++ のみ)** に**エラー**、**警告**、または**詳細な**、し、 **OK**します。 

エラーが表示されます、**出力**ウィンドウ。  

##  <a name="BKMK_Syntax_reference"></a> Natvis 構文のリファレンス  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer の要素  
`AutoVisualizer` 要素は *.natvis* ファイルのルート ノードであり、名前空間 `xmlns:` 属性を含みます。 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

`AutoVisualizer`要素を持つことができます[型](#BKMK_Type)、 [HResult](#BKMK_HResult)、 [UIVisualizer](#BKMK_UIVisualizer)、および[CustomVisualizer](#BKMK_CustomVisualizer)子。 

###  <a name="BKMK_Type"></a> Type 要素  

基本的な`Type`この例のようになります。  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 `Type`要素を指定します。  

1. 視覚エフェクトの種類を使用する必要があります (、`Name`属性)。  
   
2. その型のオブジェクトの値がどのように表示されるか ( `DisplayString` 要素)。  
   
3. 型のメンバーがどのようにユーザーが [変数] ウィンドウで型がどのように展開するときに (、`Expand`ノード)。  
   
#### <a name="templated-classes"></a>テンプレート クラス
`Name`の属性、`Type`要素のアスタリスク`*`テンプレート クラス名を使用できるワイルドカード文字として。  

オブジェクトがあるかどうかに使用する同じ視覚エフェクトでは、次の例で、`CAtlArray<int>`または`CAtlArray<float>`します。 特定の視覚化エントリがある場合、 `CAtlArray<float>`、汎用的なものより優先されます。  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

マクロ $t1、$t2 などを使用して、視覚化エントリでテンプレート パラメーターを参照してなど。 これらのマクロの例を見つけるには、Visual Studio に付属の *.natvis* ファイルをご覧ください。  

####  <a name="BKMK_Visualizer_type_matching"></a> ビジュアライザーと型の対応付け  
視覚化エントリでは、検証に失敗した場合、[次へ] の使用可能な視覚化が使用されます。  

#### <a name="inheritable-attribute"></a>継承可能な属性  
省略可能な`Inheritable`属性は、視覚エフェクトが基本型にのみ適用されますまたはすべての基本データ型を派生型かどうかを指定します。 `Inheritable` の既定値は `true`です。  

次の例では、視覚エフェクトにのみ適用されます、`BaseClass`型。  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>Priority 属性  

省略可能な`Priority`属性定義が解析に失敗した場合に代替の定義を使用する順序を指定します。 可能な値`Priority`が: `Low`、 `MediumLow`、`Medium`、 `MediumHigh`、および`High`します。 既定値は `Medium` です。 `Priority`属性を同じ優先順位の間でのみ識別 *.natvis*ファイル。  

次の例では、まず 2015 STL と一致するエントリを解析します。 解析に失敗した場合、STL の 2013年バージョンを別のエントリを使用します。  

```xml
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  

<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  

### <a name="optional-attribute"></a>Optional 属性  
配置することができます、`Optional`任意のノードの属性。 省略可能なノード内の部分式の解析に失敗すると、デバッガーでは、そのノードは無視されますの残りの部分を適用、`Type`規則。 次の型では、 `[State]` は省略不可能ですが、 `[Exception]` は省略可能です。  場合`MyNamespace::MyClass`_ という名前のフィールドが`M_exceptionHolder`の両方を`[State]`ノードと`[Exception]`がある場合、ノードが表示ない`_M_exceptionHolder`フィールドにのみ、`[State]`ノードが表示されます。

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Condition 属性  

省略可能な`Condition`属性は、多くの視覚化要素の使用と視覚化ルールを使用するかを指定します。 Condition 属性内の式が解決される場合`false`、視覚化ルールは適用されません。 評価されると、 `true`、か、ありません`Condition`属性、視覚エフェクトに適用されます。 視覚化エントリの場合、その他のロジックについては、この属性を使用することができます。 

たとえば、次の視覚エフェクトには 2 つ`DisplayString`スマート ポインター型の要素。 ときに、`_Myptr`メンバーが空の場合、最初の条件`DisplayString`に要素が解決される`true`ので、そのフォームが表示されます。 ときに、`_Myptr`メンバーが空でない場合に、条件が評価されます`false`、および 2 番目の`DisplayString`要素が表示されます。  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView および ExcludeView 属性  

`IncludeView`と`ExcludeView`属性は、要素を表示または特定のビューに表示されませんを指定します。 などの Natvis 仕様で`std::vector`、`simple`ビューが表示されない、`[size]`と`[capacity]`項目。

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

使用することができます、`IncludeView`と`ExcludeView`型および個々 のメンバーの属性。  

###  <a name="BKMK_Versioning"></a> Version 要素  
`Version`要素には、特定のモジュールとバージョンを視覚化エントリのスコープします。 `Version`要素により、名前の競合を回避できます、不用意が削減され、さまざまな種類のバージョンのさまざまな視覚エフェクトを使用します。  

異なるモジュールで使用される共通のヘッダー ファイルには、型が定義されている場合、型が、指定したモジュールのバージョンの場合にのみ、バージョン管理された視覚エフェクトが表示されます。  

次の例では、視覚エフェクトにのみ適用できます、`DirectUI::Border`型で見つかった、`Windows.UI.Xaml.dll`バージョン 1.0 ~ 1.5。 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> DisplayString 要素 
`DisplayString`要素は、変数の値として表示する文字列を指定します。 この要素には、任意の文字列を式と組み合わせて使用できます。 中かっこ内のすべてのものは式として解釈されます。 たとえば、次`DisplayString`エントリ。  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

手段型の変数はその`CPoint`この図のように表示します。  

 ![DisplayString 要素を使用して](../debugger/media/dbg_natvis_cpoint_displaystring.png "DisplayString 要素を使用します。")  

`DisplayString`式、`x`と`y`のメンバーである`CPoint`、中かっこ内にあるため、その値が評価されます。 二重中かっこを使用して、中かっこをエスケープする方法にも示しています (`{{`または`}}`)。  

> [!NOTE]
> `DisplayString` 要素でのみ、任意の文字列と中かっこ構文を使用できます。 その他のすべての視覚化要素では、デバッガーで評価できる式のみを受け入れます。  

###  <a name="BKMK_StringView"></a> StringView 要素 

`StringView`要素は、デバッガーが組み込みテキスト ビジュアライザーに送信できる値を定義します。 たとえばの次の視覚エフェクトを指定、`ATL::CStringT`型。  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

`CStringT`オブジェクトは、この例のような変数 ウィンドウが表示されます。   

![CStringT DisplayString 要素](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString 要素")  

追加、`StringView`要素は、視覚エフェクトをテキストとして表示できる値をデバッガーに指示します。  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

デバッグ中に、変数の横にある虫眼鏡アイコンを選択を選び**テキスト ビジュアライザー**文字列の表示を**m_pszData**を指します。  

 ![StringView ビジュアライザーを含む CStringT データ](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView ビジュアライザーを含む CStringT データ")  

式`{m_pszData,su}`C++ 書式指定子が含まれています**su**を Unicode 文字列として値を表示します。 詳細については、次を参照してください。[書式指定子で C++](../debugger/format-specifiers-in-cpp.md)します。  

###  <a name="BKMK_Expand"></a> 要素を展開します。 

省略可能な`Expand`ノードが [変数] ウィンドウで型を展開すると、視覚化された型の子をカスタマイズします。 `Expand`ノードが子要素を定義する子ノードの一覧を受け入れます。  

- 場合、`Expand`ノードで指定されていない視覚化エントリでは、子は、既定の展開規則を使用します。  
  
- 場合、`Expand`ノードは、デバッガー ウィンドウで、型が拡張できない、その下にある子ノードなしで指定します。  

####  <a name="BKMK_Item_expansion"></a> Item の展開  

 `Item`要素が、最も基本的で一般的な要素で、`Expand`ノード。 `Item` は 1 つの子要素を定義します。 たとえば、`CRect`フィールドを持つクラス`top`、 `left`、 `right`、および`bottom`は次の視覚化エントリがあります。  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

デバッガー ウィンドウで、`CRect`型がこの例のようになります。  

![Item 要素の展開を含む CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Item 要素の展開を含む CRect")  

デバッガーで指定された式の評価、`Width`と`Height`要素、しの値を示しています、**値**変数ウィンドウの列。 

デバッガーを自動的に作成、 **[Raw View]** のすべてのカスタム拡張ノード。 前掲のスクリーン ショットが表示されます、 **[Raw View]** Natvis 視覚化エフェクトの相違点、オブジェクトの既定の未加工ビューを表示する、ノードを展開します。 既定の展開は、基底クラスのサブツリーを作成し、子として、基底クラスのすべてのデータ メンバーを一覧表示します。  

> [!NOTE]
> Item 要素の式は、複合型を指している場合、**項目**ノード自体が展開されます。  

####  <a name="BKMK_ArrayItems_expansion"></a> Size  
`ArrayItems` ノードを使用すると、Visual Studio デバッガーによって型が配列として解釈され、その個々の要素が表示されるようになります。 `std::vector` の視覚化は良い使用例です。  

```xml
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

`std::vector` は、変数ウィンドウで展開されると、その個々の要素が表示されます。  

![ArrayItems の展開を使用して std::vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "ArrayItems の展開を使用して std::vector")  

`ArrayItems`ノードが必要です。  

- デバッガーが配列の長さを解釈するための `Size` 式 (整数に評価されることが必要)。  
- A`ValuePointer`最初の要素を指す式 (でない要素型のポインターでなければならない`void*`)。  

配列の既定の下限値は 0 です。 値を上書きするには、使用、`LowerBound`要素。 *.Natvis* Visual Studio に付属のファイルには、例が用意されています。  

>[!NOTE]
>使用することができます、`[]`演算子の例では、`vector[i]`を使用する 1 次元配列視覚エフェクトで`ArrayItems`場合でも、型自体 (たとえば`CATLArray`) が、この演算子を許可していません。  

多次元配列を指定することもできます。 その場合は、デバッガーでは、若干の詳細については子要素を正しく表示する必要があります。  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

- `Direction` 配列が行優先であるか列優先の順序であるかどうかを指定します。 
- `Rank` は配列のランクを指定します。 
- `Size` 要素は暗黙の `$i` パラメーターを受け取ります。このパラメーターは次元のインデックスに置き換えられて、その次元の配列の長さが特定されます。 前の例では、式で`_M_extent.M_base[0]`0 番目の次元の長さを指定する必要があります`_M_extent._M_base[1]`翌月 1 日、という具合です。  

ここでは、2 次元方法`Concurrency::array`デバッガー ウィンドウで次のオブジェクト。  

![ArrayItems の展開の 2 次元配列](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems の展開の 2 次元配列")  

####  <a name="BKMK_IndexListItems_expansion"></a> IndexListItems の展開  

使用することができます`ArrayItems`配列の要素は連続してメモリに配置する場合にのみ展開します。 デバッガーは、単にそのポインターをインクリメントして次の要素を取得します。 値のノードにインデックスを操作する必要がある場合を使用して、`IndexListItems`ノード。 ここでの視覚化、`IndexListItems`ノード。  

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  
```  

唯一の違い`ArrayItems`と`IndexListItems`は、 `ValueNode`、i に完全な式を受け取る<sup>th</sup> 、暗黙の型を持つ要素`$i`パラメーター。  

>[!NOTE]
>使用することができます、`[]`演算子の例では、`vector[i]`を使用する 1 次元配列視覚エフェクトで`IndexListItems`場合でも、型自体 (たとえば`CATLArray`) が、この演算子を許可していません。  

####  <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems の展開  

視覚化された型がリンク リストを表す場合、デバッガーは `LinkedListItems` ノードを使用してその子を表示できます。 次の視覚エフェクト、`CAtlList`使用している種類`LinkedListItems`:  

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  
```  

`Size` 要素はリストの長さを参照します。 `HeadPointer` は最初の要素を参照し、 `NextPointer` は次の要素を参照し、 `ValueNode` は項目の値を参照します。  

デバッガーで評価される、`NextPointer`と`ValueNode`のコンテキストの式で、`LinkedListItems`ノード要素、親リスト型ではありません。 前の例では、`CAtlList`が、`CNode`クラス (で見つかった`atlcoll.h`) のリンク リスト ノードであります。 `m_pNext` `m_element`のフィールドですが、`CNode`クラスのではありません、`CAtlList`クラス。  

`ValueNode` 空のままかを使用して、`this`を参照する、`LinkedListItems`ノード自体です。  

#### <a name="customlistitems-expansion"></a>CustomListItems 展開  
`CustomListItems` 展開を使用して、ハッシュ テーブルなどのデータ構造を走査する際にカスタム ロジックを記述することができます。 使用して、`CustomListItems`の型に合わせて評価、ただし非常に必要なすべての C++ の式を使用できるデータ構造を視覚化する`ArrayItems`、 `IndexListItems`、または`LinkedListItems`します。  

次のビジュアライザーは、`CAtlMap`の好例です、`CustomListItems`が適切です。  

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  

        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

使用することができます`Exec`内のコードを実行する、`CustomListItems`変数と展開に定義されているオブジェクトを使用して拡張します。 論理演算子、算術演算子、および代入演算子を使用する`Exec`します。 使用することはできません`Exec`関数を評価します。

`CustomListItems` 次の組み込み関数をサポートしています。

- `strlen`、`wcslen`、`strnlen`、`wcsnlen`、`strcmp`、`wcscmp`、`_stricmp`、`_strcmpi`、`_wcsicmp`、`strncmp`、`wcsncmp`、`_strnicmp`、`_wcsnicmp`、`memcmp`、`memicmp`、`wmemcmp`、`strchr`、`wcschr`、`memchr`、`wmemchr`、`strstr`、`wcsstr`、`__log2`、`__findNonNull`
- `GetLastError`、`TlsGetValue`、`DecodeHString`、`WindowsGetStringLen`、`WindowsGetStringRawBuffer`、`WindowsCompareStringOrdinal`、`RoInspectCapturedStackBackTrace`、`CoDecodeProxy`、`GetEnvBlockLength`、`DecodeWinRTRestrictedException`、`DynamicMemberLookup`、`DecodePointer`、`DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> TreeItems の展開  
 視覚化された型がツリーを表す場合、デバッガーはツリーをたどり、 `TreeItems` ノードを使用してその子を表示できます。 ここでは、視覚エフェクト、`std::map`を使用して型を`TreeItems`ノード。  

```xml
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  
```  

構文に似ています、`LinkedListItems`ノード。 `LeftPointer`、 `RightPointer`、および`ValueNode`、ツリー ノード クラスのコンテキストで評価されます。 `ValueNode` 空のままにできるかを使用して、`this`を参照する、`TreeItems`ノード自体です。  

####  <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem の展開  
 `ExpandedItem`場合、視覚化された型の子と同様に、基本クラスまたはデータ メンバーのプロパティを表示することによって要素が子の集約ビューを生成します。 デバッガーでは、指定された式を評価し、視覚化された型の子リストに、結果の子ノードを追加します。 

たとえば、スマート ポインター型`auto_ptr<vector<int>>`として表示されます。  

 ![自動&#95;ptr&#60;ベクター&#60;int&#62; &#62;既定の展開](../debugger/media/dbg_natvis_expand_expandeditem_default.png "既定の展開")  

 ベクターの値を表示するに渡される変数ウィンドウで、2 つのレベルにドリルダウンする必要がある、`_Myptr`メンバー。 `ExpandedItem` 要素を追加することで、階層から `_Myptr` 変数を排除し、vector の要素を直接表示できます。  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![自動&#95;ptr&#60;ベクター&#60;int&#62; &#62; ExpandedItem の展開](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem の展開")  

次の例では、派生クラスで基底クラスからプロパティを集計する方法を示します。 `CPanel` クラスが `CFrameworkElement`から派生しているとします。 繰り返しベースから取得したプロパティではなく`CFrameworkElement`クラス、`ExpandedItem`視覚エフェクトのノードの子リストにこれらのプロパティを追加します、`CPanel`クラス。 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

派生クラスの視覚化の対応付けを無効にする **nd** 書式指定子がここで必要になります。 それ以外の場合、式`*(CFrameworkElement*)this`なる、`CPanel`最も適切なものと既定のビジュアル化の照合ルールを入力するため、ここでも、適用する視覚化を考えています。 使用して、 **nd**書式指定子を基底クラスに視覚化があるない場合は、基底クラスの視覚化、または既定の展開を使用するデバッガーに指示します。  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Synthetic Item の展開  
 `ExpandedItem` 要素は階層を排除することでデータ ビューを平坦化しますが、`Synthetic` ノードはその反対のことを行います。 式の結果が意図的な子要素を作成することができます。 人為的な要素には、独自の子要素を持つことができます。 次の例では、 `Concurrency::array` 型の視覚化で `Synthetic` ノードを使用して、診断メッセージをユーザーに表示しています。  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  
```  

 ![合成要素の展開で:array](../debugger/media/dbg_natvis_expand_synthetic.png ":array で合成要素の拡張")  

###  <a name="BKMK_HResult"></a> HResult 要素 
 `HResult`要素に表示される情報をカスタマイズすることができます、 **HRESULT**のデバッガー ウィンドウにします。 `HRValue` 要素には、カスタマイズする **HRESULT** の 32 ビット値を格納する必要があります。 `HRDescription`要素には、デバッガー ウィンドウに表示する情報が含まれています。  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer 要素 
`UIVisualizer` 要素は、グラフィカル ビジュアライザー プラグインをデバッガーに登録するために使用します。 ダイアログ ボックスまたは他のインターフェイスを表示する変数またはオブジェクトの方法でのデータ型で一貫性のあるグラフィカル ビジュアライザーを作成します。 ビジュアライザー プラグインとして作成する必要があります、 [VSPackage](../extensibility/internals/vspackages.md)デバッガーが使用できるサービスを公開する必要があります。 *.Natvis*ファイルには、名前、公開されているサービス、および視覚化できる型の GUID など、プラグインの登録情報が含まれています。  

ここでは、UIVisualizer 要素の例を示しています。  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  

- A `ServiceId`  -  `Id`属性のペアを識別、`UIVisualizer`します。 `ServiceId`ビジュアライザーは、サービスの GUID は、パッケージが公開されます。 `Id` 1 つ以上のサービスを提供する場合、ビジュアライザーを区別する一意の識別子です。 前の例では、同じビジュアライザー サービスは、2 つのビジュアライザーを提供します。  
  
- `MenuName`属性は、デバッガーで虫眼鏡アイコンの横にあるドロップダウン リストに表示するビジュアライザーの名前を定義します。 次に例を示します。  

  ![UIVisualizer メニューのショートカット メニュー](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer メニューのショートカット メニュー")  

各種類で定義されている、 *.natvis*ファイルがすべて表示できる UI ビジュアライザーを明示的に一覧する必要があります。 デバッガーでは、登録済みのビジュアライザーで、型エントリ内のビジュアライザーの参照と一致します。 たとえば、次の種類のエントリ`std::vector`参照、`UIVisualizer`前の例。  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 例を参照することができます、`UIVisualizer`で、[イメージ ウォッチ](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017)拡張機能がメモリ内のビットマップを表示するために使用します。 

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer 要素  
 `CustomVisualizer` Visual Studio code での視覚エフェクトを制御するために作成 VSIX 拡張機能を指定する機能拡張ポイントです。 VSIX 拡張機能の記述の詳細については、次を参照してください。、 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。 

XML Natvis 定義のカスタム ビジュアライザーを作成する多くの作業ですが、Natvis はまたはをサポートしていないする内容の制約から自由します。 カスタム ビジュアライザーでは、デバッガーの拡張性 Api は、クエリを実行し、デバッグ対象プロセスを変更または Visual Studio の他の部分との通信の完全なセットにアクセスします。  

 使用することができます、 `Condition`、 `IncludeView`、および`ExcludeView`属性`CustomVisualizer`要素。
