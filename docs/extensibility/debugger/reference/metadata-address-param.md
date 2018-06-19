---
title: METADATA_ADDRESS_PARAM |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2cc91ea41003f153a1b3910510f41bc032bf221
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125988"
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
 メソッドの ID、パラメーターは、一部です。  
  
 tokParam  
 パラメーターの ID です。  
  
 dwIndex  
 パラメーターの一覧で、パラメーターのインデックス。  
  
## <a name="remarks"></a>コメント  
 この構造体の共用体の一部である、 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)ときに構造体、`dwKind`のフィールド、`DEBUG_ADDRESS_UNION`構造に設定されている`ADDRESS_KIND_PARAM`(から値、 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列挙体)。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)