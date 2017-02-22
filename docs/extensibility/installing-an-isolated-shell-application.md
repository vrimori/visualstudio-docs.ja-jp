---
title: "分離シェル アプリケーションをインストールします。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "シェル [Visual Studio] のシェル ベースのアプリケーションを展開します。"
  - "Visual Studio shell。 シェル ベースのアプリケーションを展開します"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
caps.handback.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
---
# 分離シェル アプリケーションをインストールします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

シェルのアプリをインストールするには、次の手順を実行する必要があります。  
  
-   ソリューションを準備します。  
  
-   アプリケーションの Windows インストーラー \(MSI\) パッケージを作成します。  
  
-   セットアップ ブートス トラップを作成します。  
  
 このドキュメントでのコード例のすべてに由来、 [シェルの展開サンプル](http://go.microsoft.com/fwlink/?LinkId=262245), 、MSDN web サイト コード ギャラリーからダウンロードできます。 このサンプルでは、これらの各手順の実行の結果を示します。  
  
## 前提条件  
 このトピックで説明する手順を実行するには、コンピューターに、次のツールをインストールする必要があります。  
  
-   Visual Studio SDK  
  
-   [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) バージョン 3.6  
  
 このサンプルは、Microsoft Visualization and Modeling SDK いないすべてのシェルが必要にも必要です。  
  
## ソリューションを準備します。  
 既定では、VSIX パッケージへのシェルのテンプレートを作成が、この動作はデバッグのために、主に対象としています。 シェル アプリケーションを展開する場合は、インストール中に、レジストリへのアクセスと再起動を許可するように MSI パッケージを使用する必要があります。 MSI のデプロイ用のアプリケーションを準備するには、次の手順を実行します。  
  
#### MSI 配置用のシェル アプリケーションを準備するには  
  
1.  ソリューション内の各 .vsixmanifest ファイルを編集します。  
  
     `Identifier` 要素を追加、 `InstalledByMSI` 要素と `SystemComponent` 要素にその値を設定し、 `true`します。  
  
     これらの要素を使用してアンインストールしてから、コンポーネントとユーザーをインストールしようとしていますから VSIX インストーラーを防ぐため、 **拡張機能と更新プログラム** \] ダイアログ ボックス。  
  
2.  VSIX マニフェストを含むプロジェクトごとに、MSI のインストール元の場所にコンテンツを出力するビルド タスクを編集します。 ビルドの出力で VSIX マニフェストを含めるが、.vsix ファイルを作成しません。  
  
## シェルの MSI の作成  
 MSI パッケージをビルドすることをお勧めを使用すること、 [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) 標準セットアップ プロジェクトよりも高い柔軟性を提供するためです。  
  
 Product.wxs ファイルで検出ブロックとシェルのコンポーネントのレイアウトを設定します。  
  
 ソリューションの .reg ファイルと ApplicationRegistry.wxs の両方は、レジストリ エントリを作成します。  
  
### 検出のブロック  
 検出ブロックで構成されます、 `Property` 検出するために必要な前提条件を指定する要素と `Condition` 、必須コンポーネントがコンピューターに存在しないかどうかに返されるメッセージを指定する要素。 たとえば、シェル アプリケーションが再頒布可能パッケージを Microsoft Visual Studio Shell を必要とし、検出ブロックには、次のマークアップはようになります。  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### シェルのコンポーネントのレイアウト  
 対象のディレクトリ構造およびインストールするコンポーネントを識別する要素を追加する必要があります。  
  
##### シェルのコンポーネントのレイアウトを設定するには  
  
1.  階層を作成する `Directory` 要素を表すすべてのターゲット コンピューター上のファイル システムに次の例のようにを作成するディレクトリ。  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     これらのディレクトリによって参照されて `Id` インストール必要があるファイルが指定されている場合。  
  
2.  シェルおよびシェル アプリケーションを必要とする、次の例のように、コンポーネントを識別します。  
  
    > [!NOTE]
    >  いくつかの要素は、その他のデコンパイルして .wxs ファイル内の定義を参照できます。  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  `ComponentRef` 要素を現在のコンポーネントが必要なファイルを識別するもう 1 つのデコンパイルして .wxs ファイルを参照します。 たとえば、GeneralProfile は HelpAbout.wxs で次の定義を持ちます。  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         `DirectoryRef` 要素は、ユーザーのコンピューターにどこでこれらのファイルを指定します。`Directory` 要素を指定して、インストールすることがサブディレクトリに、各 `File` 要素が組み込まれているものかをソリューションの一部として存在し、そのファイルの場所を MSI ファイルの作成時に識別するファイルを表します。  
  
    2.  `ComponentGroupRef` 要素は他のコンポーネント \(またはコンポーネントとコンポーネントのグループ\) のグループを参照します。 たとえば、 `ComponentGroupRef` ApplicationGroup の下で定義されて次のように Application.wxs します。  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  必須の Shell \(Isolated\) アプリケーションの依存関係: DebuggerProxy MasterPkgDef、リソース \(.winprf ファイルでは特に\)、アプリケーション、および PkgDefs です。  
  
