---
title: "方法: リンクされた Undo 管理を使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - リンク元に戻す管理"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 方法: リンクされた Undo 管理を使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

リンク元はユーザーが同時に複数の同じファイルの編集操作を元に戻すことができます。  たとえば複数のプログラムのファイルにテキストの変更はヘッダー ファイルおよび Visual C\+\+ のファイルリンク元に戻すトランザクションです。  リンク元に戻す機能は環境にビルド マネージャーの実装に<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> ではこの機能を処理できるようにします。  リンク元に戻す操作は一つの単位として処理する別に戻すスタックをリンクできます。親の単位に実行されます。  リンク元に戻す操作を使用する手順は次のセクションで詳しく説明します。  
  
### を使用してリンク元に戻す  
  
1.  `IVsLinkedUndoTransactionManager` へのポインターを取得するに `SVsLinkedUndoManager` の `QueryService` を呼び出します。  
  
2.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> を呼び出して最初の親によってリンクされた Undo 単位を作成します。  これは一連のリンク元に戻すスタックにグループ化して戻すスタックの開始点を設定します。  `OpenLinkedUndo` のメソッドでリンク元に厳密または非厳密にするかどうかを指定する必要があります。  非正確な動作はリンクのリンク元に戻すの兄弟を使用してドキュメントの一部はそれらのスタックにもリンク元の兄弟を閉じ残すことを意味します。  元に戻す動作が厳密にリンクされている場合、リンクされた元に戻す兄弟スタックは、すべて同時に元に戻されるか、まったく元に戻されないかのどちらかになります。  [IOleUndoManager:: 追加](http://msdn.microsoft.com/library/windows/desktop/ms680135) のメソッドを呼び出して以降のリンクに戻すスタックを追加します。  
  
3.  呼び出し <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> は 1 文字としてリンク元に戻す単位をすべてロールバックします。  
  
    > [!NOTE]
    >  実装がエディターの管理はリンク元に戻す管理を追加します。  リンク元に戻す管理の実装の詳細については[方法 : 元の管理を実装します。](../extensibility/how-to-implement-undo-management.md) を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [方法: 元に戻す管理を実装](../extensibility/how-to-implement-undo-management.md)