---
title: DEBUG_CUSTOM_VIEWER |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23e1dc26a3f8d1031357715b39ce6e2d2e485d1f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906840"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
カスタム ビューアーを識別する構造またはビジュアライザーを入力します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwID  
 複数の閲覧者またはビジュアライザーで 1 つ実装を区別するために ID`GUID`します。  
  
 bstrMenuName  
 ドロップダウン メニューに表示されるテキスト。  
  
 bstrDescription  
 カスタム ビューアーまたは型のビジュアライザーが (あります null 値を使用しない場合) の説明。  
  
 guidLang  
 提供する式エバリュエーターの言語です。  
  
 guidVendor  
 提供する式エバリュエーターのベンダー。  
  
 bstrMetric  
 メトリックをカスタム ビューアーまたは型のビジュアライザー`CLSID`格納されます。  
  
## <a name="remarks"></a>Remarks  
 この構造体のリストがへの呼び出しによって返される、 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)メソッド (と拡張機能によって、 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)メソッド)。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)