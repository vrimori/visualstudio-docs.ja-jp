---
title: '方法: 標準のエディターを開く |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fbc4c694dcaa39e61eef484f018204474e67dd7a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820346"
---
# <a name="how-to-open-standard-editors"></a>方法: 標準のエディターを開く
標準のエディターを開くと、ファイルのプロジェクトに固有のエディターを指定する代わりに、指定されたファイルの種類の標準エディターの特定の IDE を使用できます。  
  
 次の手順を実装する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>メソッド。 これにより、標準のエディターでプロジェクト ファイルが開きます。  
  
## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>標準のエディターで OpenItem メソッドを実装するには  
  
1.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>(`RDT_EditLock`) をドキュメント データ オブジェクトのファイルが既に開いているかどうかを判断します。  
  
2.  ファイルが既に開いている場合は、呼び出すことによって、ファイルを再び表面化、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>の値を指定して、メソッド`IDO_ActivateIfOpen`の`grfIDO`パラメーター。  
  
     ファイルが開かれていると、ドキュメントが、呼び出し元プロジェクトよりも、別のプロジェクトが所有するプロジェクトが開かれるエディターは、別のプロジェクトから警告を受信します。 [ファイル] ウィンドウに表示されるからです。  
  
3.  ドキュメントが開いていない場合、または実行中のドキュメントのテーブルではなく、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッド (`OSE_ChooseBestStdEditor`) ファイルの標準のエディターを開きます。  
  
     メソッドを呼び出すときに、IDE は、次のタスクを実行します。  
  
    1.  IDE のエディターのスキャン/{guidEditorType}]、[レジストリ エディターで拡張機能のサブキーは、ファイルを開くし、これを行うための優先順位が最も高い。  
  
    2.  エディターでファイルを開く IDE が決まりますが、IDE は呼び出し<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>します。 このメソッドのエディターの実装には、IDE を呼び出すに必要な情報が返されます。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>と新しく開かれたドキュメントのサイト。  
  
    3.  最後に、IDE は、通常の永続化インターフェイスを使用して、ドキュメントを読み込みます<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>します。  
  
    4.  IDE が以前階層または階層アイテムがあることを確認して場合、IDE によって呼び出さ<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>、プロジェクトをプロジェクト レベルのコンテキストを取得するメソッド<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>内で渡すへのポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>メソッドの呼び出し。  
  
4.  返す、 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> IDE を呼び出すと、IDE へのポインター<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>エディターがプロジェクトからのコンテキストを取得できるようにする場合は、プロジェクトにします。  
  
     この手順を実行するには、エディターにプロジェクトのプランの追加のサービスが使用できます。  
  
     呼び出してに、そのデータをドキュメント ビューまたはドキュメント ビュー オブジェクトがウィンドウ フレーム内に配置されて正常に場合、オブジェクトを初期化<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [開き、プロジェクト項目の保存](../extensibility/internals/opening-and-saving-project-items.md)   
 [方法: 開いているプロジェクト固有のエディター](../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 開いているドキュメントのエディターを開く](../extensibility/how-to-open-editors-for-open-documents.md)   
 [ファイルを開くコマンドを使用してファイルを表示します。](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)