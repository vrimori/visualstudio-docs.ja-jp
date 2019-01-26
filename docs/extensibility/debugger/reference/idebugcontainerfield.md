---
title: IDebugContainerField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb03d0adc7e7ff4eb02f29394afdd0f5c810c710
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988741"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
このインターフェイスは、シンボルまたはその他の記号または型のコンテナーである型を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーを実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイス。 このインターフェイスは、コンテナーを表すすべてのインターフェイスの基本クラスをもできます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 多くのインターフェイスの多くのメソッドは、このインターフェイスを返します。 使用してより専門的なインターフェイスがこのインターフェイスから取得できるこれはすべてのコンテナーの基本クラスであるため、 [QueryInterface](/cpp/atl/queryinterface)します。 このようなインターフェイスに含まれる[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)、 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)、および[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|コンテナーのフィールドの列挙子を作成します。|  
  
## <a name="remarks"></a>Remarks  
 配列 (変数のコンテナー)、(メソッドおよび変数のコンテナー) のクラスおよびメソッド (パラメーターとローカル変数のコンテナー) は、コンテナーのすべての例を示します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)