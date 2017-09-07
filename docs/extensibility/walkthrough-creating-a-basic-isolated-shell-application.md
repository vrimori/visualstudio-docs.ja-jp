---
title: "チュートリアル: 基本的な作成分離シェル アプリケーション |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
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
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e007e366847ac42d3916b16cbde190e8fd755821
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>チュートリアル: 基本的な分離シェル アプリケーションの作成
このチュートリアルでは、分離シェルのソリューションの作成、バージョン情報 ツール ウィンドウをカスタマイズおよび分離シェルをインストールするセットアップ プログラムを作成する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。 分離シェルを展開するには、また Visual Studio Shell (Isolated) 再頒布可能パッケージを使用する必要があります。  
  
## <a name="creating-an-isolated-shell-solution"></a>Isolated Shell ソリューションを作成します。  
 このセクションでは、Visual Studio 分離シェルのプロジェクト テンプレートを使用して分離シェル ソリューションを作成する方法を示します。 ソリューションには、次のプロジェクトが含まれています。  
  
-   *SolutionName*です。AboutBoxPackage プロジェクトのヘルプ/バージョン情報ボックスの外観をカスタマイズすることができます。  
  
-   分離シェル アプリケーションのさまざまなコンポーネントを定義する source.extension.vsixmanifest ファイルを含む ShellExtensionsVSIX プロジェクト。  
  
-   *SolutionName*プロジェクトは、分離シェル アプリケーションを呼び出す実行可能ファイルが生成されます。 このプロジェクトには、これにより、分離シェル アプリケーションの動作と外観をカスタマイズすると、シェルのカスタマイズ フォルダーが含まれています。  
  
-   *SolutionName* UI プロジェクトは、アクティブなメニュー コマンドとローカライズ可能な文字列を定義するサテライト アセンブリを生成します。  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>基本的な分離シェル ソリューションを作成するには  
  
1.  Visual Studio を起動し、新しいプロジェクトを作成します。  
  
2.  **新しいプロジェクト**ウィンドウで、展開**その他のプロジェクトの種類**し**Extensibility**です。 選択、 **Visual Studio 分離シェル**プロジェクト テンプレート。  
  
3.  プロジェクトに名前を`MyVSShellStub`場所を指定します。 確認して**ソリューションのディレクトリを作成**が確認され、をクリックして**OK**です。  
  
     新しいソリューションが表示される**ソリューション エクスプ ローラー**です。  
  
4.  ソリューションをビルドし、分離シェル アプリケーションのデバッグを開始します。  
  
     Visual Studio 分離シェルが表示されます。 タイトル バーを読み取ります**MyVSShellStub**です。 タイトル バーのアイコンは、\MyVSShellStub\Resource Files\ApplicationIcon.ico から生成されます。  
  
## <a name="customizing-the-application-name-and-icon"></a>アプリケーション名とアイコンのカスタマイズ  
 タイトル バーに、会社とそのロゴの名前を使用して、アプリケーションをブランド化することがあります。 次の手順では、名前と、パッケージ定義ファイル、MyVSShellStub.Application.pkgdef を変更することによってカスタム アプリケーションのタイトル バーに表示されるアイコンを変更する方法を示します。  
  
#### <a name="to-customize-the-application-name-and-icon"></a>アプリケーション名とアイコンをカスタマイズするには  
  
1.  プロジェクトで、MyVSShellStub \Shell Customization\MyVSShellStub.Application.pkgdef を開きます。  
  
2.  変更、`AppName`要素の値**"AppName"=「Fabrikam 音楽エディター」**  
  
3.  アプリケーション アイコンを変更するには、別のアイコンを \MyVSShellStub\MyVSShellStub\MyVSShellStub\ ディレクトリにコピーします。 ApplicationIcon1.ico に既存の ApplicationIcon.ico ファイルの名前を変更します。 ApplicationIcon.ico に新しいファイルの名前を変更します。  
  
