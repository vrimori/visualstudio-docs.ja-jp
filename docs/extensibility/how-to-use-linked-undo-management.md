---
title: '方法: リンクされた Undo 管理を使用して、|Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d65873ae68fe7446ddd265a3af17e694bd475465
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500421"
---
# <a name="how-to-use-linked-undo-management"></a>方法: リンクされた undo 管理の使用
リンク元に戻すには、ユーザーが同時に複数のファイルで同じの編集を元に戻すができます。 たとえば、ヘッダー ファイルと、Visual C ファイルなど、複数のプログラム ファイルのテキストの同時変更は、リンク元に戻すトランザクションです。 リンク元に戻す機能が、元に戻すマネージャーの環境の実装に組み込まれていると<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>この機能を操作することができます。 リンク元に戻すは元に戻すスタックの 1 つの undo 単位として扱われます一緒にリンクできる親元に戻す単位によって実装されます。 リンク元に戻すを使用する手順の詳細については、次のセクション。  
  
## <a name="to-use-linked-undo"></a>リンク元に戻すを使用するには  
  
1.  呼び出す`QueryService`で`SVsLinkedUndoManager`へのポインターを取得する`IVsLinkedUndoTransactionManager`します。  
  
2.  初期の親のリンクされた undo 単位を呼び出して作成<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>です。 これには、リンク元に戻すスタックにグループ化する元に戻すスタックのセットの開始位置を設定します。 `OpenLinkedUndo`メソッドも厳密なや非厳格にするリンクされた、元に戻すかどうかを指定する必要になります。 非厳格リンク元に戻す動作は、一部のリンクされた undo 兄弟付きドキュメントを閉じることができますを他のリンクされたままにしてくださいを元に戻す、スタック上の兄弟を意味します。 厳密なリンク元に戻す操作では、すべてのリンクされた undo 兄弟スタックがまとめてまたはまったく実行されませんがあることを指定します。 後続リンク元に戻すスタックを呼び出して追加[IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135)メソッド。  
  
3.  呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>を展開するすべての 1 つとして、リンク元に戻す単位のバックアップを作成します。  
  
    > [!NOTE]
    >  エディターでリンクされた undo 管理を実装するには、元に戻す管理を追加します。 リンクされた undo 管理の実装の詳細については、次を参照してください。[方法: 元に戻す管理を実装](../extensibility/how-to-implement-undo-management.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [方法: 元に戻す管理を実装](../extensibility/how-to-implement-undo-management.md)