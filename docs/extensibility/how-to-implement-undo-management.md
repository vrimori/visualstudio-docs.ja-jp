---
title: "方法: 元に戻す管理を実装 | Microsoft Docs"
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
  - "エディター [Visual Studio SDK] の従来の管理を元に戻す"
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: 元に戻す管理を実装
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

環境によって実装された Undo 管理に使用するプライマリ インターフェイスは<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> です。  元に戻す管理をサポートするには別の実装に単位 \(つまり複数のステップを含むことができる <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>。  
  
 実装方法を管理してエディターが複数のビューをサポートしているかどうかによって異なります。  各の実装の手順では次のセクションで詳しく説明します。  
  
## エディターが一つのビューをサポートします。ケース  
 このシナリオでは複数のビューをサポートしません。  1 台のエディターと 1 のドキュメントがあり元に戻す操作をサポートします。  元の管理を実装するには次の手順を使用します。  
  
#### 一つのビュー エディターの元に戻す管理をサポートします。  
  
1.  元 `IID_IOLEUndoManager` マネージャー \(\) にアクセスするドキュメントのビュー オブジェクトから `IOleUndoManager` のウィンドウ フレームの `IServiceProvider` のインターフェイスでは `QueryInterface`。  
  
2.  ビューではウィンドウ フレームにを配置すると`IServiceProvider` の `QueryInterface` を呼び出すために使用できるサイトのポインターを取得します。  
  
## エディターで複数のビューをサポートします。ケース  
 ドキュメントとビューの分離する場合通常はドキュメント自体に関連付けられた 1 個の元に戻す機能マネージャーがあります。  すべての元の単位はドキュメント データ オブジェクトに関連付けられた 1 個の元に戻す機能マネージャーに配置されます。  
  
 各ビューの 1 を持つ戻すマネージャーのクエリ ビューではなくオブジェクトはドキュメント データ CLSID\_OLEUndoManager のクラス ID を指定しているに戻すマネージャーをインスタンス化するに <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> を呼び出します。  クラス ID は OCUNDOID.h ファイルで定義されます。  
  
 独自の元に戻す機能マネージャーのインスタンスを作成するために <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> を使用するときに環境を戻すマネージャーをトラップするには次の手順を使用します。  
  
#### 環境を戻すマネージャーにフックする  
  
1.  `IID_IOleUndoManager` の <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> から返されるオブジェクトの `QueryInterface` を呼び出します。  <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> へのポインターを格納します。  
  
2.  `IID_IOleCommandTarget` の `IOleUndoManager` の呼び出し `QueryInterface`。  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> へのポインターを格納します。  
  
3.  次の StandardCommandSet97 コマンドの `IOleCommandTarget` に格納されたインターフェイスに <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> と <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> の呼び出しを中継で送信します :  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  `IID_IVsChangeTrackingUndoManager` の `IOleUndoManager` の呼び出し `QueryInterface`。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> へのポインターを格納します。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> のメソッドを呼び出すために <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> へのポインターを使用します。  
  
5.  `IID_IVsLinkCapableUndoManager` の `IOleUndoManager` の呼び出し `QueryInterface`。  
  
6.  または <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> のインターフェイスを実装する必要があるドキュメント内 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> を呼び出します。  文書を閉じると`IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` を呼び出します。  
  
7.  ドキュメントを閉じるときに`IID_IVsLifetimeControlledObject` の元に戻すマネージャーの呼び出し `QueryInterface`。  
  
8.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> を呼び出します。  
  
9. ドキュメントが変更された場合`OleUndoUnit` のクラスを含むマネージャーの呼び出し <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>。  <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> のメソッドはオブジェクトへの参照を解放 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> の直後には通常です。  
  
 `OleUndoManager` のクラスが一つの戻すスタックのインスタンスを表します。  したがって元に戻す操作またはやり直し操作のために追跡されるデータ エンティティに対して 1 回の元に戻す機能マネージャー オブジェクトがあります。  
  
> [!NOTE]
>  元のオブジェクト マネージャーはテキスト エディターで広く使用されていますがテキスト エディターの特定をサポートしていない汎用コンポーネントです。  複数のレベルに戻す操作またはやり直し操作をサポートするにはこれを行うためにこのオブジェクトを使用できます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [方法: 元に戻すスタックをクリアします](../extensibility/how-to-clear-the-undo-stack.md)