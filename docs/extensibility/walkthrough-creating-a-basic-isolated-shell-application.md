---
title: "チュートリアル: 基本的な分離シェル アプリケーションを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell のチュートリアル"
  - "シェル [Visual Studio] のチュートリアル"
  - "チュートリアル [Visual Studio]、分離シェル ベースのアプリケーション"
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# チュートリアル: 基本的な分離シェル アプリケーションを作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、分離シェル ソリューションを作成、バージョン情報\] ツール ウィンドウをカスタマイズおよび分離シェルをインストールするセットアップ プログラムを作成する方法を示します。  
  
## 必須コンポーネント  
 このチュートリアルに従うと、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。 分離シェルを展開するには、また Visual Studio Shell \(Isolated\) 再頒布可能パッケージを使用する必要があります。  
  
## 分離シェル ソリューションを作成します。  
 このセクションでは、Visual Studio シェルの分離のプロジェクト テンプレートを使用して、分離シェル ソリューションを作成する方法を示します。 ソリューションには、次のプロジェクトが含まれています。  
  
-   *SolutionName*します。AboutBoxPackage プロジェクト:\/ボックスに関するヘルプの外観をカスタマイズすることができます。  
  
-   ShellExtensionsVSIX プロジェクト、分離シェル アプリケーションのさまざまなコンポーネントを定義する source.extension.vsixmanifest ファイルが含まれています。  
  
-   *SolutionName* プロジェクトは、分離シェル アプリケーションを起動する実行可能ファイルが生成されます。 このプロジェクトには、分離シェル アプリケーションの動作と外観のカスタマイズをシェルのカスタマイズのフォルダーが含まれています。  
  
-   *SolutionName* UI プロジェクトは、アクティブなメニュー コマンドとローカライズ可能な文字列を定義するサテライト アセンブリを作成します。  
  
#### 基本的な分離シェル ソリューションを作成するには  
  
1.  Visual Studio を開き、新しいプロジェクトを作成します。  
  
2.  **新しいプロジェクト** ウィンドウで、展開 **その他のプロジェクトの種類** し **拡張**します。 選択、 **Visual Studio シェル分離** プロジェクト テンプレートです。  
  
3.  プロジェクトに名前を `MyVSShellStub` で場所を指定します。 確認して **ソリューションのディレクトリを作成** がチェックされ、クリックして **OK**します。  
  
     新しいソリューションは、 **ソリューション エクスプ ローラー**します。  
  
4.  ソリューションをビルドし、分離シェル アプリケーションのデバッグを開始します。  
  
     分離された Visual Studio シェルが表示されます。 タイトル バーを読み取り **MyVSShellStub**します。 タイトル バーのアイコンは、\\MyVSShellStub\\Resource Files\\ApplicationIcon.ico から生成されます。  
  
## アプリケーション名とアイコンをカスタマイズします。  
 タイトル バーで、会社とロゴの名前を使用して、アプリケーションをブランド化することがあります。 次の手順では、パッケージ定義ファイル、MyVSShellStub.Application.pkgdef を変更することで、カスタム アプリケーションのタイトル バーに表示されるアイコンと名前を変更する方法を示します。  
  
#### アプリケーション名とアイコンをカスタマイズするには  
  
1.  MyVSShellStub プロジェクトでは、\\Shell Customization\\MyVSShellStub.Application.pkgdef を開きます。  
  
2.  変更、 `AppName` 要素の値 **"AppName"\=「Fabrikam 音楽エディター」**  
  
3.  アプリケーション アイコンを変更するには、別のアイコンを \\MyVSShellStub\\MyVSShellStub\\MyVSShellStub\\ ディレクトリにコピーします。 ApplicationIcon1.ico を既存の ApplicationIcon.ico ファイルを変更します。 ApplicationIcon.ico を新しいファイルを変更します。  
  
4.  ソリューションをビルドし、デバッグを開始します。 分離シェル IDE が表示されます。 タイトル バーが、新しいアイコンの横 **Fabrikam 音楽エディター**します。  
  
