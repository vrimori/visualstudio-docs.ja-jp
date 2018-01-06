---
title: "Visual Studio SDK 内 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e8b1374b6934e09bbf3ce1012d551dab2831292c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK の内部
このセクションでは、Visual Studio アーキテクチャ、コンポーネント、サービス、スキーマ、ユーティリティ、および、like をなど、Visual Studio 拡張機能に関する詳細情報を提供します。  
  
## <a name="extensibility-architecture"></a>拡張可能アーキテクチャ  
 次の図は、Visual Studio の拡張可能アーキテクチャを示します。 Vspackage では、サービスとして、IDE 全体で共有されるアプリケーションの機能を提供します。 標準的な IDE では、サービスの広範な範囲など<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>IDE の windowing 機能へのアクセスを提供します。  
  
 ![環境アーキテクチャ グラフィック](../../extensibility/internals/media/environment.gif "環境")  
Visual Studio アーキテクチャの汎用化されたビュー  
  
## <a name="vspackages"></a>VSPackages  
 VSPackage は、UI 要素、サービス、プロジェクト、エディター、およびデザイナーで Visual Studio を構成および拡張するソフトウェア モジュールです。 Vspackage は、Visual Studio のサーバーの全体アーキテクチャ単位です。 詳細については、次を参照してください。 [Vspackage](../../extensibility/internals/vspackages.md)です。  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Visual Studio シェルは、基本的な機能を提供し、そのコンポーネント Vspackage および MEF 拡張機能間の相互通信をサポートします。 詳細については、次を参照してください。 [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)です。  
  
## <a name="user-experience-guidelines"></a>ユーザー エクスペリエンス ガイドライン  
 Visual Studio の新機能の設計を計画している場合は、設計と操作性のヒントについては、次のガイドラインを確認を行う必要があります: [Visual Studio ユーザー エクスペリエンス ガイドライン](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)です。  
  
## <a name="commands"></a>コマンド  
 コマンドは、ドキュメントの印刷、ビューの更新、ファイルの新規作成などのタスクを実行する関数です。  
  
 Visual Studio を拡張する場合に、コマンドを作成され、Visual Studio シェルに登録します。 これらのコマンドがでどのように表示 IDE では、たとえば、メニューやツールバーを指定することができます。 通常にカスタム コマンドが表示されます、**ツール**で表示されるメニューのおよびツール ウィンドウを表示するためのコマンド、**その他のウィンドウ**のサブメニュー、**ビュー**メニュー。  
  
 コマンドを作成するときに、そのイベント ハンドラーを作成することも必要があります。 イベント ハンドラーは、ときにコマンドは、表示するか有効になっているテキストを変更することができ、コマンドをアクティブ化されたときに適切に応答することを保証を決定します。 ほとんどの場合、IDE 処理コマンドを使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。 Visual Studio でのコマンドは、以降、ローカルの選択に基づいており、グローバルの選択に基づいて最も外側のコンテキストを続行する、最も内側のコマンドのコンテキストで処理されます。 メイン メニューに追加したコマンドは、すぐにスクリプトに利用できます。  
  
 詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../../extensibility/internals/commands-menus-and-toolbars.md)です。  
  
## <a name="menus-and-toolbars"></a>メニューとツールバー  
 メニューとツールバーは、ユーザーがコマンドを呼び出す方法を提供します。 メニューは、通常、ツール ウィンドウ上部にある個々 のテキスト項目として表示されているコマンドの行または列がします。 サブメニューは、ユーザーが、小さい矢印を含むコマンドをクリックしたときに表示されるセカンダリ メニューです。 ユーザーが特定の UI 要素を右クリックすると、コンテキスト メニューが表示されます。 いくつかの一般的なメニュー名には**ファイル**、**編集**、**ビュー**、および**ウィンドウ**します。 詳細については、次を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)です。  
  
 ツールバーは、ボタンやコンボ ボックス、リスト ボックス、テキスト ボックスなど、他のコントロールの行または列です。 ツールバー ボタンに通常のフォルダー アイコンなどのアイコン画像がある、**ファイルを開く**コマンドまたは用のプリンター、**印刷**コマンド。 ツールバーのすべての要素は、コマンドに関連付けられます。 ツール バー ボタンをクリックすると、関連付けられているコマンドを実行します。 ドロップダウン コントロールの場合は、ドロップダウン リスト内の各項目は、異なるコマンドに関連付けられています。 Splitter コントロールなど、いくつかのツール バー コントロールは、組み合わせたものです。 コントロールの一方の側がツール バー ボタンと、相手側が下向きの矢印をクリックすると、いくつかのコマンドを表示します。  
  
