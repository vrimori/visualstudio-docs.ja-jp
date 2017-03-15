---
title: "方法: プロジェクトに固有のエディターを開く | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクトの種類のプロジェクトに固有のエディターを開く"
  - "プロジェクトに固有のエディターを開くエディター [Visual Studio SDK]"
  - "プロジェクト [Visual Studio SDK] フォルダーを開く"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 方法: プロジェクトに固有のエディターを開く
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロジェクト項目によって開かれたファイルにはプロジェクトに固有のエディター主にバインドされている場合プロジェクト固有のエディターを使用してファイルを開く必要があります。  ファイルにはエディターを選択するための IDE 機能に代行させることはできません。  たとえば標準ビットマップ エディターを使用する代わりにプロジェクトに固有のファイルの情報を認識する特定のビットマップ エディターを指定する場合はこのプロジェクト固有のエディター オプションを使用できます。  
  
 IDE ではプロジェクト ファイルで開く必要がある場合に <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> のメソッドを呼び出します。  詳細については、「[ファイルを開くコマンドを使用してファイルを表示します。](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)」を参照してください。  `OpenItem` のメソッドをプロジェクトに固有のエディターでプロジェクト ファイルが開きますを持つように実行するには次のガイドラインを使用します。  
  
### プロジェクト固有のエディターで OpenItem のメソッドを実装します。  
  
1.  ドキュメント データ ファイル \(オブジェクト\) が開いているかどうかを調べるに <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> のメソッド \(RDT\_EditLock\) を呼び出します。  
  
    > [!NOTE]
    >  ドキュメント データとドキュメントのビュー オブジェクトの詳細については[ドキュメント データとカスタム エディターでドキュメント ビュー](../extensibility/document-data-and-document-view-in-custom-editors.md) を参照してください。  
  
2.  ファイルが既に開いている場合 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> のメソッドを呼び出して`grfIDO` のパラメーターに IDO\_ActivateIfOpen の値を指定してファイルに新しい表紙を付けます。  
  
     ファイルが開いてでありドキュメントが呼び出し元のプロジェクト以外のプロジェクトによって所有されている場合警告が開かれているエディターが別のプロジェクトからのあるユーザーに表示されます。  ファイルのウィンドウは現れます。  
  
3.  テキスト バッファー \(ドキュメント\) データ オブジェクトが既に開いて次のように別のビューをアタッチするにはされているビューをフックする必要があります。  プロジェクトのドキュメントのビュービュー \(\) オブジェクトをインスタンス化する代わりに推奨される方法は次のとおりです。:  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> インターフェイスへのポインターを取得 <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> サービスの呼び出し `QueryService`。  
  
    2.  ドキュメントのビュー クラスのインスタンスを作成するに <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> のメソッドを呼び出します。  
  
4.  ドキュメントのビュー オブジェクトを指定する <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> のメソッドを呼び出します。  
  
     このメソッドはドキュメント ウィンドウのドキュメントのオブジェクトで配置します。  
  
5.  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> または <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> のメソッドに適切な呼び出しを実行します。  
  
     この時点でビューは完全に初期化して開くために完了する必要があります。  
  
6.  ビューを表示し開くに <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> のメソッドを呼び出します。  
  
## 参照  
 [開く、プロジェクト項目を保存します。](../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: 標準のエディターを開く](../extensibility/how-to-open-standard-editors.md)   
 [方法: 開いているドキュメントのエディターを開く](../extensibility/how-to-open-editors-for-open-documents.md)