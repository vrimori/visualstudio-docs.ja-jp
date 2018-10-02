---
title: 'チュートリアル: 基本的な作成分離シェル アプリケーション |Microsoft Docs'
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
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68b4fb6f7bb07cbb25d2fa8552e92875c5c242bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545796"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>チュートリアル: 基本的な分離シェル アプリケーションの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[チュートリアル: 基本的な分離シェル アプリケーションを作成する](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-creating-a-basic-isolated-shell-application)します。  
  
このチュートリアルでは、分離シェルのソリューションを作成し、バージョン情報 ツール ウィンドウをカスタマイズして、分離シェルをインストールするセットアップ プログラムを作成する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。 分離シェルを展開するには、Visual Studio Shell (Isolated) 再頒布可能パッケージを使用することも必要があります。  
  
## <a name="creating-an-isolated-shell-solution"></a>分離シェルのソリューションの作成  
 このセクションでは、Visual Studio 分離シェル プロジェクト テンプレートを使用して、分離シェルのソリューションを作成する方法を示します。 ソリューションには、次のプロジェクトが含まれています。  
  
-   *SolutionName*します。AboutBoxPackage プロジェクトのヘルプ/バージョン情報ボックスの外観をカスタマイズすることができます。  
  
-   ShellExtensionsVSIX プロジェクト、分離シェル アプリケーションのさまざまなコンポーネントを定義する source.extension.vsixmanifest ファイルが含まれています。  
  
-   *SolutionName*プロジェクトで、分離シェル アプリケーションを呼び出す実行可能ファイルが生成されます。 このプロジェクトには、分離シェル アプリケーションの動作と外観をカスタマイズすることにより、シェルのカスタマイズのフォルダーが含まれています。  
  
-   *SolutionName* UI プロジェクトは、アクティブなメニュー コマンドとローカライズ可能な文字列を定義するサテライト アセンブリを生成します。  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>基本的な分離シェルのソリューションを作成するには  
  
1.  Visual Studio を起動し、新しいプロジェクトを作成します。  
  
2.  **新しいプロジェクト**ウィンドウで、展開**その他のプロジェクトの種類**し**Extensibility**します。 選択、 **Visual Studio 分離シェル**プロジェクト テンプレート。  
  
3.  プロジェクトに名前を`MyVSShellStub`場所を指定します。 確認します**ソリューションのディレクトリを作成**がチェックされ、クリックして**OK**します。  
  
     新しいソリューションが表示されます。**ソリューション エクスプ ローラー**します。  
  
4.  ソリューションをビルドし、分離シェル アプリケーションのデバッグを開始します。  
  
     Visual Studio 分離シェルが表示されます。 タイトル バーを読み取り**MyVSShellStub**します。 タイトル バーのアイコンは、\MyVSShellStub\Resource Files\ApplicationIcon.ico から生成されます。  
  
## <a name="customizing-the-application-name-and-icon"></a>アプリケーション名とアイコンをカスタマイズします。  
 タイトル バーで、会社とそのロゴの名前を使用して、アプリケーションをブランド化することがあります。 次の手順では、MyVSShellStub.Application.pkgdef、パッケージ定義ファイルを変更することで、カスタム アプリケーションのタイトル バーに表示されるアイコンと名前を変更する方法を紹介します。  
  
#### <a name="to-customize-the-application-name-and-icon"></a>アプリケーション名とアイコンをカスタマイズするには  
  
1.  MyVSShellStub プロジェクトでは、\Shell Customization\MyVSShellStub.Application.pkgdef を開きます。  
  
2.  変更、`AppName`要素の値 **"AppName"=「Fabrikam 音楽エディター」**  
  
3.  アプリケーション アイコンを変更するには、別のアイコンを \MyVSShellStub\MyVSShellStub\MyVSShellStub\ ディレクトリにコピーします。 ApplicationIcon1.ico に ApplicationIcon.ico の既存のファイルの名前を変更します。 ApplicationIcon.ico に新しいファイルの名前を変更します。  
  
