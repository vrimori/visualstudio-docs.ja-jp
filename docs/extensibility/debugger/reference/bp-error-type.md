---
title: "BP_ERROR_TYPE |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ab0dc686c4d002733bf8501be042e33c500fb8e3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

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
  
 ブレークポイントのエラーの種類は、型と、重大度で構成されます。 ブレークポイント エラーの種類が型だけではない、つまり (たとえば、 `BPET_TYPE_ERROR`、) または重大度レベル (たとえば、 `BPET_SEV_GENERAL`) を単独で。 `BPET_GENERAL_WARNING``BPET_GENERAL_ERROR`警告およびエラーの一般的なブレークポイントの定義済みの値を指定します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
