---
title: "方法: 標準のエディターを開く | Microsoft Docs"
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
  - "エディター [Visual Studio SDK] を開く"
  - "プロジェクト [Visual Studio SDK] 標準エディターの起動"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: 標準のエディターを開く
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

標準エディターを開くとIDE がプロジェクト ファイルに固有のエディターを指定する代わりに指定されたファイルの種類の標準エディターを確認できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> のメソッドを実行するには次の手順を実行します。  これは標準エディターでプロジェクト ファイルが開きます。  
  
### 標準メニュー エディターとの OpenItem のメソッドを実装します。  
  
1.  ドキュメント オブジェクトにデータ ファイルが既に開いているかどうかを確認するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>`RDT_EditLock`\(\) を呼び出します。  
  
2.  ファイルが既に開いている場合 `grfIDO` のパラメーターに `IDO_ActivateIfOpen` の値を指定する <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> のメソッドを呼び出してファイルに新しい表紙を付けます。  
  
     ファイルが開いてでありドキュメントが呼び出し元のプロジェクトとは異なるプロジェクトによって所有されている場合はプロジェクトを開くエディターが別のプロジェクトからである警告が表示されます。  ファイルのウィンドウは現れます。  
  
3.  ドキュメントが開いていない場合も実行中のドキュメントの表にファイルの標準エディターを開くに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> のメソッド \(`OSE_ChooseBestStdEditor`\) を呼び出します。  
  
     メソッドを呼び出すとIDE では次のタスクを実行します :  
  
    1.  IDE ではエディターでファイルを開くことができそのための優先順位を確認するにはレジストリ エディター guidEditorType {} \/Extensions のキーを検索します。  
  
    2.  どのエディターでファイルを開くことができるかを確認したら IDE はIDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> を呼び出します。  エディターの <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> を呼び出し新しく開かれたドキュメントをに配置できるように IDE が必要な情報このメソッドはを実装します。  
  
    3.  最後に<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> などの通常の永続化のインターフェイスを使用してドキュメントを読み込みます。  
  
    4.  階層または階層の項目が使用できることを確認したら IDE が前にプロジェクト レベルのコンテキストの <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> のポインターを <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> のメソッド呼び出しで渡すするにはプロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> のメソッドを呼び出します。  
  
4.  エディターがプロジェクトのコンテキストを取得できるようにする場合はIDE でプロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> を呼び出すとIDE に <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> のポインターを返します。  
  
     この手順を実行するにはエディターにプロジェクトにはサービスができます。  
  
     ドキュメント ビューまたはドキュメントのビュー オブジェクトがウィンドウ フレームにを配置した場合オブジェクトはデータと <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> を呼び出して初期化します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [開く、プロジェクト項目を保存します。](../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: プロジェクトに固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 開いているドキュメントのエディターを開く](../extensibility/how-to-open-editors-for-open-documents.md)   
 [ファイルを開くコマンドを使用してファイルを表示します。](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)