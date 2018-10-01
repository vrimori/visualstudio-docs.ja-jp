---
title: 分離シェル アプリケーションをインストールする |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7b1ba12f39accf863b051ec7096ee835a03ff64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539024"
---
# <a name="installing-an-isolated-shell-application"></a>分離シェル アプリケーションをインストールします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[分離シェル アプリケーションをインストールする](https://docs.microsoft.com/visualstudio/extensibility/installing-an-isolated-shell-application)します。  
  
シェルのアプリをインストールするには、次の手順を実行する必要があります。  
  
-   ソリューションを準備します。  
  
-   アプリケーションの Windows インストーラー (MSI) パッケージを作成します。  
  
-   セットアップ ブートス トラップを作成します。  
  
 すべてのコード例では、このドキュメントは、[シェルの展開サンプル](http://go.microsoft.com/fwlink/?LinkId=262245)、MSDN web サイトのコード ギャラリーからダウンロードできます。 サンプルでは、これらの各手順の実行の結果を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックで説明する手順を実行するには、コンピューターに、次のツールをインストールする必要があります。  
  
-   Visual Studio SDK  
  
-   [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720)バージョン 3.6  
  
 このサンプルは、Microsoft Visualization and Modeling SDK いないすべてのシェルが必要にも必要です。  
  
## <a name="preparing-your-solution"></a>ソリューションを準備します。  
 既定では、シェル テンプレートは、VSIX パッケージにビルドしますが、この動作は、デバッグ目的で主にします。 シェル アプリケーションを展開するときに、インストール中にレジストリのアクセスと再起動を許可する MSI パッケージを使用する必要があります。 アプリケーションの MSI の展開を準備するには、次の手順を実行します。  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>MSI の展開のシェル アプリケーションを準備するには  
  
1.  ソリューション内の各 .vsixmanifest ファイルを編集します。  
  
     `Identifier`要素を追加、`InstalledByMSI`要素と`SystemComponent`要素にその値を設定して`true`します。  
  
     これらの要素を使用してアンインストールしてから、コンポーネントとユーザーをインストールしようとしてから、VSIX インストーラーを防ぐため、**拡張機能と更新** ダイアログ ボックス。  
  
2.  VSIX マニフェストを含むプロジェクトごとに、MSI がインストール元の場所にコンテンツを出力するビルド タスクを編集します。 ビルド出力では、VSIX マニフェストが含まれますが、.vsix ファイルのビルドはありません。  
  
## <a name="creating-an-msi-for-your-shell"></a>Shell の MSI を作成します。  
 MSI パッケージを構築することをお勧めしますを使用すること、 [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720)標準セットアップ プロジェクトよりも優れた柔軟性を提供するためです。  
  
 Product.wxs ファイルで検出ブロックとシェル コンポーネントのレイアウトを設定します。  
  
 ソリューションの .reg ファイルと ApplicationRegistry.wxs の両方のレジストリ エントリを作成します。  
  
### <a name="detection-blocks"></a>検出のブロック  
 検出ブロックから成る、`Property`を検出する前提条件を指定する要素と`Condition`を返すかどうか、前提条件は、コンピューター上に存在するメッセージを指定する要素。 たとえば、シェル アプリケーションには、再頒布可能パッケージを Microsoft Visual Studio Shell は必要とし、検出のブロックには、次のマークアップはようになります。  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>シェル コンポーネントのレイアウト  
 ターゲット ディレクトリ構造と、インストールするコンポーネントを識別するために要素を追加する必要があります。  
  
##### <a name="to-set-the-layout-of-shell-components"></a>シェル コンポーネントのレイアウトを設定するには  
  
1.  階層を作成`Directory`を表すすべてのディレクトリとして次の例は、対象のコンピューター上のファイル システムを作成する要素。  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     これらのディレクトリによって参照される`Id`インストール必要があるファイルが指定されている場合。  
  
2.  シェルとシェル アプリケーションを必要とする、次の例は、コンポーネントを特定します。  
  
    > [!NOTE]
    >  いくつかの要素は、他のデコンパイルして .wxs ファイルで定義を参照できます。  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1.  `ComponentRef`要素は、現在のコンポーネントが必要なファイルを識別する別のデコンパイルして .wxs ファイルを参照します。 たとえば、GeneralProfile には、次の定義が HelpAbout.wxs でがあります。  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef`要素は、ユーザーのコンピューターにこれらのファイルを移動する場所を指定します。 `Directory`がインストールされるようにし、サブディレクトリに、各要素を指定`File`要素が組み込まれているものや、ソリューションの一部としてが存在し、そのファイルがある MSI ファイルを作成するときに識別するファイルを表します。  
  
    2.  `ComponentGroupRef`要素は他のコンポーネント (またはコンポーネントとコンポーネントのグループ) のグループを参照します。 たとえば、 `ComponentGroupRef` ApplicationGroup 下で定義されて次のように Application.wxs します。  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Shell (Isolated) アプリケーションの依存関係が必要です: DebuggerProxy、MasterPkgDef、リソース (特に .winprf ファイル)、アプリケーション、および PkgDefs します。  
  
### <a name="registry-entries"></a>レジストリ エントリ  
 Shell (Isolated) のプロジェクト テンプレートが含まれています、 *ProjectName*インストールでマージするレジストリ キーの .reg ファイル。 これらのレジストリ エントリは、インストールとクリーンアップのための両方の MSI の一部である必要があります。 ApplicationRegistry.wxs で一致するレジストリのブロックを作成することも必要があります。  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>MSI にレジストリ エントリを統合するには  
  
1.  **シェルのカスタマイズ**フォルダーを開き、 *ProjectName*レジストリ。  
  
2.  $RootFolder$ トークンのすべてのインスタンスをインストール先のディレクトリのパスに置き換えます。  
  
3.  アプリケーションに必要な他のレジストリ エントリを追加します。  
  
4.  ApplicationRegistry.wxs を開きます。  
  
5.  各レジストリ エントリで*ProjectName*.reg、次の例として、対応するレジストリのブロックを追加します。  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[Hkey_classes_root \clsid\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @「PhotoStudio DTE オブジェクト」を =|\<RegistryKey Id = 'DteClsidRegKey' Root 'HKCR' キーを = =' $(var 関数DteClsidRegKey)' アクション = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue 型 = 'string' Name =' @' 値 =' $(var 関数ShortProductName) DTE オブジェクト"/><br /><br /> \</RegistryKey >|  
    |[Hkey_classes_root \clsid\\{bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id = 'DteLocSrv32RegKey' Root 'HKCR' キーを = =' $(var 関数DteClsidRegKey) \LocalServer32' アクション = 'createAndRemoveOnUninstall' ><br /><br /> \<RegistryValue 型 = 'string' Name =' @' 値 ='[INSTALLDIR] $(var 関数ShortProductName) .exe"/><br /><br /> \</RegistryKey >|  
  
     この例では、Var.DteClsidRegKey は一番上の行で、レジストリ キーに解決されます。 解決される Var.ShortProductName`PhotoStudio`します。  
  
## <a name="creating-a-setup-bootstrapper"></a>セットアップ ブートス トラップの作成  
 すべての前提条件が最初にインストールされている場合にのみ、完了した MSI がインストールされます。 エンド ユーザー エクスペリエンスを容易にするには、収集し、アプリケーションのインストール前に、すべての前提条件をインストールするセットアップ プログラムを作成します。 インストールの成功を確認するには、これらのアクションを実行します。  
  
-   管理者によってインストールを強制します。  
  
-   Visual Studio Shell (Isolated) がインストールされているかどうかを検出します。  
  
-   順序で 1 つまたは両方のシェル インストーラーを実行します。  
  
-   再起動要求を処理します。  
  
-   MSI を実行します。  
  
### <a name="enforcing-installation-by-administrator"></a>管理者によってインストールを適用します。  
 この手順は \Program Files などに必要なディレクトリにアクセスするセットアップ プログラムを有効にするために必要な\\します。  
  
##### <a name="to-enforce-installation-by-administrator"></a>管理者によってインストールを強制するには  
  
1.  セットアップ プロジェクトのショートカット メニューを開き、選択し、**プロパティ**します。  
  
2.  **構成プロパティ/リンカー/マニフェスト ファイル**設定**UAC の実行レベル**に**requireAdministrator**します。  
  
     このプロパティは、埋め込みのマニフェスト ファイルに管理者として実行するプログラムを必要とする属性を配置します。  
  
### <a name="detecting-shell-installations"></a>シェルのインストールを検出  
 Visual Studio Shell (Isolated) をインストールする必要があるかどうかを判断するには、まず HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install のレジストリ値をチェックして既にインストールされているかどうかを決定します。  
  
> [!NOTE]
>  これらの値は、Product.wxs にシェル検出ブロックによっても読み込まれます。  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder では、Visual Studio シェルがインストールされているファイルをチェックすることができますをする場所を指定します。  
  
 シェルのインストールを検出する方法の例は、次を参照してください。、 `GetProductDirFromReg` Utilities.cpp シェルの展開サンプル内の関数。  
  
 パッケージを必要とする Visual Studio シェルの一方または両方がコンピューターにインストールされていない場合は、インストールするコンポーネントの一覧に追加する必要があります。 例については、次を参照してください。、 `ComponentsPage::OnInitDialog` ComponentsPage.cpp シェルの展開サンプル内の関数。  
  
### <a name="running-the-shell-installers"></a>シェルのインストーラーを実行しています。  
 シェルのインストーラーを実行するには、適切なコマンドライン引数を使用して Visual Studio Shell 再頒布可能パッケージを呼び出します。 少なくとも、コマンドライン引数を使用する必要があります **/norestart/q**次に実行する内容を決定するリターン コードを確認します。 次の例では、シェル (Isolated) 再頒布可能パッケージを実行します。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>シェルの言語パック インストーラーを実行しています。  
 シェルまたはシェルがインストールされているし、用言語パックする必要があるだけのことを代わりに検索する場合は、次の例のように、言語パックをインストールできます。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>戻り値の解読  
 Visual Studio Shell (Isolated) のインストールには、いくつかのオペレーティング システムで再起動が必要です。 呼び出しのリターン コードでこの条件を決定できます`ExecCmd`します。  
  
|戻り値|説明|  
|------------------|-----------------|  
|ERROR_SUCCESS|インストールが完了しました。 アプリケーションをインストールできます。|  
|ERROR_SUCCESS_REBOOT_REQUIRED|インストールが完了しました。 コンピューターが再起動した後は、アプリケーションをインストールできます。|  
|3015|インストールが進行中です。 インストールを続行するには、コンピューターの再起動が必要です。|  
  
### <a name="handling-restarts"></a>再起動を処理します。  
 使用してシェル インストーラーを実行したときに、 **/norestart**コンピューターを再起動またはコンピューターの再起動を要求しませんというに指定した引数。 ただし、再起動が必要であるし、インストーラーは、コンピューターが再起動された後、引き続きいることを確認する必要があります。  
  
 再起動を正しく処理するには、その 1 つだけセットアップ プログラムが再開に設定され、再開プロセスが正しく処理することを確認します。  
  
 ERROR_SUCCESS_REBOOT_REQUIRED または 3015 のいずれかが返された場合、コードは、インストールを続行する前にコンピューターを再起動する必要があります。  
  
 再起動を処理するには、これらのアクションを実行します。  
  
-   Windows の起動時に、インストールを再開するレジストリを設定します。  
  
-   ブートス トラップの二重の再起動を実行します。  
  
-   シェル インストーラー ResumeData キーを削除します。  
  
-   Windows を再起動します。  
  
-   Msi ファイルの開始パスをリセットします。  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Windows の起動時にセットアップを再開するレジストリを設定  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ のレジストリ キーは、管理者権限でシステムの起動時に実行し、しは消去されます。 HKEY_CURRENT_USER にはようなキーが含まれていますが、通常のユーザーとして実行されるはのインストールに適していません。 呼び出すインストーラー RunOnce キーに文字列値を配置することで、インストールを再開できます。 ただしを使用して、インストーラーを呼び出すことは推奨、 **再起動/** または開始する代わりにそれを再開しているアプリケーションに通知するようなパラメーター。 複数の再起動が必要なインストールで特に便利ですが、インストール プロセスであるかを示すパラメーターを含めることもできます。  
  
 次の例では、インストールを再開するに RunOnce レジストリ キーの値を示します。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>ブートス トラップの二重の再起動をインストールします。  
 RunOnce から直接セットアップを使用する場合、デスクトップの読み込みが完了することはできません。 完全なユーザー インターフェイスを使用できるようにするには、は、セットアップの別の実行を作成し、RunOnce インスタンスを終了する必要があります。  
  
 適切なアクセス許可を取得し、次の例として、再起動する前にしてを停止した位置を把握するのに十分な情報を提供する必要がありますように、セットアップ プログラムを再実行する必要があります。  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>シェル インストーラー ResumeData キーを削除します。  
 シェル インストーラでは、再起動後にセットアップを再開するデータを HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData レジストリ キーを設定します。 シェル インストーラーではなく、アプリケーションを再開するため、としては、次の例は、このレジストリ キーを削除します。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Windows の再起動  
 必要なレジストリ キーを設定すると後、は、Windows を再起動することができます。 次の例では、さまざまな Windows オペレーティング システムの再起動のコマンドを呼び出します。  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>MSI の開始パスをリセットします。  
 再起動する前に、現在のディレクトリは、セットアップ プログラムの場所ですが、再起動後に、場所が、system32 ディレクトリになります。 セットアップ プログラムは、次の例のように各 MSI 呼び出しの前に、現在のディレクトリをリセットする必要があります。  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>アプリケーションの MSI を実行します。  
 Visual Studio Shell インストーラーは、ERROR_SUCCESS を返した後、アプリケーションの MSI を実行できます。 セットアップ プログラムには、ユーザー インターフェイスが提供することは、ため、quiet モードで、MSI を開始 (**/q**) とログ記録 (**/L**) 次の例に示すように、します。  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

