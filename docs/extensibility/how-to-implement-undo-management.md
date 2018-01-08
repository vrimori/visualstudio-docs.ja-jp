---
title: "方法: 元に戻す管理を実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cf57b24d81e193294f5ab90f71af07b229ec5839
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-undo-management"></a>方法: 元に戻す管理の実装
元に戻す管理に使用されるプライマリ インターフェイスは<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>は環境によって実装されています。 元に戻す管理をサポートするには、元に戻す単位を実装する (つまり、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>、複数の個別のステップを含むことができます。  
  
 元に戻す管理を実装する方法は、エディターが複数のビューをサポートするかどうかどうかによって異なります。 次のセクションでは、実装ごとに手順が詳しく説明します。  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>エディターが単一のビューをサポートしている場合  
 このシナリオで、エディターは、複数のビューをサポートしません。 1 つだけのエディターと 1 つのドキュメントがあるし、元に戻すをサポートします。 次の手順を使用すると、元に戻す管理を実装します。  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>単一ビュー エディターの元に戻す管理をサポートするには  
  
1.  呼び出す`QueryInterface`上、`IServiceProvider`のウィンドウ フレーム上のインターフェイス`IOleUndoManager`、アンドゥ マネージャーにアクセスするドキュメント ビュー オブジェクトから (`IID_IOLEUndoManager`)。  
  
2.  ビューがウィンドウ フレーム内に配置された、呼び出しを使用すると、サイトのポインターを取得`QueryInterface`の`IServiceProvider`します。  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>エディターが複数のビューをサポートしている場合  
 ドキュメントとビューの分離を使っている場合は、ドキュメント自体に関連付けられている通常の複数の undo マネージャーです。 ドキュメント データ オブジェクトに関連付けられた複数の undo マネージャーには、すべて元に戻す単位が配置されます。  
  
 ドキュメント データ オブジェクトの呼び出しのうち 1 つであるビューごとに、元に戻す manager のビューのクエリではなく<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>アンドゥ マネージャーのインスタンスを作成するには、CLSID_OLEUndoManager のクラス識別子を指定します。 クラス識別子は、OCUNDOID.h ファイルで定義されます。  
  
 使用する場合<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>undo マネージャー インスタンスを作成するには、環境に、元に戻すマネージャーをフックする、次の手順を使用します。  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>環境に、元に戻すマネージャーをフックするには  
  
1.  呼び出す`QueryInterface`から返されたオブジェクト<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>の`IID_IOleUndoManager`します。 ポインターを格納<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>です。  
  
2.  呼び出す`QueryInterface`で`IOleUndoManager`の`IID_IOleCommandTarget`します。 ポインターを格納<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
3.  リレー、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>に格納されている呼び出し`IOleCommandTarget`StandardCommandSet97 コマンドを次のインターフェイス。  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  呼び出す`QueryInterface`で`IOleUndoManager`の`IID_IVsChangeTrackingUndoManager`します。 ポインターを格納<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>です。  
  
     ポインターを使用して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>を呼び出して、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>メソッドです。  
  
5.  呼び出す`QueryInterface`で`IOleUndoManager`の`IID_IVsLinkCapableUndoManager`します。  
  
6.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>、ドキュメントを実装する必要も、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient>インターフェイスです。 ドキュメントが閉じられたときに呼び出す`IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`です。  
  
7.  ドキュメントが閉じられたときに呼び出す`QueryInterface`の元に戻すマネージャー`IID_IVsLifetimeControlledObject`です。  
  
8.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> を呼び出す。  
  
9. 変更を加えられた、ドキュメント、ときに呼び出す<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>のマネージャーで、`OleUndoUnit`クラスです。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>メソッドを保持、オブジェクトへの参照を解放する通常直後に、<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>です。  
  
 `OleUndoManager`クラスは、単一の元に戻すスタック インスタンスを表します。 したがって、元に戻す/やり直しの追跡されているデータ エンティティごとの 1 つの undo マネージャー オブジェクトがあります。  
  
> [!NOTE]
>  元に戻すマネージャー オブジェクトは、テキスト エディターに広範囲に使用される、テキスト エディターの特定のサポートがないコンポーネントの一般的な勧めします。 複数レベルの取り消しまたはやり直しをサポートする場合は、このオブジェクトを使用してこれを行うことができます。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [方法: 元に戻すスタックをクリアします](../extensibility/how-to-clear-the-undo-stack.md)