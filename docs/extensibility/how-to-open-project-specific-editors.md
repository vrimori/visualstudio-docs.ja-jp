---
title: '方法: プロジェクトに固有のエディターを開く |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae2e634d36c13632619d01cc97d5726dc5576819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129046"
---
# <a name="how-to-open-project-specific-editors"></a>方法: プロジェクトに固有のエディターを開く
プロジェクトで開かれる項目のファイルは本質的に、そのプロジェクトの特定のエディターにバインドする場合、プロジェクトは、プロジェクト固有のエディターを使用してファイルを開く必要があります。 ファイルは、エディターを選択するため、IDE のメカニズムに委任することはできません。 たとえば、標準のビットマップ エディターを使用して、代わりには、プロジェクトに一意のファイル内の情報を認識する特定のビットマップ エディターを指定するのにこのプロジェクト固有のエディター オプションを使用できます。  
  
 IDE の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>メソッドによって、特定のプロジェクト ファイルが開かれることを決定する場合。 詳細については、次を参照してください。 [、開いているファイルのコマンドを使用してファイルを表示する](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)です。 次のガイドラインを使用して実装する、`OpenItem`メソッドに、プロジェクトをプロジェクトに固有のエディターを使用してファイルを開きます。  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>プロジェクトに固有のエディターを使用して OpenItem メソッドの実装  
  
1.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>メソッド (RDT_EditLock) をファイル (ドキュメント データ オブジェクト) が既に開いているかどうかを判断します。  
  
    > [!NOTE]
    >  ドキュメント データおよびドキュメント ビュー オブジェクトの詳細については、次を参照してください。[ドキュメント データとのカスタム エディターのドキュメント ビュー](../extensibility/document-data-and-document-view-in-custom-editors.md)です。  
  
2.  ファイルを既に開いている場合は、呼び出すことによって、ファイルを再び表面化、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>メソッドとの IDO_ActivateIfOpen の値を指定する、`grfIDO`パラメーター。  
  
     ファイルが開いていて、ドキュメントが、呼び出し元プロジェクト以外のプロジェクトによって所有されている、開いているエディターは、別のプロジェクトからのユーザーに、警告が表示されます。 [ファイル] ウィンドウが表示される、します。  
  
3.  テキスト バッファー (ドキュメント データ オブジェクト) が既に開いているして別のビューをアタッチする場合は、ユーザーは、そのビューをフック担当します。 プロジェクトから、表示 (ドキュメント ビュー オブジェクト) をインスタンス化するための推奨アプローチは次のとおりです。  
  
    1.  呼び出す`QueryService`上、<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>へのポインターを取得するサービス、<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>インターフェイスです。  
  
    2.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>メソッドをドキュメント ビュー クラスのインスタンスを作成します。  
  
4.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>メソッドをドキュメント ビュー オブジェクトを指定します。  
  
     このメソッドは、ドキュメント ウィンドウにドキュメント ビュー オブジェクトをサイトです。  
  
5.  いずれかに適切な呼び出しを行う、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>メソッドです。  
  
     この時点では、ビューでは、完全に初期化されを開く準備をする必要があります。  
  
6.  呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>メソッドを表示し、ビューを開きます。  
  
## <a name="see-also"></a>関連項目  
 [開くと、プロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: 標準のエディターを開く](../extensibility/how-to-open-standard-editors.md)   
 [方法: 開いているドキュメントのエディターを開く](../extensibility/how-to-open-editors-for-open-documents.md)