## 既定の Web ブラウザーのホーム ページをカスタマイズします。  
 このセクションの既定のホーム ページを変更する方法を示しています、 **Web ブラウザー** ウィンドウでは、パッケージ定義ファイルを変更します。  
  
#### 既定の Web ブラウザーのホーム ページをカスタマイズするには  
  
1.  MyVSShellStub.Application.pkgdef ファイルで、変更、 `DefaultHomePage` "http:\/\/www.microsoft.com"要素の値。  
  
2.  MyVSShellStub プロジェクトをリビルドします。  
  
3.  ソリューションをビルドし、デバッグを開始します。  
  
4.  **ビュー\/その他のウィンドウ**, 、クリックして **Web ブラウザー**します。**Web ブラウザー** ウィンドウには、米国 Microsoft Corporation のホーム ページが表示されます。  
  
## 印刷コマンドを削除します。  
 分離シェル UI プロジェクトに .vsct ファイルの形式の宣言から成る `<Define name=No_`*要素*`>`, ここで、 *要素* は標準の Visual Studio のメニューとコマンドの 1 つです。  
  
 宣言がコメントがある場合は、該当するメニューやコマンドが、分離シェルから除外されます。 逆に、宣言をコメントにすると、メニューまたはコマンドが含まれます分離シェルで。  
  
 次の手順では、.vsct ファイルで、\[印刷\] コマンドをコメント解除します。  
  
#### 印刷コマンドを削除するには  
  
1.  いることを確認、 **印刷** コマンドに表示される、 **ファイル** 分離シェル アプリケーションのメニュー。  
  
2.  MyVSShellStubUI プロジェクトでは、編集するための \\Resource Files\\MyVSShellStubUI.vsct を開きます。  
  
3.  この行をコメント解除します。  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  これには、印刷コマンドが削除されます。  
  
5.  分離シェル アプリケーションのデバッグを開始します。 いることを確認、 **ファイル\/印刷** コマンドが削除されています。  
  
## 分離シェルから機能を削除します。  
 一部のカスタム分離シェル アプリケーションでこれらの機能を設定したくない場合は、.pkgundef ファイルを編集することによって、Visual Studio に読み込まれているパッケージを削除することができます。 $RootKey$ \\Packages レジストリ キーのサブキーのいずれかでは、パッケージを指定します。  
  
> [!NOTE]
>  Visual Studio の Guid の機能を検索するには、次を参照してください。 [Visual Studio の機能のパッケージの Guid](../extensibility/package-guids-of-visual-studio-features.md)します。  
  
 次の手順では、分離シェルからエディター、XML を削除する方法を示します。  
  
#### XML エディターを削除するには  
  
1.  MyVSShellStub プロジェクトのシェルのカスタマイズ フォルダーに MyVSShellStub.pkgundef ファイルを開きます。  
  
2.  次の行をコメント解除します。  
  
     \[$RootKey$ \\Packages\\ {87569308\-4813\-40a0\-9cd0\-d7a30838ca3f}\]  
  
3.  ソリューションをリビルドし、分離シェルのデバッグを開始します。 たとえば、\\MyVSShellStub\\MyVSShellStub\\MyVSShellStubUI\\MyVSShellStubUI.vsct、XML ファイルを開きます。 ファイル内の XML のキーワードは色分けして表示しないことを確認する」と入力してその"\<"の行にも表示されません XML のツールヒント。  
  
## ヘルプのカスタマイズ\]、\[ボックスについて  
 ヘルプをカスタマイズする\/ボックスでは、分離シェル プロジェクト テンプレートの一部として作成されます。  
  
#### 会社名をカスタマイズするには  
  
1.  会社名、著作権情報、製品バージョン、および製品の説明は、MyVSShellStub.AboutBoxPackage プロジェクトの \\Properties\\AssemblyInfo.cs ファイルにあります。 このファイルを開きます。  
  