### レジストリ エントリ  
 Shell \(Isolated\) プロジェクト テンプレートに含まれる、 *ProjectName*.reg ファイルのインストールでマージするレジストリ キーです。 これらのレジストリ エントリでは、MSI のインストールとクリーンアップのための両方を含める必要があります。 ApplicationRegistry.wxs で一致するレジストリのブロックを作成することも必要があります。  
  
##### レジストリ エントリ、MSI を統合するには  
  
1.  **シェル カスタマイズ** フォルダーを開き、 *ProjectName*. 登録  
  
2.  $RootFolder$ トークンのすべてのインスタンスをインストール先のディレクトリのパスに置き換えます。  
  
3.  アプリケーションに必要な他のレジストリ エントリを追加します。  
  
4.  ApplicationRegistry.wxs を開きます。  
  
5.  各レジストリ エントリで *ProjectName*.reg、次の例として、対応するレジストリ ブロックを追加します。  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |\[{Bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6} hkey\_classes\_root \\clsid\\\]<br /><br /> @\=「PhotoStudio DTE オブジェクト」|\< レジストリ キーの Id \= 'DteClsidRegKey' Root 'HKCR' キーを \= \=' $\(var です。DteClsidRegKey\)' 操作 'createAndRemoveOnUninstall' \= \><br /><br /> \< RegistryValue 型 \= 'string' Name \=' @' 値 \=' $\(var です。ShortProductName\) DTE オブジェクト"\/\><br /><br /> \<\/レジストリ キー \>|  
    |\[Hkey\_classes\_root \\clsid\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6} \\LocalServer32\]<br /><br /> @\="$RootFolder$\\PhotoStudio.exe"|\< レジストリ キーの Id \= 'DteLocSrv32RegKey' Root 'HKCR' キーを \= \=' $\(var です。DteClsidRegKey\) \\LocalServer32' 操作 'createAndRemoveOnUninstall' \= \><br /><br /> \< RegistryValue 型 \= 'string' Name \=' @' 値 \='\[INSTALLDIR\] $\(var です。ShortProductName\) .exe"\/\><br /><br /> \<\/レジストリ キー \>|  
  
     この例では、Var.DteClsidRegKey は、先頭の行にレジストリ キーに解決されます。 解決される Var.ShortProductName `PhotoStudio`します。  
  
## セットアップ ブートス トラップの作成  
 すべての前提条件が最初にインストールされている場合にのみ、完了した MSI がインストールされます。 エンド ユーザー エクスペリエンスを容易にするには、収集し、アプリケーションのインストール前に、すべての前提条件をインストールするセットアップ プログラムを作成します。 インストールの成功を確実には、これらのアクションを実行します。  
  
-   管理者がインストールを強制実行します。  
  
-   Visual Studio Shell \(Isolated\) がインストールされているかどうかを検出します。  
  
-   順序で 1 つまたは両方のシェル インストーラーを実行します。  
  
-   再起動要求を処理します。  
  
-   MSI を実行します。  
  
### 管理者によってインストールの適用  
 \\Program などの必要なディレクトリにアクセスするセットアップ プログラムを有効にするには、この手順が必要です。  
  
##### 管理者がインストールを強制するには  
  
1.  セットアップ プロジェクトのショートカット メニューを開きを選択し **プロパティ**します。  
  
2.  **構成プロパティ\/リンカー\/マニフェスト ファイル**, 、 **UAC の実行レベル** に **requireAdministrator**します。  
  
     このプロパティは、埋め込みのマニフェスト ファイルに管理者として実行するプログラムを必要とする属性を配置します。  
  
### シェルのインストールを検出します。  
 Visual Studio Shell \(Isolated\) をインストールする必要があるかどうかを決定するには、最初を特定のレジストリ値をチェックして既にインストールされているかどうか HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Installします。  
  
> [!NOTE]
>  これらの値は、ブロックを指定して、シェル検出 Product.wxs にも読み込まれます。  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder ここで、Visual Studio Shell がインストールされ、そこにファイルをチェックすることができますの場所を指定します。  
  
 シェルのインストールを検出する方法の例は、次を参照してください。、 `GetProductDirFromReg` Utilities.cpp シェルの展開サンプル内の関数です。  
  
 パッケージを必要とする Visual Studio シェルの一方または両方がコンピューターにインストールされていない場合は、インストールするコンポーネントの一覧に追加する必要があります。 例については、次を参照してください。、 `ComponentsPage::OnInitDialog` ComponentsPage.cpp シェルの展開サンプル内の関数です。  
  
