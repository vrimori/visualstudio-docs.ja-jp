---
title: IDebugContainerField |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a911fe64f397a3a671787db00877a07f5ed1ccaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537919"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugContainerField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcontainerfield)します。  
  
このインターフェイスは、シンボルまたはその他の記号または型のコンテナーである型を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーを実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイス。 このインターフェイスは、コンテナーを表すすべてのインターフェイスの基本クラスをもできます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 多くのインターフェイスの多くのメソッドは、このインターフェイスを返します。 使用してより専門的なインターフェイスがこのインターフェイスから取得できるこれはすべてのコンテナーの基本クラスであるため、 [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)します。 このようなインターフェイスに含まれる[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)、 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)、および[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|コンテナーのフィールドの列挙子を作成します。|  
  
## <a name="remarks"></a>Remarks  
 配列 (変数のコンテナー)、(メソッドおよび変数のコンテナー) のクラスおよびメソッド (パラメーターとローカル変数のコンテナー) は、コンテナーのすべての例を示します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

