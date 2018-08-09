---
title: 拡張とカスタマイズ ツール Windows |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c11485e830d1b7bcef851a50225e15f351e64f3e
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637485"
---
# <a name="extend-and-customize-tool-windows"></a>拡張し、カスタマイズ ツール ウィンドウ
Visual Studio には、windows アプリ、およびツール ウィンドウ、ドキュメント ウィンドウ、ダイアログ ウィンドウなどのさまざまな種類が用意されています。 などの他のウィンドウ、**プロパティ**ウィンドウで、**出力**ウィンドウ、および**タスク一覧**ウィンドウで、ツール ウィンドウの種類します。  
  
## <a name="tool-windows"></a>ツール ウィンドウ  
 Visual Studio のツール ウィンドウには、通常は読み取り専用のウィンドウで、ファイル ベースでないですが。 この点で、ツール ウィンドウは、読み取り/書き込みモードでファイルを表示するドキュメント ウィンドウと異なります。 **ツールボックス**、 **ソリューション エクスプローラー**、 **[プロパティ]** ウィンドウ、および **Web ブラウザー** はツール ウィンドウの例です。  
  
 単純なツール ウィンドウを作成する方法を調べるを参照してください。[ツール ウィンドウを追加](../extensibility/adding-a-tool-window.md)します。  
  
 Visual Studio でツール ウィンドウを登録するを参照してください。[ツール ウィンドウを登録](../extensibility/registering-a-tool-window.md)します。  
  
 ツール ウィンドウは、既定では単一インスタンスです、つまり、一度に開くことができるツール ウィンドウのインスタンスは 1 つのみです。 単一インスタンスのツール ウィンドウを開いた後は、IDE が閉じられるまで開いたままです。 単一インスタンスのツール ウィンドウを閉じるときに、可視性のみを変更します。 複数インスタンスのツール ウィンドウを作成して、ウィンドウの複数のインスタンスを同時に開くことも可能です。 参照してください[マルチ インスタンスのツール ウィンドウを作成](../extensibility/creating-a-multi-instance-tool-window.md)詳細についてはします。  
  
 ツール ウィンドウを指定できます*動的*、表示される、関連する UI コンテキストが適用されるたびを意味します。 自動表示の使用により、IDE でのウィンドウの煩雑さが軽減されます。 詳細については、次を参照してください。[動的なツール ウィンドウを開いて](../extensibility/opening-a-dynamic-tool-window.md)します。  
  
 ツール ウィンドウは、ドッキング、フローティング、またはドキュメント フレームのタブ付けが可能です。 ツール ウィンドウの枠は IDE によって提供され、サイズ、位置、ドッキング状態と、その他の永続的なプロパティを制御するために使用します。 ツール ウィンドウのペインには、内容が表示されます。 既定のサイズと位置はツール ウィンドウを最初に開くときにのみ適用されます。その後、ツール ウィンドウの状態は保持されます。  
  
 ツール ウィンドウのペインでは、WPF ユーザー コントロールをホストして、ツールバーをサポートすることができます。 オーバーライドすることができます、<xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>プロパティがホストされるコントロールのハンドルを返します。  
  
 ツール ウィンドウには、さまざまな機能を追加できます。 たとえば、ツールバーを追加することができます:[ツール ウィンドウにツールバーを追加](../extensibility/adding-a-toolbar-to-a-tool-window.md)またはショートカット メニュー:[ツール ウィンドウのショートカット メニューを追加する](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)します。 ツール ウィンドウ内の項目を検索できる検索コントロールを追加することができます:[ツール ウィンドウに追加の検索](../extensibility/adding-search-to-a-tool-window.md)します。  
  
 ツール ウィンドウのイベントにサブスクライブすることができます:[イベントにサブスクライブする](../extensibility/subscribing-to-an-event.md)します。  
  
## <a name="extend-existing-tool-windows"></a>既存のツール ウィンドウを拡張します。  
 ツール ウィンドウに関する情報を追加するには、新しい**オプション**ページと、新しい設定で、**プロパティ** ページへの書き込み、**タスク一覧**と**出力** windows。 詳細については、次を参照してください。[拡張プロパティ、タスク一覧、出力、およびオプションの windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)と[拡張プロパティ、タスク一覧、出力、およびオプションの windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)します。  
  
## <a name="modal-dialog-boxes"></a>モーダル ダイアログ ボックス  
 Visual Studio 拡張機能から派生してモーダル ダイアログ ボックスを作成する必要があります<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>、し、残りの UI を制御できます。 詳細については、次を参照してください。[作成モーダル ダイアログ ボックスを管理および](../extensibility/creating-and-managing-modal-dialog-boxes.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ツール ウィンドウでの拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)