---
title: IEnumDebugPropertyInfo2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc70944150a7dabe8d6925eb26005b5c3b2eaca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883981"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
このインターフェイスの列挙[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造体。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、特定のプロパティの情報を表すには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)特定のプロパティの子を表す、このインターフェイスを取得します。 呼び出す[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)特定のスタック フレームのプロパティを表す、このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugPropertyInfo2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|指定した数を取得[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列挙体シーケンス内の構造体。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|指定した数のスキップ[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列挙体シーケンス内の構造体。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|数を取得[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)列挙子内の構造体。|  
  
## <a name="remarks"></a>Remarks  
 一般に、プロパティは、名前、値、アドレス、および種類を含めることができます情報と関連付けられているプロパティのオブジェクトまたはスタック フレームに適切なその他の情報の階層です。 参照してください[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)の詳細。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)