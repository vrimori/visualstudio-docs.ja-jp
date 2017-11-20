---
title: "DEBUG_CUSTOM_VIEWER |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_CUSTOM_VIEWER
helpviewer_keywords: DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc6f9655d2ec7bc588bcd673d5331f12f7fab262
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
カスタム ビューアーを識別する構造またはビジュアライザーを入力します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwID  
 複数のビューアーまたはいずれかによって実装されるビジュアライザーを区別するために ID`GUID`です。  
  
 bstrMenuName  
 ドロップダウン メニューに表示されるテキストです。  
  
 bstrDescription  
 カスタム ビューアーまたは型のビジュアライザー (する必要があります、null 値を使用しない場合) の説明です。  
  
 guidLang  
 提供する、式エバリュエーターの言語です。  
  
 guidVendor  
 提供する、式エバリュエーターのベンダー。  
  
 bstrMetric  
 メトリックをカスタム ビューアーまたは型のビジュアライザー`CLSID`格納されます。  
  
## <a name="remarks"></a>コメント  
 この構造体のリストがへの呼び出しによって返される、 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)メソッド (と拡張機能によって、 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)メソッド)。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)