---
title: "使用して、分離シェルを変更します。Pkgdef ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 41e91983aaf236682b4ce723143f4053b5189547
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>使用して、分離シェルを変更します。Pkgdef ファイル
.Pkgdef ファイルには、分離シェル アプリケーションをカスタマイズするのに使用できる設定がサポートしています。 アプリケーションがコンピューターにインストールされているし、アプリケーションを起動すると、Visual Studio shell によって参照されている場合に作成される値を指定します。 設定は、該当するレジストリ キーに基づいたファイルで構成されます。  
  
> [!WARNING]
>  Visual Studio の起動時、VSPackage の .vsixmanifest ファイルで宣言されていない .pkgdef ファイルがスキャンされませんに注意してください。  
  
 .Pkgdef ファイルには、各によって識別される、キーか、セクションが含まれています。`[$RootKey$]`または`[$RootKey$\`*サブキー*`]`$RootKey。 $embedded$ には、アプリケーションのルート キーであるという点です。  
  
 各セクションには、次の形式を持つ名前/値ペアが含まれています: `"` *ValueName*`"=`*値*です。  
  
 値は引用符で囲まれた文字列と、dword として表される 32 ビット整数のいずれか。 値には、次の制約があります。  
  
-   16 進形式ですべての dword 値は`dword:00000001`です。  
  
     ブール値の 1 が true の場合に表し、0 は false を表します。  
  
-   たとえばはレジストリ形式ですべての GUID 文字列`"{00000000-0000-0000-0000-000000000000}"`します。  
  
-   ローカライズ可能なリソースのすべての識別子、フォームがある"@*resourceID*"または"#*resourceID*"ここで、 *resourceID*など、アプリケーションの UI パッケージ内のリソース識別子が`"@102"`です。 アプリケーションの UI パッケージは AppLocalizationPackage 設定で参照されているパッケージです。  
  
 次に例を示します。  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 .Pkgdef ファイルにコメントを追加することができます。 単一行のコメントは、最初の&2; つの文字と&2; つのスラッシュを持ちます。  
  
 代替文字列の一覧は、次を参照してください。[置換文字列を使用します。Pkgdef とします。Pkgundef ファイル](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)します。  
  
 次のセクションでは、分離モードで Visual Studio シェルの動作に影響を与える特定のレジストリ値について説明します。 このファイルで、アプリケーションの追加のレジストリ値を定義することもできます。  
  
> [!NOTE]
>  .Pkgdef ファイルで設定を指定しない場合、対応するエントリは行われず、レジストリです。  
  
## <a name="settings"></a>設定  
 次の表では、[$RootKey$] の下で定義されている値について説明します。  
  
|名前|型|値|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True の場合、アドインを読み込むことができます。それ以外の場合は false。<br /><br /> 既定値は true です。|  
|AllowsDroppedFilesOnMainWindow|dword|メイン ウィンドウが削除されたファイルを受け入れることができる場合は true。それ以外の場合は false。 使用して開かれているメイン ウィンドウで削除されたファイル、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>。 これを使用してドキュメントを開くには、**開く**コマンドを**ファイル**アプリケーションのメニュー。<br /><br /> 既定値は true です。|  
|入った|string|プログラム アイコンの完全パス。 このアイコンは、アプリケーション名の左側に、タイトル バーに表示されます。<br /><br /> 既定値は"$RootFolder$\\*solutionName*.ico"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|AppLocalizationPackage|string|アプリケーションの UI のサテライト アセンブリを含む VSPackage の GUID です。 この VSPackage .vsct ファイルのコンパイル済みバージョンが含まれていて、その他のローカライズされた文字列を含めることができます。 特徴のセットとメニュー コマンドは、グループを有効になっているか、UI プロジェクト .vsct ファイルの設定を変更することで無効になっています。<br /><br /> 既定値は"{*vsUiPackageGuid*}"ここで、 *vsUiPackageGuid*アプリケーション UI パッケージに割り当てられた guid を指定します。|  
|アプリ名|string|アプリケーションの名前。 アプリケーション ウィンドウのタイトル バーに名前が表示されます。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
|CommandLineLogo|string|コンソール ウィンドウで、アプリケーションが実行される場合は、バナー テキスト。 この設定では、コマンド ライン ビルド処理をサポートするアプリケーションのみに影響します。<br /><br /> 既定値は"*companyName**solutionName*バージョン 1.0。"ここで、 *companyName* Windows をインストールしたときに提供された会社の名前を指定し、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|DefaultDebugEngine|string|既定の GUID は、エンジンをアプリケーションの使用をデバッグします。<br /><br /> 注: 空の GUID (すべてゼロ) では、アプリケーションにデバッグ エンジンを既定値が指定されていないことを示します。 これにより、デバッガーを使用するデバッグ エンジンを選択できます。<br /><br /> 既定値は、"{00000000-0000-0000-0000-000000000000}"です。|  
|DefaultHomePage|string|内部の Web ブラウザーのウィンドウの既定のホーム ページの URL。<br /><br /> 場合、**ホーム ページ**オプションは、アプリケーションで使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。[環境では、Web ブラウザーのオプション ダイアログ ボックス](../ide/reference/web-browser-environment-options-dialog-box.md)します。<br /><br /> 既定値は、Windows をインストールしたときに提供された会社の URL です。|  
|DefaultProjectsLocation|string|既定のプロジェクト フォルダーの完全パス。 次に例を示します。<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> 場合、 **Visual Studio プロジェクトの場所**オプションは、アプリケーションで使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。 [NIB: プロジェクトおよびソリューション]、[オプション] ダイアログ ボックスの [全般](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)します。<br /><br /> 既定値は"$MyDocuments$\\*solutionName*"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|DefaultSearchPage|string|内部の Web ブラウザーのウィンドウの既定の検索ページ URL です。<br /><br /> 場合、**検索ページ**オプションは、アプリケーションで使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。[環境では、Web ブラウザーのオプション ダイアログ ボックス](../ide/reference/web-browser-environment-options-dialog-box.md)します。<br /><br /> 既定値は、"http://search.live.com"です。|  
|DefaultUserFilesFolderRoot|string|現在のユーザーを基準とした、ユーザー フォルダーの名前はのマイ ドキュメント フォルダーです。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
|DisableOutputWindow|dword|分離シェルは、無効になっている [出力] ウィンドウを扱う必要があるかどうかを示します。<br /><br /> この値が設定されている場合は true、Visual Studio 出力は表示されず、ソリューション ビルド マネージャーで、**出力**ウィンドウと非表示に、**出力ウィンドウを表示ビルド開始時に** チェック ボックス、**プロジェクトおよびソリューション**カテゴリで、**オプション** ダイアログ ボックス。<br /><br /> 既定値は false です。|  
|HideMiscellaneousFilesByDefault|dword|非表示にする場合は true、**その他のファイル**フォルダーの既定**ソリューション エクスプ ローラー**。 それ以外の場合は false。<br /><br /> 場合、**ソリューション エクスプ ローラーを表示するその他のファイル**オプションは、アプリケーションで使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。[オプション] ダイアログ ボックスの [ドキュメント](../ide/reference/documents-environment-options-dialog-box.md)します。<br /><br /> 既定値は false です。|  
|HideSolutionConcept|dword|スタンドアロンのプロジェクトのすべてのプロジェクトを作成し、既定では、ソリューションとスタンドアロンのプロジェクトをソリューションに関連するコマンドを非表示にする場合は trueそれ以外の場合は false。<br /><br /> 場合、**常にソリューションを表示する**オプションは、アプリケーションで使用し、この設定は、オプションの既定の状態も影響します。 詳細については、次を参照してください。 [NIB: プロジェクトおよびソリューション]、[オプション] ダイアログ ボックスの [全般](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)します。<br /><br /> 既定値は false です。|  
|NewProjDlgInstalledTemplatesHdr|string|Visual Studio のインストール済みテンプレート ヘッダーの名前、**テンプレート**リストに、**新しいプロジェクト** ダイアログ ボックス。 これは、文字列またはアプリケーションの UI パッケージから読み込まれているローカライズ可能なリソース id です。<br /><br /> 既定値は"*solutionName*にインストールされたテンプレート"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|NewProjDlgSlnTreeNodeTitle|string|名前、 **Visual Studio ソリューション**内のノード、**プロジェクトの種類**ツリー、**新しいプロジェクト** ダイアログ ボックス。 これは、文字列またはアプリケーションの UI パッケージから読み込まれているローカライズ可能なリソース id です。<br /><br /> 既定値は"*solutionName*にインストールされたテンプレート"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|SolutionFileCreatorIdentifier|string|アプリケーションによって生成されたソリューション ファイルの&2; 行目に表示されるアプリケーションの識別子です。 この行は、ファイルを作成したアプリケーションを示します。 規則では、この値には、アプリケーションとアプリケーションのバージョン番号の名両方にはが含まれます。 次に例を示します。<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Visual Studio ソリューション ファイルを開くときの既定のプログラムでは、VSLauncher.exe プログラムでは、ソリューション ファイルを開くときに Visual Studio のバージョンを判断するのにこの&2; つ目の行を使用します。 アプリケーションには、その関連するソリューション ファイルを処理する独自の起動ツールが必要となります。 起動プログラムでしたも行を使用して&2; 番目のソリューション ファイルのソリューションを開くアプリケーションのバージョンを確認します。<br /><br /> 注: Visual Studio VSLauncher.exe プログラムは、分離シェル アプリケーションによって作成された .sln ファイルを処理しません。<br /><br /> 既定値は"*solutionName*ソリューション ファイルの形式バージョン 10.00" ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|SolutionFileExt|string|アプリケーションのソリューション ファイル名拡張子。 一意のファイル名拡張子 (not.sln) を選択することをお勧めします。<br /><br /> 既定値は"*solutionName*_sln"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|SplashScreenBitmap|string|アプリケーションのスプラッシュ画面のビットマップ ファイルの完全パス。<br /><br /> 既定値は、"$RootFolder$\Splash.bmp"です。|  
|ThisVersionDTECLSID|string|アプリケーションのオートメーション オブジェクトのクラス id (CLSID)。<br /><br /> アプリケーションのオートメーション オブジェクトは、Visual Studio シェルのオートメーション モデルと実装内のアプリケーションのトップレベルのオブジェクト、<xref:EnvDTE._DTE?displayProperty=fullName>インターフェイス</xref:EnvDTE._DTE?displayProperty=fullName>。<br /><br /> Hkey_classes_root \clsid レジストリ キーの下で、アプリケーションのオートメーション オブジェクトが正しく登録されているかどうかを使用して、 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)を直接アプリケーションのインスタンスを作成する関数。<br /><br /> Visual Studio シェルでは、この CLSID を使用して、ACTIVEOBJECT_WEAK フラグを使用して実行中のオブジェクト テーブル (ROT) で、アプリケーションのオートメーション オブジェクトを登録します。 これにより、使用する、 [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)アプリケーションの実行中のインスタンスへのポインターを取得します。 さらに、アプリケーションのオートメーション オブジェクトの ProgID を定義する場合、Visual Studio シェルも登録、アプリケーションの各インスタンス ROT にフォームのアイテム モニカーを使用して、 *progID*:*processID*ここで、 *progID*は、アプリケーションのオートメーション オブジェクトの ProgID と*processID*アプリケーションのインスタンスのプロセス識別子を指定します。 たとえば、次のように、モニカーを作成するとします。<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> ここで`instanceString`は、 *progID*:*processID*文字列。 使用できます`instanceMoniker`インスタンスの取得に回転 GetObject 関数を使用します。<br /><br /> ThisVersionDTECLSID 設定を省略すると、コンポーネント オブジェクト モデル (COM) ではないアプリケーションに公開されます。 ここでは、呼び出すことによって、アプリケーションのインスタンスを作成できません、 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)機能、ROT に登録することはできません。<br /><br /> VSPackage の各バージョンには、異なる CLSID が必要です。<br /><br /> 既定値は、アプリケーションのオートメーション オブジェクトに Visual Studio で生成される GUID です。|  
|ThisVersionSolutionCLSID|string|アプリケーションのソリューション オブジェクトの CLSID。<br /><br /> ソリューションのオートメーション オブジェクトを実装して、アプリケーションのインスタンスで現在開いているソリューションに関する情報を格納する、<xref:EnvDTE._Solution?displayProperty=fullName>インターフェイス</xref:EnvDTE._Solution?displayProperty=fullName>。<br /><br /> Hkey_classes_root \clsid レジストリ キーの下で、ソリューションのオートメーション オブジェクトが正しく登録されているかどうかを使用して、 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)アプリケーションのソリューション オブジェクトを直接作成する関数。<br /><br /> Visual Studio シェルでは、この CLSID を使用して、ACTIVEOBJECT_WEAK フラグを使用してソリューションのオートメーション オブジェクトを ROT に登録します。<br /><br /> この設定を省略した場合は、ソリューションのクラスがコンポーネント オブジェクト モデル (COM) に登録されていないソリューション オブジェクトを呼び出すことによって作成されることはできません、 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)機能、ROT に登録することはできません。<br /><br /> 既定値は、Visual Studio がアプリケーションのソリューション オブジェクトに対して生成される GUID です。|  
|UserFilesSubFolderName|string|ユーザー ファイルとサブフォルダーに、アプリケーションを作成するユーザーのマイ ドキュメント フォルダーのサブフォルダーの名前。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
|UserOptsFileExt|string|アプリケーションのソリューション ユーザー オプション ファイルの拡張子です。<br /><br /> 既定値は、アプリケーションのソリューション ファイルの名前です。|  
  
## <a name="binding-path-settings"></a>バインド パスの設定  
 [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] キーには、シェルがアセンブリをチェックするディレクトリの一覧が含まれています。 これらのディレクトリは、シェルがアプリケーションのプライベート アセンブリがプローブされるディレクトリの一覧に追加されます。  
  
 既定では、バインド パス エントリが追加されなく .pkgdef ファイルにします。 ただし、Visual Studio インストール ディレクトリの下にサブディレクトリは、レジストリ内のアプリケーションのバインド パス リストに自動的に追加します。  
  
-   Common7 \ide\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 ディレクトリをバインド パスを追加するには、フォームのエントリを追加"*directoryName*「=」"ここで、 *directoryName*絶対パスです。 次に例を示します。  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>プロファイルの設定  
 次の表では、[$RootKey$ \Profile] の下の関連する各パッケージに対して定義されている値について説明します。  
  
|名前|型|値|  
|----------|----------|-----------|  
|AutoSaveFile|string|アプリケーションが自動保存ファイルを保存するディレクトリ。<br /><br /> 既定値は、"$RootFolder$\Profiles\CurrentSettings.vssettings"です。|  
  
## <a name="package-satellite-dll-settings"></a>パッケージ サテライト DLL の設定  
 次の表に、値で定義されている [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] サテライト DLL の各関連付けられているパッケージの場所*vsPackageGuid*関連パッケージの guid を指定します。  
  
|名前|型|値|  
|----------|----------|-----------|  
|宣言されました。|string|DLL のファイル名。<br /><br /> 既定値は"*solutionName*ui.dll"ここで、 *solutionName*アプリケーション ソリューション ファイルの名前を指定します。|  
|パス|string|サテライト DLL を格納するディレクトリ。<br /><br /> 既定値は、「$PackageFolder$」です。|  
  
## <a name="package-menu-item-settings"></a>パッケージのメニュー項目の設定  
 [$RootKey$ \Menus] レジストリ キーでは、アプリケーションの UI のリソース ファイルを定義します。  
  
 メニュー項目の値があるフォーム"{*vsUiPackageGuid*}「=」 *resourceId*、 *versionNumber*"ここで、 *vsUiPackageGuid*アプリケーションの UI パッケージの guid を指定*resourceId*を UI 要素を含む CTMENU リソースのリソース識別子を指定しますおよび*versionNumber* CTMENU リソースの仮想バージョン番号です。 詳細については、次を参照してください。[相互運用機能アセンブリ コマンド ハンドラーの登録](../extensibility/internals/registering-interop-assembly-command-handlers.md)します。  
  
 既定では、アプリケーションの UI パッケージ .pkgdef ファイルでメニュー項目が作成されます。  
  
 メニュー項目を提供し、アプリケーションの一部として付属している各パッケージのパッケージのメニュー項目を追加します。  
  
## <a name="see-also"></a>関連項目  
 [分離シェルをカスタマイズします。](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgundef ファイル](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)