4.  ソリューションをビルドし、デバッグを開始します。 分離シェル IDE が表示されます。 タイトル バーが、単語の横にある新しいアイコン**Fabrikam 音楽エディター**します。  
  
## <a name="customizing-the-default-web-browser-home-page"></a>既定の Web ブラウザーのホーム ページをカスタマイズします。  
 このセクションの既定のホーム ページを変更する方法を示しています、 **Web ブラウザー**パッケージ定義ファイルを変更することによってウィンドウ。  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>既定の Web ブラウザーのホーム ページをカスタマイズするには  
  
1.  MyVSShellStub.Application.pkgdef ファイルで、変更、`DefaultHomePage`要素の値"http://www.microsoft.com"。  
  
2.  MyVSShellStub プロジェクトをリビルドします。  
  
3.  ソリューションをビルドし、デバッグを開始します。  
  
4.  **ビュー/その他の Windows**、 をクリックして**Web ブラウザー**します。 **Web ブラウザー**ウィンドウには、Microsoft Corporation のホーム ページが表示されます。  
  
## <a name="removing-the-print-command"></a>印刷コマンドを削除します。  
 分離シェルの UI プロジェクトで .vsct ファイル形式の宣言のセットから構成`<Define name=No_`*要素*`>`ここで、*要素*は標準の Visual Studio メニューのいずれかとコマンド。  
  
 宣言がコメント付きでない場合、そのメニューまたはコマンドは、分離シェルから除外されます。 逆に、宣言がコメントされている場合、分離シェルのメニューまたはコマンドが含まれます。  
  
 次の手順では、.vsct ファイルで、印刷コマンドをコメント解除します。  
  
#### <a name="to-remove-the-print-command"></a>印刷コマンドを削除するには  
  
1.  いることを確認、**印刷**コマンドに表示される、**ファイル**分離シェル アプリケーションのメニュー。  
  
2.  MyVSShellStubUI プロジェクトで編集するための \Resource Files\MyVSShellStubUI.vsct を開きます。  
  
3.  この行をコメント解除します。  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  これには、印刷コマンドが削除されます。  
  
5.  分離シェル アプリケーションのデバッグを開始します。 いることを確認、**ファイル/印刷**コマンドはなくなっています。  
  
## <a name="removing-features-from-the-isolated-shell"></a>分離シェルから機能の削除  
 Visual Studio で、カスタムの分離シェル アプリケーションでこれらの機能を設定したくない場合は、.pkgundef ファイルを編集することによって読み込まれるパッケージの一部を削除できます。 $RootKey$ \Packages レジストリ キーのサブキーのいずれかでは、パッケージを指定します。  
  
> [!NOTE]
>  Visual Studio の Guid の機能を検索するには、次を参照してください。[パッケージ Guid の Visual Studio 機能](../extensibility/package-guids-of-visual-studio-features.md)します。  
  
 次の手順では、分離シェルから、エディター、XML を削除する方法を示します。  
  
#### <a name="to-remove-the-xml-editor"></a>XML エディターを削除するには  
  
1.  MyVSShellStub プロジェクトのシェルのカスタマイズのフォルダーに MyVSShellStub.pkgundef ファイルを開きます。  
  
2.  次の行をコメント解除します。  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  ソリューションをリビルドし、分離シェルのデバッグを開始します。 たとえば、\MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct、XML ファイルを開きます。 ファイル内の XML のキーワードの色づけされたいないことを確認し、その入力"<"行にも表示されません XML ツールヒント。  
  
## <a name="customizing-the-helpabout-box"></a>ヘルプのカスタマイズ]、[バージョン情報ボックス  
 ヘルプをカスタマイズする/バージョン情報ボックス、これは、分離シェル プロジェクト テンプレートの一部として作成されます。  
  
#### <a name="to-customize-the-company-name"></a>会社名をカスタマイズするには  
  
