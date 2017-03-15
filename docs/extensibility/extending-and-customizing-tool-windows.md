---
title: "拡張とカスタマイズ ツール ウィンドウ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "essentials のユーザー インターフェイス"
  - "標準的なツール ウィンドウ"
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 拡張とカスタマイズ ツール ウィンドウ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio には、windows、ツール ウィンドウ、ドキュメント ウィンドウおよびダイアログ ウィンドウなどのさまざまな種類が用意されています。 \[プロパティ\] ウィンドウ、\[出力\] ウィンドウおよびタスク一覧\] ウィンドウなどの他のウィンドウには、ツール ウィンドウの種類があります。  
  
## ツール ウィンドウ  
 Visual Studio のツール ウィンドウは、ファイル ベースではない通常読み取り専用のウィンドウです。 このドキュメントのウィンドウは、読み取り\/書き込みモードでファイルを表示からが異なります。**ツールボックス**, 、**ソリューション エクスプ ローラー**, 、**プロパティ** ウィンドウ、および **Web ブラウザー** ツール ウィンドウの例を示します。  
  
 単純なツール ウィンドウを作成する方法を調べるを参照してください。 [ツール ウィンドウを追加します。](../extensibility/adding-a-tool-window.md)します。  
  
 Visual Studio でツール ウィンドウを登録するを参照してください。 [ツール ウィンドウを登録します。](../extensibility/registering-a-tool-window.md)します。  
  
 ツール ウィンドウは、単一インスタンスを既定では、ツール ウィンドウの 1 つのインスタンスをつまり開くことができる、一度にします。 単一インスタンスのツール ウィンドウを開いた後、開いたまま、IDE が閉じられるまでです。 単一インスタンスのツール ウィンドウを閉じるときに、可視性を変更します。 作成することも複数インスタンス ツール ウィンドウ、ウィンドウの複数のインスタンスが同時に開くできるようにします。 詳細については、「[複数インスタンスのツール ウィンドウを作成します。](../extensibility/creating-a-multi-instance-tool-window.md)」を参照してください。  
  
 ツール ウィンドウ、 *動的*, 、ためにも表示されている、関連する UI コンテキストが適用されるたびにします。 自動の表示の使用には、IDE でのウィンドウの煩雑さを軽減できます。 詳細については、「[動的なツール ウィンドウを開く](../extensibility/opening-a-dynamic-tool-window.md)」を参照してください。  
  
 ツール ウィンドウは、ドッキング、フローティング、またはドキュメントのフレームにタブ付きできます。 ツール ウィンドウの枠では、IDE によって提供され、サイズ、位置、ドッキング状態とその他の永続的なプロパティを制御するために使用します。 ツール ウィンドウのペインには、内容が表示されます。 既定のサイズと位置を適用のみツール ウィンドウを最初に開くとします。その後、ツール ウィンドウの状態が保持されます。  
  
 ツール ウィンドウのペインでは、WPF ユーザー コントロールをホストして、ツールバーをサポートすることができます。 オーバーライドすることができます、 <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> ホストされるコントロールのハンドルを返すプロパティ。  
  
 ツール ウィンドウには、さまざまな機能を追加できます。 たとえば、ツールバーを追加することができます: [ツール ウィンドウに、ツールバーを追加します。](../extensibility/adding-a-toolbar-to-a-tool-window.md) またはショートカット メニュー: [ツール ウィンドウのショートカット メニューを追加します。](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)です。 ツール ウィンドウ内のアイテムを検索できるようにする検索コントロールを追加することができます: [ツール ウィンドウに検索を追加します。](../extensibility/adding-search-to-a-tool-window.md)です。  
  
 ツール ウィンドウのイベントにサブスクライブすることができます: [イベントのサブスクライブ](../extensibility/subscribing-to-an-event.md)です。  
  
## 既存のツール ウィンドウを拡張します。  
 ツール ウィンドウに関する情報を追加するには、新規作成\] を **オプション** ページと、新しい設定で、 **プロパティ** \] ページへの書き込み、 **タスク一覧** と **出力** windows です。 詳細については、次のトピックを参照してください。[プロパティ、タスク一覧、出力、およびオプションの Windows の拡張](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) および[プロパティ、タスク一覧、出力、およびオプションの Windows の拡張](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## モーダル ダイアログ ボックス  
 Visual Studio 拡張機能から派生してモーダル ダイアログ ボックスを作成する必要があります <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, 、および残りの UI を制御できます。 詳細については、以下を参照してください。[作成して、モーダル ダイアログ ボックスを管理します。](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
## 参照  
 [ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)