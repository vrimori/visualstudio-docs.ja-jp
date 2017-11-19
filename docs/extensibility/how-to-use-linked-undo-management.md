---
title: "方法: リンクされた Undo 管理を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05e10305f7e4c243f799cfe33d4d9b86418eed86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-linked-undo-management"></a>方法: リンクされた Undo 管理を使用
リンク元に戻すには、ユーザーが同時に複数のファイルで同じ編集の取り消しができます。 たとえば、ヘッダー ファイルと、Visual C ファイルなど、複数のプログラム ファイルのテキストの同時変更は、リンクされた undo トランザクションです。 リンク元に戻す機能が元に戻す manager の環境の実装に組み込まれていると<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>この機能を操作することができます。 リンク元に戻すは、単一の元に戻す単位として扱われますを同時に元に戻すスタックをリンクできる親元に戻す単位によって実装されます。 リンク元に戻すを使用する手順については、次のセクションで詳しく説明します。  
  
### <a name="to-use-linked-undo"></a>リンク元に戻すを使用するには  
  
1.  呼び出す`QueryService`で`SVsLinkedUndoManager`へのポインターを取得する`IVsLinkedUndoTransactionManager`です。  
  
2.  呼び出すことによって、初期の親リンク元に戻す単位を作成する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>です。 これは、リンク元に戻すスタックにグループ化する元に戻すスタックのセットの開始位置を設定します。 `OpenLinkedUndo`メソッドは、リンク元に戻す strict または非厳格にするかどうかを指定する必要があります。 非厳格リンク元に戻す操作は、リンク元に戻す兄弟付きドキュメントのいくつか閉じることができ、もう一方のリンクのままにして、スタック上の兄弟元に戻すことを意味します。 厳密なリンクの元に戻す操作では、元に戻すかまったくないすべてのリンクされた undo 兄弟スタックがあることを指定します。 後続のリンクを元に戻すスタックを呼び出す追加[IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135)メソッドです。  
  
3.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>を以前のバージョンすべての 1 つとしてリンクされた undo ユニットをバックアップします。  
  
    > [!NOTE]
    >  エディターでリンクされた undo 管理を実装するには、元に戻す管理を追加します。 リンク元に戻す管理の実装の詳細については、次を参照してください。[する方法: 元に戻す管理を実装](../extensibility/how-to-implement-undo-management.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [方法: 元に戻す管理の実装](../extensibility/how-to-implement-undo-management.md)