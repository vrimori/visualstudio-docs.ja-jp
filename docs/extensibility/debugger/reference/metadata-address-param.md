---
title: METADATA_ADDRESS_PARAM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f91e8ddf00b191bd2574c3a360328fb00cb50960
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938069"
---
# <a name="metadataaddressparam"></a>METADATA_ADDRESS_PARAM
この構造体は、メソッドまたは関数のパラメーターを表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_PARAM {  
   _mdToken tokMethod;  
   _mdToken tokParam;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_PARAM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_PARAM {  
   public int  tokMethod;  
   public int  tokParam;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>用語  
 tokMethod  
 メソッドの ID パラメーターは一部です。  
  
 tokParam  
 パラメーターの ID。  
  
 dwIndex  
 パラメーターの一覧で、パラメーターのインデックス。  
  
## <a name="remarks"></a>Remarks  
 この構造体の共用体の一部は、 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)ときに構造体、`dwKind`のフィールド、`DEBUG_ADDRESS_UNION`構造に設定されている`ADDRESS_KIND_PARAM`(からの値、 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列挙型)。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)