2.  変更、 `AssemblyCompany` 値を **Fabrikam**, 、 `AssemblyProduct` と `AssemblyTitle` 値 **Fabrikam 音楽エディター**, 、および `AssemblyCopyright` 値を **2015 Copyright © Fabrikam**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")] [assembly: AssemblyDescription("")] [assembly: AssemblyConfiguration("")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor ")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  製品の説明を追加するには、変更、 `AssemblyDescription` 値を **Fabrikam 音楽エディターの説明**:。  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  デバッグを開始し、分離シェル アプリケーションで開く、 **ヘルプ\/約** ボックス。 変更された文字列が表示されます。 \/ボックスに関するヘルプのタイトルと同じ、 `AssemblyTitle` AssemblyInfo.cs 内の値。  
  
5.  プロパティ、 **ヘルプ** ボックス自体は MyVSShellStub.AboutBoxPackage\\AboutBox.xaml ファイルで検出します。 \/ボックスに関するヘルプの幅を変更するには、 `AboutDialogStyle` をブロックし、設定、 `Width` を 200 のプロパティ。  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window"> <Setter Property="Height" Value="Auto" /> <Setter Property="Width" Value="200" /> <Setter Property="ShowInTaskbar" Value="False" /> <Setter Property="ResizeMode" Value="NoResize" /> <Setter Property="WindowStyle" Value="SingleBorderWindow" /> <Setter Property="SizeToContent" Value="Height" /> </Style>  
    ```  
  
6.  ソリューションをリビルドし、分離シェルのデバッグを開始します。 ヘルプ\/バージョン情報ボックスを約正方形にする必要があります。  
  
## 分離シェル アプリケーションを展開する前に  
 Visual Studio Shell \(Isolated\) 再頒布可能パッケージを持っている任意のコンピューターでは、分離シェル アプリケーションをインストールできます。 再頒布可能パッケージの詳細については、次を参照してください。、 [Visual Studio 機能拡張ダウンロード](http://go.microsoft.com/fwlink/?LinkID=119298) web サイトです。  
  
## 分離シェル アプリケーションを配置します。  
 対象のコンピュータに、分離シェル アプリケーションを展開するには、セットアップ プロジェクトを作成します。 これらの操作を指定する必要があります。  
  
-   ターゲット コンピューター上のフォルダーおよびファイルのレイアウト。  
  
-   .NET Framework および Visual Studio シェルの実行時に保証起動条件は、ターゲット コンピューターにインストールされます。  
  
 次の手順では、InstallShield Limited Edition をお使いのコンピューターにインストールする必要があります。  
  
#### セットアップ プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**, ソリューション ノードを右クリックし、\[クリックして **新しいプロジェクトの追加**します。  
  
2.  **新しいプロジェクト** \] ダイアログ ボックスで、展開 **その他のプロジェクトの種類** し、\[ **セットアップと配置**します。 InstallShield のテンプレートを選択します。 新しいプロジェクトの名前 `MySetup` \] をクリックし、 **OK**します。  
  
3.  InstallShield Limited Edition が既にインストールされている場合は、次の手順に進みます。  
  
     InstallShield Limited Edition がインストールされていない場合は、InstallShield のダウンロード ページが表示されます。 指示をダウンロードして Visual Studio のバージョンと互換性がある InstallShield のバージョンを選択する製品をインストールします。 InstallShield のインストールを登録または評価版として使用するかどうかを決定する必要があります。 インストールの完了後は、Visual Studio を再起動する必要があります。  
  
    > [!IMPORTANT]
    >  InstallShield プロジェクトを作成する前に、管理者として Visual Studio を起動する必要があります。 これを行わない場合、プロジェクトをビルドするときに、エラーが表示されます。  
  
 次のステップでは、セットアップ プロジェクトを構成する方法を示します。  
  
> [!IMPORTANT]
>  セットアップ プロジェクトを構成する前に、分離シェル プロジェクトのリリースの構成は、少なくとも 1 回の作成したことを確認します。  
  
#### セットアップ プロジェクトを構成するには  
  
1.  **ソリューション エクスプ ローラー**, 下で、 **MySetup** プロジェクト **プロジェクト アシスタント**します。 下の行に、 **プロジェクト アシスタント** ウィンドウで、選択 **アプリケーション情報**します。 入力 **Fabrikam** として、会社名と **Fabrikam 音楽エディター** アプリケーション名として。 右下にある右向きの矢印を選択して、 **プロジェクト アシスタント**します。  
  
2.  選択 **\[はい\]** \[ **、アプリケーションがコンピューターにインストールするソフトウェアに必要ですか?** し、\[ **Microsoft .NET Framework 4.5 のフル パッケージ**します。  
  
3.  選択、 **アプリケーション ファイル** 、ウィンドウの下部にあるボタンをクリックし、ことを確認して、 **Fabrikam 音楽エディター** フォルダーを選択します。  
  
4.  選択、 **ファイルの追加** \] ボタンをクリックします。**ファイルの追加** \] ダイアログ ボックスで、次のファイルを追加、 **MyVSShellStub\\Release** フォルダー。  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  クリックして、 **Add Project Outputs** ボタンをクリックし、追加 **MyVSShellStub\/プライマリ出力**します。**\[OK\]** をクリックします。  
  
6.  左側のウィンドウで \[ **セットアップ先のコンピューター**, を右クリックし、 **Fabrikam 音楽エディター \[INSTALLDIR\]** ノードを追加し、 **新しいフォルダー** という名前 **拡張機能**します。  
  
7.  右クリックし、 **拡張** 左側のウィンドウでノードという名前の新しいフォルダーに追加して **アプリケーション**します。  
  
8.  選択、 **アプリケーション** フォルダーをクリック、 **Add Project Outputs** \] ボタンをクリックし、MyVSShellStub.AboutBoxPackage プロジェクトからのプライマリ出力を選択します。  
  
9. クリックして、 **ファイルの追加** ボタンをクリックし、\\MyVSShellStub\\Release\\Extensions\\Application\\ フォルダーから次のファイルを追加します。  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. 右クリックし、 **Fabrikam 音楽エディター \[INSTALLDIR\]** 左側のウィンドウでノードという名前の新しいフォルダーに追加して **1033年**します。  
  
11. 1033 フォルダーを選択し、クリックして、 **Add Project Outputs** ボタンをクリックし、MyVSShellStubUI プロジェクトからのプライマリ出力を選択します。  
  
12. 移動、 **アプリケーション ショートカット** ウィンドウです。  
  
13. クリックして **新規** ショートカットを作成して **\[ProgramFilesFolder\] \\Fabrikam\\Fabrikam Music Editor\\MyVSShellStub.Primary Output**します。  
  
14. 移動、 **インストール要件** ウィンドウです。  
  
15. すべての項目を設定 **いいえ**します。  
  
16. **ソリューション エクスプ ローラー**, 、MySetup プロジェクトで開きます **Define Setup Requirements and アクション \\ 要件**します。**要件** ウィンドウが開きます。  
  
17. 右クリックして **システム ソフトウェアの要件** 選択 **新しい起動条件の作成**します。**システム検索ウィザード** が表示されます。  
  
18. **検索をクリックしてくださいですか?** \] ウィンドウで、選択 **レジストリ エントリ** ドロップダウン リストをクリック **次**します。  
  
19. **検索する方法ですか?** \] ウィンドウの \[ **HKEY\_LOCAL\_MACHINE** レジストリ ルートとして。 入力 **SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** 64 ビット システム用または **SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** 32 ビット システムでは、入力と **インストール** レジストリ値として。**\[次へ\]** をクリックします。  
  
20. **、値をクリックしてくださいですか?** \] ウィンドウで、入力 **この製品は、Visual Studio 2015 分離 Shell 再頒布可能パッケージをインストールする必要があります。** として表示するテキスト、\] をクリックします **\[完了\]**します。  
  
21. セットアップ プロジェクトを作成する分離シェル ソリューションをリビルドします。  
  
     次のフォルダーには、setup.exe ファイルがあります。  
  
     \\MyVSShellStub\\MySetup\\MySetup\\Express\\SingleImage\\DiskImages\\DISK1  
  
## インストール プログラムのテスト  
 設定をテストするには、setup.exe ファイルを別のコンピューターにコピーし、セットアップの実行可能ファイルを実行します。 分離シェル アプリケーションを実行することができます。