4.  ソリューションをビルドし、デバッグを開始します。 Isolated shell IDE に表示されます。 タイトル バーは、単語の横にある新しいアイコン**Fabrikam 音楽エディター**です。  
  
## <a name="customizing-the-default-web-browser-home-page"></a>既定の Web ブラウザーのホーム ページをカスタマイズします。  
 このセクションでは、既定のホーム ページを変更する方法を示します、 **Web ブラウザー**ウィンドウでは、パッケージ定義ファイルを変更します。  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>既定の Web ブラウザーのホーム ページをカスタマイズするには  
  
1.  MyVSShellStub.Application.pkgdef ファイルで、変更、 `DefaultHomePage` "http://www.microsoft.com"要素の値。  
  
2.  MyVSShellStub プロジェクトをリビルドします。  
  
3.  ソリューションをビルドし、デバッグを開始します。  
  
4.  **ビュー/その他のウィンドウ**をクリックして**Web ブラウザー**です。 **Web ブラウザー**ウィンドウには、米国 Microsoft Corporation のホーム ページが表示されます。  
  
## <a name="removing-the-print-command"></a>印刷コマンドを削除します。  
 分離シェル UI プロジェクトで .vsct ファイル形式の宣言のセットから成る`<Define name=No_`*要素*`>`ここで、*要素*は標準の Visual Studio メニューとコマンドのいずれか。  
  
 宣言がコメント付きでない場合、該当するメニューやコマンドは、分離シェルから除外されます。 逆に、宣言がコメントされている場合、分離シェルでメニューまたはコマンドが含まれます。  
  
 次の手順では、印刷コマンドをコメントから .vsct ファイルでします。  
  
#### <a name="to-remove-the-print-command"></a>印刷コマンドを削除するには  
  
1.  いることを確認、**印刷**コマンドに表示される、**ファイル**分離シェル アプリケーションのメニュー。  
  
2.  MyVSShellStubUI プロジェクトでは、編集するための \Resource Files\MyVSShellStubUI.vsct を開きます。  
  
3.  この行のコメントを解除します。  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  これには、印刷コマンドを削除します。  
  
