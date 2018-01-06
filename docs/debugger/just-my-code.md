---
title: "マイ コードのみにユーザー コードのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 476ff209f96aa5729d20bd9a5a5d12c9e5a5c39a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Visual Studio で マイ コードのみを使用してユーザー コードのみをデバッグするかどうかを指定します。
自動的にステップ オーバーするシステム、フレームワーク、およびその他の非ユーザー呼び出しの呼び出し履歴 ウィンドウでそれらの呼び出しを折りたたむ Visual Studio を構成することができます。 有効またはこの動作を無効にする機能が呼び出されます*マイ コードのみ*です。 このトピックでは、c#、Visual Basic、C++、および JavaScript のプロジェクトでマイ コードのみを使用する方法について説明します。

ほとんどのプログラミング言語に対しては、マイ コードのみは既定で有効にします。
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a>有効にするにまたは、マイ コードのみを無効にします。  
 有効にするにまたはマイ コードのみを無効にするには、選択、**ツール > オプション**Visual Studio のメニュー。 **デバッグ** > **全般** ノードを選択またはクリア**マイ コードのみを有効にする**です。
  
 ![オプション] ダイアログ ボックスで [マイ コードのみを有効にする](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  **マイ コードのみを有効にする**はすべての言語のすべての Visual Studio プロジェクトに適用されるグローバル設定です。  
  
###  <a name="BKMK_Override_call_stack_filtering"></a>呼び出し履歴ビューで非ユーザー コードを表示します。  
 など、呼び出し履歴を表示するビューで、**呼び出し履歴**と**タスク**windows、マイ コードのみには、ラベルの注釈付きフレームに非ユーザー コードが折りたたまれます`[External Code]`です。 折りたたまれたフレームを表示するには選択**外部コードの表示**呼び出し履歴のコンテキスト メニューを表示します。

 ![[呼び出し履歴] ウィンドウで外部コードの表示](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  **外部コードの表示**設定は現在のユーザーのプロファイラーに保存します。 この設定は、ユーザーによって開かれたすべての言語のすべてのプロジェクトに適用されます。
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET framework マイ コードのみ  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a>ユーザー コードと非ユーザー コード  
 非ユーザー コードからユーザー コードを区別するためには、マイ コードのみは、シンボル (.pdb) ファイルおよびプログラムの最適化で検索します。 デバッガーは、バイナリが最適化されているか、.pdb ファイルが入手できないとき、コードがユーザー コードであると見なします。
  
 以下の 3 つの属性も、デバッガーが何をマイ コードであると見なすかに影響を与えます。  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> は、適用先のコードがマイ コードでないことをデバッガーに通知します。  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> は、"マイ コードのみ" がオフになっていても、コードをデバッガーから見えないようにするための属性です。  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> は、それが適用されているコードを (ステップ インではなく) ステップ スルーするよう、デバッガーに伝える属性です。  
  
 他のすべてのコードはユーザー コードであると見なされます。  
  
###  <a name="BKMK_NET_Stepping_behavior"></a>ステップ実行の動作  
 ときに、**ステップ イン**(キーボード ショートカット: F11) 非ユーザー コードは、次のユーザー ステートメントに、コードをデバッガーの手順。 ときにする**ステップ アウト**(キーボード: shift + f11)、デバッガーを実行するユーザー コードの次の行にします。 ユーザー コードが出現しない場合、アプリまで実行を続けます終了すると、ブレークポイントにヒットすると、または例外が発生します。  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a>ブレークポイントの動作  
 マイ コードのみが有効になっていることができます**すべて中断**(キーボード: Ctrl + Alt + Break) の場所で実行を停止し、表示するユーザー コードが存在しません。 停止すると、[No Source] (ソースがありません) ウィンドウが表示されます。 次に [ステップ] をクリックすると、デバッガーによってユーザー コードの次の行に進められます。  
  
###  <a name="BKMK_NET_Exception_behavior"></a>例外の動作  
 ハンドルされない例外が非ユーザー コードで発生した場合、デバッガーはユーザー コードの例外が発生した行で停止します。  
  
 初回例外がその例外に対して有効になっている場合、ユーザー コード行は緑で強調表示されます。 呼び出し履歴には、ラベルの注釈付きフレームが表示されます。 **[外部コード]**です。  
  
##  <a name="BKMK_C___Just_My_Code"></a>C++ マイ コードのみ  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a>ユーザー コードと非ユーザー コード  
 ステップ実行の動作が呼び出し履歴の動作に依存しないため、C++ での "マイ コードのみ" は .NET Framework での "マイ コードのみ" および JavaScript での "マイ コードのみ" とは異なります。  
  
 **呼び出し履歴**  
  
 既定では、デバッガーは呼び出し履歴ウィンドウで以下の関数が非ユーザー コードであると見なします。  
  
-   シンボル ファイル内に除去されたソース情報がある関数。  
  
-   シンボル ファイルがスタック フレームに対応するソース ファイルがないことを示す関数。  
  
-   `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` フォルダーの `*.natjmc` ファイルに指定された関数。  
  
 **ステップ実行**  
  
 既定では、`%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` フォルダーの `*.natstepfilter` ファイルに指定された関数だけが非ユーザー コードと見なされます。  
  
 `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` に独自の `.natstepfilter` および `.natjmc` を作成して、ステップ実行と呼び出し履歴ウィンドウの動作をカスタマイズすることができます。  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a>ステップ実行の動作  
 ときにする**ステップ イン**(キーボード ショートカット: F11) ユーザー コードから非ユーザー コードで、デバッガー、コードをステップ オーバー ユーザー コードの次の行にします。 ときにする**ステップ アウト**(キーボード: shift + f11)、デバッガーを実行するユーザー コードの次の行にします。 ユーザー コードが出現しない場合、アプリまで実行を続けます終了すると、ブレークポイントにヒットすると、または例外が発生します。  
  
 デバッガーが非ユーザー コードで実行を中断した場合 (たとえば、[すべて中断] が非ユーザー コードで停止した場合)、その非ユーザー コードでステップ実行が続けられます。  
  
###  <a name="BKMK_CPP_Exception_behavior"></a>例外の動作  
 デバッガーでは、例外が発生すると、ユーザーまたは非ユーザー コードであるかどうかにかかわらず例外で停止します。 **ユーザーよって処理されない**オプション、**例外** ダイアログ ボックスは無視されます。  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a>ステップ実行動作をカスタマイズします。  
 `*.natstepfilter` ファイルに関数を非ユーザー コードとして記述することで、それらの関数をステップ オーバーすることを指定できます。  
  
-   Visual Studio コンピューターのすべてのユーザーの非ユーザー コードを指定するに .natstepfilter ファイルを追加、`%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`フォルダーです。  
  
-   個々 のユーザーの非ユーザー コードを指定するに .natstepfilter ファイルを追加、`%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`フォルダーです。  
  
 .natstepfilter ファイルは、次の構文を使用する xml ファイルです。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|要素|説明|  
|-------------|-----------------|  
|関数|必須。 1 つ以上の関数を非ユーザー関数として指定します。|  
|`Name`|必須。 一致を照合する完全な関数名を指定する ECMA-262 書式の正規表現。 例:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> は、`MyNS::MyClass` のすべてのメソッドが非ユーザー コードと見なされることをデバッガーに知らせます。 一致照合では、大文字と小文字が区別されます。|  
|`Module`|任意。 関数を含むモジュールへの完全パスを指定する ECMA-262 書式の正規表現。 一致では、大文字と小文字を区別しません。|  
|`Action`|必須。 大文字と小文字が区別される以下のいずれかの値です。<br /><br /> -   `NoStepInto`-一致した関数をステップ オーバーするデバッガーに指示します。<br />-   `StepInto`-その他をオーバーライドする一致した関数にステップ インをデバッガーに指示`NoStepInto`一致した関数です。|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a>呼び出し履歴の動作をカスタマイズします。  
 モジュール、ソース ファイル、および関数を `*.natjmc` ファイルで指定することで、呼び出し履歴でそれらを非ユーザー コードとして扱うことを指定できます。  
  
-   Visual Studio コンピューターのすべてのユーザーの非ユーザー コードを指定するに .natjmc ファイルを追加、`%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`フォルダーです。  
  
-   個々 のユーザーの非ユーザー コードを指定するに .natjmc ファイルを追加、`%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`フォルダーです。  
  
 .natjmc ファイルは、次の構文を使用する xml ファイルです。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Module 要素の属性**  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 モジュールの完全パス。 Windows のワイルドカード文字を使用する`?`(0 個または 1 つの文字) と`*`(0 個以上の文字)。 たとえば、オブジェクトに適用された<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> は、ドライブの `\3rdParty\UtilLibs` 内のすべてのモジュールを外部コードとして扱うことをデバッガーに指示します。|  
|`Company`|任意。 実行可能ファイルに埋め込まれているモジュールを発行する会社の名前。 この属性を使用して、モジュールのあいまいさを解消することができます。|  
  
 **File 要素の属性**  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 外部コードとして扱うソース ファイルの完全パス。 パスを指定するときに Windows のワイルドカード文字、`?` および `*` を使用できます。|  
  
 **Function 要素の属性**  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 外部コードとして扱う関数の完全修飾名。|  
|`Module`|任意。 関数を含むモジュールの名前または完全パス。 この属性を使用して、同じ名前の関数のあいまいさを解消することができます。|  
|`ExceptionImplementation`|`true` に設定すると、この関数ではなく、例外をスローした関数が呼び出し履歴に表示されます。|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a>JavaScript マイ コードのみ  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a>ユーザー コードと非ユーザー コード  
 **コードの分類**  
  
 JavaScript の "マイ コードのみ" は、以下のいずれかの方法でコードを分類することでステップ実行と呼び出し履歴表示を制御します。  
  
|||  
|-|-|  
|**MyCode**|ユーザーが所有および制御するユーザー コード。|  
|**LibraryCode**|ユーザーが通常使用し、アプリケーションが正しく機能するために必要なライブラリからの非ユーザー コード (WinJS や jQuery など)。|  
|**UnrelatedCode**|非ユーザー コードで、アプリケーションが実行することをお持ちでないことと、アプリケーションが正しく機能するために依存しない直接です。 (たとえば、これが考えられます、広告 SDK 広告を表示する。)UWP プロジェクトでは、UnrelatedCode も HTTP または HTTPS URI からアプリケーションに読み込まれているすべてのコードにもと見なされます。|  
  
 JavaScript デバッガーは、以下のコードの種類を自動的に分類します。  
  
-   ホスト提供に文字列を渡すことによって実行されるスクリプト`eval`関数として分類**MyCode**です。  
  
-   文字列を渡すことによって実行されるスクリプト、`Function`コンス トラクターとして分類**LibraryCode**です。  
  
-   WinJS や Azure SDK などのフレームワーク参照に含まれているスクリプトとして分類**LibraryCode**です。  
  
-   文字列を渡すことによって実行されるスクリプト、 `setTimeout`、 `setImmediate`、または`setInterval`関数として分類**UnrelatedCode**です。  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` は、すべての Visual Studio JavaScript プロジェクトの他のユーザー コードと非ユーザー コードを指定します。  
  
 プロジェクトのルート フォルダーに `mycode.json` という名前の .json ファイルを追加することで、既定の分類を変更し、特定のファイルや URL を分類することができます。  
  
 その他のすべてのコードとして分類**MyCode**です。  
  
###  <a name="BKMK_JS_Stepping_behavior"></a>ステップ実行の動作  
  
-   関数がユーザーではない場合 (**MyCode**) コード、**ステップ イン**(キーボード ショートカット: F11) と同様に動作**ステップ オーバー** (キーボード: F10)。  
  
-   非ユーザーのステップが始まる場合 (**LibraryCode**または**UnrelatedCode**) コードで、マイ コードのみが有効でない場合、動作は一時的にステップ インし、します。 ユーザー コード、マイ コードのみにステップするときのステップを再度有効にします。  
  
-   ユーザー コード内のステップが現在の実行コンテキストから出ることになると (イベント ハンドラーの最後の行でのステップの実行など)、ユーザー コードの次に実行される行でデバッガーが停止します。 たとえば、コールバックの実行で**LibraryCode**コード、デバッガーはユーザー コードの次の行を実行するまで続きます。
  
-   **ステップ アウト**(キーボード: shift + f11) のユーザー コードの次の行で停止します。 ユーザー コードが出現しない場合、アプリまで実行を続けます終了すると、ブレークポイントにヒットすると、または例外が発生します。  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a>ブレークポイントの動作  
  
-   そのコードの分類に関係なく、コードに設定されたブレークポイントをヒット常には  
  
-   `debugger` キーワードが、  
  
    -   **LibraryCode**コード、デバッガーは常に中断します。  
  
    -   **UnrelatedCode**コード、デバッガーは停止しません。  
  
###  <a name="BKMK_JS_Exception_behavior"></a>例外の動作  
 ハンドルされていない例外が、  
  
-   **MyCode**または**LibraryCode**コード、デバッガーは常に中断します。  
  
-   **UnrelatedCode**コード、および**MyCode**または**LibraryCode**コードは、呼び出し履歴をデバッガーは中断します。  
  
 [例外] ダイアログ ボックスで、例外の最初の例外が有効になっているし、では、例外がスローされた場合**LibraryCode**または**UnrelatedCode**コード。  
  
-   例外が処理される場合、デバッガーは中断されません。  
  
-   例外が処理されない場合、デバッガーは中断します。  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a>マイ コードのみをカスタマイズします。  
 単一の Visual Studio プロジェクトのユーザー コードと非ユーザー コードを分類するには、プロジェクトのルート フォルダーに `mycode.json` という名前の .json ファイルを追加します。  
  
 分類は次の順序で行われます。  
  
1.  既定の分類  
  
2.  `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` ファイルでの分類  
  
3.  現在のプロジェクトの `mycode. json` ファイルでの分類。  
  
 分類の各手順で、前の手順はオーバーライドされます。 .Json ファイルは、すべてのキー値のペアを一覧表示する必要はありません、 **MyCode**、**ライブラリ**、および**Unrelated**値は空の配列を指定できます。  
  
 マイ コードの .json ファイルでは、次の構文を使用します。  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec",  
        . .  
        "UrlOrFileSpec"  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ]  
}  
  
```  
  
 **Eval、Function、および ScriptBlock**  
  
 **Eval**、**関数**、および**ScriptBlock**キー値のペアがどのように動的に決定生成されたコードを分類します。  
  
|||  
|-|-|  
|**評価版**|ホスト提供の `eval` 関数に文字列を渡すことで実行されるスクリプト。 既定では、Eval スクリプトとして分類**MyCode**です。|  
|**Function**|`Function` コンストラクターに文字列を渡すことで実行されるスクリプト。 既定では、Function スクリプトとして分類**LibraryCode**です。|  
|**ScriptBlock**|`setTimeout`、`setImmediate`、または `setInterval` 関数に文字列を渡すことで実行されるスクリプト。 既定では、ScriptBlock スクリプトとして分類**UnrelatedCode**です。|  
  
 以下のいずれかのキーワードに値を変更できます。  
  
-   `MyCode`スクリプトとして分類**MyCode**です。  
  
-   `Library`スクリプトとして分類**LibraryCode**です。  
  
-   `Unrelated`スクリプトとして分類**UnrelatedCode**です。  
  
 **MyCode、Libraries、および Unrelated**  
  
 **MyCode**、**ライブラリ**、および**Unrelated**キー値のペアは、url または分類に追加するファイルを指定します。  
  
|||  
|-|-|  
|**MyCode**|配列の url またはファイルとして分類される**MyCode**です。|  
|**ライブラリ**|配列の url またはファイルとして分類される**LibraryCode**です。|  
|**関連付けられていません。**|配列の url またはファイルとして分類される**UnrelatedCode**です。|  
  
 URL またはファイルの文字列には、0 個以上の文字に一致する `*` 文字を 1 つ以上含めることができます。 `*` は、正規表現 `.*` と同等です。