---
title: "Visual Studio 拡張機能の開発を始めました | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "起動されると、Visual Studio の統合を取得します。"
  - "Visual Studio での統合"
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio 拡張機能の開発を始めました
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

前に Visual Studio 拡張機能を作成してない場合、いくつかの質問があるでしょう。 最も一般的なアラートの一部を示しています。 探している情報が表示されない場合は、\[フィードバック\] ボタンを使用して \(**このページは役に立ちましたか?** 、画面の下部にある\) する情報を確認します。  
  
## Visual Studio 拡張機能を開発する必要があるソフトウェアをでしょうか。  
 Visual Studio 拡張機能を開発するために Visual Studio 2015 だけでなく、Visual Studio 2015 SDK をインストールする必要があります。   Visual Studio 2015 SDK をインストールするには通常のセットアップの一部として、または後でインストールできます。 Visual Studio SDK をインストールする方法の詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## どのようなさまざまな原因でを行う Visual Studio 拡張機能ですか。  
 別の Visual Studio 拡張機能を想定する際に無限の制限です。 もちろん、ほとんどの拡張機能のコードの記述に何かに発生する必要はありません。 ビルドする拡張機能の種類のいくつかの例を次に示します。  
  
-   構文の色分け表示、IntelliSense、コンパイラとデバッグのサポートと、Visual Studio に含まれていない言語のサポート  
  
-   その他のテンプレート、コード リファクタリング、新しいダイアログやツール ウィンドウで、コアを拡張する生産性向上ツール IDE の発生します。  
  
-   データのデザインまたはクラウドのサポートなどのシナリオの特定領域デザイナー  
  
 拡張機能の例については、チェック アウト、 [Visual Studio ギャラリー](https://visualstudiogallery.msdn.microsoft.com/)します。 参照してくださいも [Visual Studio のオープン ソース Extensions](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md)します。  
  
## Visual Studio 機能を拡張できますか。  
 理論上は、Visual Studio のあらゆる部分を拡張することができます: メニューのツールバー、コマンド、windows、ソリューション、プロジェクト、エディター、およびなどです。  
  
 実際には、ほとんどの人が拡張する機能は、コマンド、メニューとツールバー、windows、IntelliSense、およびプロジェクトを発見しました。 次に、関連するセクションへのリンクを示します。  
  
-   [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md): Visual Studio メニューおよびツールバーに、独自の項目を追加します。 Visual Studio の新機能や外部ヘルパー アプリケーションを起動するのにには、それらを使用できます。 メニュー項目に対してカスタム ショートカットを指定することもできます。  
  
-   [拡張とカスタマイズ ツール ウィンドウ](../extensibility/extending-and-customizing-tool-windows.md): 既存のツール ウィンドウを拡張または独自のツール ウィンドウを作成します。 たとえば、新しいプロパティを追加する、 **プロパティ**, 、または機能を追加する新しいツール ウィンドウを作成する可能性があります。  
  
-   [エディターと言語サービスの拡張機能](../extensibility/editor-and-language-service-extensions.md): Visual Studio の言語で表示される IntelliSense は、独自のカスタマイズを追加したり、新しいプログラミング言語のサポートを作成します。 新しいステートメント入力候補、提案、および新しいクイック ツールヒントが表示を作成することができます。 、電球を使ってとリファクタリングの提案を追加できます。 新しいプログラミング言語をサポートするためにコードを修正します。  
  
-   [プロジェクトの拡張](../extensibility/extending-projects.md)  
  
-   [ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)  
  
-   [プロパティと \[プロパティ\] ウィンドウの拡張](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md)  
  
-   [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio シェルの分離](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> どのようなプロジェクト テンプレートは、VSSDK によって提供されるでしょうか。  
 2 つの主な種類の拡張機能は、Vspackage および MEF の拡張です。 一般的に、VSPackage 拡張機能は、使用またはコマンド、ツール ウィンドウ、およびプロジェクトを拡張する拡張機能の使用されます。 MEF の拡張機能は、拡張、または Visual Studio エディターのカスタマイズに使用されます。  
  
 Visual c\# および Visual Basic の拡張機能、VSSDK はメニュー コマンド、ツール ウィンドウおよびエディターの拡張機能を作成する新しい項目テンプレートと組み合わせて使用できる空の VSIX プロジェクト テンプレートを提供します。 詳細については、「[Visual Studio 2015 SDK の新機能します。](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)」を参照してください。 パッケージのプロジェクト テンプレート、コード スニペット、その他の成果物には、このテンプレートは、他のユーザーに配布するためも行えます。  
  
 C\+\+ の場合は、VSPackage ウィザードは、メニュー コマンド、ツール ウィンドウ、およびカスタム エディターを追加するコードを提供します。  
  
 分離シェル テンプレートは、パッケージのバージョンの Visual Studio シェルをブランド化して、独自として配布することで、拡張機能に使用されます。 次のトピックでは、各種類の拡張機能を使用する方法を示しています。  
  
-   メニュー コマンド: [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   ツール ウィンドウの場合: [ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   エディターの拡張機能: [エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   基本的な vspackages にあります。 [VSPackage で拡張機能を作成します。](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX プロジェクト テンプレートの場合: [VSIX プロジェクトのテンプレートの概要](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio では、シェルを分離します。 [チュートリアル: 基本的な分離シェル アプリケーションを作成します。](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## Visual Studio のように my 拡張を取得する方法はありますか  
 \[拡張機能の UI を設計するために役立つヒントを取得 [Visual Studio ユーザー エクスペリエンス ガイドライン](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  
  
## VSSDK コードの例についてはどこで入手できますか。  
 特定の機能を実装する方法を説明するチュートリアルが含まがあるの各リンク前のセクションに示されています。 検索することもオープン ソースに GitHub の VSSDK サンプル [Visual Studio のサンプル](https://aka.ms/vs2015sdksamples)します。  
  
## My 拡張を配布する方法は教えてください。  
 別のコンピューターで、拡張機能をインストールしたり、.vsix ファイルをダブルクリックしてインストールすると、友人たちに送信することができます。 VSIX パッケージの詳細を確認できる [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)です。  
  
 Visual Studio の顧客数が多いできるように、Visual Studio ギャラリーの拡張機能を公開することもできます。 ギャラリーの拡張機能をパッケージ化の例は、次を参照してください。 [チュートリアル: Visual Studio 拡張機能を公開します。](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)します。 ギャラリーに発行するために必要なものの詳細については、次を参照してください。 [製品と Visual Studio の拡張機能](https://visualstudiogallery.msdn.microsoft.com/)します。