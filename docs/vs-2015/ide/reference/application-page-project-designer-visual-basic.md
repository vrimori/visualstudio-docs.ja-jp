---
title: '[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6dfd1d2c3d5c7467672e604ce4d7d6b9da449210
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540269"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[アプリケーション ページで、プロジェクト デザイナー (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)します。  
  
  
プロジェクト デザイナーの **[アプリケーション]** ページを使用して、プロジェクトのアプリケーション設定とプロパティを指定します。  
  
 **[アプリケーション]** ページにアクセスするには、**ソリューション エクスプローラー**のプロジェクト ノード (**[ソリューション]** ノードではありません) を選択します。 その後、メニュー バーで **[プロジェクト]**、**[プロパティ]** の順に選択します。 プロジェクト デザイナーが表示されたら、**[アプリケーション]** タブをクリックします。  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>アプリケーションの全般設定  
 次のオプションでは、アプリケーションの全般設定を構成できます。  
  
 **アセンブリ名**  
 アセンブリ マニフェストが含まれる出力ファイルの名前を指定します。 このプロパティを変更すると、**[出力名]** プロパティも変更されます。 コマンド プロンプトで [/out (Visual Basic)](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) を使用して変更することもできます。 プログラムを使用してこのプロパティにアクセスする方法については、「<xref:VSLangProj.ProjectProperties.AssemblyName%2A>」を参照してください。  
  
 **ルート名前空間**  
 プロジェクト内のすべてのファイルで使用する基本の名前空間を指定します。 たとえば、**[ルート名前空間]** を `Project1` に設定し、コード内のいずれの名前空間にも存在しない `Class1` がある場合、その名前空間は `Project1.Class1` になります。 また、コード内の名前空間 `Order` に `Class2` がある場合、その名前空間は `Project1.Order.Class2` になります。  
  
 **[ルート名前空間]** をクリアした場合は、コードにプロジェクトの名前空間の構造を指定できます。  
  