## <a name="tool-windows"></a>ツール ウィンドウ  
 ツール ウィンドウは、情報を表示する、IDE で使用されます。 **ツールボックス**、**ソリューション エクスプ ローラー**、**プロパティ**ウィンドウ、および**Web ブラウザー**ツール ウィンドウの例を示します。  
  
 ツール ウィンドウは、通常、ユーザーが操作できるさまざまなコントロールを提供します。 インスタンス、**プロパティ**ウィンドウによりユーザーは特定の目的で使用されるオブジェクトのプロパティを設定できます。 **プロパティ**ウィンドウは、この点で特殊なも一般的なさまざまな状況で使用できるためです。 同様に、**出力**ウィンドウは、Visual Studio での多くのサブシステムを使用すると、Visual Studio ユーザーに出力を行うために使用できるため、一般的なテキスト ベースの出力を提供するために特殊化は。  
  
 Visual Studio は、いくつかのツール ウィンドウを含むは、次の図を検討してください。  
  
 ![スクリーン ショット](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 ツール ウィンドウの一部は、1 つのペインがソリューション エクスプ ローラー ツール ウィンドウを表示し、他のツール ウィンドウを非表示にタブをクリックして使用可能になりますにまとめてドッキングされます。 図は、他の 2 つのツール ウィンドウを示しています、**エラー一覧**と**出力**ウィンドウで、1 つのペインにまとめてドッキングします。  
  
 また、いくつかのエディター ウィンドウを表示するメイン ドキュメント ウィンドウも示します。 ツール ウィンドウは通常 1 つのインスタンスが (たとえば、1 つだけを開くことができます**ソリューション エクスプ ローラー**)、エディター ウィンドウが、個別のドキュメントの編集に使用されるそれぞれの複数インスタンスですべてのドッキングを持つことができます同じウィンドウです。 この図では 2 つのエディター ウィンドウ、フォームの 1 つのデザイナー ウィンドウとスタート ページがブラウザー ウィンドウを持つドキュメント ウィンドウを使用します。 [タブ] をクリックして、ドキュメント ウィンドウ内のすべてのウィンドウは使用できますが、EditorPane.cs ファイルを含む、エディター ウィンドウが表示され、アクティブなです。  
  
 Visual Studio を拡張する場合に、拡張子を持つ windows ユーザーが Visual Studio できる対話ツールを作成できます。 Visual Studio ユーザーがドキュメントを編集できる、独自のエディターを作成することもできます。 ツール ウィンドウおよびエディターは、Visual Studio に統合をプログラミングをドッキングするか、正しくタブに表示することはできません。 Visual Studio で正しく登録されているときに自動的には、一般的なツール ウィンドウと Visual Studio のドキュメント ウィンドウの機能。 詳細については、次を参照してください。[の拡張とツール ウィンドウのカスタマイズ](../../extensibility/extending-and-customizing-tool-windows.md)です。  
  
## <a name="document-windows"></a>ドキュメント ウィンドウ  
 ドキュメント ウィンドウは、マルチ ドキュメント インターフェイス (MDI) ウィンドウのフレームを使用した子ウィンドウです。 通常ドキュメント ウィンドウがテキスト エディター、フォーム エディター (デザイナーとも呼ばれます)、または編集コントロールをホストするため使用されますが、他の機能の種類をホストすることもできます。 **新しいファイル** ダイアログ ボックスには、Visual Studio で提供されるドキュメント ウィンドウの例が含まれています。  
  
 ほとんどのエディターは、プログラミング言語または HTML ページ、フレーム セット、C++ ファイル、またはヘッダー ファイルなどのファイルの種類に固有です。 テンプレートを選択して、**新しいファイル**ダイアログ ボックスで、ユーザーを動的に作成、ドキュメント ウィンドウ、テンプレートに関連付けられているファイルの種類のエディターのです。 ドキュメント ウィンドウには、既存のファイルを開く際にも作成されます。  
  
 ドキュメント ウィンドウは、MDI クライアント領域に制限されます。 各ドキュメント ウィンドウは、上部にタブを持つされ、タブ オーダーが MDI 領域で開いている可能性がある他のウィンドウにリンクされます。 ドキュメント ウィンドウのタブを右クリックすると、MDI 領域を複数の水平または垂直タブ グループに分割するオプションを含むショートカット メニューが表示されます。 MDI 領域を分割により、複数のファイルを同時に表示できます。 詳細については、次を参照してください。[ドキュメント ウィンドウ](../../extensibility/internals/document-windows.md)します。  
  
## <a name="editors"></a>エディター  
 Visual Studio エディターを使用すると、カスタマイズして、Managed Extensibility Framework (MEF) を使用してコンテンツの種類に使用できます。 多くの場合 (たとえば、メニュー コマンドまたはショートカット キー)、シェルの機能を含める場合は、VSPackage と MEF 拡張機能を組み合わせることができますが、エディターを拡張する VSPackage を作成する必要はありません。  
  
 データベースの読み書きをする場合、またはデザイナーを使用する場合などのカスタム エディターを作成することもできます。 メモ帳やワードパッドなど外部エディターを使用することもできます。 詳細については、次を参照してください。[エディターおよび言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)です。  
  
## <a name="language-services"></a>言語サービス  
 Visual Studio エディターで新しいプログラミング キーワードや新しいプログラミング言語もサポートする場合は、言語サービスを作成します。 各言語サービスは、完全に、一部、またはまったくない特定のエディターの機能を実装可能性があります。 構成方法に応じて、言語サービスは、構文の強調表示、かっこの照合、IntelliSense のサポート、およびエディターでその他の機能を提供できます。  
  
 言語サービスの中核は、パーサーおよびスキャナーです。 スキャナー (または lexer) がソース ファイルをトークンとして知られている要素に分割し、パーサーはこれらのトークンの間の関係を確立します。 言語サービスを作成するときにを Visual Studio は、トークンと言語の文法を理解できるように、パーサーとスキャナーを実装する必要があります。 マネージまたはアンマネージ言語サービスを作成することができます。 詳細については、次を参照してください。[レガシ言語サービスの機能拡張](../../extensibility/internals/legacy-language-service-extensibility.md)です。  
  
## <a name="projects"></a>プロジェクト  
 Visual Studio では、プロジェクトを整理し、ソース コードとその他のリソースを作成する開発者が使用できるコンテナーです。 プロジェクトの整理、ビルド、デバッグ、およびソース コードを配置することができます、Web サービスとデータベース、およびその他のリソースへの参照します。 Vspackage では、プロジェクトの種類、プロジェクトのサブタイプ、およびカスタム ツールを提供することによって、Visual Studio プロジェクト システムを拡張できます。  
  
 プロジェクトは、連携するアプリケーションを作成する 1 つまたは複数のプロジェクトのグループを含むソリューションにも収集できます。 ソリューションに関連するプロジェクトとステータスの情報は、2 つのソリューション ファイル、テキスト ベースのソリューション (.sln) ファイルおよびバイナリのソリューション ユーザー オプション (.suo) ファイルに格納されます。 これらのファイルは以前のバージョンので使用されていたグループ (.vbg) ファイルと同様に[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、し、ワークスペース (.dsw) とユーザーのオプション (.opt) ファイルの以前のバージョンで使用されていた[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]です。  
  
 詳細については、次を参照してください。[プロジェクト](../../extensibility/internals/projects.md)と[ソリューション](../../extensibility/internals/solutions.md)です。  
  
## <a name="project-and-item-templates"></a>プロジェクトと項目テンプレート  
 Visual Studio には、定義済みのプロジェクト テンプレートとプロジェクト項目テンプレートが含まれています。 また、独自のテンプレートを作成または、コミュニティからのテンプレートを取得し、Visual Studio に統合できます。 [MSDN コード ギャラリー](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio)テンプレートおよび拡張機能にアクセスする場所がします。  
  
 テンプレートには、プロジェクトの構造とアプリケーション、コントロール、ライブラリ、またはクラスの特定の種類を構築するために必要な基本的なファイルが含まれます。 テンプレートのいずれかのようなソフトウェアを開発する場合は、テンプレートに基づいているプロジェクトを作成し、そのプロジェクト内のファイルを変更します。  
  
> [!NOTE]
>  このテンプレートのアーキテクチャはサポートされていません[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクト。 作成する方法については[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクト テンプレートを参照してください[ウィザードのデザイン](/cpp/ide/designing-a-wizard)です。  
  
 詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)です。  
  
## <a name="properties-and-options"></a>プロパティとオプション  
 **プロパティ**ウィンドウが 1 つまたは複数選択した項目のプロパティを表示:[の拡張プロパティ](../../extensibility/internals/extending-properties.md)オプション ページがなど、特定のコンポーネントに関連するオプションのセットを含む、プログラミング言語または VSPackage:[オプションと [オプション] ページ](../../extensibility/internals/options-and-options-pages.md)です。 設定は、インポート、エクスポートされた通常の UI 関連の機能:[ユーザー設定のサポート](../../extensibility/internals/support-for-user-settings.md)です。  
  
## <a name="visual-studio-services"></a>Visual Studio サービス  
 サービスは、特定のコンポーネントを使用するインターフェイスのセットを提供します。 Visual Studio では、一連の拡張機能を含め、すべてのコンポーネントで使用できるサービスを提供します。 たとえば、Visual Studio services には、ツール ウィンドウを表示するか、ヘルプ、ステータス バー、または UI イベントへのアクセスを有効にする、動的に非表示が有効にします。 Visual Studio エディターには、エディターの拡張機能をインポートできるサービスも用意されています。 詳細については、次を参照してください。[を使用するとサービスを提供する](../../extensibility/using-and-providing-services.md)です。  
  
## <a name="debugger"></a>デバッガー  
 デバッガーは、言語固有のデバッグ コンポーネントをユーザー インターフェイスです。 新しい言語サービスを作成した場合に、デバッガーにフックするために特定のデバッグ エンジンを作成する必要があります。 詳細については、次を参照してください。 [Visual Studio デバッガーの機能拡張](../../extensibility/debugger/visual-studio-debugger-extensibility.md)です。  
  
## <a name="source-control"></a>ソース管理  
 ソース管理プラグインまたは VSPackage の実装方法の詳細については、次を参照してください。[ソース管理](../../extensibility/internals/source-control.md)です。  
  
## <a name="wizards"></a>ウィザード  
 組み合わせて、ウィザードを作成するには、新しいプロジェクトの種類と、その型の新しいプロジェクトを作成するときに、ユーザーが適切な意思決定を行う、ウィザードを使用できるようにします。 詳細については、次を参照してください。[ウィザード](../../extensibility/internals/wizards.md)です。  
  
## <a name="custom-tools"></a>カスタム ツール  
 カスタム ツールを使用すると、ツールをプロジェクト内の項目に関連付けるし、ファイルを保存するたびに、そのツールを実行できます。 詳細については、次を参照してください。[カスタム ツール](../../extensibility/internals/custom-tools.md)です。  
  
## <a name="vssdk-utilities"></a>VSSDK ユーティリティ  
 VSSDK には、Vspackage のさまざまな側面を操作するために必要な場合がありますユーティリティのセットが含まれています。 詳細については、次を参照してください。 [VSSDK ユーティリティ](../../extensibility/internals/vssdk-utilities.md)です。  
  
## <a name="using-windows-installer"></a>Windows インストーラーを使用します。  
 場合によっては、VSIX インストーラーではなく、Windows インストーラーを使用する必要があります。 たとえば、レジストリに書き込む必要があります。 Windows インストーラーを使用して、拡張機能と方法の詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../../extensibility/internals/installing-vspackages-with-windows-installer.md)です。  
  
## <a name="help-viewer"></a>ヘルプ ビューアー  
 ヘルプ ビューアーには、独自のヘルプおよび F1 ページを統合できます。 詳細については、次を参照してください。 [Microsoft ヘルプ ビューアー SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)です。