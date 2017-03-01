---
title: "IDebugContainerField |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7cf087725f8cfcb8ba53da739706ededcddb61c4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcontainerfield"></a>IDebugContainerField
このインターフェイスは、シンボルまたはその他のシンボルまたは型用のコンテナーである型を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーを実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイスです。 このインターフェイスは、また、コンテナーを表すすべてのインターフェイスの基本クラスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 多くのインターフェイスの多くのメソッドは、このインターフェイスを返します。 使用してより専門的なインターフェイスがこのインターフェイスから取得できるこれはすべてのコンテナーの基本クラスであるため、 [QueryInterface](/visual-cpp/atl/queryinterface)します。 このようなインターフェイスには、 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)、 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)、および[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 上のメソッドだけでなく、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|コンテナーのフィールドの列挙子を作成します。|  
  
## <a name="remarks"></a>コメント  
 配列 (変数のコンテナー)、(メソッドおよび変数のコンテナー) のクラスおよびメソッド (パラメーターおよびローカル変数のコンテナー) は、コンテナーのすべての例を示します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
