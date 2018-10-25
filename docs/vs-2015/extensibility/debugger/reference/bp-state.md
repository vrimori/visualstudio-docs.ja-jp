---
title: BP_STATE |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: edc77eb589370df81c38027b7cb13a223aff1227
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863465"
---
# <a name="bpstate"></a>BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

バインドされたブレークポイントの存在を指定し、かどうかには有効に指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>メンバー  
 BPS_NONE  
 ブレークポイントが存在しないことを指定します。  
  
 BPS_DELETED  
 ブレークポイントが削除されたことを指定します。  
  
 BPS_DISABLED  
 ブレークポイントが無効になっていることを指定します。  
  
 BPS_ENABLED  
 ブレークポイントが有効になっていることを指定します。  
  
## <a name="remarks"></a>Remarks  
 返される、 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)