### シェルのインストーラーを実行しています。  
 シェルのインストーラーを実行するには、適切なコマンドライン引数を使用して Visual Studio Shell 再頒布可能パッケージを呼び出します。 少なくとも、コマンドライン引数を使用する必要があります **\/norestart \/q** 、どうすればよいの横を決定するリターン コードを確認します。 次の例では、シェル \(Isolated\) 再頒布可能パッケージを実行します。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### シェルの言語パック インストーラーを実行しています。  
 代わりに、シェルやシェルがインストールされてとを調べるだけ必要な言語パックの場合は、次の例のように、言語パックをインストールできます。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### 戻り値の解読  
 Visual Studio Shell \(Isolated\) のインストールには、いくつかのオペレーティング システムで再起動が必要です。 呼び出しのリターン コードによってこの状態を判断できます `ExecCmd`します。  
  
|戻り値|説明|  
|---------|--------|  
|ERROR\_SUCCESS を返します|インストールが完了します。 アプリケーションをインストールするようになりました。|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|インストールが完了します。 コンピューターの再起動後、アプリケーションをインストールすることができます。|  
|3015|インストールが進行中です。 インストールを続行するには、コンピューターの再起動が必要です。|  
  
### 再起動の処理  
 使用してシェル インストーラーを実行したときに、 **\/norestart** コンピューターを再起動またはコンピューターの再起動を要求しないというに指定した引数。 ただし、再起動が必要であるし、コンピューターが再起動された後、インストーラーを続行することを確認する必要があります。  
  
 再起動を正しく処理するには、その 1 つだけのセットアップ プログラムには、再開に設定され、再開プロセスを正しく処理されますを確認します。  
  
 ERROR\_SUCCESS\_REBOOT\_REQUIRED または 3015 のいずれかが返された場合、コードは、インストールを続行する前にコンピューターを再起動する必要があります。  
  
 再起動を処理するためには、これらのアクションを実行します。  
  
-   Windows の起動時に、インストールを再開するレジストリを設定します。  
  
-   ブートス トラップの 2 つの再起動を実行します。  
  
-   シェル インストーラー ResumeData キーを削除します。  
  
-   Windows を再起動します。  
  
-   Msi ファイルの開始パスをリセットします。  
  
### Windows の起動時に、セットアップを再開するレジストリを設定  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ レジストリ キーの管理権限のあるシステムの起動時に実行され、消去されます。HKEY\_CURRENT\_USER ようなキーが含まれていますが、標準ユーザーとして実行されるはインストールに適していません。 によって、インストーラーが呼び出さ RunOnce キーで文字列値を配置することで、インストールを再開できます。 ただし、推奨を使用して、インストーラーを呼び出すこと、 **\/restart** または開始する代わりにそれを再開してアプリケーションに通知するようなパラメーターです。 セットアップは何回か再起動が必要なインストールで特に便利であるかを示すためにパラメーターを含めることもできます。  
  
 次の例では、インストールを再開するに RunOnce レジストリ キーの値を示します。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### ブートス トラップの 2 つの再起動をインストールします。  
 セットアップは RunOnce から直接使用する場合、デスクトップを完全に読み込むことはできません。 完全なユーザー インターフェイスを使用できるようにするには、セットアップの別の実行を作成し、RunOnce インスタンスを終了する必要があります。  
  
 できるように、適切なアクセス許可を取得し、次の例のように、再起動する前にしてを停止した位置を知るには、十分な情報を提供する必要があります、セットアップ プログラムを再実行する必要があります。  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### シェル インストーラー ResumeData キーを削除します。  
 シェル インストーラーのセット、 HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData レジストリ キーとデータを再起動した後にセットアップを再開します。 シェル インストーラーではなく、アプリケーションを再開するため、次の例のように、このレジストリ キーを削除します。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### Windows の再起動  
 必要なレジストリ キーを設定した後は、Windows を再起動することができます。 次の例では、さまざまな Windows オペレーティング システムの再起動のコマンドを呼び出します。  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### MSI の開始パスをリセットします。  
 再起動する前に、現在のディレクトリは、セットアップ プログラムの場所が、場所は再起動後に、system32 ディレクトリになります。 セットアップ プログラムは、次の例のように MSI の各呼び出しの前に、現在のディレクトリをリセットする必要があります。  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### アプリケーションの MSI を実行します。  
 Visual Studio Shell のインストーラーには、error\_success を返しますが返された、後に、アプリケーションの MSI を実行できます。 セットアップ プログラムが提供するため、ユーザー インターフェイス、サイレント モードで、MSI を開始 \(**\/q**\) のログ出力を \(**\/L**\) 次の例を示します。  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## 参照  
 [チュートリアル: 基本的な分離シェル アプリケーションを作成します。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)