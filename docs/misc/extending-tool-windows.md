---
title: "ツール ウィンドウの拡張 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ウィンドウ [Visual Studio SDK]、ツール"
  - "ドキュメント ウィンドウ"
  - "ツール ウィンドウ"
  - "ウィンドウ [Visual Studio SDK]、ドキュメント"
ms.assetid: 252f7b99-b44a-4a63-88d9-3a0ca48ac4f1
caps.latest.revision: 37
caps.handback.revision: 37
manager: "douge"
---
# ツール ウィンドウの拡張
Visual Studio のツール ウィンドウは一般に、ファイルベースでない読み取り専用のウィンドウです。 この点で、ツール ウィンドウは、読み取り\/書き込みモードでファイルを表示するドキュメント ウィンドウと異なります。**ツールボックス**、**ソリューション エクスプローラー**、**\[プロパティ\]** ウィンドウ、および **Web ブラウザー** はツール ウィンドウの例です。  
  
 Visual Studio 2010 以降のすべてのツール ウィンドウは WPF ベースです。 Visual Studio 2010 より前の Visual Studio のバージョンでは、ツール ウィンドウは Windows フォーム ベースでした。 Windows フォーム ベースのウィンドウも表示できますが、新しいツール ウィンドウは WPF ベースである必要があります。  
  
## ツール ウィンドウの要点  
 ツール ウィンドウを用意するには、Visual Studio で登録し、既定のサイズと場所を指定する必要があります。 詳細については、「[レジストリ内のツール ウィンドウ](../extensibility/tool-windows-in-the-registry.md)」を参照してください。  
  
 ツール ウィンドウは通常、メニュー コマンドをクリックすることで、作成または起動されます。 ツール ウィンドウをプログラムで作成するには、「[ツール ウィンドウをプログラムで開く](../misc/opening-a-tool-window-programmatically.md)」を参照してください。  
  
 ツール ウィンドウは、既定では単一インスタンスです、つまり、一度に開くことができるツール ウィンドウのインスタンスは 1 つのみです。 単一インスタンスのツール ウィンドウを開いた後は、IDE が閉じられるまで開いたままです。 単一インスタンスのツール ウィンドウの終了ボタンをクリックすると、可視性のみが変更されます。 複数インスタンスのツール ウィンドウを作成して、ウィンドウの複数のインスタンスを同時に開くことも可能です。 詳細については、「[複数インスタンスのツール ウィンドウを作成します。](../extensibility/creating-a-multi-instance-tool-window.md)」を参照してください。  
  
 ツール ウィンドウは、ドッキング、フローティング、またはドキュメント フレームのタブ付けが可能です。 ツール ウィンドウの枠は IDE によって提供され、サイズ、位置、ドッキング状態と、その他の永続的なプロパティを制御するために使用します。 ツール ウィンドウのペインには、内容が表示されます。 既定のサイズと位置はツール ウィンドウを最初に開くときにのみ適用されます。その後、ツール ウィンドウの状態は保持されます。  
  
 ツール ウィンドウのペインでは、WPF ユーザー コントロールをホストして、ツールバーをサポートすることができます。<xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> プロパティをオーバーライドして、ホストされるコントロールのハンドルを返すことができます。  
  
 ツール ウィンドウは*動的* \(*自動表示*とも呼ばれます\) にすることができます。 動的なツール ウィンドウは、関連する UI コンテキストが適用されるたびに表示されます。 自動表示の使用により、IDE でのウィンドウの煩雑さが軽減されます。 詳細については、「[動的なツール ウィンドウを開く](../extensibility/opening-a-dynamic-tool-window.md)」を参照してください。  
  
 VSPackage は、ツール ウィンドウを作成する唯一の方法ではありません。 Visual Studio 自動化モデルを使用することで、アドインはツール ウィンドウを作成できます。 詳細については、「[How to: Create and Control Tool Windows](../Topic/How%20to:%20Create%20and%20Control%20Tool%20Windows.md)」を参照してください。  
  
## 参照  
 [Tool Windows](../misc/extending-tool-windows.md)   
 [ドキュメント ウィンドウ](../extensibility/internals/document-windows.md)   
 [ツール ウィンドウに検索を追加します。](../extensibility/adding-search-to-a-tool-window.md)