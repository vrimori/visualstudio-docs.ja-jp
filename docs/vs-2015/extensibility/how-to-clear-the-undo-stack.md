---
title: '方法: 元に戻すスタックをクリア |Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d445b4ce79dc2f048ee95c1a356863f1ed524dad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210289"
---
# <a name="how-to-clear-the-undo-stack"></a>方法: 元に戻すスタックをクリア
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

次の手順では、元に戻すスタックをクリアする方法について説明します。  
  
### <a name="to-clear-the-undo-stack"></a>元に戻すスタックをクリアするには  
  
1.  元に戻すスタックの使用をオフにする、 [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799)メソッド。 この例を次に示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [方法: 元に戻すの管理を実装する](../extensibility/how-to-implement-undo-management.md)