> [!NOTE]
>  [Namespace ステートメント](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2)で Global グローバル キーワードを使用する場合は、プロジェクトのルート名前空間以外の名前空間を定義できます。 **[ルート名前空間]** をクリアすると、`Global` は最上位レベルの名前空間になり、`Namespace` ステートメントの `Global` キーワードは不要になります。 詳細については、「[Visual Basic における名前空間](http://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88)」の「名前空間のステートメントでの Global キーワード」を参照してください。  
  
 コードで名前空間を作成する方法については、「[Namespace ステートメント](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2)」を参照してください。  
  
 ルート名前空間プロパティの詳細については、「[/rootnamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783)」を参照してください。  
  
 プログラムを使用してこのプロパティにアクセスする方法については、「<xref:VSLangProj.ProjectProperties.RootNamespace%2A>」を参照してください。  
  
 **ターゲット フレームワーク (すべての構成)**  
 アプリケーションが対象とする .NET Framework のバージョンを指定します。 このオプションの値は、コンピューター上にインストールされている .NET Framework のバージョンによって異なる場合があります。  
  
 既定値は、**[新しいプロジェクト]** ダイアログ ボックスで指定したターゲット フレームワークと一致します。  
  
> [!NOTE]
>  [[必須コンポーネント] ダイアログ ボックス](../../ide/reference/prerequisites-dialog-box.md)にリストされている必須コンポーネントのパッケージは、ダイアログ ボックスを初めて開いたときに自動的に設定されます。 その後、プロジェクトのターゲット フレームワークを変更した場合は、新しいターゲット フレームワークに合わせて必須コンポーネントを手動で指定する必要があります。  
  
 詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../../ide/how-to-target-a-version-of-the-dotnet-framework.md)」と「[Visual Studio のマルチ ターゲットの概要](../../ide/visual-studio-multi-targeting-overview.md)」を参照してください。  
  
 **アプリケーションの種類**  
 ビルドするアプリケーションの種類を指定します。 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] アプリの場合は、**[Windows ストア アプリ]**、**[クラス ライブラリ]**、または **[WinMD ファイル]** を指定できます。 他のほとんどのアプリケーションの種類では、**[Windows アプリケーション]**、**[コンソール アプリケーション]**、**[クラス ライブラリ]**、**[Windows サービス]**、または **[Web コントロール ライブラリ]** を指定できます。  
  
 Web アプリケーション プロジェクトでは、**[クラス ライブラリ]** を指定する必要があります。  
  
 **[WinMD ファイル]** オプションを指定した場合、種類を Windows ランタイムのプログラミング言語に射影できます。 WinMD ファイルとしてプロジェクトの出力をパッケージ化することで、複数の言語でアプリケーションをコード化し、すべて同じ言語で記述した場合と同様に、コードを相互運用することができます。 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] アプリを含む、Windows ランタイム ライブラリをターゲットとするソリューションに対して、**[WinMD ファイル]** オプションを使用できます。 詳細については、「[C# および Visual Basic での Windows ランタイム コンポーネントの作成](http://go.microsoft.com/fwlink/?LinkId=231895)」を参照してください。  
  
> [!NOTE]
>  Windows ランタイムでは、どの言語で使用される場合でも、ネイティブ オブジェクトとして表示されるように種類を射影できます。 たとえば、Windows ランタイムと対話する JavaScript アプリケーションでは JavaScript オブジェクト セットとして使用され、C# アプリケーションでは .NET オブジェクト コレクションとしてライブラリが使用されます。 WinMD ファイルとしてプロジェクトの出力をパッケージ化することで、Windows ランタイムで使用されるのと同じテクノロジを利用できます。  
  
 **[アプリケーションの種類]** プロパティの詳細については、「[/target (Visual Basic)](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c)」を参照してください。 プログラムを使用してこのプロパティにアクセスする方法については、「<xref:VSLangProj.ProjectProperties.OutputType%2A>」を参照してください。  
  
 **アイコン**  
 プログラム アイコンとして使用する .ico ファイルを設定します。 **[\<参照...>]** を選択して、既存のグラフィックを参照します。 詳細については、「[/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92)」 (または「[/win32icon (C# コンパイラ オプション)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138)」) を参照してください。 プログラムを使用してこのプロパティにアクセスする方法については、「<xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>」を参照してください。  
  
 **スタートアップ フォーム / スタートアップ オブジェクト / スタートアップ URI**  
 アプリケーションのスタートアップ フォームまたはエントリ ポイントを指定します。  
  
 **[アプリケーション フレームワークを有効にする]** が選択されている場合 (既定)、この一覧のタイトルは **[スタートアップ フォーム]** となり、フォームのみが表示されます。これは、アプリケーション フレームワークでは、オブジェクトではなく、スタートアップ フォームのみがサポートされるためです。  
  
 プロジェクトが WPF ブラウザー アプリケーションの場合、この一覧のタイトルは **[スタートアップ URI]** となり、既定値は **Page1.xaml** となります。 **[スタートアップ URI]** 一覧では、アプリケーションの起動時に表示されるユーザー インターフェイス リソース (XAML 要素) を指定できます。 詳細については、「<xref:System.Windows.Application.StartupUri%2A>」を参照してください。  
  
 **[アプリケーション フレームワークを有効にする]** の選択を解除すると、この一覧は **[スタートアップ オブジェクト]** になり、フォームと、`Sub Main` を含むクラスまたはモジュールの両方が表示されます。  
  
 **[スタートアップ オブジェクト]** では、アプリケーションの読み込み時に呼び出されるようにエントリ ポイントを定義します。 通常、これは、アプリケーションのメイン フォーム、またはアプリケーションの起動時に実行する必要がある `Sub Main` プロシージャに設定されます。 クラス ライブラリにはエントリ ポイントがないため、このプロパティのオプションのみが **[(なし)]** になります。 詳細については、「[/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0)」を参照してください。 プログラムを使用してこのプロパティにアクセスする方法については、「<xref:VSLangProj.ProjectProperties.StartupObject%2A>」を参照してください。  
  
 **アセンブリ情報**  
 このボタンをクリックすると、[[アセンブリ情報] ダイアログ ボックス](../../ide/reference/assembly-information-dialog-box.md)が表示されます。  
  
 **アプリケーション フレームワークを有効にする**  
 プロジェクトでアプリケーション フレームワークを使用するかどうかを指定します。 このオプションの設定は、**[スタートアップ フォーム]**/**[スタートアップ オブジェクト]** で使用できるオプションに影響します。  
  
 このチェック ボックスがオンになっている場合、アプリケーションでは標準の `Sub Main` が使用されます。 このチェック ボックスをオンにすると、**[Windows アプリケーション フレームワーク プロパティ]** セクションの機能が有効になります。その場合、スタートアップ フォームを選択する必要もあります。  
  
 このチェック ボックスをオフにすると、アプリケーションでは、**[スタートアップ フォーム]** で指定したカスタムの `Sub Main` が使用されます。 この場合、スタートアップ オブジェクト (メソッドまたはクラスのカスタム `Sub Main`) またはフォームを指定できます。 また、**[Windows アプリケーション フレームワーク プロパティ]** セクションのオプションが使用できなくなります。  
  
 **Windows 設定の表示**  
 このボタンをクリックすると、app.manifest ファイルが生成され、開きます。 Visual Studio ではこのファイルを使用して、アプリケーションのマニフェスト データを生成します。 その後、次のように、app.manifest の `<requestedExecutionLevel>` タグを変更し、UAC 要求実行レベルを設定します。  
  
 `<requestedExecutionLevel level="asInvoker" />`  
  
 ClickOnce は `asInvoker` のレベル、または仮想化モードで機能します (マニフェストは生成されません)。 仮想化モードを指定するには、app.manifest からタグ全体を削除します。  
  
 マニフェストの生成の詳細については、「[Windows Vista の ClickOnce 配置](../../deployment/clickonce-deployment-on-windows-vista.md)」を参照してください。  
  
## <a name="windows-application-framework-properties"></a>Windows アプリケーション フレームワーク プロパティ  
 次の設定は、**[Windows アプリケーション フレームワーク プロパティ]** セクションで使用できます。 これらのオプションは、**[アプリケーション フレームワークを有効にする]** チェック ボックスがオンになっている場合にのみ使用できます。 この後に続くセクションでは、Windows Presentation Foundation (WPF) アプリケーションの **Windows アプリケーション フレームワーク プロパティ**の設定について説明します。  
  
 **XP Visual スタイルを有効にする**  
 Windows XP Visual スタイル (*Windows XP テーマ*ともいう) を有効または無効にします。 Windows XP Visual スタイルを有効にすると、角が丸いコントロールや色が動的に切り替わるコントロールなどを使用できます。 既定ではオンです。 Windows XP Visual スタイルの詳細については、「[Windows XP の機能と Windows フォーム コントロール](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)」を参照してください。  
  
 **単一インスタンスのアプリケーションを作成する**  
 このチェック ボックスをオンにすると、ユーザーはアプリケーションの複数のインスタンスを実行できなくなります。 既定では、このチェック ボックスはオフになっています。 この設定により、アプリケーションの複数のインスタンスを実行できるようになります。  
  
 **シャットダウン時に My.Settings を保存する**  
 ユーザーがコンピューターをシャットダウンしたときにアプリケーションの `My.Settings` 設定が保存されるように指定する場合は、このチェック ボックスをオンにします。 この設定は既定で有効になります。 このオプションが無効になっている場合は、`My.Settings.Save` を呼び出して、アプリケーション設定を手動で保存できます。  
  
 **認証モード**  
 現在ログオンしているユーザーを識別するために Windows 認証を使用するように指定する場合は、**[Windows]** (既定) を選択します。 `My.User` オブジェクトを使用すれば、実行時にこの情報を取得することができます。 既定の Windows 認証方法を使用せずに、独自のコードを指定してユーザーを認証する場合は、**[アプリケーション定義]** を選択します。  
  
 **シャットダウン モード**  
 他のフォームが開いている場合でも、スタートアップ フォームとして設定されているフォームが閉じられたときにアプリケーションを終了するように指定する場合は、**[スタートアップ フォームが閉じるとき]** (既定) を選択します。 最後のフォームが閉じられたとき、または `My.Application.Exit` や `End` ステートメントが明示的に呼び出されたときにアプリケーションを終了するように指定する場合は、**[最後のフォームが閉じるとき]** を選択します。  
  
 `Shutdown` を明示的に呼び出したときにアプリケーションが終了するように指定する場合は、**[明示的にシャットダウンするとき]** を選択します。  
  
 最後のウィンドウが閉じられたとき、または `Shutdown` を明示的に呼び出したときにアプリケーションが終了するように指定する場合は、**[最後のウィンドウを閉じるとき]** を選択します。 これは、既定の設定です。  
  
 メイン ウィンドウが閉じられたとき、または `Shutdown` を明示的に呼び出したときにアプリケーションが終了するように指定する場合は、**[メイン ウィンドウを閉じるとき]** を選択します。  
  
 **スプラッシュ スクリーン**  
 スプラッシュ スクリーンとして使用するフォームを選択します。 フォームまたはテンプレートを使用して、事前にスプラッシュ スクリーンを作成しておく必要があります。 既定値は **[(なし)]** です。  
  
 **アプリケーション イベントの表示**  
 このボタンをクリックすると、イベント コード ファイルが表示され、アプリケーション フレームワーク イベント (`Startup`、`Shutdown`、`UnhandledException`、`StartupNextInstance` および `NetworkAvailabilityChanged`) に対してイベントを記述できます。 また、特定のアプリケーション フレームワーク メソッドをオーバーライドすることもできます。 たとえば、`OnInitialize` をオーバーライドして、スプラッシュ スクリーンの表示動作を変更することができます。  
  
### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Windows Presentation Foundation (WPF) アプリケーションの Windows アプリケーション フレームワーク プロパティ  
 プロジェクトが Windows Presentation Foundation アプリケーションである場合は、**Windows アプリケーション フレームワーク プロパティ**で以下の設定を使用できます。 これらのオプションは、**[アプリケーション フレームワークを有効にする]** チェック ボックスがオンになっている場合にのみ使用できます。 次の表にリストされているオプションは、WPF アプリケーションまたは WPF ブラウザー アプリケーションのみで使用できます。 WPF ユーザー コントロールやカスタム コントロール ライブラリでは使用できません。  
  
 **シャットダウン モード**  
 このプロパティは、Windows Presentation Foundation アプリケーションにのみ適用されます。  
  
 <xref:System.Windows.Application.Shutdown%2A> を明示的に呼び出したときにアプリケーションが終了するように指定する場合は、**[明示的にシャットダウンするとき]** を選択します。  
  
 最後のウィンドウが閉じられたとき、または <xref:System.Windows.Application.Shutdown%2A> を明示的に呼び出したときにアプリケーションが終了するように指定する場合は、**[最後のウィンドウを閉じるとき]** を選択します。 これは、既定の設定です。  
  
 メイン ウィンドウが閉じられたとき、または <xref:System.Windows.Application.Shutdown%2A> を明示的に呼び出したときにアプリケーションが終了するように指定する場合は、**[メイン ウィンドウを閉じるとき]** を選択します。  
  
 この設定の使用方法の詳細については、「<xref:System.Windows.Application.Shutdown%2A>」を参照してください。  
  
 **XAML の編集**  
 XAML エディターでアプリケーション定義ファイル (Application.xaml) を開き、変更する場合は、このボタンをクリックします。 このボタンをクリックすると、アプリケーション定義ノードに Application.xaml が開きます。 リソースの定義などの特定のタスクを実行するには、このファイルを編集する必要があります。 アプリケーション定義ファイルが存在しない場合、プロジェクト デザイナーで作成されます。  
  
 **アプリケーション イベントの表示**  
 コード エディターで `Application` の部分クラス ファイル (Application.xaml.vb) を表示する場合は、このボタンをクリックします。 ファイルが存在しない場合、プロジェクト デザイナーで、適切なクラス名と名前空間を使用して作成されます。  
  
 特定のアプリケーション状態が変化すると (アプリケーション スタートアップやシャットダウンなどで)、<xref:System.Windows.Application> オブジェクトでイベントが発生します。 このクラスで公開されるイベントの完全な一覧については、「<xref:System.Windows.Application>」を参照してください。 これらのイベントは、`Application` 部分クラスのユーザー コード セクションで処理されます。  
  
## <a name="see-also"></a>関連項目  
[アプリケーション プロパティの管理](../../ide/application-properties.md) [Office ソリューションのコードの記述](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)



