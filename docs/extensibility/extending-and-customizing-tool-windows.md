---
title: "拡張して、ツール ウィンドウをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 74616bf92b1424b4749354d1f0a7b3232e66a335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-and-customizing-tool-windows"></a>拡張して、ツール ウィンドウをカスタマイズします。
Visual Studio には、windows、ツール ウィンドウ、ドキュメント ウィンドウおよびダイアログ ウィンドウなどのさまざまな種類が用意されています。 [プロパティ] ウィンドウ、出力ウィンドウ、[タスク一覧] ウィンドウなどの他のウィンドウは、ツール ウィンドウの種類です。  
  
## <a name="tool-windows"></a>ツール ウィンドウ  
 Visual Studio のツール ウィンドウは、ファイル ベースではない通常読み取り専用のウィンドウです。 この点で、ツール ウィンドウは、読み取り/書き込みモードでファイルを表示するドキュメント ウィンドウと異なります。 **ツールボックス**、 **ソリューション エクスプローラー**、 **[プロパティ]** ウィンドウ、および **Web ブラウザー** はツール ウィンドウの例です。  
  
 簡単なツール ウィンドウを作成する方法を調べるには、次を参照してください。[ツール ウィンドウを追加する](../extensibility/adding-a-tool-window.md)です。  
  
 Visual Studio でツール ウィンドウを登録するを参照してください。[ツール ウィンドウを登録する](../extensibility/registering-a-tool-window.md)です。  
  
 ツール ウィンドウは、既定では単一インスタンスです、つまり、一度に開くことができるツール ウィンドウのインスタンスは 1 つのみです。 単一インスタンスのツール ウィンドウを開いた後は、IDE が閉じられるまで開いたままです。 単一インスタンスのツール ウィンドウを閉じると、その可視性のみを変更します。 複数インスタンスのツール ウィンドウを作成して、ウィンドウの複数のインスタンスを同時に開くことも可能です。 参照してください[複数インスタンス ツール ウィンドウを作成する](../extensibility/creating-a-multi-instance-tool-window.md)詳細についてはします。  
  
 ツール ウィンドウを指定できます*動的*にも表示される、関連する UI コンテキストが適用されるたびにします。 自動表示の使用により、IDE でのウィンドウの煩雑さが軽減されます。 詳細については、次を参照してください。[動的ツール ウィンドウを開いて](../extensibility/opening-a-dynamic-tool-window.md)です。  
  
 ツール ウィンドウは、ドッキング、フローティング、またはドキュメント フレームのタブ付けが可能です。 ツール ウィンドウの枠は IDE によって提供され、サイズ、位置、ドッキング状態と、その他の永続的なプロパティを制御するために使用します。 ツール ウィンドウのペインには、内容が表示されます。 既定のサイズと位置はツール ウィンドウを最初に開くときにのみ適用されます。その後、ツール ウィンドウの状態は保持されます。  
  
 ツール ウィンドウのペインでは、WPF ユーザー コントロールをホストして、ツールバーをサポートすることができます。 オーバーライドすることができます、<xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>ホストされるコントロールのハンドルを取得するプロパティです。  
  
 ツール ウィンドウにさまざまな機能を追加することができます。 たとえば、ツールバーを追加することができます:[ツール ウィンドウにツールバーを追加する](../extensibility/adding-a-toolbar-to-a-tool-window.md)またはショートカット メニュー:[ツール ウィンドウのショートカット メニューを追加する](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)です。 使用すると、ツール ウィンドウ内で項目を検索する検索コントロールを追加することができます:[ツール ウィンドウに追加する検索](../extensibility/adding-search-to-a-tool-window.md)です。  
  
 ツール ウィンドウのイベントにサブスクライブすることができます:[イベントのサブスクライブ](../extensibility/subscribing-to-an-event.md)です。  
  
## <a name="extending-existing-tool-windows"></a>既存のツール ウィンドウの拡張  
 ツール ウィンドウに関する情報を追加するには新しい**オプション**ページと、新しい設定で、**プロパティ** ページへの書き込み、**タスク一覧**と**出力** windows です。 詳細については、次を参照してください。[プロパティ、タスク一覧、出力、およびオプションの Windows の拡張](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)と[プロパティ、タスク一覧、出力、およびオプションの Windows の拡張](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)です。  
  
## <a name="modal-dialog-boxes"></a>モーダル ダイアログ ボックス  
 Visual Studio 拡張機能では、それらから派生することでモーダル ダイアログ ボックスを作成する必要があります<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>、し、残りの UI を制御することができます。 詳細については、次を参照してください。 [作成して、モーダル ダイアログ ボックスを管理する](../extensibility/creating-and-managing-modal-dialog-boxes.md)です。  
  
## <a name="see-also"></a>参照  
 [ツール ウィンドウでの拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)