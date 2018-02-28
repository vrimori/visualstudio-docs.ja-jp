---
title: "方法: 元に戻すスタックをクリア |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e2592ad8bbec0ddf87731d25f5c46c714a3336d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-the-undo-stack"></a>方法: 元に戻すスタックをクリアします
次の手順では、元に戻すスタックをクリアする方法について説明します。  
  
### <a name="to-clear-the-undo-stack"></a>元に戻すスタックをクリアするには  
  
1.  元に戻すスタックの使用をオフにする、 [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799)メソッドです。 この例を次に示します。  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>参照  
 [方法: 元に戻す管理の実装](../extensibility/how-to-implement-undo-management.md)