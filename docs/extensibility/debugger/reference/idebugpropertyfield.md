---
title: IDebugPropertyField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1489e8ef7bf41274806d1d6b1b134b54268457cf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874207"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
このインターフェイスは、取得、およびプロパティを設定できるようにする機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーを実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)します。 このインターフェイスは、クラスのプロパティの概念をサポートする特殊化です。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用[QueryInterface](/cpp/atl/queryinterface)からこのインターフェイスを取得する、 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)インターフェイスの場合、 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)メソッドを返します。`FIELD_KIND_PROP`します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)と[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|プロパティを取得するメソッドを取得します。|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|プロパティを設定するメソッドを取得します。|  
  
## <a name="remarks"></a>Remarks  
 プロパティは、マネージ コードの概念であり、変数として扱われるメソッドを表します。 プロパティは、アンマネージの C++ ではありません。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)