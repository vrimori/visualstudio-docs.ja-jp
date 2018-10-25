---
title: Visual Studio SDK の内部 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d22e5c1384e4b24bd3b05cb868a40cede19ba1f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214709"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK の内部
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ここでは、Visual Studio のアーキテクチャ、コンポーネント、サービス、スキーマ、ユーティリティ、およびなどを含む、Visual Studio 拡張機能に関する詳細な情報を示します。  
  
## <a name="extensibility-architecture"></a>機能拡張アーキテクチャ  
 次の図は、Visual Studio の拡張可能アーキテクチャを示します。 Vspackage では、サービスとして、IDE 全体で共有されているアプリケーションの機能を提供します。 標準的な IDE では、サービスの広範な範囲など<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>IDE のウィンドウ化機能へのアクセスを提供します。  
  
 ![環境アーキテクチャ グラフィック](../../extensibility/internals/media/environment.gif "環境")  
Visual Studio のアーキテクチャの汎用化されたビュー  
  
## <a name="vspackages"></a>VSPackages  
 VSPackage は、UI 要素、サービス、プロジェクト、エディター、およびデザイナーで Visual Studio を構成および拡張するソフトウェア モジュールです。 Vspackage は、Visual Studio のサーバーの全体アーキテクチャ単位です。 詳細については、「 [VSPackages](../../extensibility/internals/vspackages.md)」を参照してください。  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Visual Studio shell は、基本的な機能を提供し、そのコンポーネント Vspackage および MEF 拡張機能間の相互通信をサポートします。 詳細については、次を参照してください。 [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)します。  
  
