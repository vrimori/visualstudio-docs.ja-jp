---
title: BUILT_TYPE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0955ca40e136e5b89f105430f3dd887b66f25a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853312"
---
# <a name="builttype"></a>BUILT_TYPE
この構造体には、メタデータから取得したフィールドの種類に関する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```csharp  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 ulAppDomainID  
 シンボルが元のアプリケーションの ID。 これは、アプリケーションのインスタンスを一意に識別するに使用されます。  
  
 guidModule  
 このフィールドが含まれるモジュールの GUID です。  
  
 pUnderlyingField  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)この組み込みのフィールドに関連付けられている基になるフィールドを識別するオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 共用体の一部としてこの構造体が表示されます、 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)ときに構造体、`dwKind`のフィールド、`TYPE_INFO`構造に設定されている`TYPE_KIND_BUILT`(からの値、 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列挙型)。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)