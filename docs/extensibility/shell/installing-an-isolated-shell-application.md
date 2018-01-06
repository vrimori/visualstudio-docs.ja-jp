---
title: "分離シェル アプリケーションをインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6672ed634ad8c8056ae372c9d1d9a3fa44b56243
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="installing-an-isolated-shell-application"></a>分離シェル アプリケーションをインストールします。
シェル アプリケーションをインストールするには、次の手順を実行する必要があります。  
  
-   ソリューションを準備します。  
  
-   アプリケーションの Windows インストーラー (MSI) パッケージを作成します。  
  
-   セットアップ ブートス トラップを作成します。  
  
 このドキュメントでのコード例のすべてを起源、[シェルの展開サンプル](http://go.microsoft.com/fwlink/?LinkId=262245)、MSDN web サイト コード ギャラリーからダウンロードできます。 このサンプルでは、これらの各手順の実行の結果を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックで説明する手順を実行するには、コンピューターに、次のツールをインストールする必要があります。  
  
-   Visual Studio SDK  
  
-   [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720)バージョン 3.6  
  
 このサンプルは、Microsoft Visualization and Modeling SDK すべてシェルが必要にも必要です。  
  
## <a name="preparing-your-solution"></a>ソリューションを準備します。  
 既定では、シェル テンプレートは、VSIX パッケージにビルドしますが、主にデバッグの目的でこの動作が対象としています。 シェル アプリケーションを展開する場合は、インストール中にレジストリへのアクセスと再起動を許可する MSI パッケージを使用する必要があります。 MSI デプロイのアプリケーションを準備するのには、次の手順を実行します。  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>MSI デプロイのシェル アプリケーションを準備するには  
  
1.  ソリューション内の各 .vsixmanifest ファイルを編集します。  
  
     `Identifier`要素を追加、`InstalledByMSI`要素と`SystemComponent`要素にその値を設定して`true`です。  
  
     これらの要素を防ぐ VSIX インストーラーを使用してアンインストールしてから、コンポーネントとユーザーをインストールしようとして、**拡張機能と更新プログラム** ダイアログ ボックス。  
  
2.  VSIX マニフェストを含むプロジェクトごとに、MSI がインストール元の場所にコンテンツを出力するビルド タスクを編集します。 VSIX マニフェストに含めるビルド出力が、.vsix ファイルを作成しません。  
  
## <a name="creating-an-msi-for-your-shell"></a>シェルの MSI を作成します。  
 MSI パッケージを作成することをお勧めを使用すること、 [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720)標準セットアップ プロジェクトよりも高い柔軟性を提供するためです。  
  
 Product.wxs ファイルには、検出のブロックとシェルのコンポーネントのレイアウトを設定します。  
  
 ソリューションの .reg ファイルと ApplicationRegistry.wxs の両方は、レジストリ エントリを作成します。  
  
### <a name="detection-blocks"></a>検出のブロック  
 検出ブロックから成る、`Property`検出するために必要な前提条件を指定する要素と`Condition`を返すかどうか、前提条件は、存在しないコンピューター上のメッセージを指定する要素。 たとえば、シェル アプリケーションは、再頒布可能パッケージ、Microsoft Visual Studio シェルを必要とし、検出ブロックは、次のマークアップのようにします。  
  
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
  
### <a name="layout-of-shell-components"></a>シェルのコンポーネントのレイアウト  
 ターゲット ディレクトリ構造およびインストールするコンポーネントを識別する要素を追加する必要があります。  
  
##### <a name="to-set-the-layout-of-shell-components"></a>シェルのコンポーネントのレイアウトを設定するには  
  
1.  階層を作成`Directory`を次の例のように、対象のコンピューター上のファイル システムで作成するディレクトリのすべてを表す要素。  
  
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
  
     これらのディレクトリによって参照される`Id`インストールしなければならないファイルが指定されている場合。  
  
2.  シェルとシェル アプリケーションを必要とする、次の例のように、コンポーネントを識別します。  
  
    > [!NOTE]
    >  いくつかの要素は、その他のデコンパイルして .wxs ファイル内の定義を参照できます。  
  
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
  
    1.  `ComponentRef`要素は、現在のコンポーネントが必要なファイルを識別する別のデコンパイルして .wxs ファイルを参照します。 たとえば、GeneralProfile に次の定義 HelpAbout.wxs です。  
  
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
  
         `DirectoryRef`要素は、ユーザーのコンピューターでこれらのファイルの移動先を指定します。 `Directory`要素にはインストールするように指定、ディレクトリのサブディレクトリに、各`File`要素が組み込まれているか、ソリューションの一部として存在し、そのファイルがある MSI ファイルの作成時に識別するファイルを表します。  
  
    2.  `ComponentGroupRef`要素は他のコンポーネント (またはコンポーネントおよびコンポーネントのグループ) のグループを参照します。 たとえば、 `ComponentGroupRef` ApplicationGroup 下で定義されて次のように Application.wxs です。  
  
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
    >  Shell (Isolated) のアプリケーションの依存関係が必要な: DebuggerProxy、MasterPkgDef、リソース (.winprf ファイルでは特に)、アプリケーション、および PkgDefs です。  
  
### <a name="registry-entries"></a>レジストリ エントリ  
 Shell (Isolated) のプロジェクト テンプレートが含まれています、 *ProjectName*インストールでマージするレジストリ キーの .reg ファイル。 これらのレジストリ エントリは、インストールとクリーンアップのための両方の msi ファイルの一部である必要があります。 ApplicationRegistry.wxs で一致するレジストリのブロックを作成することも必要があります。  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Msi ファイル内のエントリをレジストリに統合するには  
  
1.  **シェルのカスタマイズ**フォルダーを開き、 *ProjectName*レジストリ。  
  
2.  $RootFolder$ トークンのすべてのインスタンスをインストール先のディレクトリのパスに置き換えます。  
  
3.  アプリケーションを必要とするその他のレジストリ エントリを追加します。  
  
4.  ApplicationRegistry.wxs を開きます。  
  
5.  各レジストリ エントリで*ProjectName*.reg、次の例として、対応するレジストリ ブロックを追加します。  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[Hkey_classes_root \clsid\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @=「PhotoStudio DTE オブジェクト」|\<RegistryKey Id = 'DteClsidRegKey' Root 'HKCR' キー = =' $(var 関数DteClsidRegKey)' アクション 'createAndRemoveOnUninstall' = = ><br /><br /> \<RegistryValue 型 = 'string' 名前 =' @' の値 =' $(var 関数ShortProductName) DTE オブジェクト '/><br /><br /> \</RegistryKey >|  
    |[Hkey_classes_root \clsid\\{bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id = 'DteLocSrv32RegKey' Root 'HKCR' キー = =' $(var 関数DteClsidRegKey) \LocalServer32' 操作 'createAndRemoveOnUninstall' = = ><br /><br /> \<RegistryValue 型 = 'string' 名前 =' @' の値 ='[INSTALLDIR] $(var 関数ShortProductName) .exe '/><br /><br /> \</RegistryKey >|  
  
     この例では、Var.DteClsidRegKey は先頭の行に、レジストリ キーに解決されます。 解決される Var.ShortProductName`PhotoStudio`です。  
  
## <a name="creating-a-setup-bootstrapper"></a>セットアップ ブートス トラップの作成  
 すべての前提条件が最初にインストールされている場合にのみ、完了した MSI がインストールされます。 エンド ユーザー エクスペリエンスを容易にするには、収集して、アプリケーションのインストール前に、すべての前提条件をインストールするセットアップ プログラムを作成します。 インストールの成功を確実には、これらのアクションを実行します。  
  
-   管理者によってインストールを強制します。  
  
-   Visual Studio Shell (Isolated) がインストールされているかどうかを検出します。  
  
-   順序で 1 つまたは両方のシェル インストーラーを実行します。  
  
-   再起動要求を処理します。  
  
-   MSI を実行します。  
  
### <a name="enforcing-installation-by-administrator"></a>管理者によってインストールの適用  
 この手順は \Program Files などの必要なディレクトリにアクセスするセットアップ プログラムを有効にするために必要な\\します。  
  
##### <a name="to-enforce-installation-by-administrator"></a>管理者によってインストールを強制するには  
  
1.  セットアップ プロジェクトのショートカット メニューを開き、選択**プロパティ**です。  
  
2.  **構成プロパティ/リンカー/マニフェスト ファイル**設定、 **UAC の実行レベル**に**requireAdministrator**です。  
  
     このプロパティは、埋め込まれたマニフェスト ファイルに管理者として実行するプログラムを必要とする属性を格納します。  
  
### <a name="detecting-shell-installations"></a>シェルのインストールを検出します。  
 Visual Studio Shell (Isolated) をインストールする必要があるかどうかを決定するには、まず HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install のレジストリ値をチェックしてインストールされているかどうかを決定します。  
  
> [!NOTE]
>  これらの値は、ブロックを指定して、シェル検出 Product.wxs でも読み込まれます。  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder では、ここで、Visual Studio Shell がインストールされ、そこにファイルをチェックすることができます、場所を指定します。  
  
 シェルのインストールを検出する方法の例は、次を参照してください。、 `GetProductDirFromReg` Utilities.cpp シェルの展開サンプルでの関数。  
  
 いずれかまたは両方をパッケージが必要とする Visual Studio シェルがインストールされていないコンピューターの場合は、インストールするコンポーネントの一覧に追加する必要があります。 例については、次を参照してください。、 `ComponentsPage::OnInitDialog` ComponentsPage.cpp シェルの展開サンプルでの関数。  
  
### <a name="running-the-shell-installers"></a>シェルのインストーラーを実行しています。  
 シェルのインストーラーを実行するには、適切なコマンドライン引数を使用して Visual Studio Shell の再頒布可能パッケージを呼び出します。 少なくとも、コマンドライン引数を使用する必要があります**/norestart/q**次に実行する内容を決定するリターン コードを確認します。 次の例では、Shell (Isolated 再頒布可能パッケージ) が実行されます。  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>シェルの言語パック インストーラーを実行しています。  
 見つかった場合は代わりにシェルまたはシェルがインストールされていること、およびだけが必要な言語パックを次の例のように、言語パックをインストールできます。  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>戻り値を解明  
 Visual Studio Shell (Isolated) のインストールには、いくつかのオペレーティング システムで再起動が必要です。 呼び出しのリターン コードでこの条件を決定できます`ExecCmd`です。  
  
|戻り値|説明|  
|------------------|-----------------|  
|ERROR_SUCCESS を返します|インストールが完了しました。 アプリケーションをインストールできます。|  
|ERROR_SUCCESS_REBOOT_REQUIRED|インストールが完了しました。 コンピューターの再起動後、アプリケーションをインストールすることができます。|  
|3015|インストールが進行中です。 インストールを続行するには、コンピューターの再起動が必要です。|  
  
### <a name="handling-restarts"></a>再起動の処理  
 使用してシェル インストーラーを実行したとき、 **/norestart**コンピューターを再起動またはコンピューターの再起動を求める考えないからというに指定した引数、します。 ただし、再起動が必要であるし、コンピューターが再起動された後に、インストーラーを続行することを確認する必要があります。  
  
 再起動を正しく処理するには、その 1 つだけセットアップ プログラムは再開に設定され、再開プロセスが正しく処理することを確認します。  
  
 ERROR_SUCCESS_REBOOT_REQUIRED または 3015 のいずれかが返される場合は、コードは、インストールを続行する前にコンピューターを再起動する必要があります。  
  
 再起動を処理するには、これらの操作を実行します。  
  
-   Windows の起動時に、インストールを再開する、レジストリを設定します。  
  
-   ブートス トラップの二重の再起動を実行します。  
  
-   シェル インストーラー ResumeData キーを削除します。  
  
-   Windows を再起動します。  
  
-   Msi ファイルの開始パスをリセットします。  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Windows の起動時に、セットアップを再開するレジストリを設定  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ レジストリ キーは、管理者権限を持つシステムの起動時を実行し、し、消去されます。 HKEY_CURRENT_USER にはようなキーが含まれていますが、通常のユーザーとして実行されがインストールの場合は適切でないです。 呼び出すインストーラー RunOnce キーに文字列値を設定することによって、インストールを再開できます。 ただしを使用して、インストーラーを呼び出すことは推奨、 **再起動/**または開始する代わりにそれを再開して、アプリケーションに通知するようなパラメーターです。 インストール プロセスでは複数の再起動が必要なインストールで特に便利であるかを示すためにパラメーターを含めることもできます。  
  
 次の例では、インストールを再開するに RunOnce レジストリ キーの値を示します。  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>ブートス トラップの二重の再起動をインストールします。  
 セットアップを RunOnce から直接使用する場合、デスクトップの読み込みが完了することはできません。 完全なユーザー インターフェイスを使用できるようにするにはセットアップの別の実行を作成する必要がありますして RunOnce インスタンスを終了します。  
  
 適切なアクセス許可を取得し、停止した、再起動の前に、次の例を理解するのに十分な情報を提供する必要がありますようにセットアップ プログラムを再実行する必要があります。  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>シェル インストーラー ResumeData キーを削除します。  
 シェル インストーラは、再起動後にセットアップを再開するデータを HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData のレジストリ キーを設定します。 シェル インストーラーではなく、アプリケーションを再開するため、次の例のように、このレジストリ キーを削除します。  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Windows の再起動  
 必要なレジストリ キーを設定した後は、Windows を再起動することができます。 次の例では、別の Windows オペレーティング システムの再起動のコマンドを呼び出します。  
  
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
 、再起動の前には、現在のディレクトリは、セットアップ プログラムの場所が、再起動後に、場所は、system32 ディレクトリになります。 セットアップ プログラムは、次の例のように MSI の各呼び出しの前に、現在のディレクトリをリセットする必要があります。  
  
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
 Visual Studio Shell インストーラーには、error_success を返しますが返された、後に、アプリケーションの MSI を実行できます。 セットアップ プログラムが提供するため、ユーザー インターフェイス、非表示モードで、MSI を開始 (**/q**) のログ出力を (**/L**) 次の例を示します。  
  
```cpp  
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
  
## <a name="see-also"></a>参照  
 [チュートリアル: 基本的な分離シェル アプリケーションを作成する](walkthrough-creating-a-basic-isolated-shell-application.md)