## <a name="user-experience-guidelines"></a>ユーザー エクスペリエンス ガイドライン  
 Visual Studio の新機能の設計を計画している場合は、デザインと使いやすさのヒントについては、次のガイドラインを参照してくださいを行う必要があります: [Visual Studio ユーザー エクスペリエンス ガイドライン](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  
  
## <a name="commands"></a>コマンド  
 コマンドは、ドキュメントの印刷、ビューの更新、ファイルの新規作成などのタスクを実行する関数です。  
  
 Visual Studio を拡張するときは、コマンドを作成し、Visual Studio shell に登録します。 これらのコマンドでの表示方法、IDE では、たとえば、メニューまたはツールバーを指定することができます。 通常にカスタム コマンドが表示されます、**ツール**で表示されるメニューのおよびツール ウィンドウを表示するためのコマンド、**その他の Windows**のサブメニューで開く、**ビュー**メニュー。  
  
 コマンドを作成するときに、そのイベント ハンドラーを作成することも必要があります。 イベント ハンドラーは、ときにコマンドは、表示するか有効になっているテキストを変更することができ、コマンドをアクティブ化されるときに適切に応答することを保証を決定します。 ほとんどの場合、IDE を使用してコマンドを処理、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。 Visual Studio でのコマンドは、最も内側のコマンド コンテキスト、ローカルの選択に基づくし、グローバルの選択に基づいて、最も外側のコンテキストに進みます以降に処理されます。 メイン メニューに追加したコマンドは、すぐにスクリプトに利用できます。  
  
 詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
## <a name="menus-and-toolbars"></a>メニューおよびツールバー  
 メニューとツールバーは、ユーザーがコマンドを呼び出す方法を提供します。 メニューは、通常、ツール ウィンドウの上部にあるテキストの個々 の項目として表示されるコマンドの行または列です。 サブメニューは、ユーザーは、小さな矢印を含むコマンドをクリックしたときに表示されるセカンダリ メニューです。 ユーザーが特定の UI 要素を右クリックすると、コンテキスト メニューが表示されます。 いくつかの一般的なメニュー名には**ファイル**、**編集**、**ビュー**、および**ウィンドウ**します。 詳細については、次を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
 ツールバーは、ボタンとコンボ ボックス、リスト ボックス、テキスト ボックスなどの他のコントロールの行または列には。 ツール バー ボタンなどのフォルダーのアイコン、アイコンのイメージを通常がある、**ファイルを開く**コマンドまたは用のプリンターを**印刷**コマンド。 ツールバーのすべての要素は、コマンドに関連付けられます。 ツール バー ボタンをクリックすると、関連付けられているコマンドを実行します。 ドロップダウン コントロールでは、場合は、ドロップダウン リストの各項目は異なるコマンドに関連付けられています。 分割線コントロールなど、いくつかのツール バー コントロールでは、ハイブリッドです。 コントロールの 1 つの辺がツール バー ボタンと、もう一方の側が下向きの矢印がクリックされたときに、いくつかのコマンドを表示します。  
  
## <a name="tool-windows"></a>ツール ウィンドウ  
 ツール ウィンドウは、情報を表示する、IDE で使用されます。 **ツールボックス**、**ソリューション エクスプ ローラー**、**プロパティ**ウィンドウ、および**Web ブラウザー**ツール ウィンドウの例を示します。  
  
 ツール ウィンドウは、通常ユーザーが操作できるさまざまなコントロールを提供します。 たとえば、**プロパティ**ウィンドウでは、ユーザーが特定の目的で使用されるオブジェクトのプロパティを設定できます。 **プロパティ**ウィンドウは、この意味で特別ながも一般的なさまざまな状況で使用できるためです。 同様に、**出力**ウィンドウが Visual Studio での多くのサブシステムを使用すると、Visual Studio ユーザーに出力を提供する使用できますが、一般的なテキスト ベースの出力を提供するために特殊化されました。  
  
 いくつかのツール ウィンドウを含む、Visual Studio の次の図を検討してください。  
  
 ![スクリーン ショット](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 ツール ウィンドウの一部は、ソリューション エクスプ ローラー ツール ウィンドウを表示し、その他のツール ウィンドウを非表示がタブをクリックして利用できるように 1 つのペインにまとめてドッキングされます。 図は、その他の 2 つのツール ウィンドウを示しています、**エラー一覧**と**出力**ウィンドウで、1 つのペインにまとめてドッキングされます。  
  
 また、メイン ドキュメントのウィンドウでは、いくつかのエディター ウィンドウを示しています。 ツール ウィンドウは通常 1 つのインスタンスが (たとえば、いずれかのみを開くことができます**ソリューション エクスプ ローラー**)、エディター ウィンドウが、個別のドキュメントを編集するが使用されますですべてのドッキングの複数のインスタンスを持つことができます同じウィンドウ。 この図では 2 つのエディター ウィンドウ、1 つのフォーム デザイナー ウィンドウとスタート ページを表示するブラウザー ウィンドウを持つドキュメント ウィンドウを使用します。 ドキュメント ウィンドウで、すべての windows は、タブをクリックしてが EditorPane.cs ファイルを含むエディター ウィンドウが表示され、アクティブ。  
  
 Visual Studio を拡張すると、拡張機能で、ユーザーが Visual Studio windows を操作するツールを作成できます。 Visual Studio ユーザーがドキュメントを編集できる、独自のエディターを作成することもできます。 ツール ウィンドウおよびエディターは、Visual Studio に統合される予定であるために、ドッキングまたはタブに正しく表示することをプログラムする必要はありません。 Visual Studio で正しく登録されたときに、自動的にあるツール ウィンドウと Visual Studio のドキュメント ウィンドウの一般的な機能。 詳細については、次を参照してください。[拡張とカスタマイズ ツール Windows](../../extensibility/extending-and-customizing-tool-windows.md)します。  
  
## <a name="document-windows"></a>ドキュメント ウィンドウ  
 ドキュメント ウィンドウは、マルチ ドキュメント インターフェイス (MDI) ウィンドウのフレームの子ウィンドウです。 通常のドキュメント ウィンドウがテキスト エディター、フォーム エディター ([デザイナー] とも呼ばれます)、または編集コントロールをホストするため使用されますが、その他の機能の種類をホストすることもできます。 **新しいファイル** ダイアログ ボックスには、Visual Studio にはドキュメント ウィンドウの例が含まれています。  
  
 ほとんどのエディターは、プログラミング言語または HTML ページ、フレーム セット、C++ ファイルのヘッダー ファイルなどのファイルの種類に固有です。 テンプレートを選択して、**新しいファイル**ダイアログ ボックスで、ユーザーを動的に作成、ドキュメント ウィンドウ、テンプレートに関連付けられているファイルの種類のエディターの。 ドキュメント ウィンドウには、ユーザーが既存のファイルを開いたときにも作成されます。  
  
 ドキュメント ウィンドウは、MDI クライアント領域に制限されます。 各ドキュメント ウィンドウは、上部のタブを持つし、タブ オーダーが MDI 領域で開いている可能性がある他のウィンドウにリンクさせます。 ドキュメント ウィンドウのタブを右クリックして、MDI の領域を水平または垂直タブ グループを複数に分割するオプションを含むショートカット メニューが表示されます。 MDI 領域を分割により、複数のファイルを同時に表示できます。 詳細については、次を参照してください。[ドキュメント Windows](../../extensibility/internals/document-windows.md)します。  
  
## <a name="editors"></a>エディター  
 Visual Studio エディターでは、カスタマイズし、Managed Extensibility Framework (MEF) を使用して独自のコンテンツの種類を使用できます。 多くの場合は、(メニュー コマンドやショートカット キーなど)、シェルから機能を含める場合は、VSPackage を使用した、MEF 拡張機能を組み合わせることができますが、エディターを拡張するために VSPackage を作成する必要はありません。  
  
 読み取りし、書き込みデータベースにする場合、またはデザイナーを使用する場合、例のカスタム エディターを作成することもできます。 メモ帳やワードパッドなどの外部のエディターを使用することもできます。 詳細については、次を参照してください。[エディターと言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)します。  
  
## <a name="language-services"></a>言語サービス  
 新しいプログラミング キーワードまたはでも新しいプログラミング言語をサポートするために、Visual Studio エディターを設定する場合は、言語サービスを作成します。 各言語サービスは、完全に、一部、またはまったくない、特定のエディター機能を実装できます。 構成方法に応じて、言語サービスは、構文の強調表示、かっこの照合、IntelliSense のサポート、およびその他のエディターの機能を提供できます。  
  
 言語サービスの中核はパーサーとスキャナーです。 スキャナー (または字句解析器) は、トークンと呼ばれる要素にソース ファイルを分割し、パーサーは、それらのトークンの間の関係を確立します。 言語サービスを作成するときに、Visual Studio は、トークンと言語の文法を理解できるように、パーサーとスキャナーを実装する必要があります。 マネージまたはアンマネージ言語サービスを作成することができます。 詳細については、次を参照してください。[レガシ言語サービスの機能拡張](../../extensibility/internals/legacy-language-service-extensibility.md)します。  
  
## <a name="projects"></a>プロジェクト  
 Visual Studio では、プロジェクトは、開発者が整理し、ソース コードとその他のリソースの作成に使用するコンテナーです。 プロジェクトの整理、ビルド、デバッグ、およびソース コードを配置するように、Web サービスとデータベース、およびその他のリソースへの参照します。 Vspackage では、プロジェクトの種類、プロジェクト、サブタイプ、およびカスタム ツールを提供することで、Visual Studio プロジェクト システムを拡張できます。  
  
 プロジェクトは、ソリューション、連携してアプリケーションを作成する 1 つまたは複数のプロジェクトのグループ化にも収集できます。 ソリューションに関連するプロジェクトとステータスの情報は、2 つのソリューション ファイル、テキスト ベースのソリューション (.sln) ファイルおよびバイナリ ソリューション ユーザー オプション (.suo) ファイルに格納されます。 これらのファイルは以前のバージョンので使用されていたグループ (.vbg) ファイルと同様に[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]、し、ワークスペース (.dsw) とユーザーのオプション (.opt) ファイルの以前のバージョンで使用されていた[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]します。  
  
 詳細については、次を参照してください。[プロジェクト](../../extensibility/internals/projects.md)と[ソリューション](../../extensibility/internals/solutions.md)します。  
  
## <a name="project-and-item-templates"></a>プロジェクト テンプレートと項目テンプレート  
 Visual Studio には、定義済みのプロジェクト テンプレートとプロジェクト項目テンプレートが含まれています。 また、独自のテンプレートを作成または、コミュニティからのテンプレートを取得し、Visual Studio に統合できます。 [MSDN コード ギャラリー](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio)テンプレートおよび拡張機能にアクセスする場所です。  
  
 テンプレートには、プロジェクトの構造および特定の種類のアプリケーション、コントロール、ライブラリ、またはクラスを構築するために必要な基本的なファイルが含まれます。 テンプレートのいずれかのようなソフトウェアを開発する場合は、テンプレートに基づいているプロジェクトを作成し、そのプロジェクト内のファイルを変更します。  
  
> [!NOTE]
>  このテンプレートのアーキテクチャはサポートされていません[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクト。 作成する方法については[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクト テンプレートを参照してください[ウィザードのデザイン](http://msdn.microsoft.com/library/a7c0be7e-9297-4fed-83e3-5645c896d56b)します。  
  
 詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)します。  
  
## <a name="properties-and-options"></a>プロパティとオプション  
 **プロパティ**ウィンドウには、1 つまたは複数選択した項目のプロパティが表示されます:[拡張プロパティ](../../extensibility/internals/extending-properties.md)オプション ページなど、特定のコンポーネントに関連するオプションのセットを含めることが、プログラミング言語または VSPackage:[オプションとオプション ページ](../../extensibility/internals/options-and-options-pages.md)します。 設定は、通常、UI 関連機能をインポートおよびエクスポートすることができます:[ユーザー設定のサポート](../../extensibility/internals/support-for-user-settings.md)します。  
  
## <a name="visual-studio-services"></a>Visual Studio サービス  
 サービスは、特定のコンポーネントを使用するインターフェイスのセットを提供します。 Visual Studio では、一連の拡張機能を含め、すべてのコンポーネントで使用できるサービスを提供します。 たとえば、Visual Studio services には、ツール ウィンドウを表示または非表示に動的に、ヘルプ、ステータス バー、または UI イベントへのアクセスを有効にするが有効にします。 Visual Studio エディターには、エディターの拡張機能によってインポートできるサービスも提供します。 詳細については、次を参照してください。[を使用すると、サービスを提供する](../../extensibility/using-and-providing-services.md)します。  
  
## <a name="debugger"></a>デバッガー  
 デバッガーは、言語固有のデバッグ コンポーネントをユーザー インターフェイスです。 新しい言語サービスを作成した場合、デバッガーにフックする特定のデバッグ エンジンを作成する必要があります。 詳細については、次を参照してください。 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)します。  
  
## <a name="source-control"></a>ソース管理  
 ソース管理プラグインまたは VSPackage の実装方法の詳細については、次を参照してください。[ソース管理](../../extensibility/internals/source-control.md)します。  
  
## <a name="wizards"></a>ウィザード  
 組み合わせて、ウィザードを作成するには新しいプロジェクトの種類と、ユーザーがその型の新しいプロジェクトを作成するときに、正しい決定を行う、ウィザードを使用できるようにします。 詳細については、次を参照してください。[ウィザード](../../extensibility/internals/wizards.md)します。  
  
## <a name="custom-tools"></a>カスタム ツール  
 カスタム ツールを使用すると、ツールをプロジェクト内の項目に関連付けるし、ファイルを保存するたびに、そのツールを実行します。 詳細については、次を参照してください。[カスタム ツール](../../extensibility/internals/custom-tools.md)します。  
  
## <a name="vssdk-utilities"></a>VSSDK ユーティリティ  
 VSSDK には、Vspackage のさまざまな側面を操作するために必要なユーティリティのセットが含まれています。 詳細については、次を参照してください。 [VSSDK ユーティリティ](../../extensibility/internals/vssdk-utilities.md)します。  
  
## <a name="using-windows-installer"></a>Windows インストーラーを使用します。  
 場合によっては、VSIX インストーラーではなく、Windows インストーラーを使用する必要があります。 たとえば、レジストリに書き込む必要があります。 Windows インストーラーを拡張機能と使用方法の詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../../extensibility/internals/installing-vspackages-with-windows-installer.md)します。  
  
## <a name="help-viewer"></a>ヘルプ ビューアー  
 ヘルプ ビューアーには、独自のヘルプと F1 ページを統合できます。 詳細については、次を参照してください。 [Microsoft ヘルプ ビューアー SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)します。

