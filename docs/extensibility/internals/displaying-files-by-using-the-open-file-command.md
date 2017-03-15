---
title: "ファイルを開くコマンドを使用してファイルを表示します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ファイルを開くコマンドをサポートするプロジェクトの種類"
  - "ファイルを開くコマンド"
  - "永続化、ファイルを開くコマンドをサポートします。"
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ファイルを開くコマンドを使用してファイルを表示します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次の手順はIDE に [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] で ENT1ENT \[入力\] メニューで使用できる  **ファイルを開く**  のコマンドの処理方法について説明します。  この手順はプロジェクトがコマンドから送信された呼び出しに対してどのように応答するかについて説明します。  
  
 ユーザーが \[ENT1ENT\] メニューの  **ファイルを開く**  のコマンドをクリックし\[ENT2ENT\] ダイアログ ボックスからファイルを選択すると次の処理が実行されます。  
  
1.  実行中のドキュメントの表を使用してファイルがプロジェクトで既に開いているかどうかを判定します。  
  
    -   ファイルが開くとウィンドウに新しい表紙を付けます。  
  
    -   ファイルが開いていない場合はそのプロジェクトがファイルを開くことができるかを決定する各プロジェクトを照会するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> を呼び出します。  
  
        > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> プロジェクトの実装ではプロジェクトでファイルを開く優先度レベルを示す値を指定します。  優先順位値は <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> の列挙型に設定されます。  
  
2.  各プロジェクトにはプロジェクト ファイルを開くことによって重要度を示す優先順位に応答します。  
  
3.  IDE ではプロジェクトでファイルを開くかを確認するには次の条件が使用されています :  
  
    -   優先順位とするプロジェクト \(DP\_Intrinsic\) ファイルを開きます。  複数のプロジェクトがこの優先度をクリックして応答したりする最初のプロジェクト ファイルを開きます。  
  
    -   プロジェクトの優先順位 \(\) DP\_Intrinsic 応答がすべてのプロジェクトが同じをクリックしアクティブ プロジェクトのファイルが低い優先順位。  プロジェクトがアクティブではない場合応答最初のプロジェクト ファイルを開きます。  
  
    -   プロジェクトのファイル \(DP\_Unsupported\) の所有権を要求しない場合そのファイルはプロジェクト ファイルを開きます。  
  
         そのほかのファイル プロジェクトのインスタンスを作成するとプロジェクトは値 DP\_CanAddAsExternal が常に応答します。  この値はプロジェクトでファイルを開くことができることを示します。  このプロジェクトは他のプロジェクトにも開いているファイルを格納するために使用されます。  このプロジェクト項目の一覧は失われます ; このプロジェクトではファイルを開く機能を使用する場合にのみ  **ソリューション エクスプローラー**  に表示されます。  
  
         ファイルを開くことができることをそのほかのファイル プロジェクトを示すプロジェクトのインスタンスは作成されませんでした。  この場合IDE でそのほかのファイルのインスタンスを示すプロジェクトとファイルを開くプロジェクトを作成します。  
  
4.  すべてのプロジェクトでファイルを開くまたは IDE をとそのプロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> のメソッドを呼び出します。  
  
5.  プロジェクトプロジェクトに固有のエディターまたは標準エディターを使用してファイルを開くかどうかを選択できます。  詳細については、「[方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)」および「[方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)」をそれぞれ参照してください。  
  
## 参照  
 [コマンドを開く\] を使用してファイルを表示します。](../Topic/Displaying%20Files%20By%20Using%20the%20Open%20With%20Command.md)   
 [開く、プロジェクト項目を保存します。](../../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)