5.  分離シェル アプリケーションのデバッグを開始します。 いることを確認、**ファイル]/[印刷**コマンドが消えます。  
  
## <a name="removing-features-from-the-isolated-shell"></a>分離シェルから機能の削除  
 一部のカスタム分離シェル アプリケーションでこれらの機能を設定したくない場合、.pkgundef ファイルを編集することによって Visual Studio に読み込まれているパッケージを削除することができます。 $RootKey$ \Packages レジストリ キーのサブキーのいずれかでは、パッケージを指定します。  
  
> [!NOTE]
>  Visual Studio の Guid の機能を検索するには、次を参照してください。[パッケージ Guid の Visual Studio の機能](../extensibility/package-guids-of-visual-studio-features.md)します。  
  
 次の手順では、分離シェルからエディター、XML を削除する方法を示します。  
  
#### <a name="to-remove-the-xml-editor"></a>XML エディターを削除するには  
  
1.  シェルのカスタマイズ プロジェクトのフォルダーに、MyVSShellStub MyVSShellStub.pkgundef ファイルを開きます。  
  
2.  次の行のコメントを解除します。  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  ソリューションをリビルドし、分離シェルのデバッグを開始します。 たとえば、\MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct、XML ファイルを開きます。 ファイル内の XML キーワードの色分け表示されましていないことを確認し、その入力"<"行にも表示されません XML のツールヒント。  
  
## <a name="customizing-the-helpabout-box"></a>カスタマイズのヘルプ/バージョン情報ボックス  
 ヘルプをカスタマイズすることができます/バージョン情報ボックス、分離シェル プロジェクト テンプレートの一部として作成するがします。  
  
#### <a name="to-customize-the-company-name"></a>会社名をカスタマイズするには  
  
1.  会社名、著作権情報、製品バージョン、および製品の説明は MyVSShellStub.AboutBoxPackage プロジェクト \Properties\AssemblyInfo.cs ファイルにあります。 このファイルを開きます。  
  
2.  変更、`AssemblyCompany`値を**Fabrikam**、`AssemblyProduct`と`AssemblyTitle`値**Fabrikam 音楽エディター**、および`AssemblyCopyright`値を**2015 Copyright © Fabrikam**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")]  
    ```  
  
3.  製品の説明を追加するには、変更、`AssemblyDescription`値**Fabrikam 音楽エディターの説明**:。  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.")]  
    ```  
  
4.  デバッグを開始して、分離シェル アプリケーションで開いて、**ヘルプ/約**ボックス。 変更された文字列が表示されます。 ヘルプ/バージョン情報ボックスのタイトルと同じ、 `AssemblyTitle` AssemblyInfo.cs 内の値。  
  
5.  プロパティ、**ヘルプ/に関する**ボックス自体が MyVSShellStub.AboutBoxPackage\AboutBox.xaml ファイルに見つかりました。 ヘルプ/バージョン情報ボックスの幅を変更するには、`AboutDialogStyle`をブロックし、設定、`Width`を 200 プロパティ。  
  
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
 分離シェル アプリケーションは、Visual Studio Shell (Isolated) 再頒布可能パッケージを持っている任意のコンピューターにインストールできます。 再頒布可能パッケージの詳細については、次を参照してください。、 [Visual Studio 拡張機能のダウンロード](http://go.microsoft.com/fwlink/?LinkID=119298)web サイトです。  
  
## <a name="deploying-the-isolated-shell-application"></a>分離シェル アプリケーションを配置します。  
 対象のコンピュータに、分離シェル アプリケーションを展開するには、セットアップ プロジェクトを作成します。 これらの操作を指定する必要があります。  
  
-   ターゲット コンピューター上のファイルとフォルダーのレイアウトです。  
  
-   .NET Framework および Visual Studio シェルのランタイムを保証する起動条件は、ターゲット コンピューターにインストールされます。  
  
 次の手順では、InstallShield Limited Edition をお使いのコンピューターにインストールする必要があります。  
  
#### <a name="to-create-the-setup-project"></a>セットアップ プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**ソリューション ノードを右クリックし、クリックして**新しいプロジェクトの追加**です。  
  
2.  **新しいプロジェクト**] ダイアログ ボックスで、展開**その他のプロジェクトの種類**し、[**セットアップと配置**です。 InstallShield のテンプレートを選択します。 新しいプロジェクトの名前`MySetup` をクリックし、 **OK**です。  
  
3.  InstallShield Limited Edition が既にインストールされている場合は、次の手順に進みます。  
  
     InstallShield Limited Edition がインストールされていない場合は、InstallShield のダウンロード ページが表示されます。 ダウンロードして Visual Studio のバージョンと互換性がある InstallShield のバージョンを選択する製品をインストールする手順に従います。 InstallShield のインストールを登録または評価版として使用するかどうかを決定する必要があります。 インストールが完了した後には、Visual Studio を再起動する必要があります。  
  
    > [!IMPORTANT]
    >  InstallShield プロジェクトを作成する前に、管理者として Visual Studio を起動する必要があります。 これを行わない場合に、プロジェクトをビルドするときに、エラーが表示されます。  
  
 次の手順では、セットアップ プロジェクトを構成する方法を示します。  
  
> [!IMPORTANT]
>  セットアップ プロジェクトを構成する前に、分離シェル プロジェクトのリリースの構成は、少なくとも 1 回が組み込まれていることを確認してください。  
  
#### <a name="to-configure-the-setup-project"></a>セットアップ プロジェクトを構成するには  
  
1.  **ソリューション エクスプ ローラー**下で、 **MySetup**プロジェクト**プロジェクト アシスタント**です。 下の行に、**プロジェクト アシスタント**ウィンドウで、選択**アプリケーション情報**です。 入力**Fabrikam**として、会社名と**Fabrikam 音楽エディター**アプリケーション名として。 右下にある前方の矢印を選択して、**プロジェクト アシスタント**です。  
  
2.  選択**はい** **アプリケーションがコンピューターにインストールされているすべてのソフトウェアに必要ですか?**し、 **Microsoft .NET Framework 4.5 のフル パッケージ**です。  
  
3.  選択、**アプリケーション ファイル**、ウィンドウの下部にあるボタンをクリックし、ことを確認して、 **Fabrikam 音楽エディター**フォルダーを選択します。  
  
4.  選択、**ファイルの追加**ボタンをクリックします。 **ファイルの追加** ダイアログ ボックスから次のファイルを追加、 **MyVSShellStub\Release**フォルダー。  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  クリックして、 **Add Project Outputs**ボタンをクリックし、追加**MyVSShellStub/プライマリ出力**です。 **[OK]** をクリックします。  
  
6.  左側のウィンドウで **展開先コンピューター**を右クリックし、 **Fabrikam 音楽エディター [INSTALLDIR]**ノードを追加し、**新しいフォルダー**という名前**拡張機能**します。  
  
7.  右クリックし、**拡張**左側のウィンドウでノードという新しいフォルダーを追加および**アプリケーション**です。  
  
8.  選択、**アプリケーション**フォルダーをクリック、 **Add Project Outputs**ボタンをクリックし、MyVSShellStub.AboutBoxPackage プロジェクトからのプライマリ出力を選択します。  
  
9. クリックして、**ファイルの追加**ボタンをクリックし、\MyVSShellStub\Release\Extensions\Application\ フォルダーから、次のファイルを追加します。  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. 右クリックし、 **Fabrikam 音楽エディター [INSTALLDIR]**左側のウィンドウでノードという新しいフォルダーを追加および**1033**です。  
  
11. 1033 フォルダーを選択し、クリックして、 **Add Project Outputs**ボタンをクリックし、MyVSShellStubUI プロジェクトからのプライマリ出力を選択します。  
  
12. 移動、**アプリケーション ショートカット**ウィンドウです。  
  
13. をクリックして**新規**ショートカットを作成しを選択する**[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**です。  
  
14. 移動、**インストール面接**ウィンドウです。  
  
15. すべての項目を設定**いいえ**です。  
  
16. **ソリューション エクスプ ローラー**、MySetup プロジェクトで開きます**Define Setup Requirements and アクション \ 要件**です。 **要件**ウィンドウが開きます。  
  
17. 右クリックして**システム ソフトウェア要件**選択**新しい起動条件の作成**です。 **システム検索ウィザード**が表示されます。  
  
18. **たい項目を検索しますか?**  ウィンドウで、選択**レジストリ エントリ**クリックしてドロップダウン リストで**次へ**です。  
  
19. **検索する方法ですか?**ペインで、 **HKEY_LOCAL_MACHINE**レジストリ ルートとして。 入力**SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 64 ビット システムのまたは**SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** 32 ビット システムでは、入力と**インストール**レジストリ値として。 **[次へ]**をクリックします。  
  
20. **値を行うにはクリックしてください?**  ウィンドウで、入力**この製品が、Visual Studio 2015 分離シェル再頒布可能パッケージをインストールする必要があります。** 表示テキストとクリックとして**完了**です。  
  
21. セットアップ プロジェクトを作成する分離シェル ソリューションをリビルドします。  
  
     次のフォルダーに setup.exe ファイルをご覧ください。  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>インストール プログラムをテストします。  
 セットアップをテストするには、別のコンピューターに、setup.exe ファイルをコピーし、セットアップの実行可能ファイルを実行します。 分離シェル アプリケーションを実行することができます。
