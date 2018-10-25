---
title: MACHINE_INFO_FIELDS |Microsoft Docs
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
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfcb00115ec4cdde5944ffb22d685cb23068bca6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929414"
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

特定のマシンを取得する情報の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>メンバー  
 MCIF_NAME  
 初期化/使用、`bstrName`フィールド構造にします。  
  
 MCIF_FLAGS  
 初期化/使用、`Flags`フィールド構造にします。  
  
 MIF_ALL  
 すべての構造でフィールドを初期化するか、/使用します。  
  
## <a name="remarks"></a>Remarks  
 これらの値が渡される、 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)メソッドのメンバーを示す、 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)構造体が初期化されるは。  
  
 使用されることも、`Fields`のメンバー、`MACHINE_INFO`フィールドが使用し、有効なときは、構造体。  
  
 これらのフラグは、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

