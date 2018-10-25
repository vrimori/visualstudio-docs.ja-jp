---
title: '方法: 元に戻す管理の実装 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50af6d65ad98c15506c4f7b015634a44455cd0aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815210"
---
# <a name="how-to-implement-undo-management"></a>方法: 元に戻す管理の実装
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

元に戻すの管理に使用される主要なインターフェイスは<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>、環境によって実装されます。 元に戻す管理をサポートするには、実装元に戻す単位 (つまり、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>、複数の個々 のステップを含むことができます。  
  
 元に戻す管理を実装する方法は、エディターが複数のビューをサポートするかどうかどうかによって異なります。 各実装の手順は、次のセクションで詳細を示します。  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>エディターが 1 つのビューをサポートしている場合  
 このシナリオでと、エディターでは複数のビューはサポートされていません。 1 つだけのエディターと 1 つのドキュメントがあるし、元に戻すをサポートします。 次の手順を使用すると、元に戻す管理を実装します。  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>単一ビュー エディターの元に戻す管理をサポートするには  
  
1.  呼び出す`QueryInterface`上、`IServiceProvider`インターフェイスのウィンドウ フレームを`IOleUndoManager`、元に戻すマネージャーにアクセスするドキュメント ビュー オブジェクトから (`IID_IOLEUndoManager`)。  
  
2.  ビューはウィンドウ フレームに配置された、場合に、呼び出しに使用できること、サイトのポインターを取得します。`QueryInterface`の`IServiceProvider`します。  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>エディターが複数のビューをサポートしている場合  
 ドキュメントとビューの分離した場合は、ドキュメント自体に関連付けられている通常の 1 つの元に戻すマネージャーです。 すべての元に戻す単位は、ドキュメント データ オブジェクトに関連付けられている 1 つの元に戻すマネージャーに配置されます。  
  
 ドキュメント データ オブジェクトの呼び出しのうち 1 つであるビューごとに元に戻すマネージャーには、ビューのクエリではなく<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>を元に戻すマネージャーをインスタンス化するには、CLSID_OLEUndoManager のクラス識別子を指定します。 クラス識別子は、OCUNDOID.h ファイルで定義されます。  
  
 使用する場合<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>を元に戻すマネージャー インスタンスを作成するには、環境に、元に戻すマネージャーをフックする、次の手順を使用します。  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>環境に、元に戻すマネージャーをフックするには  
  
1. 呼び出す`QueryInterface`から返されるオブジェクトで<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>の`IID_IOleUndoManager`します。 ポインターを格納<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>します。  
  
2. 呼び出す`QueryInterface`で`IOleUndoManager`の`IID_IOleCommandTarget`します。 ポインターを格納<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
3. リレー、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>に格納されている呼び出し`IOleCommandTarget`StandardCommandSet97 コマンドを次のインターフェイス。  
  
   -   cmdidUndo  
  
   -   cmdidMultiLevelUndo  
  
   -   cmdidRedo  
  
   -   cmdidMultiLevelRedo  
  
   -   cmdidMultiLevelUndoList  
  
   -   cmdidMultiLevelRedoList  
  
4. 呼び出す`QueryInterface`で`IOleUndoManager`の`IID_IVsChangeTrackingUndoManager`します。 ポインターを格納<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>します。  
  
    ポインターを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>を呼び出す、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>メソッド。  
  
5. 呼び出す`QueryInterface`で`IOleUndoManager`の`IID_IVsLinkCapableUndoManager`します。  
  
6. 呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>、ドキュメントを実装する必要も、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient>インターフェイス。 ドキュメントが閉じられたときに呼び出す`IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`します。  
  
7. ドキュメントが閉じられたときに呼び出す`QueryInterface`で元に戻すマネージャー`IID_IVsLifetimeControlledObject`します。  
  
8. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> を呼び出す。  
  
9. 変更されたドキュメントをときに呼び出す<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>のマネージャーで、`OleUndoUnit`クラス。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>メソッドは、オブジェクトへの参照を解放する通常直後に、<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>します。  
  
   `OleUndoManager`クラスは、1 つの元に戻すスタックのインスタンスを表します。 したがって、undo または redo の追跡されているデータ エンティティごとに 1 つの元に戻すマネージャー オブジェクトがあります。  
  
> [!NOTE]
>  元に戻すマネージャー オブジェクトは、テキスト エディターに広範囲に使用される、中に、テキスト エディターの特定のサポートを持たない全般コンポーネントになります。 複数レベルの取り消しまたはやり直しをサポートする場合は、このオブジェクトを使用してこれを行うことができます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [方法: 元に戻すスタックをクリアする](../extensibility/how-to-clear-the-undo-stack.md)

