---
title: "拡張 SDK と比較して NuGet を使用した参照の追加 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
ms.assetid: 2175581e-83cb-444c-bb52-cc1fca8ea196
caps.latest.revision: 21
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3f4740d442a7ef24803d6360cdcc480d9d6fca84

---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>拡張 SDK と比較して NuGet を使用した参照の追加
Visual Studio を対象とする NuGet 拡張機能、またはソフトウェア開発キット (SDK) を使用して、Visual Studio プロジェクト内で使用するためのパッケージを提供できます。 このトピックでは&2; つのメカニズムの類似点と相違点を説明し、特定のタスクにとって最善のメカニズムを選択しやすくなります。  
  
-   NuGet は、オープン ソースのパッケージ管理システムであり、ライブラリをプロジェクトのソリューションに組み込むプロセスを簡略化します。 詳細については、[NuGet の概要](http://go.microsoft.com/fwlink/?LinkId=254877)に関するページを参照してください。  
  
-   SDK は、Visual Studio が単一の参照項目として取り扱うファイルのコレクションです。 **[参照マネージャー]** ダイアログ ボックスでは、このダイアログ ボックスを表示した時点で開いていたプロジェクトに関連するすべての SDK が一覧表示されます。 SDK をプロジェクトに追加すると、IntelliSense、**[ツールボックス]**、デザイナー、**[オブジェクト ブラウザー]**、MSBuild、配置、デバッグおよびパッケージの各機能を通じて、その SDK のすべての内容にアクセスできます。 詳細については、「[Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md)」 (ソフトウェア開発キットの作成) を参照してください。  
  
## <a name="which-mechanism-should-i-use"></a>使用するメカニズムの決定  
 次の表を使用して、SDK の参照機能と NuGet の参照機能を比較できます。  
  
|特性|SDK のサポート対象|SDK に関するメモ|NuGet のサポート対象|NuGet に関するメモ|  
|-------------|-----------------|---------------|-------------------|-----------------|  
|このメカニズムは、1 つのエンティティを参照し、その結果、すべてのファイルと機能が使用できるようになります。|○|**[参照マネージャー]** ダイアログ ボックスを使用して SDK を追加し、その結果、開発ワークフローの実行中にすべてのファイルと機能が使用できるようになります。|○||  
|MSBuild は、アセンブリと Windows メタデータ (.winmd) ファイルを自動的に使用します。|Y|SDK 内の参照は、コンパイラに対して自動的に渡されます。|Y||  
|MSBuild は、.h ファイルまたは .lib ファイルを自動的に使用します。|○|*SDKName*.props ファイルは、.h ファイルまたは .lib ファイルを自動的に使用するために Visual C++ のディレクトリなどをセットアップする方法を Visual Studio に伝えます。|N||  
|MSBuild は、.js ファイルまたは .css ファイルを自動的に使用します。|○|**ソリューション エクスプローラー**で JavaScript SDK 参照ノードを展開し、個別の .js ファイルまたは .css ファイルを表示した後、それらのファイルをそれぞれのソース ファイルにドラッグすることにより、`<source include/>` タグを生成できます。 SDK は、F5 キーを使用する方法と自動的なパッケージ設定方法をサポートします。|○||  
|MSBuild は、**[ツールボックス]** 内のコントロールを自動的に追加します。|○|**[ツールボックス]** は SDK を使用し、指定されたタブの中にコントロールを表示することができます。|N||  
|このメカニズムでは、VSIX (Visual Studio Installer for extensions) をサポートします。|Y|VSIX には、SDK パッケージを作成するための特別なマニフェストとロジックがあります。|Y|VSIX は、別のセットアップ プログラムに埋め込むことができます。|  
|**オブジェクト ブラウザー**は、参照を列挙します。|○|**オブジェクト ブラウザー**は SDK 内にある参照の一覧を自動的に取得し、それらを列挙します。|N||  
|ファイルとリンクは、**[参照マネージャー]** ダイアログ ボックスに自動的に追加されます (ヘルプへのリンクなどが自動的に設定されます)。|○|**[参照マネージャー]** ダイアログ ボックスでは、SDK が自動的に列挙され、ヘルプへのリンクや SDK の依存関係の一覧も表示されます。|N|NuGet では独自の **[NuGet パッケージの管理]** ダイアログ ボックスが表示されます。|  
|このメカニズムでは複数のアーキテクチャがサポートされます。|Y|SDK は、複数の構成で出荷することができます。 MSBuild は、各プロジェクト構成に適したファイルを使用します。|N||  
|このメカニズムでは複数の構成がサポートされます。|Y|SDK は、複数の構成で出荷することができます。 プロジェクトのアーキテクチャに基づいて、MSBuild は各プロジェクト アーキテクチャに適したファイルを使用します。|N||  
|このメカニズムでは、"not to copy" (コピーしない) を指定できます。|Y|ファイルを \redist と \designtime どちらのフォルダーにドロップするかに応じて、使用側アプリケーション パッケージにどのファイルをコピーするかを制御できます。|N|どのファイルをコピーするかを、パッケージ マニフェスト内で宣言します。|  
|内容は、ローカライズされたファイル内に表示されます。|Y|設計時の操作を向上させるために、SDK 内にあるローカライズされた XML ドキュメントが自動的に含まれます。|N||  
|MSBuild は、SDK の複数バージョンの同時使用をサポートします。|Y|SDK は、複数バージョンの同時使用をサポートします。|N|これは参照を行いません。 プロジェクト内で NuGet ファイルの複数のバージョンを一度に使用することはできません。|  
|このメカニズムでは、複数の適切なターゲット フレームワーク、Visual Studio の複数のバージョン、および複数のプロジェクトの種類の指定がサポートされています。|○|**[参照マネージャー]** ダイアログ ボックスと **[ツールボックス]** では、プロジェクトに適用する SDK のみが表示されるため、ユーザーは適切な SDK をより簡単に選択できます。|Y (部分的)|Pivot は Target Framework です。 ユーザー インターフェイスに対してフィルター処理は実行されません。 インストール時に、エラーが返される可能性があります。|  
|このメカニズムでは、ネイティブ WinMD に関する登録情報の指定がサポートされています。|Y|SDKManifest.xml 内で、.winmd ファイルと .dll ファイル間の関連付けを指定できます。|N||  
|このメカニズムでは、他の SDK に対する依存関係の指定がサポートされています。|Y|SDK は、ユーザーへの通知のみを実行します。ユーザーは、これらの SDK のインストールと参照を手動で実行する必要があります。|Y|NuGet は取得を自動的に実行し、ユーザーへの通知を行いません。|  
|このメカニズムは、アプリケーション マニフェストや Framework ID のような [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] の概念と統合されています。|Y|SDK は、[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] に固有の概念を渡す必要があります。その結果、パッケージ化機能と、F5 キーを使用する方法は、[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] で使用可能な SDK で正常に機能します。|N||  
|このメカニズムは、[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリケーション用のアプリケーション デバッグ パイプラインと統合されています。|Y|SDK は、[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] に固有の概念を渡す必要があります。その結果、パッケージ化機能と、F5 キーを使用する方法は、[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] で使用可能な SDK で正常に機能します。|Y|NuGet の内容は、プロジェクトの一部になります。 F5 に関して特別な考慮事項は必要ありません。|  
|このメカニズムは、アプリケーション マニフェストに統合されます。|Y|SDK は、[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] に固有の概念を渡す必要があります。その結果、パッケージ化機能と、F5 キーを使用する方法は、[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] で使用可能な SDK で正常に機能します。|Y|NuGet の内容は、プロジェクトの一部になります。 F5 に関して特別な考慮事項は必要ありません。|  
|このメカニズムは、非参照ファイルを配置します (たとえば、[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリケーションのテストを実行するためのテスト フレームワークを配置します)。|Y|\redist フォルダーにファイルをドロップした場合は、それらのファイルは自動的に配置されます。|Y||  
|このメカニズムは、Visual Studio IDE 内のプラットフォーム SDK を自動的に追加します。|Y|[!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK または Windows Phone SDK を特定のレイアウトで特定の位置にドロップすると、その SDK は Visual Studio のすべての機能に自動的に統合されます。|N||  
|このメカニズムでは、開発者のクリーンなコンピューターがサポートされています  (つまり、インストールは必要なく、ソース・コード管理からの単純な取得が機能します)。|N|SDK を参照するには、ソリューションと SDK を個別にチェックインする必要があります。 MSBuild が SDK を反復処理する、レジストリとは異なる&2; つの既定の場所から SDK をチェックインできます (詳細については、「[Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md)」 (ソフトウェア開発キットの作成) を参照してください)。 代わりに、カスタムの位置に SDK が配置されている場合は、プロジェクト ファイル内で次のコードを指定できます。<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> 次に、その場所に SDK をチェックインします。|Y|ソリューションをチェック アウトすることもでき、その場合は Visual Studio が直ちにファイルを認識して、そのファイルを処理します。|  
|パッケージ作成者から成る既存の大規模コミュニティに参加することもできます。|N/A|このコミュニティは新しく作成されたものです。|Y||  
|パッケージ使用者から成る既存の大規模コミュニティに参加することもできます。|N/A|このコミュニティは新しく作成されたものです。|Y||  
|パートナーのエコシステム (カスタム ギャラリー、リポジトリなど) に参加できます。|N/A|使用可能なリポジトリには、Visual Studio ギャラリー、Microsoft ダウンロード センター、および [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] が含まれます。|Y||  
|このメカニズムは、パッケージ作成と使用の両方を対象にした、継続的な統合ビルド サーバーに統合されます。|Y|SDK は、チェックインの位置 (SDKReferenceDirectoryRoot プロパティ) をコマンド ラインの一部として MSBuild に渡す必要があります。|Y||  
|このメカニズムでは、安定バージョンとプレリリース パッケージ バージョンの両方がサポートされています。|Y|SDK では、複数のバージョンに対する参照の追加をサポートしています。|Y||  
|このメカニズムでは、インストール済みパッケージの自動更新がサポートされています。|Y|SDK が VSIX として、または Visual Studio の自動更新の一部として提供されている場合は、SDK は自動的な通知を行います。|Y||  
|このメカニズムには、パッケージを作成および使用するためのスタンドアロンの .exe ファイルが含まれています。|Y|SDK には MSBUILD.exe が含まれています。|Y||  
|パッケージは、バージョン管理機能にチェックインできます。|Y|Documents ノードの外部にある場所でチェックインを行うことはできません。つまり、拡張 SDK をチェックインできない可能性があります。拡張 SDK のサイズは大きい可能性があります。|Y||  
|PowerShell インターフェイスを使用して、パッケージを作成および使用することができます。|Y (使用)、N (作成)|SDK を作成するためのツールはありません。 使用するには、コマンド ラインで MSBuild を実行します。|Y||  
|デバッグをサポートするために、シンボル パッケージを使用できます。|Y|.pdb ファイルを SDK 内にドロップすると、そのファイルが自動的に使用されます。|Y||  
|このメカニズムでは、パッケージ マネージャーの自動更新がサポートされています。|N/A|SDK を変更するには、MSBuild を使用します。|Y||  
|このメカニズムでは、軽量のマニフェスト ファイル形式がサポートされています。|Y|SDKManifest.xml では、多くの属性がサポートされていますが、通常必要とされるのは、小規模なサブセットです。|Y||  
|このメカニズムは、Visual Studio のすべてのエディションで使用できます。|Y|SDK では、Visual Studio Express から [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] まで、Visual Studio のすべてのエディションがサポートされています。|Y|NuGet では、Express から [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] まで、Visual Studio のすべてのエディションがサポートされています。|  
|このメカニズムは、すべてのプロジェクトの種類で使用できます。|N|SDK では [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 以降の [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] アプリケーションがサポートされています。|N|許可されているプロジェクトの一覧をレビューできます。|  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)


<!--HONumber=Feb17_HO4-->


