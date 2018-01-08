---
title: "方法: 標準のエディターを開く |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dcf36dc8f4ef818a84719bc534a09ecf30baf76f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-standard-editors"></a>方法: 標準のエディターを開く
標準のエディターを開くときに、ファイルのプロジェクトに固有のエディターを指定する代わりに、指定されたファイルの種類の標準エディターの決定、IDE を使用できます。  
  
 実装するのには、次の手順を完了、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>メソッドです。 これにより、標準のエディターでプロジェクト ファイルが開きます。  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>標準のエディターを使用して OpenItem メソッドの実装  
  
1.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>(`RDT_EditLock`) をドキュメント データ オブジェクトのファイルが既に開いているかどうかを判断します。  
  
2.  ファイルを既に開いている場合は、呼び出すことによって、ファイルを再び表面化、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>の値を指定して、メソッド`IDO_ActivateIfOpen`の`grfIDO`パラメーター。  
  
     ファイルが開いていて、ドキュメントは、呼び出し元プロジェクトよりも、別のプロジェクトによって所有されて、プロジェクトが開かれるエディターが別のプロジェクトからは、警告を受信します。 [ファイル] ウィンドウが表示される、します。  
  
3.  ドキュメントが開いていない場合または実行中のドキュメント テーブルではなく、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッド (`OSE_ChooseBestStdEditor`) ファイルの標準のエディターを開きます。  
  
     メソッドを呼び出すときに、IDE には、次のタスクを実行します。  
  
    1.  IDE、エディターのスキャン/{guidEditorType}/エディターを決定するレジストリのサブキーを拡張機能は、ファイルを開くことができますされ、これを行うための最も高い優先順位を持ちます。  
  
    2.  IDE が決定したらエディターは、ファイルを開くことができます、IDE によって呼び出さ<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>です。 このメソッドのエディターの実装を呼び出して、IDE に必要な情報を返します<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>と新しく開かれたドキュメントをサイトです。  
  
    3.  最後に、IDE は、通常の永続化インターフェイスを使用して、ドキュメントを読み込みます<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>です。  
  
    4.  IDE が以前の階層または階層アイテムが使用できることを確認して場合、IDE によって呼び出さ<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>プロジェクトをプロジェクト レベルのコンテキストを取得するメソッド<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>戻るを渡してへのポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>メソッドの呼び出しです。  
  
4.  返す、 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> IDE を呼び出すと、IDE へのポインター<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>プロジェクトからコンテキストを取得するエディターを使用する場合、プロジェクトにします。  
  
     この手順を実行すると、エディターにプロジェクト オファーの追加のサービスことができます。  
  
     呼び出してに、そのデータをドキュメント ビューまたはドキュメント ビュー オブジェクトが正常にコンテナーに配置ウィンドウ フレームの場合、オブジェクトを初期化<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [開くと、プロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: プロジェクトに固有のエディターを開く](../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 開いているドキュメントのエディターを開く](../extensibility/how-to-open-editors-for-open-documents.md)   
 [ファイルを開くコマンドを使用したファイルの表示](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)