1.  \Properties\AssemblyInfo.cs ファイルで、MyVSShellStub.AboutBoxPackage プロジェクトで、会社名、著作権情報、製品バージョン、および製品の説明が見つかりました。 このファイルを開きます。  
  
2.  変更、`AssemblyCompany`値を**Fabrikam**、`AssemblyProduct`と`AssemblyTitle`値を**Fabrikam 音楽エディター**、および`AssemblyCopyright`値を**Copyright ©Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  製品の説明を追加するには、変更、`AssemblyDescription`値を**Fabrikam 音楽エディターの説明**:。  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  デバッグを開始し、分離シェル アプリケーションで開きます、**ヘルプ/約**ボックス。 変更された文字列が表示されます。 ヘルプ/バージョン情報ボックスのタイトルは同じ、 `AssemblyTitle` AssemblyInfo.cs 内の値。  
  
5.  プロパティ、**ヘルプ/について**ボックス自体が MyVSShellStub.AboutBoxPackage\AboutBox.xaml ファイルが見つかりません。 ヘルプ/バージョン情報ボックスの幅を変更するには、`AboutDialogStyle`をブロックし、設定、 `Width` 200 プロパティ。  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  ソリューションをリビルドし、分離シェルのデバッグを開始します。 ヘルプ/バージョン情報ボックスを約正方形にする必要があります。  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>分離シェル アプリケーションを展開する前に  
 分離シェル アプリケーションは、Visual Studio Shell (Isolated) 再頒布可能パッケージをされているコンピューターにインストールできます。 再頒布可能パッケージの詳細については、次を参照してください。、 [Visual Studio 機能拡張ダウンロード](http://go.microsoft.com/fwlink/?LinkID=119298)web サイト。  
  
## <a name="deploying-the-isolated-shell-application"></a>分離シェル アプリケーションを展開します。  
 対象のコンピュータに、分離シェル アプリケーションを展開するには、セットアップ プロジェクトを作成します。 これらの操作を指定する必要があります。  
  
-   ターゲット コンピューター上のフォルダーおよびファイル レイアウト。  
  
-   .NET Framework と Visual Studio シェルのランタイムを保証する起動条件は、ターゲット コンピューターにインストールされます。  
  
 次の手順では、InstallShield Limited Edition をコンピューターにインストールする必要があります。  
  
#### <a name="to-create-the-setup-project"></a>セットアップ プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**ソリューション ノードを右クリックし、クリックして**新しいプロジェクトの追加**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開**その他のプロジェクトの種類**選び**セットアップと配置**。 InstallShield のテンプレートを選択します。 新しいプロジェクトの名前`MySetup` をクリックし、 **OK**します。  
  
3.  InstallShield Limited Edition が既にインストールされている場合は、次の手順に進みます。  
  
     InstallShield Limited Edition が既にインストールされていない場合は、InstallShield のダウンロード ページが表示されます。 ダウンロードして Visual Studio のバージョンと互換性がある InstallShield のバージョンを選択、製品をインストールする手順を実行します。 InstallShield のインストールを登録または評価版として使用するかどうかを決定する必要があります。 インストールが完了した後は、Visual Studio を再起動する必要があります。  
  
    > [!IMPORTANT]
    >  InstallShield プロジェクトを作成する前に、管理者として Visual Studio を起動する必要があります。 これを行わない場合に、プロジェクトをビルドするときに、エラーが表示されます。  
  
 次の手順では、セットアップ プロジェクトを構成する方法を示します。  
  
> [!IMPORTANT]
>  セットアップ プロジェクトを構成する前に、分離シェル プロジェクトのリリースの構成は、少なくとも 1 回を構築したことを確認します。  
  
#### <a name="to-configure-the-setup-project"></a>セットアップ プロジェクトを構成するには  
  
1.  **ソリューション エクスプ ローラー**下で、 **MySetup**プロジェクトで、選択**プロジェクト アシスタント**します。 下の行に、**プロジェクト アシスタント**ウィンドウで、選択**アプリケーション情報**します。 入力**Fabrikam**会社名としてと**Fabrikam 音楽エディター**として、アプリケーションの名前。 右下にある右向きの矢印を選択、**プロジェクト アシスタント**します。  
  
2.  選択**はい** **はアプリケーションに必要なソフトウェアをコンピューターにインストールするでしょうか。** し、 **Microsoft .NET Framework 4.5 のフル パッケージ**します。  
  
3.  選択、**アプリケーション ファイル**、ウィンドウの下部にあるボタンをクリックし、ことを確認、 **Fabrikam 音楽エディター**フォルダーを選択します。  
  
4.  選択、**ファイルの追加**ボタンをクリックします。 **ファイルの追加** ダイアログ ボックスで、次のファイルを追加、 **MyVSShellStub\Release**フォルダー。  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  をクリックして、 **Add Project Outputs**ボタンをクリックし、追加**MyVSShellStub/プライマリ出力**します。 **[OK]** をクリックします。  
  
6.  左側のウィンドウで **セットアップ先のコンピューター**を右クリックし、 **Fabrikam 音楽エディター [INSTALLDIR]** ノードを追加し、**新しいフォルダー**という名前の**拡張機能**.  
  
7.  右クリックし、**拡張**左側のウィンドウでノードという名前の新しいフォルダーを追加および**アプリケーション**します。  
  
8.  選択、**アプリケーション**フォルダーをクリックして、 **Add Project Outputs**ボタンをクリックし、MyVSShellStub.AboutBoxPackage プロジェクトからのプライマリ出力を選択します。  
  
9. をクリックして、**ファイルの追加**ボタンをクリックし、\MyVSShellStub\Release\Extensions\Application\ フォルダーから、次のファイルを追加します。  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. 右クリックし、 **Fabrikam 音楽エディター [INSTALLDIR]** 左側のウィンドウでノードという名前の新しいフォルダーを追加および**1033**します。  
  
11. 1033 フォルダーを選択し、クリックして、 **Add Project Outputs**ボタンをクリックし、MyVSShellStubUI プロジェクトからのプライマリ出力を選択します。  
  
12. 移動、**アプリケーション ショートカット**ウィンドウ。  
  
13. クリックして**新規**ショートカットを作成し、選択する **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**します。  
  
14. 移動、**インストール インタビュー**ウィンドウ。  
  
15. すべての項目を設定**いいえ**します。  
  
16. **ソリューション エクスプ ローラー**、MySetup プロジェクトで開きます**Define Setup Requirements and アクション \ 要件**します。 **要件**ウィンドウが開きます。  
  
17. 右クリックして**システム ソフトウェアの要件**選択**新しい起動条件の作成**です。 **システム検索ウィザード**が表示されます。  
  
18. **内容を検索するでしょうか。** ウィンドウで、選択**レジストリ エントリ**ドロップダウン リストをクリックします**次**。  
  
19. **検索する方法でしょうか。** ペインで、 **HKEY_LOCAL_MACHINE**としてレジストリ ルート。 入力**SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 64 ビット システム用または**SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 32 ビット システムでは、を入力します。**インストール**レジストリ値として。 **[次へ]** をクリックします。  
  
20. **内容と、値は?** ウィンドウで、入力**この製品は、Visual Studio 2015 分離シェル再頒布可能パッケージをインストールする必要があります。** 表示テキストをクリックします**完了**します。  
  
21. セットアップ プロジェクトを作成する分離シェルのソリューションを再構築します。  
  
     次のフォルダーには、setup.exe ファイルがあります。  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>インストール プログラムをテストします。  
 セットアップをテストするには、別のコンピューターに、setup.exe ファイルをコピーし、セットアップ実行可能ファイルを実行します。 分離シェル アプリケーションを実行する必要があります。

