---
title: "方法: 元に戻すスタックをクリアします | Microsoft Docs"
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
  - "エディター [Visual Studio SDK] レガシーの元に戻すスタックをクリアします。"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: 元に戻すスタックをクリアします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

次の手順ではをに戻すスタックをクリアする方法について説明します。  
  
### 戻すスタックを消去するには  
  
1.  戻すスタックの使用を消去する [IOleUndoManager:: DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) のメソッド。  次はこの一例です :  
  
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
  
## 参照  
 [方法: 元に戻す管理を実装](../extensibility/how-to-implement-undo-management.md)