---
title: Visual Studio 拡張機能の開発を始めました |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/18/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7bc03568465efa022981ade059b0de68019a5978
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Visual Studio 拡張機能の開発を開始
Visual Studio 拡張機能を初めて作成する場合に、いくつかの疑問をもたれるかもしれません。 ここでは、最も一般的なものの一部を一覧にしています。 探している情報が見つからない場合は、フィードバック ボタンを使用して (画面の下部にある **このページは役に立ちましたか?** ) お探しの情報を問い合わせてください。  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Visual Studio 拡張機能を開発するために必要なソフトウェアはなんですか。  
 Visual Studio 拡張機能を開発するために Visual Studio だけでなく、Visual Studio SDK をインストールする必要があります。 通常のセットアップの一部として、Visual Studio SDK をインストールすることができますし、または後からインストールすることもできます。 Visual Studio SDK のインストールに関する詳細は、次の [Visual Studio SDK](../extensibility/visual-studio-sdk.md) を参照してください。  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio 拡張機能で実行できるどのようなさまざまな原因ですか。  
 Visual Studio 拡張機能のさまざまな仮定するとする際に無限の制限。 もちろん、ほとんどの拡張機能をコードの記述を行うには何かが、大文字である必要はありません。 ビルドできる拡張機能の種類のいくつかの例を次に示します。  
  
-   含まれていない Visual Studio は、構文の色分け、IntelliSense、コンパイラとデバッグのサポートと言語のサポート  
  
-   その他のテンプレート、コードのリファクタリング、新しいダイアログやツール ウィンドウで、コアを拡張する生産性向上ツール IDE エクスペリエンスします。  
  
-   データのデザインまたはクラウドのサポートなどのシナリオのドメイン固有のデザイナー  
  
 拡張機能の例については、チェック アウト、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)です。 さまざまな拡張機能はオープン ソース、および市場には、GitHub リポジトリへのリンクが含まれています。 
  
## <a name="which-visual-studio-features-can-i-extend"></a>Visual Studio 機能を拡張できますか。  
 理論上は、Visual Studio のあらゆる部分を拡張することができます: メニューのツールバー、コマンド、ウィンドウ、ソリューション、プロジェクト、エディターに対し、およびなどです。  
  
 実際には、ほとんどの人が拡張する機能は、コマンド、メニューとツールバー、ウィンドウ、IntelliSense、およびプロジェクトを発見しました。 次に、関連するセクションへのリンクを示します。  
  
-   [メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md): Visual Studio のメニューおよびツールバーに、独自の項目を追加します。 Visual Studio の新機能または独自の外部ヘルパー アプリケーションを開始するのにには、それらを使用できます。 メニュー項目のカスタム ショートカットを指定することもできます。  
  
-   [拡張とツール ウィンドウのカスタマイズ](../extensibility/extending-and-customizing-tool-windows.md): 既存のツール ウィンドウの拡張や、独自のツール ウィンドウを作成します。 インスタンスに新しいプロパティを追加する可能性があります、**プロパティ**、または機能を追加する新しいツール ウィンドウを作成する可能性があります。  
  
-   [エディターと言語サービスの拡張機能](../extensibility/editor-and-language-service-extensions.md): IntelliSense が提供する Visual Studio の言語では、独自のカスタマイズを追加するか新しいプログラミング言語のサポートを作成します。 新しいステートメント入力候補、提案、および新しいクイック ツールヒントが表示を作成することができます。 、電球を使ってリファクタリングの候補を追加して、新しいプログラミング言語をサポートするためにコードを修正します。  
  
-   [プロジェクトの拡張](../extensibility/extending-projects.md)  
  
-   [ユーザー設定とオプションの拡張](../extensibility/extending-user-settings-and-options.md)  
  
-   [プロパティとプロパティ ウィンドウの拡張](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Visual Studio の他の部分の拡張](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio の分離シェル](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>VSSDK によって提供されるどのようなプロジェクト テンプレート  
 2 つの主な種類の拡張機能は、Vspackage および MEF 拡張機能です。 一般に、VSPackage 拡張機能は、使用するか、コマンド、ツール ウィンドウ、およびプロジェクトを拡張する拡張機能で使用されます。 MEF 拡張機能は、拡張または Visual Studio エディターのカスタマイズに使用されます。  
  
 Visual c# および Visual Basic の拡張機能、VSSDK には、メニュー コマンド、ツール ウィンドウおよびエディター拡張機能を作成する新しい項目テンプレートと共に使用できる空の VSIX プロジェクト テンプレートが用意されています。 また、他のユーザーに配布するパッケージ プロジェクト テンプレート、コード スニペット、およびその他の成果物にこのテンプレートを使用することができます。  
  
 C++ の場合は、VSPackage ウィザードは、メニュー コマンド、ツール ウィンドウ、およびカスタム エディターを追加するコードを提供します。  
  
 Isolated Shell テンプレートを使用すると、パッケージのバージョンの Visual Studio シェルをブランド化して、独自として配布することで拡張機能です。 次のトピックでは、それぞれの種類の拡張機能の作業を開始する方法を示します。  
  
-   メニュー コマンド:[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   ツール ウィンドウ:[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   エディターの拡張機能:[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   基本的な Vspackage: [VSPackage の拡張機能の作成](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX プロジェクトのテンプレート: [VSIX プロジェクト テンプレートの概要](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio 分離シェル:[チュートリアル: 基本的な分離シェル アプリケーションを作成します。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Visual Studio のように拡張機能を取得する方法は?  
 拡張機能の UI を設計するための便利なヒントを取得[Visual Studio ユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)です。  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>VSSDK コードの例を検索する場所は?  
 特定の機能を実装する方法を示すチュートリアルがある各リンク前のセクションに一覧表示します。 検索することもオープン ソースの github VSSDK のサンプル[Visual Studio のサンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples)です。  
  
## <a name="how-can-i-distribute-my-extension"></a>My の拡張機能を配布する方法は?  
 別のコンピューターで、拡張機能をインストールしたり、.vsix ファイルをダブルクリックしてインストールすると、友人に送信することができます。 VSIX パッケージでについて詳しく調べますできます[Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)です。  
  
 多数の Visual Studio のお客様にできるように、Visual Studio Marketplace で拡張機能を公開することもできます。 パッケージ化するのには、Marketplace 拡張機能の例は、次を参照してください。[チュートリアル: Visual Studio 拡張機能を公開](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)です。 詳細については、Marketplace に発行するために実行する必要がありますを参照してください。[製品と Visual Studio の拡張機能](/vsts/integrate/ide/extensions/overview)します。
