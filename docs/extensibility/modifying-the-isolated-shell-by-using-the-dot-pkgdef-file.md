---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: "使用して分離シェルを変更します。Pkgdef ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a0e654e603abe0e4f1546e5b06c2b3644af2067e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>使用して分離シェルを変更します。Pkgdef ファイル
.Pkgdef ファイルは、分離シェル アプリケーションのカスタマイズに使用できる設定をサポートします。 これには、アプリケーションがコンピューターにインストールされているし、アプリケーションを起動すると、Visual Studio shell によって参照されているときに作成される値を指定します。 設定は、該当するレジストリ キーに基づき、ファイルで構成されます。  
  
> [!WARNING]
>  Visual Studio の起動時、VSPackage の .vsixmanifest ファイルで宣言されていない .pkgdef ファイルはスキャンされませんに注意してください。  
  
 .Pkgdef ファイルには、各によって識別される、キーか、セクションが含まれています。`[$RootKey$]`または`[$RootKey$\`*サブキー*`]`$RootKey$ は、アプリケーションのルート キー。  
  
 各セクションには、次の形式を持つ名前/値ペアが含まれています: `"` *ValueName*`"=`*値*です。  
  
 値は引用符で囲まれた文字列と、dword として表される 32 ビット整数のいずれか。 値では、次の制約があります。  
  
-   Dword 値はすべて 16 進形式、たとえば`dword:00000001`します。  
  
     ブール値は、1 が true の場合に表し、0 は false を表します。  
  
-   GUID のすべての文字列はレジストリ形式、たとえば、`"{00000000-0000-0000-0000-000000000000}"`です。  
  
-   すべてのローカライズ可能なリソース識別子があるフォーム"@*resourceID*"または"#*resourceID*"ここで、 *resourceID*は、アプリケーションの UI パッケージ内のリソース識別子たとえば、`"@102"`です。 アプリケーションの UI パッケージは AppLocalizationPackage 設定で参照されているパッケージです。  
  
 たとえば、オブジェクトに適用された  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 .Pkgdef ファイルにコメントを追加することができます。 単一行コメントは、最初の 2 つの文字と 2 つのスラッシュを持ちます。  
  
 代替文字列の一覧は、次を参照してください。[で置換文字列を使用します。Pkgdef およびです。Pkgundef ファイル](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)です。  
  
 次のセクションでは、分離モードで Visual Studio シェルの動作に影響する特定のレジストリ値について説明します。 このファイルで、アプリケーションの追加のレジストリ値を定義することもできます。  
  
> [!NOTE]
>  .Pkgdef ファイルで設定を指定しない場合、対応するエントリは実施されません、レジストリにします。  
  
## <a name="settings"></a>設定  
 次の表では、[$RootKey$] の下で定義されている値について説明します。  
  
|name|型|[値]|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True の場合は、アドインを読み込むことができます。それ以外の場合は false です。<br /><br /> 既定値は true です。|  
|AllowsDroppedFilesOnMainWindow|dword|メイン ウィンドウが削除されたファイルを受け入れることができる場合は true。それ以外の場合は false です。 使用して、メイン ウィンドウ上にドロップされたファイルが開かれた、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>メソッドです。 これを使用してドキュメントを開くと、**開く**コマンドを**ファイル**アプリケーションのメニュー。<br /><br /> 既定値は true です。|  
|入った|string|プログラム アイコンの完全パス。 このアイコンは、アプリケーション名の左側に、タイトル バーに表示されます。<br /><br /> 既定値は"$RootFolder$\\*solutionName*.ico"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|AppLocalizationPackage|string|アプリケーションの UI のサテライト アセンブリを含む VSPackage の GUID です。 この VSPackage では、.vsct ファイルのコンパイル済みバージョンが含まれ、その他のローカライズされた文字列を含めることができます。 機能セットとメニュー コマンドは、グループを有効になっているか、UI プロジェクトの .vsct ファイル内の設定を変更することで無効になっています。<br /><br /> 既定値は"{*vsUiPackageGuid*}"、どこで*vsUiPackageGuid*アプリケーション UI パッケージに割り当てられた GUID です。|  
|AppName|string|アプリケーションの名前。 名前は、アプリケーション ウィンドウのタイトル バーに表示されます。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
|CommandLineLogo|string|コンソール ウィンドウで、アプリケーションの実行時に、バナー テキスト。 この設定では、コマンド ライン ビルド操作をサポートするアプリケーションのみに影響します。<br /><br /> 既定値は"*companyName**solutionName*バージョン 1.0"ここで、 *companyName* Windows をインストールしたときに提供する会社との名前を指定*。solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|DefaultDebugEngine|string|既定値の GUID は、エンジンをアプリケーションの使用をデバッグします。<br /><br /> 注: 空の GUID (すべてゼロ) では、アプリケーションに既定のデバッグ エンジンが指定されていないことを示します。 これにより、デバッガーを使用するデバッグ エンジンを選択できます。<br /><br /> 既定値は、"{00000000-0000-0000-0000-000000000000}"です。|  
|DefaultHomePage|string|内部の Web ブラウザーのウィンドウの既定のホーム ページの URL。<br /><br /> 場合、**ホーム ページ**オプションは、アプリケーションでは、使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。[環境では、Web ブラウザーのオプション ダイアログ ボックス](../ide/reference/web-browser-environment-options-dialog-box.md)です。<br /><br /> 既定値は、Windows のインストール時に提供された会社の URL です。|  
|DefaultProjectsLocation|string|既定のプロジェクト フォルダーの完全パス。 たとえば、オブジェクトに適用された<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> 場合、 **Visual Studio プロジェクトの場所**オプションは、アプリケーションでは、使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。 [NIB: [全般]、[プロジェクトおよびソリューションのオプション] ダイアログ ボックス](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)です。<br /><br /> 既定値は"$MyDocuments$\\*solutionName*"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|DefaultSearchPage|string|内部の Web ブラウザーのウィンドウの既定の検索ページ URL。<br /><br /> 場合、**検索ページ**オプションは、アプリケーションでは、使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。[環境では、Web ブラウザーのオプション ダイアログ ボックス](../ide/reference/web-browser-environment-options-dialog-box.md)です。<br /><br /> 既定値は、"http://search.live.com"です。|  
|DefaultUserFilesFolderRoot|string|現在のユーザーに対して、ユーザー フォルダーの名前はのマイ ドキュメント フォルダーです。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
|DisableOutputWindow|dword|分離シェルは、無効になっているは、出力ウィンドウを扱う必要があるかどうかを示します。<br /><br /> この値が設定されている場合は true、Visual Studio 出力は表示されず、ソリューション ビルド マネージャーで、**出力**ウィンドウと非表示を切り替えます、**出力ウィンドウを表示ビルド開始時に** チェック ボックス、 **プロジェクトおよびソリューション**カテゴリで、**オプション** ダイアログ ボックス。<br /><br /> 既定値は false です。|  
|HideMiscellaneousFilesByDefault|dword|非表示にする場合は true、**その他のファイル**で既定のフォルダー**ソリューション エクスプ ローラー**。 それ以外の場合は false。<br /><br /> 場合、**ソリューション エクスプ ローラーで表示するその他のファイル**オプションは、アプリケーションでは、使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。[オプション ダイアログ ボックスのドキュメントでは、環境、](../ide/reference/documents-environment-options-dialog-box.md)です。<br /><br /> 既定値は false です。|  
|HideSolutionConcept|dword|スタンドアロンのプロジェクトのすべてのプロジェクトを作成し、既定では、ソリューションとプロジェクトのスタンドアロン ソリューションに関連するコマンドを非表示にする場合は trueそれ以外の場合は false です。<br /><br /> 場合、**常にソリューションを表示する**オプションは、アプリケーションでは、使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。 [NIB: [全般]、[プロジェクトおよびソリューションのオプション] ダイアログ ボックス](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)です。<br /><br /> 既定値は false です。|  
|NewProjDlgInstalledTemplatesHdr|string|Visual Studio のインストール済みテンプレート ヘッダーの名前、**テンプレート**一覧に、**新しいプロジェクト** ダイアログ ボックス。 これは、文字列またはアプリケーションの UI パッケージから読み込まれているローカライズ可能なリソース識別子のどちらかです。<br /><br /> 既定値は"*solutionName*にインストールされたテンプレート"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|NewProjDlgSlnTreeNodeTitle|string|名前、 **Visual Studio ソリューション**内のノード、**プロジェクトの種類**ツリーで、**新しいプロジェクト** ダイアログ ボックス。 これは、文字列またはアプリケーションの UI パッケージから読み込まれているローカライズ可能なリソース識別子のどちらかです。<br /><br /> 既定値は"*solutionName*にインストールされたテンプレート"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|SolutionFileCreatorIdentifier|string|アプリケーションによって生成されるソリューション ファイルの 2 番目の行として表示されるアプリケーション識別子。 この行は、ファイルを作成したアプリケーションを示します。 規則では、この値には、アプリケーションおよびアプリケーションのバージョン番号の両方に名前が含まれます。 たとえば、オブジェクトに適用された<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Visual Studio ソリューション ファイルを開くときの既定のプログラムである、VSLauncher.exe プログラムは、ソリューション ファイルを開くときに Visual Studio のバージョンを確認するのにこの 2 つ目の行を使用します。 アプリケーションには、その関連するソリューション ファイルを処理する、独自のランチャーが必要です。 ランチャーでしたも行を使用して 2 番目のソリューション ファイルにソリューションを開くアプリケーションのバージョンを決定します。<br /><br /> 注意: Visual Studio VSLauncher.exe プログラムは、分離シェル アプリケーションによって作成された .sln ファイルを処理しません。<br /><br /> 既定値は"*solutionName*ソリューション ファイルの形式バージョン 10.00" ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|SolutionFileExt|string|アプリケーションのソリューション ファイル名拡張子。 一意のファイル名拡張子 (not.sln) を選択することをお勧めします。<br /><br /> 既定値は"*solutionName*_sln"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|SplashScreenBitmap|string|アプリケーションのスプラッシュ画面のビットマップ ファイルの完全パス。<br /><br /> 既定値は、"$RootFolder$\Splash.bmp"です。|  
|ThisVersionDTECLSID|string|アプリケーションのオートメーション オブジェクトのクラス id (CLSID)。<br /><br /> アプリケーションのオートメーション オブジェクトは、Visual Studio シェル オートメーション モデルと実装でアプリケーションの最上位レベル オブジェクト、<xref:EnvDTE._DTE?displayProperty=fullName>インターフェイスです。<br /><br /> Hkey_classes_root \clsid レジストリ キーの下でアプリケーションのオートメーション オブジェクトが正しく登録されているかどうかは、使用することができます、 [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)直接、アプリケーションのインスタンスを作成する関数。<br /><br /> Visual Studio シェルでは、この CLSID を使用して、ACTIVEOBJECT_WEAK フラグを使用して実行中のオブジェクト テーブル (ROT) でアプリケーションのオートメーション オブジェクトを登録します。 使用できます、 [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)アプリケーションの実行中のインスタンスへのポインターを取得します。 さらに、アプリケーション オートメーション オブジェクトの ProgID を定義する場合、Visual Studio シェルはまた、アプリケーションの各インスタンスに登録 ROT 形式の項目のモニカーを使用して*progID*:*processID*ここで、 *progID*は、アプリケーションのオートメーション オブジェクトの ProgID および*processID*アプリケーションのインスタンスのプロセス識別子を指定します。 たとえば、次のように、モニカーを作成する場合。<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> ここで`instanceString`は、 *progID*:*processID*文字列。 使用して`instanceMoniker`インスタンスの取得に回転 GetObject 関数を使用します。<br /><br /> ThisVersionDTECLSID 設定を省略すると、コンポーネント オブジェクト モデル (COM) ではないアプリケーションに公開されます。 ここでは、呼び出すことによって、アプリケーションのインスタンスを作成できません、 [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)関数し、ROT に登録することはできません。<br /><br /> VSPackage の各バージョンには、異なる CLSID 必要があります。<br /><br /> 既定値は、Visual Studio がアプリケーションのオートメーション オブジェクトに対して生成される GUID です。|  
|ThisVersionSolutionCLSID|string|アプリケーションのソリューション オブジェクトの CLSID。<br /><br /> ソリューションのオートメーション オブジェクトには、アプリケーションと実装のインスタンスで現在開いているソリューションについての情報が含まれています、<xref:EnvDTE._Solution?displayProperty=fullName>インターフェイスです。<br /><br /> Hkey_classes_root \clsid レジストリ キーの下で、ソリューションのオートメーション オブジェクトが正しく登録されているかどうかは、使用することができます、 [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)アプリケーションのソリューション オブジェクトを直接作成する関数。<br /><br /> Visual Studio シェルでは、この CLSID を使用して、rot ACTIVEOBJECT_WEAK フラグを使用して、ソリューションのオートメーション オブジェクトを登録します。<br /><br /> この設定を省略すると、し、ソリューションのクラスは、コンポーネント オブジェクト モデル (COM) に登録されていません、solution オブジェクトを呼び出すことによって作成されることはできません、 [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)関数に登録することはできませんROT です。<br /><br /> 既定値は、Visual Studio がアプリケーションのソリューション オブジェクトに対して生成される GUID です。|  
|UserFilesSubFolderName|string|ユーザー ファイルとサブフォルダーに、アプリケーションを作成するユーザーのマイ ドキュメント フォルダーの下のサブフォルダーの名前。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
|UserOptsFileExt|string|アプリケーションのソリューション ユーザー オプション ファイルの拡張子。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
  
## <a name="binding-path-settings"></a>バインド パスの設定  
 [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] キーには、シェルがアセンブリをチェックするディレクトリの一覧が含まれています。 これらのディレクトリは、シェル アプリケーションのプライベート アセンブリがプローブされるディレクトリの一覧に追加されます。  
  
 既定では、バインド パス エントリが追加されなく .pkgdef ファイルにします。 ただし、Visual Studio インストール ディレクトリの下にサブディレクトリは、レジストリ内のアプリケーション バインド パス リストに自動的に追加されます。  
  
-   Common7 \ide\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 ディレクトリをバインド パスを追加するには、フォームのエントリを追加"*ディレクトリ名*「=」"、どこで*ディレクトリ名*絶対パスです。 たとえば、オブジェクトに適用された  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>プロファイルの設定  
 次の表では、[$RootKey$ \Profile] の下の関連する各パッケージに対して定義されている値について説明します。  
  
|name|型|[値]|  
|----------|----------|-----------|  
|AutoSaveFile|string|アプリケーションが自動保存ファイルを格納するディレクトリ。<br /><br /> 既定値は、"$RootFolder$\Profiles\CurrentSettings.vssettings"です。|  
  
## <a name="package-satellite-dll-settings"></a>パッケージ サテライト DLL の設定  
 次の表で定義されている値 [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] サテライト、関連付けられているパッケージごとの DLL の場所*vsPackageGuid* 、関連付けられたパッケージの GUID です。  
  
|name|型|[値]|  
|----------|----------|-----------|  
|DllName|string|DLL のファイル名。<br /><br /> 既定値は"*solutionName*ui.dll"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|パス|string|サテライト DLL を格納するディレクトリ。<br /><br /> 既定値は、「$PackageFolder$」です。|  
  
## <a name="package-menu-item-settings"></a>パッケージのメニュー項目の設定  
 [$RootKey$ \Menus] レジストリ キーでは、アプリケーションの UI リソース ファイルを定義します。  
  
 メニュー項目の値、フォームがある"{*vsUiPackageGuid*}「=」 *resourceId*、 *versionNumber*"ここで、 *vsUiPackageGuid*の GUID ですアプリケーションの UI パッケージ*resourceId* UI 要素を含む CTMENU のリソースのリソース識別子と*versionNumber* CTMENU の仮想バージョン番号は、リソースです。 詳細については、次を参照してください。[相互運用機能アセンブリ コマンド ハンドラーの登録](../extensibility/internals/registering-interop-assembly-command-handlers.md)です。  
  
 既定では、アプリケーションの UI パッケージの .pkgdef ファイルでメニュー項目が作成されます。  
  
 メニュー項目を提供して、アプリケーションの一部として配布される各パッケージのパッケージのメニュー項目を追加します。  
  
## <a name="see-also"></a>参照  
 [分離シェルのカスタマイズ](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgundef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)