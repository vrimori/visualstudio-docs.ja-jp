---
title: BP_ERROR_TYPE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676ec19fec1406d85e6a7d9e66865b2794f72aa6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103007"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
ブレークポイントのエラーの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>メンバー  
 BPET_NONE  
 ブレークポイントのエラーがないを指定します。  
  
 BPET_TYPE_WARNING  
 警告スタイル ブレークポイント エラーを指定します。  
  
 BPET_TYPE_ERROR  
 エラーのスタイル ブレークポイント エラーを指定します。  
  
 BPET_SEV_HIGH  
 重要度の高いブレークポイント エラーを指定します。  
  
 BPET_SEV_GENERAL  
 中重要度ブレークポイント エラーを指定します。  
  
 BPET_SEV_LOW  
 ブレークポイントの重要度の低いエラーを指定します。  
  
 BPET_TYPE_MASK  
 マスク スタイル ブレークポイント エラーを指定します。  
  
 BPET_SEV_MASK  
 重大度マスク スタイル ブレークポイント エラーを指定します。  
  
 BPET_GENERAL_WARNING  
 一般的な型の警告ブレークポイント エラーを指定します。  
  
 BPET_GENERAL_ERROR  
 一般的なエラー スタイルのブレークポイントのエラーを指定します。  
  
 BPET_ALL  
 すべてのブレークポイント エラーの種類を指定します。  
  
## <a name="remarks"></a>コメント  
 これらの値は、ビットごとと組み合わせること`OR`用に使用されると、`dwType`のメンバー、 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)構造体。 パラメーターとして渡される、 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)メソッドです。  
  
 ブレークポイントのエラーの種類は、型と、重大度で構成されます。 ブレークポイント エラーの種類が型だけではない、つまり (たとえば、 `BPET_TYPE_ERROR`、) または重大度レベル (たとえば、 `BPET_SEV_GENERAL`) を単独で。 `BPET_GENERAL_WARNING` `BPET_GENERAL_ERROR`警告およびエラーの一般的なブレークポイントの定義済みの値を指定します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)